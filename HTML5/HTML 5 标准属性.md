| 属性            | 值                 | 描述                                                         |
| :-------------- | :----------------- | :----------------------------------------------------------- |
| accesskey       | *character*        | 规定访问元素的键盘快捷键<br />Alt+“”<br />以下元素支持 accesskey 属性：<a>, <area>, <button>, <input>, <label>, <legend> 以及 <textarea>。 |
| class           | *classname*        | 规定元素的类名（用于规定样式表中的类）。<br /><element contenteditable="true \| false"> |
| contenteditable | true  false        | 规定是否允许用户编辑内容。                                   |
| contextmenu     | *menu_id*          | 规定元素的上下文菜单。目前只有 Firefox 支持 contextmenu 属性。<br /><p contextmenu="supermenu">本段落拥有一个名为 "supermenu" 的上下文菜单。这个菜单会在用户右键单击该段落时出现。</p>  <br/><br/><menu id="supermenu"><br/>  <command label="Step 1: Write Tutorial" onclick="doSomething()"><br/>  <command label="Step 2: Edit Tutorial" onclick="doSomethingElse()"><br/></menu> |
| data-yourvalue  | *value*            | 创作者定义的属性。HTML 文档的创作者可以定义他们自己的属性。必须以 "data-" 开头。<br /><element data-*="somevalue"> |
| dir             | ltr  rtl           | 规定元素中内容的文本方向。<br /><element dir="ltr l trl”>    |
| draggable       | true  false  auto  | 规定是否允许用户拖动元素。<br /><element draggable="true \| false \| auto”> |
| dropzone        | copy move  link    | 规定在拖动被拖动数据时是否进行复制、移动或链接。<br /><element dropzone="copy \| move \| link”> |
| hidden          | hidden             | 规定该元素是无关的。被隐藏的元素不会显示。                   |
| id              | *id*               | 规定元素的唯一 ID。                                          |
| item            | *empty**url*       | 用于组合元素。                                               |
| itemprop        | *url**group value* | 用于组合项目。                                               |
| lang            | *language_code*    | 规定元素中内容的语言代码。[语言代码参考手册](http://www.w3school.com.cn/tags/html_ref_language_codes.asp)。<br />**注释：**lang 属性在以下标签中**无效**：<base>, <br/>, <frame>, <frameset>, <hr>, <iframe>, <param> 以及 <script>。 |
| spellcheck      | true false         | 规定是否必须对元素进行拼写或语法检查。                       |
| style           | *style_definition* | 规定元素的行内样式。                                         |
| subject         | *id*               | 规定元素对应的项目。                                         |
| tabindex        | *number*           | 规定元素的 tab 键控制次序。<br /><element tabindex="number"> |
| title           | *text*             | 规定有关元素的额外信息。                                     |

