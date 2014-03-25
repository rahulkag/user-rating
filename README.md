

 Create by Rahul kag 6:19 PM 3/11/2014
 for more dtls - contact kag.rahul@gmail.com

    ;(function($) { 
    $.fn.myRating = function( options  ) {
        /* default settings */
        var settings = $.extend({
            readonly   : 'true', // true for static rating only and false for the clickable star.
            score      : '0',      // total score of item 
            userscore  : '0',      // ratedby user 
            count      : '',     // rating count means no of user rated   
            size       : 'medium',  // size if star large or medium currently no option for small
            click      : function(){}   /// default function for click
        }, options);
        
       return this.each( function() {
           //var score = this.getAttribute("data-score");
           //var userscore = this.getAttribute('data-user-score');
           //alert( settings.size );
           var that  = this,
                score        = settings.score,
                userScore    = settings.userscore,
                ratingcount  = settings.count ,
                starsize     = settings.size.toUpperCase(),
                _starSize, _staticWidth, _userWidth;            
             var ratingdiv = $(document.createElement('div')),
                 ul        = $(document.createElement('ul')),
                 sli       = $(document.createElement('li')),
                 uli       = $(document.createElement('li'));
           
            ratingdiv.addClass('myrating').addClass( starsize );
            ul.addClass("star-ul").appendTo(ratingdiv);            
            sli.addClass('all-rating-li').appendTo(ul);
            uli.addClass('user-rating-li').appendTo(ul);
           // adding rating count 
           if(ratingcount){
               if(typeof ratingcount !="" || typeof ratingcount != "0" || typeof ratingcount != "undefined" ){
                   var rcount  = $(document.createElement('span')).addClass( 'rating-count' );
                   rcount.text( "(" +ratingcount+")" ).appendTo( ratingdiv );
               }
           }
                      
            if(starsize == "LARGE"){
                _starSize = 40;
            }else if(starsize == "MEDIUM"){
                _starSize = 20;
            }
           _staticWidth = _starSize * score;
           _userWidth   = _starSize * userScore;
           sli.width( _staticWidth );           
           uli.width( _userWidth );
           if(settings.readonly.toUpperCase() == "FALSE"){
               var li1 = $( document.createElement('li')).addClass('score-1 li').attr('score','1').appendTo(ul),
                   li2 = $( document.createElement('li')).addClass('score-2 li').attr('score','2').appendTo(ul),
                   li3 = $( document.createElement('li')).addClass('score-3 li').attr('score','3').appendTo(ul),
                   li4 = $( document.createElement('li')).addClass('score-4 li').attr('score','4').appendTo(ul), 
                   li5 = $( document.createElement('li')).addClass('score-5 li').attr('score','5').appendTo(ul);
               li1.click(function(){  settings.click.call( this, '1' );  });
               li2.click(function(){  settings.click.call( this, '2' );  });
               li3.click(function(){  settings.click.call( this, '3' );  });
               li4.click(function(){  settings.click.call( this, '4' );  });
               li5.click(function(){  settings.click.call( this, '5' );  });  
          
           } else {
                  ratingdiv.css( 'pointer-events' , 'none' );
          }            
           ratingdiv.appendTo( this );           
        });
      }
     })(jQuery);                     
     ---------------------------------
     css -
     .MEDIUM .star-ul {
    background: url("http://assets2-dev.livecache.net/L6/3/IOGLO/815954651/176546052/Stars_Medium.png") repeat-x scroll left top rgba(0, 0, 0, 0);
    height: 20px;
    list-style: none outside none;
    margin-bottom: 0;
    margin-left: 0;
    margin-top: 0;
    overflow: hidden;
    padding: 0;
    position: relative;
    width: 100px;float:left; }
    .MEDIUM .star-ul .all-rating-li {
    background: url("http://assets2-dev.livecache.net/L6/3/IOGLO/815954651/176546052/Stars_Medium.png") repeat scroll left center rgba(0, 0, 0, 0);
    display: block;
    height: 20px;
    position: absolute;}
    .MEDIUM .star-ul .user-rating-li {
    background: url("http://assets2-dev.livecache.net/L6/3/IOGLO/815954651/176546052/Stars_Medium.png") repeat scroll left bottom rgba(0, 0, 0, 0);
    display: block;
    height: 20px;
    position: absolute;
    z-index: 2;}
    .MEDIUM .star-ul .score-1:hover {width	: 20px;}
    .MEDIUM .star-ul.score-2:hover {width	: 40px;}
     .MEDIUM .star-ul .score-3:hover {width: 60px;}
     .MEDIUM .star-ul .score-4:hover {width: 80px;}
     .MEDIUM .star-ul .score-5:hover {width: 100px;}
     .MEDIUM .star-ul .score-1{left: 0px;}
     .MEDIUM .star-ul .score-2{left: 20px;}
     .MEDIUM .star-ul .score-3{left: 40px;}
     .MEDIUM .star-ul .score-4{left: 60px;}
     .MEDIUM .star-ul .score-5{left: 80px;}
    .MEDIUM .star-ul .li {
        display: block;
        height: 20px;
        padding: 0;
        position: absolute;
        text-decoration: none;
        text-indent: -9000px;
        width: 20px;
        z-index: 20;
    }
      .MEDIUM .star-ul .li:hover {
          background: url("http://assets2-dev.livecache.net/L6/3/IOGLO/815954651/176546052/Stars_Medium.png") repeat scroll left bottom rgba(0, 0, 0, 0);
          left: 0;
          z-index: 10;
          cursor: pointer;
      }
      .block-cursor{
          pointer-events: none;
      }
      /** css for large star */
      	.LARGE .star-ul {
      		    background: url("http://assets0-dev.livecache.net/L6/3/IOGLO/815954570/176546009/Stars_Large.png") repeat-x scroll left top rgba(0, 0, 0, 0) !important;
      		    height: 40px !important;list-style: none outside none !important;margin-bottom: 0 !important;margin-left: 0 !important;
      		    margin-top: 0 !important;padding: 0 !important;position: relative !important;width: 200px !important;
          float:left;
      	}
      	.LARGE .star-ul .all-rating-li {
      		    background: url("http://assets0-dev.livecache.net/L6/3/IOGLO/815954570/176546009/Stars_Large.png") repeat scroll left center rgba(0, 0, 0, 0) !important;
      		    display: block !important;
      		    height: 40px !important;
      		    position: absolute !important;
      		    text-indent: -9000px !important;
      		    z-index: 1 !important;
      	}
      	.LARGE .star-ul .user-rating-li{
      		    background: url("http://assets0-dev.livecache.net/L6/3/IOGLO/815954570/176546009/Stars_Large.png") repeat scroll left bottom rgba(0, 0, 0, 0) !important;
      		    display: block !important;height: 40px !important;position: absolute !important;text-indent: -9000px !important;
      		    z-index: 2 !important;
      	}
      
      
      	.LARGE .star-ul .li{display: block;height: 40px;padding: 0;position: absolute;text-decoration: none;text-indent: -9000px;width: 40px;z-index: 20;    cursor: pointer;	}
      	.LARGE .star-ul .li:hover {background: url("http://assets0-dev.livecache.net/L6/3/IOGLO/815954570/176546009/Stars_Large.png") repeat scroll left bottom rgba(0, 0, 0, 0);left: 0;z-index: 2;}
      
      .LARGE .rating-count {float: left;font-size: 24px;line-height: 40px;margin: 0 5px;}	
      	.LARGE .star-ul .score-1:hover { width	: 40px;}
      	.LARGE .star-ul .score-2:hover { width	: 80px;}
      	.LARGE .star-ul .score-3:hover { width	: 120px;}
      	.LARGE .star-ul .score-4:hover { width	: 160px;}
      	.LARGE .star-ul .score-5:hover { width	: 200px;}
      
      	.LARGE .star-ul .score-1{  left	: 0px;}
      	.LARGE .star-ul .score-2{  left	: 40px;}
      	.LARGE .star-ul .score-3{  left	: 80px;}
      	.LARGE .star-ul .score-4{  left	: 120px;}
      	.LARGE .star-ul .score-5{  left	: 160px;}
      	------------------------------------------------------
      	html - 
      	<div class="rate"></div>
      	------------------------------------------------------
      	how to call into your code 
      	$('.rate').myRating({
            readonly   : 'false', // true for static rating only and false for the clickable star.[defaout is static ]
            score      : '4',      // total score of item 
            userscore  : '2.5',      // ratedby user 
            count      : '10',     // Count means no of user rated   
            size       : 'medium',  // size if star large or medium currently no option for small
            click      : function(score){
                    alert( "score - "+ score );
            }
        });
