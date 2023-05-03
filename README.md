Download Link: https://assignmentchef.com/product/solved-cs2030s-practical-assessment-1
<br>
<table width="683">

 <tbody>

  <tr>

   <td width="683">A quiz comprises questions of various forms such as multiple-choice questions (MCQ), true-false questions (TFQ), multiple-response questions (MRQ), fill-in-the-blanks, etc. After a quiz has been attempted by a student, the answers are locked-in for eventual grading (either automatically or by the examiner).<strong>Task</strong>In this task, we shall implement various types of quiz questions and how they are answered as well as graded.<strong>Take note of the following</strong>You are NOT allowed to use any java libraries, other than those from java.lang. In other words, import statements are not necessary.Ensure that there are NO cyclic dependencies in your implementation.Write each class/interface/enum in its own file.Ensure that ALL object properties and class constants are declared private final.You are NOT allowed to use Java reflection, i.e. Object::getClasses and other methods from the Classclass; in general keep to constructs that have been covered in the module.You are NOT allowed to use instanceof, other than within the same class (e.g. obj instanceof A within class A).You are NOT allowed to use null or any form of null values.You may assume that all tests provide valid arguments to methods; hence there is no need to validate method arguments.You are required to complete ALL levels.<strong>Level 1</strong>Write an immutable class FillInBlank with a constructor that takes in a question of type String, followed by the expected answer of type int.Include the answer method that takes in an integer as a guess. Note that the default guess is 0.

    <table width="609">

     <tbody>

      <tr>

       <td width="609">jshell&gt; FillInBlank fib = new FillInBlank(“Snow white and the ? dwarfs”, 7)fib ==&gt; Snow white and the ? dwarfs; Your answer: 0 jshell&gt; fib.answer(7)$.. ==&gt; Snow white and the ? dwarfs; Your answer: 7 jshell&gt; fib.answer(7).answer(3)$.. ==&gt; Snow white and the ? dwarfs; Your answer: 3 jshell&gt; fibfib ==&gt; Snow white and the ? dwarfs; Your answer: 0</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

<table width="609">

 <tbody>

  <tr>

   <td width="609">jshell&gt; Question q = new FillInBlank(“Snow white and the ? dwarfs”, 7) q ==&gt; Snow white and the ? dwarfs; Your answer: 0 jshell&gt; q.answer(3)$.. ==&gt; Snow white and the ? dwarfs; Your answer: 3</td>

  </tr>

 </tbody>

</table>

<h2>Level 2</h2>

Write an immutable MCQ class with a constructor that takes in a question of type String, the options as an array of Strings, and the expected answer choice of type int. You may assume that there are two or more options.

Include the answer method that takes in an integer as a guess.

jshell&gt; MCQ mcq = new MCQ(“Colour of orange?”, new String[]{“red”, “green”, “blue”, “orang mcq ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ ? ]




jshell&gt; mcq.answer(4)

$.. ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ 4:orange ]




jshell&gt; mcq.answer(4).answer(3)

$.. ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ 3:blue ]




jshell&gt; mcq.answer(4).answer(3).answer(4)

$.. ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ 4:orange ]

jshell&gt; mcq mcq ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ ? ]

<h2>Level 3</h2>

Write an immutable TFQ class for true-false questions with a constructor that takes in a question of type String, and the expected answer that is one of the Strings “True” or “False”.

Since a true-false question is just a multiple-choice question of two options, we can answer TFQs as though they are

MCQs.

In addition to the answer method in the preceding level, include another answer method that takes in “True” or “False” as a guess. You may assume that either “True” or “False” will be passed to the answer method. There is no need to check for case-sensitivity.

jshell&gt; TFQ tfq = new TFQ(“An orange is blue.”, “False”) tfq ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ ? ]




jshell&gt; tfq.answer(“True”)

$.. ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ 1:True ]




jshell&gt; tfq.answer(“False”)

$.. ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ 2:False ]




jshell&gt; MCQ mcq = tfq

mcq ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ ? ]




jshell&gt; mcq.answer(1)

$.. ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ 1:True ]




jshell&gt; tfq.answer(2)

$.. ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ 2:False ]




jshell&gt; mcq.answer(“True”)

|  Error:

|  incompatible types: java.lang.String cannot be converted to int

|  mcq.answer(“True”)

