## 区分ie浏览器和其他浏览器

- > html的hack
  >
  > > ```html
  > > <!--[if IE ６]>
  > >     <ｐ>只有IE6认识我<／p>
  > > <![endif]-->
  > > <!--[if gte IE 9]>
  > >        <h1>大于等于IE9的浏览器能看到</h1>
  > > <![endif]-->
  > > <!--[if lte IE 8]>
  > >        <h1 class="red">您的浏览器版本过低，IE8及以下版本不支持新样式，请更新浏览器</h1>
  > > <![endif]-->
  > > ```

- > css的hack
  >
  > ```css
  > _background:pink;    //仅IE6识别
  > ！background:pink;    //仅IE6、7识别
  > background:pink\0/;    //仅IE8识别
  > background:pink\0;    //IE8、9、10识别
  > background:pink\9;    //IE6-10识别(未成功)
  > ```
  >
  > 