jquery-lineTo author:caoke qq:914890674
=============

//两点之间相连箭头效果

$(function(){
	$(".block").eq(1).lineTo(".end")
	$(".block").eq(2).lineTo(".end")
	$(".end").lineTo($(".block").eq(2))
})
	
