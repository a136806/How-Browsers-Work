
## من انتم؟:



أنا 
‏<a href="mailto:yoga1290@gmail.com">يوسف جميل (Youssef Gamil)</a‪>‬

 طالب كمبيوتر ,حاسيس ان فيه وقت كتير في حياتي عشان اعمل حاجات كتير لتطوير أشياء مفيدة... أو ترجمة كتاب زي ده!


هدا التكست ملخص و مترجم من كتاب 

‏<a href="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/">HTML5 ROCKS/ HOW BROWSERS WORK: BEHIND THE SCENES OF MODERN WEB BROWSERS</a>


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

‏- Address bar for inserting the URI
‏- Back and forward buttons
‏- Bookmarking options
‏- A refresh and stop buttons for refreshing and stopping the loading of current documents
‏- Home button that gets you to your home page


جبهة الــUI ليس لها اي مواصفات رسمية ، بس دا بيكون اجتهاد و خبرة سنين و متصفحات بتنقل من بعض.

الــHTML5 ليس له مواصفات معينة لالوجهات ‪"‬الــ‪"‬UI ،بس بيوصف شويت الحاجات المشتركة.




‪#‬# الهيكل العام لدي المتصفح:



‏- UI:
	جبهة المستخدم ، التي تتضمن كل شئ ثابت، كشريت العنوان و زر الرجوع	
‏- The browser engine:
 اللي بيضبط الوجهات مع  rendering engine

‏- The rendering engine ‫:‬ 
 مسؤل عن عرض المحتويات المطلوبة.كـدمج مكونات الــHTML5 مع الــCSS وازهارها علي الشاشة.

‏- Network:
مسئول عن   التعامل مع بروتكول الــHTTP 

‏- UI backend:
يستخدم  في عرض الوجهات الــUI الاساسية من نظام التشغيل OS‪.‬

‏- JavaScript interpreter:
بيترجم و ينفذ كود الـJavaScript 

‏- Data Storage:
بتكون منصلة و لديها القدرة علي التخزين الدائم، تحتفض بمعلومات مثل الــCookies،
تتمتع النسخة الجديدة HTML5 علي جميع مواصفات قواعد البينات بس بتكون خفيفة.
‏‪'‬web database‪'‬


‏<img src="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/layers.png">


جدير بالذكر ان Chrome‪,‬ غير كل المتصفحات ، يخلق rendering engine الخاص لكل صفحة أو tab. 



‏### Chapter 2



‏# THE RENDERING ENGINE




وضيفته هي  عرض المكونات المطلوبة علي الشاشة…
 في اساس هو بيعرض الــHTML و الــXML و الصور. و لكنه قادر علي عرض مكونات اخري عن طريق plug‪-‬in او extension‪;‬
مثال: عرض الــPDF عن طريق PDF viewing plug‪-‬in.
.‫.‬لكننا سنركز علي المهام الاساسي، و هو عرض الصور ،و الــHTML و الـCSS .




‏## RENDERING ENGINES




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

‏<img src="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/flow.png" >

يبدأ الـrendering engine بتكوين شجرة من الـDOM بعد مرحلة المعالجة للـHTML، تسمي بــ‪"‬content tree‪"‬.
تعالج الـCSS اللي موجود داخل الصفة و الموجود خارجها اذا احتاجته.
من معلومات الـCSS و اوامر الـHTML المتحكمة في المرئيات، يكون شجرة اخري تسمي render tree‪"‬". 


الـ"render tree‪"‬،
بتحتوي علي المستطيلات بمكونات مرئية كالوان أو مساحات. المستطيلات تكون بالترتيب الصحيح لكي تعرض علي شاشة.

بعد تكوين الـrender tree ، تأتي مرحلة الـ"ـlayout"،
ويعني ، ان نعتي كول جزء من الشجرة (node) موقع دقيق علي الشاشة.

يأتي بعد ذلك مرحلة التلوين أو الـ"painting".

وهي تلوين كل خلية/جزء من شجرة الـrender tree
بإستخدام الـUI‪-‬backend.


من المهم أن نفهم أن هذة العملية تدريجية.
من أجل تجربة أفضل للمستخدم، فإن محرك الـrender يحاولة عرض المحتويات على الشاشة في أسرع وقت ممكن.
لن ينتظر حتى يتم تحليل جميع HTML قبل البدء في بناء وتخطيط الشجرة render tree.
و ييتم تحليل أجزاء من المحتوى وعرضها، و تستمرت العملية مع بقية محتويات التي تأتي من الشبكة.

مثال عن الخطوات لمحرك الويب-كيت (Webkit):



‏<img src="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/‪webkitflow‬.png" >


مثال عن الخطوات لمحرك الـجيكو (Gecko):


‏<img src="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/‪image008.jpg‬" >



‏Gecko يستدعي الشجرة التي أنشانها في مرحلة التلوين ‪(‬Render Tree‪)‬،و يكون شجرة الـ"Frame Tree".
كل خلية منها عبارة عن Frame (إطار أو جزء من الصفحة).

يستخدم الويب-كيت (WebKit) الـــــ‪"‬layout‪"‬ لتحديد اماكن المكونات ، وتعرف بالظ"Reflow" في المحرك الـجيكو.(Gecko)

"آتاشمنت" أو "Attachment" ،هي اسم الذي يطلقه الويب-كيت (WebKit) علي ما يتكون من دمجك خليات شجرة الـDOM أو DOM Nodes مع المعلومات المرئية عنها، وذلك لتكوين شجرة الـRender أو الـ‪"‬Render Tree‪"‬.

فرق بسيت بين الجيكو و الويب-كيت، ان الجيكو بيكون فيه مرحلة الـ"Content Sink" بين شجرة الـDOM أو ‪(‬DOM Tree‪)‬ و الـHTML ، و هي لا تغير في النتيجة عن الويب-كيت، و لكنها عامل لتكوين الـDOM.
سنتحدث عنها فيما بعد.



‏### ‪###‬ Chapter 3




‏# ‪#‬ PARSING — GENERAL




