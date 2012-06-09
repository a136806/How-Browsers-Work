‪#‬CHAPTER 3



## 3.1 PARSING — GENERAL


التحليل أو الـParsing هي عملية هامة جدا في المحرك ‪(‬Rendering Engine‪)‬، وسوف ندخلها أكثر عمقا. دعونا نبدأ مع مقدمة قليلا عن تحليل.

تحليل الصفحة يعني تحويلها الي حيكل يفهمه و يستخدمه الكود code.
نتيجة التحليل غلبا ما تكون شجرة تمثل محتوي الصفحة أو النص، و تسمي بـ‪"‬Parse Tree‪"‬ أو الـ‪"‬Syntax Tree‪"‬.

مثال — ٢+٣-١ ممكن تمثيلها في:

‏‪![Figure ‬5‪: mathematical expression tree node](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image009.png)‬


#‪#‬# Grammer


كل نوع ملف له القواعد الخاصة به ،  و يكون الفصل بين النصوص و الكلمات المميزة اللي بتفهم المتصفح!..تعرف ب- context free grammar.


#‪#‬# 3.1.2 Parser - Lexer combination

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



## Translation ##


## الترجمة 


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


‪#‬## Formal definitions for vocabulary and syntax ###


في الواقع، النحو ذات نفسه بيصف بالـ
‏‪[‬ regular expressions ‪](http://www.regular-expressions.info/).‬



