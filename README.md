# Regular = react(ractive) + angular.

regular is a live template engine helping us to create reactive component, there are some basic feature.

1. __data-binding__ like angular.
2. __string-based__ template with buildin rule like  if/else ,list and dynamic include.
3. the template's rule is extensiable(need Parser packaged).
4. __independent lifecycle__ in every component. so component can be integrated with whatever framework you already used.
5. __nested component__
6. the definition of Business logic based on Class, just like [angular-classy](http://davej.github.io/angular-classy/) do for angular
7. __directive, filter, event__ is supported, and extend easily.

__example__

with less than 20 line code then you already have a simple note component, you can also see it in [jsfiddle](http://jsfiddle.net/leeluolee/e6yD3/)

```javascript
var NoteApp = Regular.extend({
  template: 
    "{{#list notes as c}}\
        <p>{{c.content}} <a href='#' on-click={{this.remove(c)}}>remove</a></p>\
     {{/list}}\
     <textarea r-model={{draftComment}}></textarea><button on-click={{this.add()}}>new Note</button>",
  remove: function(c){
    var notes = this.data.notes;
    var index = notes.indexOf(c);
    if(~index) notes.splice(index,1);
  },
  add: function(){
    var data = this.data;
    data.notes.push({content: data.draftComment})
    data.draftComment = "";
  }
});

new NoteApp({
  data{
    notes:[]
  }
}).inject(document.body);
```



__There also a  [todomvc demo](http://jsfiddle.net/leeluolee/5Err9/) rewirte by regularjs__


## Browser Compatibility

regularjs's target browser contains __ie6/7/8/9__, and other mordern browser;


## Download

1. install with bower 
  * confirm you installed [bower](https://github.com/bower/bower) or just type `npm install -g bower`
  * `bower install regularjs` or add regularjs dependency in you `bower.json`

2. clone this repo, or download the [latest package]

3. now you can find `regular.js` and `regular.min.js` in `dist` folder;



## Guide && Docs

* __[regular's Offcial Guide](http://leeluolee.gitbooks.io/regular-guide/)__(use gitbook)


## Community


* If you find bugs or have suggestion, please feel free to open [an issue](https://github.com/regularjs/regular/issues)

* Ask any questions on [Stack Overflow](http://stackoverflow.com/questions/tagged/regularjs) with tag `regularjs`. 

* Social 
  1. twitter: follow the [@regularjs](https://twitter.com/regularjs). 
  2. weibo: chinese friends can also follow author's weibo[@拴萝卜的棍子](http://weibo.com/luobolee)

## Contribute


regularjs is still in heavily development, helping us with pull-request. there is some recommend to contributor.

* Please [open issue](https://github.com/regularjs/regular/issues) before sending pull request, 
* if needed, add your testcase at `test/specs` folder. always make sure the `gulp mocha` is passed, and the `test/runner/index.html` is passed in every target browser


## [LICENSE](https://github.com/regularjs/regular/blob/master/LICENSE)

MIT.