|             ^—-^

<h2>Level 4</h2>

After a student answers a question (possibly through multiple attempts), the question is then locked for marking later. Define a mark method that returns 1 if the guess is the same as the answer, and 0 otherwise.

Define a lock method such that changes in an answer can only be accepted before locking, and marking can only proceed after locking. The same applies for all types of questions. Note that in the sample test cases below, variable q is declared of type Question.

jshell&gt; q.answer(3).answer(4)

$.. ==&gt; Snow white and the ? dwarfs; Your answer: 4




jshell&gt; q.answer(3).answer(7).lock()

$.. ==&gt; Snow white and the ? dwarfs; Your answer: 7




jshell&gt; q.answer(3).answer(7).lock().answer(5)

|  Error:

|  cannot find symbol

|    symbol:   method answer(int)

|  q.answer(3).answer(7).lock().answer(5)

|  ^———————————^




jshell&gt; q.answer(3).answer(7).mark()

|  Error:

|  cannot find symbol

|    symbol:   method mark()

|  q.answer(3).answer(7).mark()

|  ^————————^




jshell&gt; q.answer(3).answer(7).lock().mark()

$.. ==&gt; 1

jshell&gt; q.answer(3).answer(7) instanceof FillInBlank

$.. ==&gt; true




jshell&gt; q.answer(3).answer(7).lock() instanceof FillInBlank

$.. ==&gt; true




jshell&gt; q.mark()

|  Error:

|  cannot find symbol

|    symbol:   method mark()

|  q.mark()

|  ^—-^

jshell&gt; q = new MCQ(“Colour of orange?”, new String[]{“red”, “green”, “blue”, “orange”}, 4

q ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ ? ]




jshell&gt; q.mark()

|  Error:

|  cannot find symbol

|    symbol:   method mark()

|  q.mark()

|  ^—-^

jshell&gt; q.answer(4).mark()

|  Error:

|  cannot find symbol

|    symbol:   method mark()

|  q.answer(4).mark()

|  ^————–^




jshell&gt; q.answer(4).lock().answer(3)

|  Error:

|  cannot find symbol

|    symbol:   method answer(int)

|  q.answer(4).lock().answer(3)

|  ^———————–^




jshell&gt; q.answer(4).lock().mark()

$.. ==&gt; 1

jshell&gt; q.answer(4).answer(3)

$.. ==&gt; Colour of orange? [1:red][2:green][3:blue][4:orange]; Your answer: [ 3:blue ]




jshell&gt; q.answer(4).answer(3) instanceof MCQ

$.. ==&gt; true




jshell&gt; q.answer(4).answer(3).lock() instanceof MCQ

$.. ==&gt; true




<table width="609">

 <tbody>

  <tr>

   <td width="609"> jshell&gt; q.mark()|  Error:|  cannot find symbol|    symbol:   method mark()|  q.mark()|  ^—-^ jshell&gt; q.answer(1).mark()|  Error:|  cannot find symbol|    symbol:   method mark()|  q.answer(1).mark()|  ^————–^ jshell&gt; q.answer(1).lock().answer(2)|  Error:|  cannot find symbol|    symbol:   method answer(int)|  q.answer(1).lock().answer(2)|  ^———————–^ jshell&gt; q.answer(1).lock().mark()$.. ==&gt; 0 jshell&gt; q.answer(1).answer(2)$.. ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ 2:False ] jshell&gt; q.answer(1).answer(2) instanceof TFQ$.. ==&gt; true jshell&gt; q.answer(1).answer(2).lock() instanceof TFQ $.. ==&gt; true</td>

  </tr>

 </tbody>

</table>

