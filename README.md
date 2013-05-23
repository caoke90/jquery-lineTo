jquery-lineTo author:caoke qq:914890674
=============

//author:caoke qq:914890674
(function($){
	$.fn.extend({
		//两点之间相连
		lineTo:function(where){
			var begin=$(this).position();
			var end=$(where).position();
			
			//两个点
			var a1=new Vec2(begin.left,begin.top)
			var a2=new Vec2(end.left,end.top)
			
			//向量
			var b1=a2.sub(a1).scale(1/20);
			
			//箭点
			var c1=a2.sub(b1).rotate(a2,Math.PI/4);
			var c2=a2.sub(b1).rotate(a2,-Math.PI/4);
			
			var minx=Math.min(a1.x,a2.x,c1.x,c2.x);
			var miny=Math.min(a1.y,a2.y,c1.y,c2.y);
			var maxx=Math.max(a1.x,a2.x,c1.x,c2.x);
			var maxy=Math.max(a1.y,a2.y,c1.y,c2.y);
			var width=maxx-minx;
			var height=maxy-miny;
			
			var paper = Raphael(minx,miny,width,height)
			//连线
			paper.path("M"+(a1.x-minx)+","+(a1.y-miny)+"L"+(a2.x-minx)+","+(a2.y-miny))
			//箭头
			paper.path("M"+(c1.x-minx)+","+(c1.y-miny)+"L"+(a2.x-minx)+","+(a2.y-miny)+"L"+(c2.x-minx)+","+(c2.y-miny))
			this.removepaper=function(){paper.remove()}
			return this;
		}
	})
})(jQuery)

$(function(){
	$(".block").eq(1).lineTo(".end")
	$(".block").eq(2).lineTo(".end")
	$(".end").lineTo($(".block").eq(2))
})
		
