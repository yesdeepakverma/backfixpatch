# backfixpatch
some patches to backfix js


I found there shold be some patches to backfix js hosted at 
https://code.google.com/p/group972301/source/browse/ep+web+for+checkout/WebContent/js/backfix.min.js?r=61



Now after patches this file should be called as 
bajb_backdetect.Initialise();
bajb_backdetect.OnBack = function(){// your javascript code goes here.
                                    // may include history.back() but it should be the last line statement.
                                          }

// I moved history.back() to source onBack function beacuse It makes sense that history.back should be optional.
// The problem I was in , I required to performa a widnow.location in bajb_backdetect.OnBack and I don't want the history.back()
// and window.location is not so fast that is immediatly perform a location redirect. So this returns control to history.back() as per original source code.

// If you wish you can include history.back() functionality in bajb_backdetect.OnBack.


// Also I changed 
if (window.location.hash == '') {  to 

if ((window.location.hash == '' ) && (window.location.href.slice(-1) != '#'))

Because In my project code there was more achor tag with <a href='#' onclick="dosomejs()">link name</a>

so In that case whenever I cliks on these kind of anchor tags or any such tag, this results in calling of bajb_backdetect.OnBack which is what I do not want. Also I want a custom funtion to be called before bajb_backdetect.OnBack gets called hence a custom function.

As I didn't find any way to send patch to original souce code , SO I create this a patch git repo.

link to original code is
https://code.google.com/p/group972301/


:-)

Happy Patching .....   (:+)







