## من انتم؟:
أنا 
<a href="mailto:yoga1290@gmail.com">يوسف جميل (Youssef Gamil)</a‪>‬
<br>
 طالب كمبيوتر ,حاسيس ان فيه وقت كتير في حياتي عشان اعمل حاجات كتير لتطوير أشياء مفيدة... أو ترجمة كتاب زي ده!
<br> 
هدا التكست ملخص و مترجم من كتاب 
<a href="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/">HTML5 ROCKS/ HOW BROWSERS WORK: BEHIND THE SCENES OF MODERN WEB BROWSERS</a>
<br>
الذي يلخص ابحاث دفيلبر اسرائيلية جوجلية "تالي جارسريل" , التي امضت وقت طويل في مراجعة مصادر المتصفحات.

<br>
# المقدمة:
<br>
......

#الفهرس:
‫-‬ المقدمة
	‫-‬المتصفحات اللي حنتكلم عنها
	‫-‬ مهمة المتثصفح الاساسية
	- هيكل المتصفح
‫…….‬


## المتصفح:
<br>
هناك 5 متصفحات اساسية تستعمل اليوم 
<br>
-  Internet Explorer, Firefox, Safari, Chrome و Opera.
<br>
 الامثلة ستكون من متصفحات شبه مفتوحة المصدر
<br>
 (  Firefox, Chrome and Safari ).

## المتصفح موجود ليه أساسن؟:

مهمة المتصفح الأساسية هي تجميع المكونات التتي تحتاج اليها من الانترنت و عن طريق طلبها من الخادم و ثم اطلاقها علي شاشتك!
المكونات غالبا تكون صفحات HTML , PDF , PDF , أو صور أو أخري. عنوان المكونات يكون متحدد من المستخم عن طريق الـURI (Uniform Resource Identifier).

الطريقة التي يفسر بها المتصفح صفحات الــHTML ، بتكون مشروحة بتفاصيل بمواصفات الـــ
<br>
HTML و CSS
<br>
المطفق عليها في العالم من الـــ
<br>
W3C (World Wide Web Consortium)
<br>
زمان، كان كل متصفح بيخترع مواصفاته ، فكانت الحياة صعبة علي المطورين.
بس دلوقتي معضم المتصفحات تعمل بنفس الطريقة.
<br>
<br>

معضم المتصفحات اليوم لها نفس الوجهة ، من ابحاجات المشترقة هي:

- Address bar for inserting the URI
- Back and forward buttons
- Bookmarking options
- A refresh and stop buttons for refreshing and stopping the loading of current documents
- Home button that gets you to your home page

<br>
جبهة الــUI ليس لها اي مواصفات رسمية ، بس دا بيكون اجتهاد و خبرة سنين و متصفحات بتنقل من بعض.
<br>
  الــHTML5 ليس له مواصفات معينة لالوجهات ‪"‬الــ‪"‬UI ،بس بيوصف شويت الحاجات المشتركة.


#الهيكل العام لدي المتصفح:
<br>

- UI:
	جبهة المستخدم ، التي تتضمن كل شئ ثابت، كشريت العنوان و زر الرجوع	

- The browser engine:
اللي بيضبط الوجهات مع  rendering engine

- The rendering engine ‫:‬ 
مسؤل عن عرض المحتويات المطلوبة.
<br>
كـدمج مكونات الــHTML5 مع الــCSS وازهارها علي الشاشة.

- Network:
مسئول عن   التعامل مع بروتكول الــHTTP 

- UI backend:
يستخدم  في عرض الوجهات الــUI الاساسية من نظام التشغيل OS‪.‬

- JavaScript interpreter:
بيترجم و ينفذ كود الـJavaScript 

- Data Storage:
بتكون منصلة و لديها القدرة علي التخزين الدائم، تحتفض بمعلومات مثل الــCookies،
تتمتع النسخة الجديدة HTML5 علي جميع مواصفات قواعد البينات بس بتكون خفيفة.
‪'‬web database‪'‬

<br>
<img src="http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/layers.png">
<br>

جدير بالذكر ان Chrome‪,‬ غير كل المتصفحات ، يخلق  rendering engine الخاص لكل صفحة tab‪.‬
