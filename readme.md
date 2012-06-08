
## من انتم؟:



أنا 
‏<a href="mailto:yoga1290@gmail.com">يوسف جميل (Youssef Gamil)</a‪>‬

 طالب كمبيوتر ,حاسيس ان فيه وقت كتير في حياتي عشان اعمل حاجات كتير لتطوير أشياء مفيدة... أو ترجمة كتاب زي ده!


هدا التكست ملخص و مترجم من كتاب
 
‏‪[‬HTML5 ROCKS ‪/‬ HOW BROWSERS WORK‪:‬ BEHIND THE SCENES OF MODERN WEB BROWSER‪](http://www.html5rocks.com/en/tutorials/)‬


الذي يلخص ابحاث دفيلبر اسرائيلية جوجلية "تالي جارسريل" , التي امضت وقت طويل في مراجعة مصادر المتصفحات.




# المقدمة:


......

# الفهرس:


الفهرس‪:‬

المقدمة‪-‬ 
المتصفحات اللي حنتكلم عنها‪-‬ 
مهمة المتثصفح الاساسية‪-‬ 
هيكل المتصفح‪-‬ 




## المتصفح:



هناك 5 متصفحات اساسية تستعمل اليوم 
‏-  Internet Explorer, Firefox, Safari, Chrome و Opera.

 الامثلة ستكون من متصفحات شبه مفتوحة المصدر
‏ (  Firefox, Chrome and Safari ).



## المتصفح موجود ليه أساسن؟:



مهمة المتصفح الأساسية هي تجميع المكونات التتي تحتاج اليها من الانترنت و عن طريق طلبها من الخادم و ثم اطلاقها علي شاشتك!

 المكونات غالبا تكون صفحات HTML , PDF , PDF , أو صور أو أخري.

 عنوان المكونات يكون متحدد من المستخم عن طريق الـURI (Uniform Resource Identifier).

الطريقة التي يفسر بها المتصفح صفحات الــHTML ، بتكون مشروحة بتفاصيل بمواصفات الـــ
‏HTML و CSS 
المطفق عليها في العالم من الـــ 
‏W3C (World Wide Web Consortium)

زمان، كان كل متصفح بيخترع مواصفاته ، فكانت الحياة صعبة علي المطورين.بس دلوقتي معضم المتصفحات تعمل بنفس الطريقة.



معضم المتصفحات اليوم لها نفس الوجهة ، من ابحاجات المشترقة هي:

‏‪*‬ Address bar for inserting the URI
‏‪*‬ Back and forward buttons
‏‪*‬ Bookmarking options
‏‪*‬ A refresh and stop buttons for refreshing and stopping the loading of current documents
‏‪*‬ Home button that gets you to your home page


جبهة الــUI ليس لها اي مواصفات رسمية ، بس دا بيكون اجتهاد و خبرة سنين و متصفحات بتنقل من بعض.

الــHTML5 ليس له مواصفات معينة لالوجهات ‪"‬الــ‪"‬UI ،بس بيوصف شويت الحاجات المشتركة.




‪#‬# الهيكل العام لدي المتصفح:



‏‪*‬ UI‪:‬

جبهة المستخدم ، التي تتضمن كل شئ ثابت، كشريت العنوان و زر الرجوع	
‏‪*‬ The browser engine‪:‬

اللي بيضبط الوجهات مع  rendering engine

‏‪*‬ The rendering engine‪:‬ 

مسؤل عن عرض المحتويات المطلوبة.كـدمج مكونات الــHTML5 مع الــCSS وازهارها علي الشاشة.

‏‪*‬ Network‪:‬

مسئول عن   التعامل مع بروتكول الــHTTP 

‏‪*‬ UI backend‪:‬

يستخدم  في عرض الوجهات الــUI الاساسية من نظام التشغيل OS‪.‬

‏‪*‬ Javascript Interpreter‪:‬

بيترجم و ينفذ كود الـJavaScript 

‏‪*‬ Data Storage‪:‬

بتكون منصلة و لديها القدرة علي التخزين الدائم، تحتفض بمعلومات مثل الــCookies،
تتمتع النسخة الجديدة HTML5 علي جميع مواصفات قواعد البينات بس بتكون خفيفة.
‏‪'‬web database‪'‬

‏‪![Figure 1: Browser main components.](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/layers.png)‬

جدير بالذكر ان Chrome‪,‬ غير كل المتصفحات ، يخلق rendering engine الخاص لكل صفحة أو tab. 



‏‪###‬ Chapter 2


‏‪##‬ THE RENDERING ENGINE


وضيفته هي  عرض المكونات المطلوبة علي الشاشة…
 في اساس هو بيعرض الــHTML و الــXML و الصور. و لكنه قادر علي عرض مكونات اخري عن طريق plug‪-‬in او extension‪;‬
مثال: عرض الــPDF عن طريق PDF viewing plug‪-‬in.
.‫.‬لكننا سنركز علي المهام الاساسي، و هو عرض الصور ،و الــHTML و الـCSS .



‏‪##‬ RENDERING ENGINE




المتصفحات اللي بنكلم عنها بتتكون من ٢ rendering engines،  و هما:

‏Firefox بيستخدم الجيكو (Gecko)
‏Safari و Chrome بيستخدموا الويب-كيت (Webkit).

‏Webkit هو مفتوح المصدر
و الذي بدأ خصيصا للينكس Linux ، ثم عدلته آبل Apple ليعمل علي  الماك و الويندوز.
‏Mac & Windows.

لمزيد من المعلومات:

‏<a href="http://webkit.org">Webkit.org</a>




‏## THE MAIN FLOW:


يبدأ الــrendering engine بتجميع المكونات المطلوبة من الشبكة Network Layer.
غالبا، بيقسمها علي ٨ كيلو قطعة.
الخطوات الاساسية للــrendering engine تتمثل في الخطوات التالية:

‏‪![Figure 2: Rendering engine basic flow](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/flow.png)‬

يبدأ الـrendering engine بتكوين شجرة من الـDOM بعد مرحلة المعالجة للـHTML، تسمي بــ‪"‬content tree‪"‬.
تعالج الـCSS اللي موجود داخل الصفة و الموجود خارجها اذا احتاجته.
من معلومات الـCSS و اوامر الـHTML المتحكمة في المرئيات، يكون شجرة اخري تسمي render tree‪"‬". 


الـ"render tree‪"‬،
بتحتوي علي المستطيلات بمكونات مرئية كالوان أو مساحات. المستطيلات تكون بالترتيب الصحيح لكي تعرض علي شاشة.

بعد تكوين الـrender tree ، تأتي مرحلة الـ"ـlayout"،
ويعني ، ان نعتي كول جزء من الشجرة (node) موقع دقيق علي الشاشة.

يأتي بعد ذلك مرحلة التلوين أو الـ"painting".

وهي تلوين كل خلية/جزء من شجرة الـrender tree
بإستخدام الـUI‪-‬backend.


من المهم أن نفهم أن هذة العملية تدريجية.
من أجل تجربة أفضل للمستخدم، فإن محرك الـrender يحاولة عرض المحتويات على الشاشة في أسرع وقت ممكن.
لن ينتظر حتى يتم تحليل جميع HTML قبل البدء في بناء وتخطيط الشجرة render tree.
و ييتم تحليل أجزاء من المحتوى وعرضها، و تستمرت العملية مع بقية محتويات التي تأتي من الشبكة.

مثال عن الخطوات لمحرك الويب-كيت (Webkit):

‏‪![Figure 3: Webkit main flow](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/webkitflow.png)‬

مثال عن الخطوات لمحرك الـجيكو (Gecko):

‪![‬
‏‪Figure 4: Mozilla's Gecko rendering engine main flow(3.6)](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image008.jpg)‬


‏Gecko يستدعي الشجرة التي أنشانها في مرحلة التلوين ‪(‬Render Tree‪)‬،و يكون شجرة الـ"Frame Tree".
كل خلية منها عبارة عن Frame (إطار أو جزء من الصفحة).

يستخدم الويب-كيت (WebKit) الـــــ‪"‬layout‪"‬ لتحديد اماكن المكونات ، وتعرف بالظ"Reflow" في المحرك الـجيكو.(Gecko)

"آتاشمنت" أو "Attachment" ،هي اسم الذي يطلقه الويب-كيت (WebKit) علي ما يتكون من دمجك خليات شجرة الـDOM أو DOM Nodes مع المعلومات المرئية عنها، وذلك لتكوين شجرة الـRender أو الـ‪"‬Render Tree‪"‬.

فرق بسيت بين الجيكو و الويب-كيت، ان الجيكو بيكون فيه مرحلة الـ"Content Sink" بين شجرة الـDOM أو ‪(‬DOM Tree‪)‬ و الـHTML ، و هي لا تغير في النتيجة عن الويب-كيت، و لكنها عامل لتكوين الـDOM.
سنتحدث عنها فيما بعد.


‏### Chapter 3
‏# PARSING — GENERAL

التحليل أو الـParsing هي عملية هامة جدا في المحرك ‪(‬Rendering Engine‪)‬، وسوف ندخلها أكثر عمقا. دعونا نبدأ مع مقدمة قليلا عن تحليل.

تحليل الصفحة يعني تحويلها الي حيكل يفهمه و يستخدمه الكود code.
نتيجة التحليل غلبا ما تكون شجرة تمثل محتوي الصفحة أو النص، و تسمي بـ‪"‬Parse Tree‪"‬ أو الـ‪"‬Syntax Tree‪"‬.

مثال — ٢+٣-١ ممكن تمثيلها في:

‏‪![Figure ‬5‪: mathematical expression tree node](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image009.png)‬


‏## 3.1.1 Grammars


كل نوع ملف له القواعد الخاصة به ،  و يكون الفصل بين النصوص و الكلمات المميزة اللي بتفهم المتصفح!..تعرف ب- context free grammar.

‏## 3.1.2 Parser - Lexer combination

التحليل بينقسم إلي جزئين:
التحليل الآبجدي ، و تحليل النحو.
التحليل الأبجدي بيقسم النص الي أجزاء صغيرة بنفس الترتيب أو Tokens.
أما التحليل النحوي فهو تطبيق القواعد.

‏Parsers بتنقسم الي جزئين،
جزء بيقسم النصوص lexer و المسؤل عن التصرف في الحروف الغريبة كالمسافة أو (سطر جديد) ،
و الاخر  بيبني شجرة باستخدام ما تكون من ال lexer علي حسب نوع الملف/النص.‪(‬parser‪)‬

‏‪![Figure 6: from source document to parse trees](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image011.png)‬

‏The parsing process is iterative. The parser will usually ask the lexer for a new token and try to match the token with one of the syntax rules. If a rule is matched, a node corresponding to the token will be added to the parse tree and the parser will ask for another token.

‏If no rule matches, the parser will store the token internally, and keep asking for tokens until a rule matching all the internally stored tokens is found. If no rule is found then the parser will raise an exception. This means the document was not valid and contained syntax errors.


‏‪##‬ Translation


الترجمة:

‏Many times the parse tree is not the final product. Parsing is often used in translation - transforming the input document to another format. An example is compilation. The compiler that compiles a source code into machine code first parses it into a parse tree and then translates the tree into a machine code document.
تغالبا ما بيكون شجرة التحليل هي آخر حاجة...غالبا التحليل بيستخدم في الترجمة لخلق شيء جديد! ... زي تحويل الكود لكود الآلة.


‏‪![Figure 7: compilation flow](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image013.png)‬


‏Parsing example



‏In figure 5 we built a parse tree from a mathematical expression. Let's try to define a simple mathematical language and see the parse process.
من شكل 5، شجرة التحليل مكونة من عملية حسابية ،لنضرب مثال بسيط )غير واقعي(: 

‏Vocabulary:
افترض أن اللغة مكونة من -،+، و أرقام.

‏Syntax:

* في اللغتنا، النحو حيكون مبني من أجزاء من ‪**‬التعبيرات‪**‬ و ‪**‬المصطلحات‪**‬ و ‪**‬العمليات‪**‬ (فهمت أنا كدا؟!)
* في اللغتنا، ‪**‬التعبيرات‪**‬ ممكن تكون كتير و ما لها حد أقصي
* في اللغتنا، **التعبيرات‪**‬ من **مصطلح** و **عملية** ، ثم **مصتلح** و **عملية**،… إلخ.

حيث، **العملية** هي: + أو - ، **المصطلح** هو رقم أو رقم ناتج من **تعبير** آخر!


٢+٣-١ علي ثبيل المثال: الـ٢+٣ هو **تعبير** مكون من ٢و٣ كـ**مصطلحات** ، و + كـ**عملية** ، فيكون تعبير آكبر مكون من:
ناتج الـ**تعبير** الصابق (٢+٣) و ** عملية** (-) و **مصتلح** (١).


‏‪###‬ Formal definitions for vocabulary and syntax

في الواقع، النحو ذات نفسه بيصف بالـ
‏‪[‬ regular expressions ‪](http://www.regular-expressions.info/).‬