<table width="609">

 <tbody>

  <tr>

   <td width="609">jshell&gt; Question q = new FillInBlank(“Snow white and the ? dwarfs”, new OffByOneGrader(7) q ==&gt; Snow white and the ? dwarfs; Your answer: 0 jshell&gt; q.answer(7).lock().mark()$.. ==&gt; 2 jshell&gt; q.answer(6).lock().mark()$.. ==&gt; 1 jshell&gt; q.answer(8).lock().mark()$.. ==&gt; 1 jshell&gt; q.answer(5).lock().mark()$.. ==&gt; 0 jshell&gt; q.answer(10).lock().mark()$.. ==&gt; 0 jshell&gt; Question q = new FillInBlank(“? blind mice”, new FreeTenMarksGrader()) q ==&gt; ? blind mice; Your answer: 0 jshell&gt; q.answer(3).lock().mark()$.. ==&gt; 10 jshell&gt; q.mark()|  Error:|  cannot find symbol|    symbol:   method mark()|  q.mark()</td>

  </tr>

 </tbody>

</table>

jshell&gt; q = new TFQ(“An orange is blue.”, “False”) q ==&gt; An orange is blue. [1:True][2:False]; Your answer: [ ? ] <strong>Level 5</strong>

Fill-in-the-blank questions may require more subjective marking. We can do this by introducing a Grader when constructing the question.

You will need to define two graders:

OffByOneGrader that constructs a grader with the expected answer, and awards two marks if the guess is exactly the same as the answer, and one mark if the guess is off-by-one. Otherwise, no marks are awarded. FreeTenMarksGrader that awards ten marks regardless of the guess.

<table width="609">

 <tbody>

  <tr>

   <td width="609">jshell&gt; String[] options = {“apple”, “banana”, “car”, “orange”} options ==&gt; String[4] { “apple”, “banana”, “car”, “orange” } jshell&gt; int[] answers = {2, 1, 4} answers ==&gt; int[3] { 2, 1, 4 } jshell&gt; MRQ mrq = new MRQ(“Pick the fruits.”, options, answers)mrq ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ ] jshell&gt; mrq.answer(4)$.. ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ 4 ] jshell&gt; mrq.answer(4).answer(3)$.. ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ 3 4 ] jshell&gt; mrq.answer(4).answer(3).answer(4)$.. ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ 3 ] jshell&gt; mrqmrq ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ ] jshell&gt; String[] options = {“apple”, “banana”, “car”, “orange”} options ==&gt; String[4] { “apple”, “banana”, “car”, “orange” } jshell&gt; int[] answers = {2, 1, 4} answers ==&gt; int[3] { 2, 1, 4 } jshell&gt; Question q = new MRQ(“Pick the fruits.”, options, answers)q ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ ] jshell&gt; q.mark()|  Error:|  cannot find symbol|    symbol:   method mark()|  q.mark()|  ^—-^ jshell&gt; q.answer(1).mark()|  Error:|  cannot find symbol|    symbol:   method mark()|  q.answer(1).mark()|  ^————–^ jshell&gt; q.answer(1).lock().answer(2)|  Error:|  cannot find symbol|    symbol:   method answer(int)|  q.answer(1).lock().answer(2)|  ^———————–^ jshell&gt; q.answer(1).lock().mark()$.. ==&gt; 0 jshell&gt; q.answer(4).answer(1)$.. ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ 1 4 ]</td>

  </tr>

 </tbody>

</table>

|  ^—-^

jshell&gt; q.answer(0).lock().mark()

$.. ==&gt; 10

<h2>Level 6</h2>

Write an immutable MRQ class with a constructor that takes in a question of type String, the options as an array of Strings, and an int array of expected answers.

Include the answer method that takes in an integer as a guess. This method has a toggling effect, i.e. if the guess was already selected, answering it will unselect the guess. You may assume that there is at least one expected answer.

Define a mark method that returns 1 only if the guesses are the same as the answers. Otherwise, 0 is returned.

Note that MRQ is meant to be an extension to the existing implementation. Removing MRQ should not cause the preceding levels to fail.




<table width="683">

 <tbody>

  <tr>

   <td rowspan="2" width="37"> </td>

   <td width="609"> jshell&gt; q.answer(4).answer(1).lock().mark()$.. ==&gt; 0 jshell&gt; q.answer(4).answer(1).answer(4)$.. ==&gt; Pick the fruits. [1:apple][2:banana][3:car][4:orange]; Your answer: [ 1 ] jshell&gt; q.answer(4).answer(1).answer(2).lock().mark()$.. ==&gt; 1 jshell&gt; q.answer(1) instanceof MRQ$.. ==&gt; true jshell&gt; q.answer(1).lock() instanceof MRQ $.. ==&gt; true</td>

   <td rowspan="2" width="37"> </td>

  </tr>

  <tr>

   <td width="609"></td>

  </tr>

 </tbody>

</table>