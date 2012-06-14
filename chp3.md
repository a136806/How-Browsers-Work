# CHAPTER 3

## 3.1 PARSING — GENERAL


التحليل أو الـParsing هي عملية هامة جدا في المحرك ‪(‬Rendering Engine‪)‬، وسوف ندخلها أكثر عمقا. دعونا نبدأ مع مقدمة قليلا عن تحليل. 
 تحليل الصفحة يعني تحويلها الي حيكل يفهمه و يستخدمه الكود code.
 نتيجة التحليل غلبا ما تكون شجرة تمثل محتوي الصفحة أو النص، و تسمي بـ‪"‬Parse Tree‪"‬ أو الـ‪"‬Syntax Tree‪"‬.

مثال — ٢+٣-١ ممكن تمثيلها في:

‏‪![Figure ‬5‪: mathematical expression tree node](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/image009.png)‬


## 3.1.1 GRAMMER

 
كل نوع ملف له القواعد الخاصة به ،  و يكون الفصل بين النصوص و الكلمات المميزة اللي بتفهم المتصفح!..تعرف ب- context free grammar.


##
#‪#‬ 3.1.2 PARSER-LEXER COMBINATION
##


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


سعتها ممكن نعرف لغتنا بالشكل دا، مستجدمين ال-[Regular Expression](http://en.wikipedia.org/wiki/Regular_expression) :

INTEGER :0|[1-9][0-9]*
PLUS : +
MINUS: -
و غالبا النحو بيعرف بطرقة BNF.
ممكن نعرف لغتنا بهذا الشكل:
expression :=  term  operation  term
operation :=  PLUS | MINUS
term := INTEGER | expression

عامتا، طريقة BNF ،من غير حاجات زيادة أو محتويات أو context free grammar ، بتشتغل مع أي parser تقليدي.

### 3.1.6 Types of parsers

في نوعان أساسيان من parsers ، واحد بيشتغل من فوق لتحت و الآخر من تحت لفوق.
بمعني، أن لو عرفت الحاجات الأساسية السهلة ممكن تجيب بيها الحاجات الأصعب و المعقدة (من تحت لفوق) ، أو العكس، تجيب الحاجات الصعبة المعقدة و تبحث عن علاقة بها و بين الحاجات اللي لسة ما قرأتها (من فوق لتحت).


يعني parser لو قرأها من فوق لتحت ، حيعتبر 2 + 3 مصتلح (expression) ، و 2+3-1 كمصتلح أكبر مرتبط.

Parsers اللي بتقرأ من تحت-فوق بتستخدم
StackInput:

The bottom up parser will scan the input until a rule is matched it will then replace the matching input with the rule. This will go on until the end of the input. The partly matched expression is placed on the parsers stack.StackInput
 2 + 3 - 1
term+ 3 - 1
term operation3 - 1
expression- 1
expression operation1
expression 
This type of bottom up parser is called a shift-reduce parser, because the input is shifted to the right (imagine a pointer pointing first at the input start and moving to the right) and is gradually reduced to syntax rules.