# books
#### 一些前端工具书
;

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta HTTP-EQUIV="pragma" CONTENT="no-cache">
	<meta HTTP-EQUIV="Cache-Control" CONTENT="no-cache, must-revalidate">
	<meta HTTP-EQUIV="expires" CONTENT="0">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Title</title>
    <link href="./css/iconfont/iconfont.css" rel="stylesheet">
	<link href="./css/evaluation.css?v=20211208" rel="stylesheet">
	<!-- 埋码 -->
	<script src="./js/buriedCode.js"></script>
</head>
<body>
	<div class="wrapper" id="wrapper">
		<div class="loadingClass" id="loadingId" data-flag="true">
			<img src="./img/load.gif" width="24px" style="position: absolute;left: 50%;top: 50%;">

		</div>
	    <div class="popup" id="evaluationPopup" data-flag="false">

	        <div class="header">
				<span class="headerSpan">
					<i class="closeIcon iconfont">&#xe612;</i>
	            <span class="title" data-i18n-text="toolEvaluation.plsComment"></span>
	            <span class="title" id="showToolNameTitle"></span>
	            <span class="title" data-i18n-text="toolEvaluation.plsCommentAfter"></span>
				</span>

	        </div>
	        <div class="body">

	        	<p class="overall notEmpty" data-i18n-text="toolEvaluation.overall"></p>

	            <div class="score-box clearfix">
	                <div class="starBox">
	                	<div class="starShow">
	                		<div data-i18n-text="toolEvaluation.feature"></div>
		                	<div id="features"></div>
		                    <div class="starToWords"></div>
	                	</div>
	                	<p class="toolTips" data-i18n-text="toolEvaluation.toolTip.features"></p>
	                </div>

	                <div class="starBox">
	                	<div  class="starShow">
	                		<div data-i18n-text="toolEvaluation.performance"></div>
		                	<div id="performance"></div>
		                    <div class="starToWords"></div>
		                </div>
		                <p class="toolTips" data-i18n-text="toolEvaluation.toolTip.performance"></p>
	                </div>

	                <div class="starBox">
	                	<div class="starShow">
	                		<div data-i18n-text="toolEvaluation.easeOfUse"></div>
		                	<div id="easeOfUse"></div>
		                    <div class="starToWords"></div>
	                	</div>
	                	<p class="toolTips" data-i18n-text="toolEvaluation.toolTip.easeOfUse"></p>
	                </div>
	            </div>

	            <div class="willBox">
                    <div class="opinionLabel notEmpty" data-i18n-text="toolEvaluation.useingToolContinue"></div>
                    <div class="opinionShow">
                    	<span data-i18n-text="toolEvaluation.absolutelyNo"></span>
                    	<span data-i18n-text="toolEvaluation.absolutelyYes"></span>
                    </div>
                    <ul id="willLevelList">
                    	<li data-title="1"><span class="fakeTitle">1</span>1</li>
                    	<li data-title="2"><span class="fakeTitle">2</span>2</li>
                    	<li data-title="3"><span class="fakeTitle">3</span>3</li>
                    	<li data-title="4"><span class="fakeTitle">4</span>4</li>
                    	<li data-title="5"><span class="fakeTitle">5</span>5</li>
                    	<li data-title="6"><span class="fakeTitle">6</span>6</li>
                    	<li data-title="7"><span class="fakeTitle">7</span>7</li>
                    	<li data-title="8"><span class="fakeTitle">8</span>8</li>
                    	<li data-title="9"><span class="fakeTitle">9</span>9</li>
                    	<li data-title="10"><span class="fakeTitle">10</span>10</li>
                    </ul>
                </div>
                <div class="opinionBox scrollStyle" style="position:relative;">
                    <div class="opinionLabel opinionComentLabel" data-i18n-text="toolEvaluation.opinion"></div>
                    <div class="keyListContainer">
	                    <div>
		                    <div class="keywordLabel notEmpty" data-i18n-text="toolEvaluation.keywordLabel"></div>
		                    <div class="changeKeywords">
		                        <span class="changeIcon"></span>
			                    <span  class="changeText" data-i18n-text="toolEvaluation.changeLabel"></span>
		                    </div>
	                    </div>
	                    <div class="keyWordsContent clearfix">
	                    </div>
                    </div>
                    <div class="textIptBox">
                    	<div id="selectLabelBox" class="clearfix"></div>
                    	<div style="position:relative;width: 412px;">
	                        <textarea id="opinion" wrap="soft" autocomplete="off" spellcheck="false" data-i18n-placeholder="toolEvaluation.opinionTip" rows="4" maxlength="500"></textarea>
                        </div>
                    </div>
                    <span id="limit500">0/500</span>
                </div>
                <div class="anonymousBox">
                	<div>
                		<i id="isAnonymous" class="iconfont"></i>
                		<span class="smallSize" data-i18n-text="toolEvaluation.submitAnonymous"></span>
                	</div>
                </div>

	            <div class="bottom-box">
					<button id="cancelBtn" data-i18n-text="toolEvaluation.cancelBtn"></button>
	                <button id="submitBtn" data-i18n-text="toolEvaluation.submitBtn"></button>
	            </div>

	        </div>
	    </div>

	    <div id="evaluationSuccessPop" data-flag="true">
	    	<i class="closeIcon"></i>
	    	<div class="successContent">
				<img src="./img/success.png" class="successTnankWordsImg"/>
	    		<p class="successTnankWords" data-i18n-text="toolEvaluation.thanksWords"></p>
	    		<button id="successDoneBtn" data-i18n-text="toolEvaluation.prize.close"></button>
	    	</div>
	    </div>
		<div id="acquireMedalPop" data-flag="true">
			<div id="autoclosepart">
				<span id="countdown"></span>s
				<span data-i18n-text="toolEvaluation.close"></span>
				<img id="medalCloseBtn" class="medal-close-btn" src="./img/autoclose.png" alt="" />
			</div>
			<div class="dialog-medal">
				<img id="dialogMedaltip" class="dialog-medal-tip"
                    src="./img/new_medal_tip.png" alt="">
				<img id="dialogMedaltipEn" class="dialog-medal-tip"
                    src="./img/new_medal_tip_en.png" alt="">
                <img id="dialogMedalImg" class="dialog-medal-img"
                    src="" alt=""/>
                <div id="medalName" class="dialog-medal-name"></div>
            </div>
            <p id="getMedalTime" class="dialog-medal-rules"></p>
            <p id="levelSlogan" class="dialog-medal-slogans"></p>
            <button id="acquireMedalBtn" class="button-tips" data-i18n-text="toolEvaluation.iacquire"></button>
            <button id="goViewMedals" class="button-tips" data-i18n-text="toolEvaluation.gotoview"></button>
            <p id="hasMoreMedals" class="dialog-medal-morerules" data-i18n-text="toolEvaluation.getmoremedals"></p>
	    </div>
	</div>

<script type="text/javascript" src="/s3/jquery.min.3.6.0.js"></script>
<script type="text/javascript" src="./js/layer.js"></script>
<script type="text/javascript" src="/s3/jquery.i18n.properties-min-1.0.9.js"></script>
<script type="text/javascript" src="./js/crsfcookie.js?v=20220630"></script>
<script type="text/javascript" src="./js/evaluation.js?v=20220420"></script>
<script>
	window.hwa&&window.hwa('trackPageView','P480344891F2BF2',{data:{page_hierarchy:'c:{GTS服务工具市场}g:{评价埋码}f:{追加评价}',reserver_v_1:'DongGuan',reserver_v_2: 'com.huawei.gtstools'}});
</script>

</body>
</html>
