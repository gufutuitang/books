# books
#### 一些前端工具书
;
(function (win, doc) {

	var baseUrl = (win.location.protocol == "https:" ? "https:" : "http:");
	var iframe = document.querySelector('#toolEvPop'),
		evaluationCallback;
	win.openToolEvaluationPopup = function (callback, obj) {
		// 不同环境更换参数（test、beta、pro）
		obj['mode'] = 'test'

		evaluationCallback = callback;
		var isEn = obj.isEn || false;
		var toolPlatForm = obj.toolPlatForm;
		var toolId = obj.toolId;
		var mode = obj.mode;
		var reqProtocolLink = window.top.location.origin;
		var curProtocol = window.location.protocol;
		var evaluator = obj.evaluator;
		var keywordFlag = (obj.keywordFlag == "undefined" || obj.keywordFlag == undefined) ? true : obj.keywordFlag; //不传时默认为true
		var keywordDisplayRule = obj.keywordDisplayRule || 1; //不传时默认为1,按照评价次数+创建时间排序

		window.sessionStorage.setItem("appId", obj.appId);
		window.sessionStorage.setItem("appKey", obj.appKey);
		window.sessionStorage.setItem("reqProtocol", obj.reqProtocol);
		window.sessionStorage.setItem("host", obj.host);
		window.sessionStorage.setItem("projectPath", obj.projectPath);
		window.sessionStorage.setItem("reqProtocolLink",reqProtocolLink);

		if (!iframe) {
			iframe = doc.createElement('iframe');
			iframe.style.cssText = "position:fixed;width:100%;height:100%;left:0px;top:0px;border:none;z-index:9999;display:block;";
			iframe.setAttribute('id', 'toolEvPop');
		}
		iframe.style.display = 'none';
		var param = '/evaluation-master/starRate/starRate.html?isEn=' + isEn + '&toolPlatForm=' + toolPlatForm + '&mode=' + mode + '&toolId=' + toolId + '&evaluator=' + evaluator + '&keywordFlag=' + keywordFlag + '&keywordDisplayRule=' + keywordDisplayRule;
		if(Object.prototype.hasOwnProperty.call(obj, "module")) {
			var paramModuleUrl = encodeURIComponent(encodeURIComponent(obj.module.url));
			obj.module.url = paramModuleUrl;
			param += '&moduleId=' + obj.module.id + '&moduleName=' + encodeURIComponent(encodeURIComponent(obj.module.name)) + '&moduleURL=' + paramModuleUrl;
		}
		param += '&param=' + encodeURIComponent(encodeURIComponent(JSON.stringify(obj)));
		iframe.src = obj.projectPath;
		iframe.src += param;
		if (iframe.attachEvent) {
			iframe.attachEvent("onload", function () { // IE
				doc.getElementById('toolEvPop').contentWindow.postMessage(obj, curProtocol+obj.projectPath);
			});
		} else {
			iframe.onload = function () { // 非IE
				doc.getElementById('toolEvPop').contentWindow.postMessage(obj, curProtocol+obj.projectPath);
			};
		}

		doc.body.appendChild(iframe);
	}
	win.closeToolEvaluationPopup = function (flag, content) {
		iframe.style.display = 'none';
		if (content && content['keyCommentIds']) {
			content['keyCommentIds'] = content.keyCommentIds.join(',')
		}
		if (evaluationCallback) {
			evaluationCallback(flag, content);
		}
	}
	win.addEventListener('message', function (e) {
		if (e.data && e.data.from === 'toolEvaluation') {
			win.closeToolEvaluationPopup(e.data.flag, e.data.info);
		} else if (e.data.from === 'openToolEvaluation') {
			iframe.style.display = 'block';
		}
	}, false);

})(window, window.document);
