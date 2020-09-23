<div align="center">

## Cross Fading News Ticker


</div>

### Description

A new approach to displaying a news ticker. This script will smoothly fade one news headline in to another. Works on IE,NS4&NS6
 
### More Info
 
Enter your ticker items/news headlines into the JavaScript array (NewsArray) at the top of the code.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Nick Radford](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/nick-radford.md)
**Level**          |Intermediate
**User Rating**    |4.6 (195 globes from 42 users)
**Compatibility**  |
**Category**       |[Graphics](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics__2-75.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/nick-radford-cross-fading-news-ticker__2-3065/archive/master.zip)





### Source Code

```
<html>
<head>
<title>Cross Fading News Ticker</title>
<style>
<!--
a{text-decoration:none;}
-->
</style>
<script language="JavaScript">
<!--
//Cross Fading News Ticker - Copyright (c) 2002, Nick Radford
//Use this script as you want... though give me credit for it!
NewsDelay=3000		//Time each story is displayed for
NewsFadeDelay=1000	//Time taken to fade from one story to the next
NewsFont='Arial'	//Ticket font family
NewsFontSize='4'	//Ticket font size
NewsTextColor=new Array("#000000","#111111","#222222","#333333","#444444","#555555","#666666","#777777","#888888","#999999","#aaaaaa","#bbbbbb","#cccccc","#dddddd","#eeeeee","#ffffff")
NewsStory=0		//Working Variable
LastNewsStory=0		//Working Variable
NewsColor=0		//Working Variable
NewsArray=new Array(
	'Cross Fading News Ticker. <br>Copyright &copy; 2002, Nick Radford' , 'http://www.URL1.com',
	'Place any text you want into the JavaScript array at the top of this script' , 'http://www.URL2.com',
	'And this script will smoothly fade from one text entry...' , 'http://www.URL3.com',
	'Into the next one..!' , 'http://www.URL4.com',
	'You can also define hyperlinks for each ticker entry' , 'http://www.URL5.com',
	'Dont forget... <br>If you like this script<br>vote for me..!' , 'http://www.URL6.com',
	'')
function DisplayNews(){
	LastNewsStory=NewsStory
	NewsStory++; if( NewsStory>(Math.floor(NewsArray.length/2)) ){NewsStory=1}
	FadeNews()
}
function FadeNews(){
	if (NewsColor<(NewsTextColor.length)/2){var NewsLayer=1}
	else {var NewsLayer=2}
	//Old Story
	if (LastNewsStory>0){
		var NewsText = '<a href="'+ NewsArray[(LastNewsStory-1)*2+1] +'"><font color="'+ NewsTextColor[NewsColor] +'" face="'+ NewsFont +'" size="'+ NewsFontSize +'">'+ NewsArray[(LastNewsStory-1)*2] +'</font></a>'
			if(document.layers){ document.eval('newslayer'+(3-NewsLayer)).document.write(NewsText); document.eval('newslayer'+(3-NewsLayer)).document.close() }//NN4
			if(document.all){ eval('newslayer'+(3-NewsLayer)).innerHTML=NewsText }//IE
			if(!document.all && document.getElementById){ document.getElementById('newslayer'+(3-NewsLayer)).innerHTML=NewsText }//NN6
	}
	//New Story
		var NewsText = '<a href="'+ NewsArray[(NewsStory-1)*2+1] +'"><font color="'+ NewsTextColor[(NewsTextColor.length)-NewsColor-1] +'" face="'+ NewsFont +'" size="'+ NewsFontSize +'">'+ NewsArray[(NewsStory-1)*2] +'</font></a>'
			if(document.layers){ document.eval('newslayer'+NewsLayer).document.write(NewsText); document.eval('newslayer'+NewsLayer).document.close() }//NN4
			if(document.all){ eval('newslayer'+NewsLayer).innerHTML=NewsText }//IE
			if(!document.all && document.getElementById){ document.getElementById('newslayer'+NewsLayer).innerHTML=NewsText; }//NN6
	NewsColor++
	if (NewsColor>=NewsTextColor.length){ NewsColor=0; setTimeout('DisplayNews()',NewsDelay) }
	else { setTimeout('FadeNews()',NewsFadeDelay/NewsTextColor.length) }
}
//-->
</script>
</head>
<body bgcolor="#ffffff" onload="DisplayNews()">
	<div id="newslayer1" style="position:absolute; left:20; top:20; width:300; height:200; z-index:1; visibility:visible;"> </div>
	<div id="newslayer2" style="position:absolute; left:20; top:20; width:300; height:200; z-index:2; visibility:visible;"> </div>
</body>
</html>
```

