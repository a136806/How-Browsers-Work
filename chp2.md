‏‪#‬ Chapter 2


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




‏‪##‬ THE MAIN FLOW‪:‬


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