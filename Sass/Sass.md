# Sass（Syntactically Awesome StyleSheets）

Sass 是对 CSS 的扩展，让 CSS 语言更强大、优雅。 它允许你使用[变量](http://sass.bootcss.com/docs/sass-reference/#variables_)、[嵌套规则](http://sass.bootcss.com/docs/sass-reference/#nested_rules)、 [mixins](http://sass.bootcss.com/docs/sass-reference/#mixins)、[导入](http://sass.bootcss.com/docs/sass-reference/#import)等众多功能， 并且完全兼容 CSS 语法。 Sass 有助于保持大型样式表结构良好， 同时也让你能够快速开始小型项目， 特别是在搭配 [Compass 样式库](http://compass-style.org/)一同使用时。

## 特色

-   完全兼容 CSS3
-   在 CSS 语言基础上添加了扩展功能，比如变量、嵌套 (nesting)、混合 (mixin)
-   对颜色和其它值进行操作的{Sass::Script::Functions 函数}
-   函数库[控制指令](http://sass.bootcss.com/docs/sass-reference/#control_directives)之类的高级功能
-   良好的格式，可对输出格式进行定制
-   [支持 Firebug](https://addons.mozilla.org/en-US/firefox/addon/103988)

## 语法

Sass 有两种语法。 第一种被称为 SCSS (Sassy CSS)，是一个 CSS3 语法的扩充版本，这份参考资料使用的就是此语法。 也就是说，所有符合 CSS3 语法的样式表也都是具有相同语法意义的 SCSS 文件。 另外，SCSS 理解大多数 CSS hacks 以及浏览器专属语法，例如[IE 古老的 `filter` 语法](http://msdn.microsoft.com/en-us/library/ms533754%28VS.85%29.aspx)。 这种语种语法的样式表文件需要以 `.scss` 扩展名。

第二种比较老的语法成为缩排语法（或者就称为 "Sass"）， 提供了一种更简洁的 CSS 书写方式。 它不使用花括号，而是通过缩排的方式来表达选择符的嵌套层级，I 而且也不使用分号，而是用换行符来分隔属性。 很多人认为这种格式比 SCSS 更容易阅读，书写也更快速。 缩排语法具有 Sass 的所有特色功能， 虽然有些语法上稍有差异； 这些差异在{file:INDENTED_SYNTAX.md 所排语法参考手册}中都有描述。 使用此种语法的样式表文件需要以 `.sass` 作为扩展名。

任一语法都可以[导入](http://sass.bootcss.com/docs/sass-reference/#import)另一种语法撰写的文件中。 只要使用 `sass-convert` 命令行工具，就可以将一种语法转换为另一种语法：

```
# 将 Sass 转换为 SCSS
$ sass-convert style.sass style.scss

# 将 SCSS 转换为 Sass
$ sass-convert style.scss style.sass
```

## 使用 Sass

Sass 有三种使用方式： 命令行工具、独立的 Ruby 模块，以及包含 Ruby on Rails 和 Merb 作为支持 Rack 的框架的插件。 所有这些方式的第一步都是安装 Sass gem：

```
gem install sass
```

如果你使用的是 Windows， 就需要先[安装 Ruby](http://rubyinstaller.org/download.html)。

如果要在命令行中运行 Sass ,只要输入

```
sass input.scss output.css
```

你还可以命令 Sass 监视文件的改动并更新 CSS ：

```
sass --watch input.scss:output.css
```

如果你的目录里有很多 Sass 文件，你还可以命令 Sass 监视整个目录：

```
sass --watch app/sass:public/stylesheets
```

使用 `sass --help` 可以列出完整的帮助文档。

在 Ruby 代码中使用 Sass 是非常容易的。 安装 Sass gem 之后，你可以执行 `require "sass"` ， 然后就可以像这样使用 {Sass::Engine} ：

```
engine = Sass::Engine.new("#main {background-color: #0000ff}", :syntax => :scss)
engine.render #=> "#main { background-color: #0000ff; }\n"
```

### Rack/Rails/Merb 插件

如果需要在 Rails 3 之前的版本中启用 Sass，可以把这一行加到 `environment.rb` 中：

```
config.gem "sass"
```

对于 Rails 3，则是把这一行加到 Gemfile 中：

```
gem "sass"
```

要在 Merb 中启用 Sass，需要把这一行加到 `config/dependencies.rb` 中：

```
dependency "merb-haml"
```

在 Rack 应用中启用 Sass，需要在 `config.ru` 中添加：

```
require 'sass/plugin/rack'
use Sass::Plugin::Rack
```

Sass 样式表跟视图（views）的运作方式不同。 它并没有任何动态内容， 所以只需要在 Sass 文件更新时生成 CSS 即可。 默认情况下，`.sass` 和 `.scss` 文件是放在 public/stylesheets/sass 目录下的（这可以通过 [`:template_location`](http://sass.bootcss.com/docs/sass-reference/#template_location-option) 选项进行配置）。 然后，在需要的时候，它们会被编译成相应的 CSS 文件并被放到 public/stylesheets 目录下。 例如，public/stylesheets/sass/main.scss 文件将会被编译为 public/stylesheets/main.css 文件。

### 缓存

默认情况下，Sass 会对编译过的模板（template）和[partials](http://sass.bootcss.com/docs/sass-reference/#partials) 进行缓存。 这将明显加快大量 Sass 文件的重新编译速度， 并且在 Sass 模板被切割为多个文件并通过 [`@import`](http://sass.bootcss.com/docs/sass-reference/#import) 引入形成一个大文件时效果最好。

如果不使用框架，Sass 将会把缓存的模板放入 `.sass-cache` 目录。 在 Rails 和 Merb 中，将被放到 `tmp/sass-cache` 目录。 此目录可以通过 [`:cache_location`](http://sass.bootcss.com/docs/sass-reference/#cache_location-option) 选项进行配置。 如果你不希望 Sass 启用缓存功能， 可以将 [`:cache`](http://sass.bootcss.com/docs/sass-reference/#cache-option) 选项设置为 `false`。

### 选项

可以通过`environment.rb`在Rails或`config.ru`Rack中设置{Sass :: Plugin :: Configuration＃options Sass :: Plugin＃options}哈希来设置选项...

```
Sass::Plugin.options[:style] = :compact
```

...或者通过在Merb中设置`Merb::Plugin.config[:sass]`哈希`init.rb`...

```
Merb::Plugin.config[:sass][:style] = :compact
```

...或者通过将选项哈希传递给{Sass :: Engine＃initialize}。所有相关选项也可通过标志`sass`和`scss`命令行可执行文件获得。可用选项包括：

{#style-option} `:style` ：设置CSS输出的样式。请参阅[输出样式](http://sass.bootcss.com/docs/sass-reference/#output_style)。

{＃syntax-option} `:syntax` ：输入文件的语法，`:sass`用于缩进语法和`:scss`CSS扩展语法。这仅在您自己构建{Sass :: Engine}实例时有用; 使用{Sass :: Plugin}时，它会自动正确设置。默认为`:sass`。

{＃property_syntax-option} `:property_syntax` ：强制缩进语法文档对属性使用一种语法。如果未使用正确的语法，则会引发错误。 `:new`强制在属性名称后使用冒号。例如：`color: #0f3` 或`width: $main_width`。`:old`强制在属性名称前使用冒号。例如：`:color #0f3` 或`:width $main_width`。默认情况下，任一语法都有效。这对SCSS文档没有影响。

{#cache-option} `:cache` ：是否应该缓存已解析的Sass文件，从而提高速度。默认为true。

{#read_cache-option} `:read_cache` ：如果已设置`:cache`且未设置，则仅读取Sass缓存（如果存在），如果不存在则不写入。

{#cache_store-option} `:cache_store` ：如果将其设置为{Sass :: CacheStores :: Base}的子类的实例，则该缓存存储将用于存储和检索缓存的编译结果。默认为使用该[`:cache_location`选项](http://sass.bootcss.com/docs/sass-reference/#cache_location-option)初始化的{Sass :: CacheStores :: Filesystem} 。

{#never_update-option} `:never_update` ：即使模板文件发生更改，是否永远不应更新CSS文件。将此设置为true可能会带来很小的性能提升。它总是默认为false。只在Rack，Ruby on Rails或Merb中有意义。

{＃always_update-option} `:always_update` ：每次访问控制器时是否应更新CSS文件，而不是仅在修改模板时更新。默认为false。只在Rack，Ruby on Rails或Merb中有意义。

{＃always_check-option} `:always_check` ：每次访问控制器时是否应检查Sass模板的更新，而不是仅在服务器启动时检查。如果Sass模板已更新，它将被重新编译并覆盖相应的CSS文件。在生产模式下默认为false，否则为true。只在Rack，Ruby on Rails或Merb中有意义。

{#prow-option} `:poll` ：如果为true，则始终使用{Sass :: Plugin :: Compiler＃watch}的轮询后端而不是本机文件系统后端。

{＃full_exception-option} `:full_exception` ：Sass代码中的错误是否应该导致Sass在生成的CSS文件中提供详细描述。如果设置为true，则错误将与行号和源代码段一起显示为CSS文件中的注释和页面顶部（在支持的浏览器中）。否则，Ruby代码中将引发异常。在生产模式下默认为false，否则为true。只在Rack，Ruby on Rails或Merb中有意义。

{＃template_location-option} `:template_location` ：应用程序的根sass模板目录的路径。如果哈希值`:css_location`被忽略，则此选项指定输入和输出目录之间的映射。也可以给出一个2元素列表的列表，而不是散列。默认为`css_location + "/sass"`。只在Rack，Ruby on Rails或Merb中有意义。请注意，如果指定了多个模板位置，则所有模板位置都将放置在导入路径中，允许您在它们之间导入。 **请注意，由于可以采用多种可能的格式，因此只能直接设置此选项，不能访问或修改此选项。使用{Sass :: Plugin :: Configuration＃template_location_array Sass :: Plugin＃template_location_array}，{Sass :: Plugin :: Configuration＃add_template_location Sass :: Plugin #add_template_location}和{Sass :: Plugin :: Configuration＃remove_template_location Sass ::插件#lele_template_location}方法**。

{#css_location-option} `:css_location` ：应该写入CSS输出的路径。`:template_location`哈希时会忽略此选项。默认为`"./public/stylesheets"`。只在Rack，Ruby on Rails或Merb中有意义。

{#cache_location-option} `:cache_location` ：`sassc`应该将高速缓存文件写入的路径。默认为`"./tmp/sass-cache"`Rails和Merb，或`"./.sass-cache"`其他。如果设置了该[`:cache_store`选项](http://sass.bootcss.com/docs/sass-reference/#cache_location-option)，则忽略该[选项](http://sass.bootcss.com/docs/sass-reference/#cache_location-option)。

{#unix_newlines-option} `:unix_newlines` ：如果为true，则在编写文件时使用Unix风格的换行符。只有在Windows上有意义，并且只有当Sass正在编写文件时（在Rack，Rails或Merb中，直接使用{Sass :: Plugin}时，或者在使用命令行可执行文件时）。

{#filename-option} `:filename` ：正在呈现的文件的文件名。这仅用于报告错误，并在使用Rack，Rails或Merb时自动设置。

{#line-option} `:line` ：Sass模板第一行的编号。用于报告错误的行号。如果Sass模板嵌入在Ruby文件中，这很有用。

{#load_paths-option} `:load_paths` ：应搜索使用该[`@import`](http://sass.bootcss.com/docs/sass-reference/#import)指令导入的Sass模板的文件系统路径或导入器数组。这些可能是`Pathname`{Sass :: Importers :: Base}的字符串，对象或子类。默认为工作目录，在Rack，Rails或Merb中，无论`:template_location`是什么。负载路径也由{Sass.load_paths}和`SASS_PATH`环境变量通知。

{#cilesystem_importer-option} `:filesystem_importer` ：用于处理普通字符串加载路径的{Sass :: Importers :: Base}子类。这应该从文件系统导入文件。它应该是一个继承自{Sass :: Importers :: Base}的Class对象，其构造函数采用单个字符串参数（加载路径）。默认为{Sass :: Importers :: Filesystem}。

{#line_numbers-option} `:line_numbers` ：设置为true时，会将定义选择器的行号和文件作为注释发送到编译的CSS中。用于调试，尤其是在使用import和mixins时。也可以调用此选项`:line_comments`。使用`:compressed`输出样式或`:debug_info`/ `:trace_selectors`选项时自动禁用。

{#trace_selectors-option} `:trace_selectors` ：设置为true时，在每个选择器之前发出完整的导入跟踪和mixins。这对于样式表导入和mixin包含的浏览器内调试很有帮助。此选项取代该`:line_comments`选项，并被该选项取代`:debug_info`。使用`:compressed`输出样式时自动禁用 。

{#spin_info-option} `:debug_info` ：设置为true时，导致定义选择器的行号和文件以浏览器可以理解的格式发送到编译的CSS中。与[FireSass Firebug扩展](https://addons.mozilla.org/en-US/firefox/addon/103988)一起使用[，](https://addons.mozilla.org/en-US/firefox/addon/103988) 用于显示Sass文件名和行号。使用`:compressed`输出样式时自动禁用。

{#custom-option} `:custom` ：一个选项，可供各个应用程序设置，使数据可用于{Sass :: Script :: Functions自定义Sass函数}。

{#snilent-option} `:quiet` ：设置为true时，会导致警告被禁用。

### 语法选择

Sass命令行工具将使用文件扩展名来确定您使用的语法，但并不总是有文件名。在`sass` 命令行程序默认为缩进语法，但你可以通过该 `--scss`选项，如果输入应该被解释为SCSS语法。或者，您可以使用与`scss`程序完全相同的命令行程序，`sass`但默认情况下假设语法为SCSS。

### 编码

在Ruby 1.9及更高版本上运行时，Sass知道文档的字符编码。默认情况下，Sass假定所有样式表都使用操作系统默认的编码系统进行编码。对于许多用户来说，这将是`UTF-8`网络事实上的标准。但是，对于某些用户来说，它可能是更本地的编码。

如果要为样式表使用与操作系统默认值不同的编码，则可以`@charset`像在CSS中一样使用声明。`@charset "encoding-name";`在样式表的开头添加（在任何空格或注释之前），Sass会将其解释为给定的编码。请注意，无论使用何种编码，都必须可以转换为Unicode。

Sass还将遵守[CSS规范中指定的](http://www.w3.org/TR/CSS2/syndata.html#charset)任何Unicode BOM和非ASCII兼容的Unicode编码 ，尽管这*不是*指定文档字符集的推荐方法。需要注意的是萨斯不支持晦涩`UTF-32-2143`， `UTF-32-3412`，`EBCDIC`，`IBM1026`，和`GSM 03.38`编码，因为Ruby没有对他们的支持，他们是极不可能永远在实践中使用。

#### 输出编码

通常，Sass将尝试使用与输入样式表相同的编码对输出样式表进行编码。但是，为了使它能够执行此操作，输入样式表必须具有`@charset`声明; 否则，Sass将默认将输出样式表编码为`UTF-8`。此外，`@charset`如果输出不是纯ASCII ，它将向输出添加声明。

当编辑带`@charset`声明的其他样式表时`@import`，Sass会将它们转换为与主样式表相同的编码。

请注意，Ruby 1.8对字符编码没有很好的支持，因此Sass在其下运行时的行为有点不同于Ruby 1.9及更高版本。在Ruby 1.8中，Sass只使用`@charset`样式表中的第一个声明或任何其他样式表`@import`。

## CSS扩展

### 嵌套规则

Sass允许CSS规则彼此嵌套。然后内部规则仅适用于外部规则的选择器。例如：

```
#main p {
  color: #00ff00;
  width: 97%;

  .redbox {
    background-color: #ff0000;
    color: #000000;
  }
}
```

被编译为：

```
#main p {
  color: #00ff00;
  width: 97%; }
  #main p .redbox {
    background-color: #ff0000;
    color: #000000; }
```

这有助于避免重复父选择器，并使具有大量嵌套选择器的复杂CSS布局更加简单。例如：

```
#main {
  width: 97%;

  p, div {
    font-size: 2em;
    a { font-weight: bold; }
  }

  pre { font-size: 3em; }
}
```

被编译为：

```
#main {
  width: 97%; }
  #main p, #main div {
    font-size: 2em; }
    #main p a, #main div a {
      font-weight: bold; }
  #main pre {
    font-size: 3em; }
```

### 引用父选择符： `&`

有时，以默认的其他方式使用嵌套规则的父选择器很有用。例如，您可能希望在该选择器悬停时或者当body元素具有某个类时具有特殊样式。在这些情况下，您可以使用该`&`字符显式指定应插入父选择器的位置。例如：

```
a {
  font-weight: bold;
  text-decoration: none;
  &:hover { text-decoration: underline; }
  body.firefox & { font-weight: normal; }
}
```

被编译为：

```
a {
  font-weight: bold;
  text-decoration: none; }
  a:hover {
    text-decoration: underline; }
  body.firefox a {
    font-weight: normal; }
```

`&` 在编译时将被替换为父选择符，输出到 CSS 中。 也就是说，如果你有一个深层嵌套的规则，父选择符也会在 `&` 被替换之前被完整的解析， 例如：

```
#main {
  color: black;
  a {
    font-weight: bold;
    &:hover { color: red; }
  }
}
```

被编译为：

```
#main {
  color: black; }
  #main a {
    font-weight: bold; }
    #main a:hover {
      color: red; }
```

### 嵌套属性

CSS在“命名空间”中有很多属性; 例如`font-family`，`font-size`和`font-weight` 都在`font`命名空间。在CSS中，如果要在同一名称空间中设置一组属性，则必须每次都输入它。Sass为此提供了一个快捷方式：只需编写一次名称空间，然后将每个子属性嵌套在其中。例如：

```
.funky {
  font: {
    family: fantasy;
    size: 30em;
    weight: bold;
  }
}
```

被编译为：

```
.funky {
  font-family: fantasy;
  font-size: 30em;
  font-weight: bold; }
```

属性名称空间本身也可以具有值。例如：

```
.funky {
  font: 2px/3px {
    family: fantasy;
    size: 30em;
    weight: bold;
  }
}
```

被编译为：

```
.funky {
  font: 2px/3px;
    font-family: fantasy;
    font-size: 30em;
    font-weight: bold; }
```

### 占位符选择器： `%foo`

Sass支持一种称为“占位符选择器”的特殊类型的选择器。这些看起来像class和id选择器，除了`#`或被`.`替换为`%`。它们意味着与[`@extend`指令](http://sass.bootcss.com/docs/sass-reference/#extend)一起使用; 有关更多信息，请参阅[`@extend`-Only Selectors](http://sass.bootcss.com/docs/sass-reference/#placeholders)。

在没有任何使用的情况下`@extend`，使用占位符选择器的规则集将不会呈现给CSS。

## 评论：`/* */`和`//`

Sass支持标准的多行CSS注释`/* */`，以及单行注释`//`。尽可能在CSS输出中保留多行注释，同时删除单行注释。例如：

```
/* This comment is
 * several lines long.
 * since it uses the CSS comment syntax,
 * it will appear in the CSS output. */
body { color: black; }

// These comments are only one line long each.
// They won't appear in the CSS output,
// since they use the single-line comment syntax.
a { color: green; }
```

被编译为：

```
/* This comment is
 * several lines long.
 * since it uses the CSS comment syntax,
 * it will appear in the CSS output. */
body {
  color: black; }

a {
  color: green; }
```

当注释的第一个字母是时`!`，注释将被插值并且即使在压缩输出模式下也总是呈现为css输出。这对于将生成的版权声明添加到生成的CSS非常有用。

## SassScript

除了普通的CSS属性语法之外，Sass还支持一小组名为SassScript的扩展。SassScript允许属性使用变量，算术和额外函数。SassScript可用于任何属性值。

SassScript还可用于生成选择器和属性名称，这在编写[mixins](http://sass.bootcss.com/docs/sass-reference/#mixins)时很有用。这是通过[插值](http://sass.bootcss.com/docs/sass-reference/#interpolation_)完成的。

### 互动壳牌

您可以使用交互式shell轻松尝试使用SassScript。要启动shell，请运行带有该`-i`选项的sass命令行。在提示符下，输入任何合法的SassScript表达式以对其进行评估并打印出结果：

```
$ sass -i
>> "Hello, Sassy World!"
"Hello, Sassy World!"
>> 1px + 1px + 1px
3px
>> #777 + #777
#eeeeee
>> #777 + #888
white
```

### 变量： `$`

使用SassScript最直接的方法是使用变量。变量以美元符号开头，并设置为CSS属性：

```
$width: 5em;
```

然后，您可以在属性中引用它们：

```
#main {
  width: $width;
}
```

变量仅在定义它们的嵌套选择器级别内可用。如果它们是在任何嵌套选择器之外定义的，那么它们随处可用。

用于使用前缀字符的变量`!`; 这仍然有效，但它已被弃用并打印警告。 `$`是推荐的语法。

变量也习惯于定义`=`而不是`:`; 这仍然有效，但它已被弃用并打印警告。 `:`是推荐的语法。

### 数据类型

SassScript 支持六种主要的数据类型：

-   数字（例如 `1.2`、`13`、`10px`）
-   文本字符串，无论是否有引号（例如 `"foo"`、`'bar'`、`baz`）
-   颜色（例如 `blue`、`#04a3f9`、`rgba(255, 0, 0, 0.5)`）
-   布尔值（例如 `true`、`false`）
-   空值（例如 `null`）
-   值列表，用空格或逗号分隔（例如 `1.5em 1em 0 2em`、`Helvetica, Arial, sans-serif`）

SassScript 还支持所有其他 CSS 属性值类型， 例如 Unicode 范围和 `!important` 声明。 然而，它不会对这些类型做特殊处理。 它们只会被当做不带引号的字符串看待。

#### 字符串

CSS 提供了两种类型的字符串：带引号的字符串，例如 `"Lucida Grande"` 或 `'http://sass-lang.com'`； 不带引号的字符串，例如 `sans-serif` 或 `bold`。 SassScript 能够识别这两种字符串， 并且，如果一种类型的字符串 and in general if one kind of string is used in the Sass document, that kind of string will be used in the resulting CSS.

但是有一个例外：当使用[`#{}`插值时](http://sass.bootcss.com/docs/sass-reference/#interpolation_)，引用的字符串是不加引号的。这使得更容易使用例如[mixin中的](http://sass.bootcss.com/docs/sass-reference/#mixins)选择器名称。例如：

```
@mixin firefox-message($selector) {
  body.firefox #{$selector}:before {
    content: "Hi, Firefox users!";
  }
}

@include firefox-message(".header");
```

被编译为：

```
body.firefox .header:before {
  content: "Hi, Firefox users!"; }
```

值得注意的是，在使用[不推荐使用的`=`属性语法时](http://sass.bootcss.com/docs/sass-reference/#sassscript)，所有字符串都被解释为不带引号，无论它们是否用引号编写。

#### 清单

列表是Sass如何表示CSS声明的值，如`margin: 10px 15px 0 0`或`font-face: Helvetica, Arial, sans-serif`。列表只是一系列其他值，用空格或逗号分隔。事实上，个别值也算作列表：它们只是一个项目的列表。

列表本身并没有做太多，但[Sass列表功能](http://sass.bootcss.com/docs/sass-reference/Sass/Script/Functions.html#list-functions) 使它们变得有用。{Sass :: Script :: Functions #nth nth function}可以访问列表中的项目，{Sass :: Script :: Functions＃join join function}可以将多个列表连接在一起，{Sass :: Script ::函数＃append append function}可以将项添加到列表中。该[`@each`规则](http://sass.bootcss.com/docs/sass-reference/#each-directive)还可以为列表中的每个项添加样式。

除了包含简单值之外，列表还可以包含其他列表。例如，`1px 2px, 5px 6px`是包含列表`1px 2px`和列表的两项列表`5px 6px`。如果内部列表与外部列表具有相同的分隔符，则需要使用括号清除内部列表的开始和停止位置。例如，`(1px 2px) (5px 6px)`也是包含列表`1px 2px`和列表的两项列表`5px 6px`。不同之处在于外部列表是以空格分隔的，之前是逗号分隔的。

当列表转换为纯CSS时，Sass不会添加任何括号，因为CSS不理解它们。这意味着，`(1px 2px) (5px 6px)`和`1px 2px 5px 6px` 看起来一样，当他们成为CSS。但是，当它们是Sass时它们不一样：第一个是包含两个列表的列表，而第二个是包含四个数字的列表。

列表中也可以没有任何项目。这些列表表示为`()`。它们无法直接输出到CSS; 如果你试图做，例如`font-family: ()`，Sass会引发错误。如果列表包含空列表或空值，则在`1px 2px () 3px`或中`1px 2px null 3px`，在将包含列表转换为CSS之前，将删除空列表和空值。

### 运算

所有数据类型都支持等式运算 (`==` and `!=`)。 另外，每种数据类型也有其支持的特殊运算符。

#### 数字运算

SassScript 支持数字的标准运算（加 `+`、减 `-`、乘 `*`、除 `/`和取模 `%`），并且，如果需要的话，也可以在不同单位间做转换：

```
p {
  width: 1in + 8pt;
}
```

被编译为：

```
p {
  width: 1.111in; }
```

数字也支持关系运算（`<`、`>`、`<=`、`>=`）， 等式运算（`==`、`!=`）被所有数据类型支持。

##### 除法运算和 `/`

CSS 允许 `/` 出现在属性值里，作为分隔数字的一种方法。 既然 SassScript 是 CSS 属性语法的扩展， 他就必须支持这种语法，同时也允许 `/` 用在除法运算上。 也就是说，默认情况下，在 SassScript 里用 `/` 分隔的两个数字， 都会在 CSS 中原封不动的输出。

然而，在以下三种情况中，`/` 会被解释为除法运算。 这就覆盖了绝大多数真正使用除法运算的情况。 这些情况是：

1.  如果数值或它的任意部分是存储在一个变量中或是函数的返回值。
2.  如果数值被圆括号包围。
3.  如果数值是另一个数学表达式的一部分。

例如：

```
p {
  font: 10px/8px;             // 纯 CSS，不是除法运算
  $width: 1000px;
  width: $width/2;            // 使用了变量，是除法运算
  width: round(1.5)/2;        // 使用了函数，是除法运算
  height: (500px/2);          // 使用了圆括号，是除法运算
  margin-left: 5px + 8px/2px; // 使用了加（+）号，是除法运算
}
```

被编译为：

```
p {
  font: 10px/8px;
  width: 500px;
  height: 250px;
  margin-left: 9px; }
```

如果你希望在纯 CSS 中使用变量和 `/`， 你可以用 `#{}` 包住变量。 例如：

```
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```

被编译为：

```
p {
  font: 12px/30px; }
```

#### 颜色运算

所有算数运算都支持颜色值， 并且是分段运算的。 也就是说，红、绿、蓝各颜色分量会单独进行运算。 例如：

```
p {
  color: #010203 + #040506;
}
```

计算公式为 `01 + 04 = 05`、`02 + 05 = 07` 和 `03 + 06 = 09`， 并且被合成为：

```
p {
  color: #050709; }
```

一般 {Sass::Script::Functions color functions} 比颜色运算更有用，并且能达到相同的效果。

算数运算也能将数字和颜色值一起运算，同样也是分段运算的。 例如：

```
p {
  color: #010203 * 2;
}
```

计算公式为 `01 * 2 = 02`、`02 * 2 = 04` 和 `03 * 2 = 06`， 并且被合成为：

```
p {
  color: #020406; }
```

注意那些有 alpha 通道的颜色（像那些通过 {Sass::Script::Functions#rgba rgba} 或 {Sass::Script::Functions#hsla hsla} 函数创建的）必须要有同样的 alpha 值，才能执行颜色运算。 T颜色运算不会影响 alpha 值。 例如：

```
p {
  color: rgba(255, 0, 0, 0.75) + rgba(0, 255, 0, 0.75);
}
```

被编译为：

```
p {
  color: rgba(255, 255, 0, 0.75); }
```

一个颜色的alpha 通道可以通过 {Sass::Script::Functions#opacify opacify} 和 {Sass::Script::Functions#transparentize transparentize} 函数进行调整。 例如：

```
$translucent-red: rgba(255, 0, 0, 0.5);
p {
  color: opacify($translucent-red, 0.3);
  background-color: transparentize($translucent-red, 0.25);
}
```

被编译为：

```
p {
  color: rgba(255, 0, 0, 0.9);
  background-color: rgba(255, 0, 0, 0.25); }
```

IE 滤镜需要每个颜色都包含 alpha 层， 并且得用 #AABBCCDD 这样严格的格式。你可以轻松的利用 {Sass::Script::Functions#ie_hex_str ie_hex_str} 函数对其做转换。 例如：

```
$translucent-red: rgba(255, 0, 0, 0.5);
$green: #00ff00;
div {
  filter: progid:DXImageTransform.Microsoft.gradient(enabled='false', startColorstr='#{ie-hex-str($green)}', endColorstr='#{ie-hex-str($translucent-red)}');
}
```

被编译为：

```
div {
  filter: progid:DXImageTransform.Microsoft.gradient(enabled='false', startColorstr=#FF00FF00, endColorstr=#80FF0000);
}
```

#### 字符串运算

`+` 运算符可以用来连接字符串：

```
p {
  cursor: e + -resize;
}
```

被编译为：

```
p {
  cursor: e-resize; }
```

注意，如果有引号的字符串被添加了一个没有引号的字符串 （也就是，带引号的字符串在 `+` 符号左侧）， 结果会是一个有引号的字符串。 同样的，如果一个没有引号的字符串被添加了一个有引号的字符串 （没有引号的字符串在 `+` 符号左侧）， 结果将是一个没有引号的字符串。 例如：

```
p:before {
  content: "Foo " + Bar;
  font-family: sans- + "serif";
}
```

被编译为：

```
p:before {
  content: "Foo Bar";
  font-family: sans-serif; }
```

默认情况下，如果两个值彼此相邻，它们会被用空格连接起来：

```
p {
  margin: 3px + 4px auto;
}
```

被编译为：

```
p {
  margin: 7px auto; }
```

在文本字符串中，#{} 形式的表达式可以被用来在字符串中添加动态值：

```
p:before {
  content: "I ate #{5 + 10} pies!";
}
```

被编译为：

```
p:before {
  content: "I ate 15 pies!"; }
```

空值会被视作空字符串：

```
$value: null;
p:before {
  content: "I ate #{$value} pies!";
}
```

被编译为：

```
p:before {
  content: "I ate  pies!"; }
```

#### 布尔运算

SassScript 支持布尔值做 `and`、`or` 和 `not` 运算。

#### 列表操作

列表不支持任何特殊操作。相反，它们使用 [列表函数进行操作](http://sass.bootcss.com/docs/sass-reference/Sass/Script/Functions.html#list-functions)。

### 圆括号

圆括号可以用来改变运算顺序：

```
p {
  width: (1em + 2em) * 3;
}
```

被编译为：

```
p {
  width: 9em; }
```

### 函数

SassScript 定义了一些有用的函数， 这些函数可以像普通 CSS 函数语法一样被调用：

```
p {
  color: hsl(0, 100%, 50%);
}
```

被编译为：

```
p {
  color: #ff0000; }
```

#### 关键词参数

Sass 函数允许指定明确的关键词参数 (keyword arguments) 进行调用。 上面的例子也可以写成：

```
p {
  color: hsl($hue: 0, $saturation: 100%, $lightness: 50%);
}
```

虽然不够简明，但可以让样式表阅读起来会更方便。 关键词参数让函数具有更灵活的接口， 即便参数众多，也不会让使用变得困难。

命名参数（named arguments）可以以任意顺序传入，并且，具有默认值的参数可以省略掉。 由于命名参数也是变量名称，因此，下划线、短横线可以交换使用。

完整的 Sass 函数列表和它们的参数名称，以及在 Ruby 里如何定义你自己的函数的步骤，请见 {Sass::Script::Functions}。

### 插值： `#{}`

您还可以使用＃{}插值语法在选择器和属性名称中使用SassScript变量：

```
$name: foo;
$attr: border;
p.#{$name} {
  #{$attr}-color: blue;
}
```

被编译为：

```
p.foo {
  border-color: blue; }
```

也可以使用`#{}`将SassScript放入属性值。在大多数情况下，这并不比使用变量更好，但使用`#{}`确实意味着它附近的任何操作都将被视为纯CSS。例如：

```
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```

被编译为：

```
p {
  font: 12px/30px; }
```

### 变量默认值： `!default`

你可以在变量尚未赋值前，通过在值的末尾处添加 `!default` 标记来为其指定。 也就是说，如果该变量已经被赋值， 就不会再次赋值， 但是，如果还没有被赋值，就会被指定一个值。

例如：

```
$content: "First content";
$content: "Second content?" !default;
$new_content: "First time reference" !default;

#main {
  content: $content;
  new-content: $new_content;
}
```

被编译为：

```
#main {
  content: "First content";
  new-content: "First time reference"; }
```

变量的值如果是 `null` 的话，会被 !default 当做没有值：

```
$content: null;
$content: "Non-null content" !default;

#main {
  content: $content;
}
```

被编译为：

```
#main {
  content: "Non-null content"; }
```

## `@` 规则和指令

Sass 支持所有 CSS3 的 `@` 规则， 以及一些 Sass 专属的规则，也被称为“指令（directives）”。 这些规则在 Sass 中具有不同的功效，详细解释如下。 也可参考 [控制指令（control directives）](http://sass.bootcss.com/docs/sass-reference/#control_directives) 和 [mixin 指令（mixin directives）](http://sass.bootcss.com/docs/sass-reference/#mixins)。

### `@import`

Sass 扩展了 CSS 的 `@import` 规则，让它能够引入 SCSS 和 Sass 文件。 所有引入的 SCSS 和 Sass 文件都会被合并并输出一个单一的 CSS 文件。 另外，被导入的文件中所定义的变量或 [mixins](http://sass.bootcss.com/docs/sass-reference/#mixins) 都可以在主文件中使用。

Sass 会在当前目录下寻找其他 Sass 文件， 如果是 Rack、Rails 或 Merb 环境中则是 Sass 文件目录。 也可以通过 [`:load_paths`](http://sass.bootcss.com/docs/sass-reference/#load_paths-option) 选项 或者在命令行中使用 `--load-path` 选项来指定额外的搜索目录。

`@import` 根据文件名引入。 默认情况下，它会寻找 Sass 文件并直接引入， 但是，在少数几种情况下，它会被编译成 CSS 的 `@import` 规则：

-   如果文件的扩展名是 `.css`。
-   I如果文件名以 `http://` 开头。
-   如果文件名是 `url()`。
-   如果 `@import` 包含了任何媒体查询（media queries）。

如果上述情况都没有出现，并且扩展名是 `.scss` 或 `.sass`， 该名称的 Sass 或 SCSS 文件就会被引入。 如果没有扩展名， Sass 将试着找出具有 `.scss` 或 `.sass` 扩展名的同名文件并将其引入。

例如：

```
@import "foo.scss";
```

或

```
@import "foo";
```

两者都将引入 `foo.scss` 文件， 而

```
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
```

将被编译为：

```
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
```

也可以通过一个 `@import` 引入多个文件。例如：

```
@import "rounded-corners", "text-shadow";
```

将引入 `rounded-corners` 和 `text-shadow` 两个文件。

导入可能包含`#{}`插值，但仅限于某些限制。根据变量动态导入Sass文件是不可能的; 插值仅适用于CSS导入。因此，它只适用于`url()`进口。例如：

```
$family: unquote("Droid+Sans");
@import url("http://fonts.googleapis.com/css?family=#{$family}");
```

会编译到

```
@import url("http://fonts.googleapis.com/css?family=Droid+Sans");
```

#### 片段

如果你有一个 SCSS 或 Sass 文件需要引入， 但是你又不希望它被编译为一个 CSS 文件， 这时，你就可以在文件名前面加一个下划线，就能避免被编译。 这将告诉 Sass 不要把它编译成 CSS 文件。 然后，你就可以像往常一样引入这个文件了，而且还可以省略掉文件名前面的下划线。

例如，你有一个文件叫做 `_colors.scss`。 这样就不会生成 `_colors.css` 文件了， 而且你还可以这样做

```
@import "colors";
```

来引入 `_colors.scss` 文件。

注意，在同一个目录不能同时存在带下划线和不带下划线的同名文件。 例如， `_colors.scss` 不能与 `colors.scss` 并存。

#### 嵌套 `@import`

虽然大部分时间只需在顶层文件使用 `@import` 就行了， 但是，你还可以把他们包含在 CSS 规则 和 `@media`规则中。

像基类一样`@import`，这包括`@import`ed文件的内容。但是，导入的规则将嵌套在与原始规则相同的位置`@import`。

例如，如果`example.scss`包含

```
.example {
  color: red;
}
```

然后

```
#main {
  @import "example";
}
```

会编译到

```
#main .example {
  color: red;
}
```

指令，它们只允许在一个文档的基本水平，像`@mixin`或`@charset`，都没有在被文件允许`@import`以嵌套的上下文编

`@import`在mixins或控制指令中嵌套是不可能的。

### `@media`

`@media`Sass中的指令就像在纯CSS中一样，具有一个额外的功能：它们可以嵌套在CSS规则中。如果`@media`指令出现在CSS规则中，它将被冒泡到样式表的顶层，将所有选择器放在规则内的路上。这样可以轻松添加特定于媒体的样式，而无需重复选择器或破坏样式表的流程。例如：

```
.sidebar {
  width: 300px;
  @media screen and (orientation: landscape) {
    width: 500px;
  }
}
```

被编译为：

```
.sidebar {
  width: 300px; }
  @media screen and (orientation: landscape) {
    .sidebar {
      width: 500px; } }
```

`@media`查询也可以彼此嵌套。然后使用`and`运算符组合查询。例如：

```
@media screen {
  .sidebar {
    @media (orientation: landscape) {
      width: 500px;
    }
  }
}
```

被编译为：

```
@media screen and (orientation: landscape) {
  .sidebar {
    width: 500px; } }
```

最后，`@media`查询可以包含SassScript表达式（包括变量，函数和运算符）来代替要素名称和要素值。例如：

```
$media: screen;
$feature: -webkit-min-device-pixel-ratio;
$value: 1.5;

@media #{$media} and ($feature: $value) {
  .sidebar {
    width: 500px;
  }
}
```

被编译为：

```
@media screen and (-webkit-min-device-pixel-ratio: 1.5) {
  .sidebar {
    width: 500px; } }
```

### `@extend`

当一个类应该具有另一个类的所有样式以及它自己的特定样式时，通常会出现设计页面的情况。处理此问题的最常用方法是在HTML中使用更通用的类和更具体的类。例如，假设我们有一个正常错误的设计，也有一个严重的错误。我们可能会像这样编写标记：

```
<div class="error seriousError">
  Oh no! You've been hacked!
</div>
```

我们的风格如下：

```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  border-width: 3px;
}
```

不幸的是，这意味着我们必须永远记住使用`.error`同`.seriousError`。这是一个维护负担，导致棘手的错误，并且可以将非语义样式问题带入标记。

该`@extend`指令通过告诉Sass一个选择器应该继承另一个选择器的样式来避免这些问题。例如：

```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

被编译为：

```
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd;
}

.seriousError {
  border-width: 3px;
}
```

这意味着除了特定于的样式之外，`.error` 还应用了定义的所有样式。实际上，每个带有类的元素也都有类。`.seriousError``.seriousError``.seriousError``.error`

使用其他规则`.error`会为工作`.seriousError`为好。例如，如果我们有针对黑客引起的错误的特殊样式：

```
.error.intrusion {
  background-image: url("/image/hacked.png");
}
```

然后`<div class="seriousError intrusion">` 也会有`hacked.png`背景图片。

#### 这个怎么运作

`@extend`通过`.seriousError`在扩展选择器（.eg `.error`）出现的样式表中的任何位置插入扩展选择器（例如）来工作。因此上面的例子：

```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.error.intrusion {
  background-image: url("/image/hacked.png");
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

被编译为：

```
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd; }

.error.intrusion, .seriousError.intrusion {
  background-image: url("/image/hacked.png"); }

.seriousError {
  border-width: 3px; }
```

合并选择器时，`@extend`足够聪明以避免不必要的重复，因此会将某些内容`.seriousError.seriousError`翻译成`.seriousError`。此外，它不会产生无法匹配的选择器，例如`#main#footer`。

#### 扩展复杂选择器

类选择器不是唯一可以扩展的东西。这是可能的延伸仅涉及单个元件，例如任何选择`.special.cool`，`a:hover`或`a.user[href^="http://"]`。例如：

```
.hoverlink {
  @extend a:hover;
}
```

就像类一样，这意味着所有定义的样式`a:hover` 也适用于`.hoverlink`。例如：

```
.hoverlink {
  @extend a:hover;
}
a:hover {
  text-decoration: underline;
}
```

被编译为：

```
a:hover, .hoverlink {
  text-decoration: underline; }
```

就像`.error.intrusion`上面一样，任何使用的规则`a:hover`也适用`.hoverlink`，即使它们也有其他选择器。例如：

```
.hoverlink {
  @extend a:hover;
}
.comment a.user:hover {
  font-weight: bold;
}
```

被编译为：

```
.comment a.user:hover, .comment .user.hoverlink {
  font-weight: bold; }
```

#### 多个扩展

单个选择器可以扩展多个选择器。这意味着它继承了所有扩展选择器的样式。例如：

```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.attention {
  font-size: 3em;
  background-color: #ff0;
}
.seriousError {
  @extend .error;
  @extend .attention;
  border-width: 3px;
}
```

被编译为：

```
.error, .seriousError {
  border: 1px #f00;
  background-color: #fdd; }

.attention, .seriousError {
  font-size: 3em;
  background-color: #ff0; }

.seriousError {
  border-width: 3px; }
```

实际上，每个带有类的元素`.seriousError` 也都有类`.error` *和*类`.attention`。因此，文档后面定义的样式优先： `.seriousError`具有背景颜色`#ff0`而不是`#fdd`，因为`.attention`后面定义的颜色`.error`。

也可以使用以逗号分隔的选择器列表来编写多个扩展。例如，`@extend .error, .attention` 与...相同`@extend .error; @extend.attention`。

#### 链接扩展

一个选择器可以扩展另一个选择器，而另一个选择器又扩展第三个选择器。例如：

```
.error {
  border: 1px #f00;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
.criticalError {
  @extend .seriousError;
  position: fixed;
  top: 10%;
  bottom: 10%;
  left: 10%;
  right: 10%;
}
```

现在，所有类`.seriousError`都有类`.error`，所有类`.criticalError`都有类`.seriousError` *和*类`.error`。它被编译为：

```
.error, .seriousError, .criticalError {
  border: 1px #f00;
  background-color: #fdd; }

.seriousError, .criticalError {
  border-width: 3px; }

.criticalError {
  position: fixed;
  top: 10%;
  bottom: 10%;
  left: 10%;
  right: 10%; }
```

#### 选择器序列

选择器序列，例如`.foo .bar`或`.foo + .bar`，目前无法扩展。但是，嵌套选择器本身可以使用`@extend`。例如：

```
#fake-links .link {
  @extend a;
}

a {
  color: blue;
  &:hover {
    text-decoration: underline;
  }
}
```

被编译为

```
a, #fake-links .link {
  color: blue; }
  a:hover, #fake-links .link:hover {
    text-decoration: underline; }
```

##### 合并选择器序列

有时，选择器序列会扩展另一个选择器，该选择器会出现 在这种情况下，需要合并两个序列。例如：

```
#admin .tabbar a {
  font-weight: bold;
}
#demo .overview .fakelink {
  @extend a;
}
```

虽然技术上可以生成所有可能匹配任一序列的选择器，但这会使样式表太大。例如，上面的简单示例需要十个选择器。相反，Sass只生成可能有用的选择器。

当合并的两个序列没有共同的选择器时，则生成两个新的选择器：一个在第二个序列之前具有第一个序列，而在第一个序列之前具有第二个序列。例如：

```
#admin .tabbar a {
  font-weight: bold;
}
#demo .overview .fakelink {
  @extend a;
}
```

被编译为：

```
#admin .tabbar a,
#admin .tabbar #demo .overview .fakelink,
#demo .overview #admin .tabbar .fakelink {
  font-weight: bold; }
```

如果两个序列共享一些选择器，那么这些选择器将合并在一起，只有差异（如果仍然存在）将交替。在此示例中，两个序列都包含id `#admin`，因此生成的选择器将合并这两个id：

```
#admin .tabbar a {
  font-weight: bold;
}
#admin .overview .fakelink {
  @extend a;
}
```

这被编译为：

```
#admin .tabbar a,
#admin .tabbar .overview .fakelink,
#admin .overview .tabbar .fakelink {
  font-weight: bold; }
```

#### `@extend`- 只有选择者

有时您会为您只想要的类编写样式`@extend`，而不想直接在HTML中使用。在编写Sass库时尤其如此，`@extend`如果需要，可以为用户提供样式，如果不需要则忽略。

如果为此使用普通类，则在生成样式表时最终会创建大量额外的CSS，并且存在与HTML中使用的其他类冲突的风险。这就是为什么Sass支持“占位符选择器”（例如`%foo`）。

占位符选择器看起来像类和id选择器，除了`#`或被`.`替换为`%`。它们可以在类或id可以使用的任何地方使用，并且它们本身可以防止将规则集呈现给CSS。例如：

```
// This ruleset won't be rendered on its own.
#context a%extreme {
  color: blue;
  font-weight: bold;
  font-size: 2em;
}
```

但是，占位符选择器可以扩展，就像类和ID一样。将生成扩展选择器，但基本占位符选择器不会生成。例如：

```
.notice {
  @extend %extreme;
}
```

被编译为：

```
#context a.notice {
  color: blue;
  font-weight: bold;
  font-size: 2em; }
```

#### 该`!optional`旗

通常，当您扩展选择器时，如果`@extend`不起作用则会出错。例如，如果您编写`a.important {@extend .notice}`，如果没有包含的选择器，则会出错`.notice`。如果包含的唯一选择器`.notice`是`h1.notice`，则也是一个错误，因为`h1`与之冲突`a`并且因此不会生成新的选择器。

但有时，您希望允许`@extend`不生成任何新的选择器。为此，只需`!optional`在选择器后添加标志即可。例如：

```
a.important {
  @extend .notice !optional;
}
```

#### `@extend` 在指令中

`@extend`在指令中使用有一些限制，例如 `@media`。Sass无法使`@media`块外的CSS规则适用于其中的选择器而不会通过复制样式来创建大量样式表膨胀。这意味着如果使用`@extend`within `@media`（或其他CSS指令），则只能扩展出现在同一指令块中的选择器。

例如，以下工作正常：

```
@media print {
  .error {
    border: 1px #f00;
    background-color: #fdd;
  }
  .seriousError {
    @extend .error;
    border-width: 3px;
  }
}
```

但这是一个错误：

```
.error {
  border: 1px #f00;
  background-color: #fdd;
}

@media print {
  .seriousError {
    // INVALID EXTEND: .error is used outside of the "@media print" directive
    @extend .error;
    border-width: 3px;
  }
}
```

有一天，我们希望`@extend`在浏览器中本地支持，这将允许它在内部`@media`和其他指令中使用。

### `@debug`

该`@debug`指令将SassScript表达式的值打印到标准错误输出流。它对于调试具有复杂SassScript的Sass文件非常有用。例如：

```
@debug 10em + 12em;
```

输出：

```
Line 1 DEBUG: 22em
```

### `@warn`

该`@warn`指令将SassScript表达式的值打印到标准错误输出流。对于需要警告用户弃用或从较小的mixin使用错误中恢复的库来说，它非常有用。`@warn`和之间有两个主要区别`@debug`：

1.  您可以使用`--quiet`命令行选项或`:quiet`Sass选项关闭警告。
2.  样式表跟踪将与消息一起打印出来，以便被警告的用户可以看到他们的样式在哪里引起警告。

用法示例：

```
@mixin adjust-location($x, $y) {
  @if unitless($x) {
    @warn "Assuming #{$x} to be in pixels";
    $x: 1px * $x;
  }
  @if unitless($y) {
    @warn "Assuming #{$y} to be in pixels";
    $y: 1px * $y;
  }
  position: relative; left: $x; top: $y;
}
```

## 控制指令

SassScript支持基本控制指令，仅在某些条件下包含样式，或者在变化时多次包含相同的样式。

**请注意，控制指令是一项高级功能，不建议在日常样式的过程中使用**。它们主要用于[mixins](http://sass.bootcss.com/docs/sass-reference/#mixins)，特别是像[Compass](http://compass-style.org/)这样的库的一部分，因此需要很大的灵活性。

### `@if`

该`@if`指令需要SassScript表达和使用嵌套在它下面的样式，如果表达式返回以外的任何其他`false`或`null`：

```
p {
  @if 1 + 1 == 2 { border: 1px solid;  }
  @if 5 < 3      { border: 2px dotted; }
  @if null       { border: 3px double; }
}
```

被编译为：

```
p {
  border: 1px solid; }
```

该`@if`声明后面可以跟几个`@else if`声明和一个`@else`声明。如果`@if`语句失败，`@else if`则按顺序尝试语句，直到成功或`@else`到达为止。例如：

```
$type: monster;
p {
  @if $type == ocean {
    color: blue;
  } @else if $type == matador {
    color: red;
  } @else if $type == monster {
    color: green;
  } @else {
    color: black;
  }
}
```

被编译为：

```
p {
  color: green; }
```

### `@for`

该`@for`指令重复输出一组样式。对于每次重复，使用计数器变量来调整输出。该指令有两种形式： `@for $var from <start> through <end>`和`@for $var from <start> to <end>`。注意关键字的区别`through`和`to`。`$var`可以是任何变量名称，如`$i`; `<start>`并且`<end>`是应该返回整数的SassScript表达式。

该`@for`语句设置`$var`为指定范围内的每个连续数字，并且每次使用该值输出嵌套样式`$var`。对于具有以下形式`from ... through`，所述范围*包括*的值`<start>`和 `<end>`，但形式`from ... to`运行至*但不包括*的值`<end>`。使用`through`语法，

```
@for $i from 1 through 3 {
  .item-#{$i} { width: 2em * $i; }
}
```

被编译为：

```
.item-1 {
  width: 2em; }
.item-2 {
  width: 4em; }
.item-3 {
  width: 6em; }
```

### `@each`

该`@each`规则的形式`@each $var in <list>`。 `$var`可以是任何变量名，例如`$length`或`$name`，`<list>`是一个返回列表的SassScript表达式。

该`@each`规则集`$var`列表中的每个项目，然后输出它包含使用该值的风格`$var`。例如：

```
@each $animal in puma, sea-slug, egret, salamander {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
  }
}
```

被编译为：

```
.puma-icon {
  background-image: url('/images/puma.png'); }
.sea-slug-icon {
  background-image: url('/images/sea-slug.png'); }
.egret-icon {
  background-image: url('/images/egret.png'); }
.salamander-icon {
  background-image: url('/images/salamander.png'); }
```

### `@while`

该`@while`指令采用SassScript表达式并重复输出嵌套样式，直到语句求值为止`false`。这可以用来实现比`@for`语句更复杂的循环，尽管这很少是必要的。例如：

```
$i: 6;
@while $i > 0 {
  .item-#{$i} { width: 2em * $i; }
  $i: $i - 2;
}
```

被编译为：

```
.item-6 {
  width: 12em; }

.item-4 {
  width: 8em; }

.item-2 {
  width: 4em; }
```

## Mixin Directives

Mixins允许您定义可以在整个样式表中重复使用的样式，而无需使用非语义类`.float-left`。Mixins还可以包含完整的CSS规则，以及Sass文档中其他地方允许的任何其他规则。他们甚至可以采取一些[参数](http://sass.bootcss.com/docs/sass-reference/#mixin-arguments) ，这些[参数](http://sass.bootcss.com/docs/sass-reference/#mixin-arguments)可以让你用很少的mixin来制作各种各样的风格。

### 定义Mixin： `@mixin`

Mixins是用`@mixin`指令定义的。接下来是mixin的名称和可选的[参数](http://sass.bootcss.com/docs/sass-reference/#mixin-arguments)，以及包含mixin内容的块。例如，`large-text`mixin定义如下：

```
@mixin large-text {
  font: {
    family: Arial;
    size: 20px;
    weight: bold;
  }
  color: #ff0000;
}
```

Mixins还可能包含选择器，可能与属性混合。选择器甚至可以包含[父引用](http://sass.bootcss.com/docs/sass-reference/#referencing_parent_selectors_)。例如：

```
@mixin clearfix {
  display: inline-block;
  &:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
  }
  * html & { height: 1px }
}
```

### Including a Mixin: `@include`

Mixins包含在带有该`@include`指令的文档中。这将使用mixin的名称和可选的[参数传递给它](http://sass.bootcss.com/docs/sass-reference/#mixin-arguments)，并将mixin定义的样式包含在当前规则中。例如：

```
.page-title {
  @include large-text;
  padding: 4px;
  margin-top: 10px;
}
```

被编译为：

```
.page-title {
  font-family: Arial;
  font-size: 20px;
  font-weight: bold;
  color: #ff0000;
  padding: 4px;
  margin-top: 10px; }
```

Mixins也可以包含在任何规则之外（即文档的根目录），只要它们不直接定义任何属性或使用任何父引用。例如：

```
@mixin silly-links {
  a {
    color: blue;
    background-color: red;
  }
}

@include silly-links;
```

被编译为：

```
a {
  color: blue;
  background-color: red; }
```

Mixin定义还可以包括其他mixins。例如：

```
@mixin compound {
  @include highlighted-background;
  @include header-text;
}

@mixin highlighted-background { background-color: #fc0; }
@mixin header-text { font-size: 20px; }
```

mixin可能不直接或间接地包含在内。也就是说，禁止使用mixin递归。

仅定义后代选择器的Mixins可以安全地混合到文档的最顶层。

### 参数

Mixins可以将参数SassScript值作为参数，这些参数在包含mixin时提供，并在mixin中作为变量提供。

在定义mixin时，参数被写为以逗号分隔的变量名，全部在名称后面的括号中。然后，当包括mixin时，可以以相同的方式传入值。例如：

```
@mixin sexy-border($color, $width) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}

p { @include sexy-border(blue, 1in); }
```

被编译为：

```
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }
```

Mixins还可以使用常规变量设置语法为其参数指定默认值。然后，当包含mixin时，如果它没有传入该参数，则将使用默认值。例如：

```
@mixin sexy-border($color, $width: 1in) {
  border: {
    color: $color;
    width: $width;
    style: dashed;
  }
}
p { @include sexy-border(blue); }
h1 { @include sexy-border(blue, 2in); }
```

被编译为：

```
p {
  border-color: blue;
  border-width: 1in;
  border-style: dashed; }

h1 {
  border-color: blue;
  border-width: 2in;
  border-style: dashed; }
```

#### 关键字参数

也可以使用显式关键字参数包含Mixins。例如，我们上面的例子可以写成：

```
p { @include sexy-border($color: blue); }
h1 { @include sexy-border($color: blue, $width: 2in); }
```

虽然这不太简洁，但它可以使样式表更容易阅读。它还允许函数呈现更灵活的接口，提供许多参数而不会变得难以调用。

命名参数可以按任何顺序传递，并且可以省略具有默认值的参数。由于命名参数是变量名，因此下划线和短划线可以互换使用。

#### 变量参数

有时候，mixin采用未知数量的参数是有意义的。例如，用于创建框阴影的mixin可能会将任意数量的阴影作为参数。对于这些情况，Sass支持“变量参数”，它是mixin声明末尾的参数，它接受所有剩余的参数并将它们打包为[列表](http://sass.bootcss.com/docs/sass-reference/#lists)。这些参数看起来就像普通参数一样，但后面跟着`...`。例如：

```
@mixin box-shadow($shadows...) {
  -moz-box-shadow: $shadows;
  -webkit-box-shadow: $shadows;
  box-shadow: $shadows;
}

.shadows {
  @include box-shadow(0px 4px 5px #666, 2px 6px 10px #999);
}
```

被编译为：

```
.shadows {
  -moz-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  -webkit-box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
  box-shadow: 0px 4px 5px #666, 2px 6px 10px #999;
}
```

调用mixin时也可以使用变量参数。使用相同的语法，可以展开值列表，以便将每个值作为单独的参数传递。例如：

```
@mixin colors($text, $background, $border) {
  color: $text;
  background-color: $background;
  border-color: $border;
}

$values: #ff0000, #00ff00, #0000ff;
.primary {
  @include colors($values...);
}
```

被编译为：

```
.primary {
  color: #ff0000;
  background-color: #00ff00;
  border-color: #0000ff;
}
```

您可以使用变量参数来包装mixin并添加其他样式，而无需更改mixin的参数签名。如果这样做，即使是关键字参数也会传递给包装的mixin。例如：

```
@mixin wrapped-stylish-mixin($args...) {
  font-weight: bold;
  @include stylish-mixin($args...);
}

.stylish {
  // The $width argument will get passed on to "stylish-mixin" as a keyword
  @include wrapped-stylish-mixin(#00ff00, $width: 100px);
}
```

### 将内容块传递给Mixin

可以将一个样式块传递给mixin，以便放置在mixin所包含的样式中。样式将出现在`@content`mixin中找到的任何指令的位置。这使得可以定义与选择器和指令的构造有关的抽象。

例如：

```
@mixin apply-to-ie6-only {
  * html {
    @content;
  }
}
@include apply-to-ie6-only {
  #logo {
    background-image: url(/logo.gif);
  }
}
```

产生：

```
* html #logo {
  background-image: url(/logo.gif);
}
```

可以用`.sass`简写语法完成相同的mixin ：

```
=apply-to-ie6-only
  * html
    @content

+apply-to-ie6-only
  #logo
    background-image: url(/logo.gif)
```

**注意：**当`@content`指令多次指定或在循环中指定时，样式块将在每次调用时重复。

#### 可变范围和内容块

传递给mixin的内容块在定义块的范围内进行评估，而不是在mixin的范围内。这意味着mixin的局部变量**不能**在传递的样式块中使用，变量将解析为全局值：

```
$color: white;
@mixin colors($color: blue) {
  background-color: $color;
  @content;
  border-color: $color;
}
.colors {
  @include colors { color: $color; }
}
```

编译为：

```
.colors {
  background-color: blue;
  color: white;
  border-color: blue;
}
```

此外，这清楚地表明在传递的块中使用的变量和mixin与定义块的周围的其他样式有关。例如：

```
#sidebar {
  $sidebar-width: 300px;
  width: $sidebar-width;
  @include smartphone {
    width: $sidebar-width / 3;
  }
}
```

## 功能指令

可以在sass中定义自己的函数，并在任何值或脚本上下文中使用它们。例如：

```
$grid-width: 40px;
$gutter-width: 10px;

@function grid-width($n) {
  @return $n * $grid-width + ($n - 1) * $gutter-width;
}

#sidebar { width: grid-width(5); }
```

变为：

```
#sidebar {
  width: 240px; }
```

正如您所看到的，函数可以访问任何全局定义的变量，也可以像mixin一样接受参数。函数可能包含多个语句，您必须调用`@return`以设置函数的返回值。

与mixins一样，您可以使用关键字参数调用Sass定义的函数。在上面的例子中，我们可以像这样调用函数：

```
#sidebar { width: grid-width($n: 5); }
```

建议您在函数前添加前缀以避免命名冲突，以便样式表的读者知道它们不属于Sass或CSS。例如，如果您在ACME Corp工作，您可能已将上述功能命名为`-acme-grid-width`。

用户定义的函数也 以与mixin相同的方式支持[变量参数](http://sass.bootcss.com/docs/sass-reference/#variable_arguments)。

## 输出方式

虽然Sass输出的默认CSS样式非常好并且反映了文档的结构，但品味和需求各不相同，因此Sass支持其他几种样式。

Sass允许您通过设置[`:style`选项](http://sass.bootcss.com/docs/sass-reference/#style-option) 或使用`--style`命令行标志在四种不同的输出样式之间进行选择。

### `:nested`

嵌套样式是默认的Sass样式，因为它反映了CSS样式的结构和它们样式化的HTML文档。每个属性都有自己的行，但缩进不是常量。每个规则都根据嵌套的深度缩进。例如：

```
#main {
  color: #fff;
  background-color: #000; }
  #main p {
    width: 10em; }

.huge {
  font-size: 10em;
  font-weight: bold;
  text-decoration: underline; }
```

在查看大型CSS文件时，嵌套样式非常有用：它允许您轻松掌握文件的结构，而无需实际读取任何内容。

### `:expanded`

Expanded是一种更典型的人造CSS样式，每个属性和规则占用一行。属性在规则中缩进，但规则不以任何特殊方式缩进。例如：

```
#main {
  color: #fff;
  background-color: #000;
}
#main p {
  width: 10em;
}

.huge {
  font-size: 10em;
  font-weight: bold;
  text-decoration: underline;
}
```

### `:compact`

紧凑型比嵌套式或扩展型占用更少的空间。它也更多地关注选择者而不是他们的属性。每个CSS规则只占用一行，并在该行上定义每个属性。嵌套规则彼此相邻放置，没有换行符，而单独的规则组在它们之间有换行符。例如：

```
#main { color: #fff; background-color: #000; }
#main p { width: 10em; }

.huge { font-size: 10em; font-weight: bold; text-decoration: underline; }
```

### `:compressed`

压缩样式占用尽可能少的空间，除了分隔选择器和文件末尾的换行符所必需的空格之外没有空格。它还包括一些其他的小压缩，例如选择最小的颜色表示。它并不意味着人类可读。例如：

```
#main{color:#fff;background-color:#000}#main p{width:10em}.huge{font-size:10em;font-weight:bold;text-decoration:underline}
```

## 扩展Sass

Sass为具有独特要求的用户提供了许多高级自定义。使用这些功能需要对Ruby有很好的理解。

### 定义自定义Sass函数

用户可以使用Ruby API定义自己的Sass函数。有关更多信息，请参阅[源文档](http://sass.bootcss.com/docs/sass-reference/Sass/Script/Functions.html#adding_custom_functions)。

### 缓存商店

Sass缓存已解析的文档，以便可以重复使用它们，而无需再次解析它们，除非它们已更改。默认情况下，Sass会将这些缓存文件写入指示的文件系统上的某个位置[`:cache_location`](http://sass.bootcss.com/docs/sass-reference/#cache_location-option)。如果您无法写入文件系统或需要跨ruby进程或计算机共享缓存，则可以定义自己的缓存存储并设置该[`:cache_store` 选项](http://sass.bootcss.com/docs/sass-reference/#cache_store-option)。有关创建自己的缓存存储的详细信息，请参阅{Sass :: CacheStores :: Base源文档}。

### 定制进口商

Sass导入器负责传递路径`@import`并为这些路径找到适当的Sass代码。默认情况下，此代码是从{Sass :: Importers :: Filesystem filesystem}加载的，但可以添加导入程序以通过HTTP从数据库加载，或使用与Sass预期不同的文件命名方案。

每个导入器负责一个负载路径（或者后端的相应概念）。可以将导入程序`:load_paths`与普通文件系统路径一起放在{file：SASS_REFERENCE.md＃load_paths-option 数组}中。

解析时`@import`，Sass将通过加载路径查找成功导入路径的导入程序。找到一个后，将使用导入的文件。

用户创建的导入程序必须从{Sass :: Importers :: Base}继承。