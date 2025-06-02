لو معاك array of n integers as input  واديتلك عدد من الqueries كل مرة بديلك رقم واسالك, هل الرقم ده اقدر اعمله عن طريق xor operations على اي ارقام من ال input array ؟ 


الحل الbrute force هو انك تكون كل subsets الممكنة وتعملهم لكل واحدة xor. ولكن الحل ده time complexity 2^n فاكيد هيجيب TLE.

وهنا بيظهر analogy with linear algebra بالتحديد gauss elimination .  (لو مكنتش بتحب الكورس دا زيي, متقلقش مش هنطول هنا (: ).




"""

having 3 vecotrs A, B and C . can vecotr D be represented as linear combination of the three vectors?

"""



السؤال ده يقدر gauss elimination  يجاوبنا عليه كالتالي:


"""

combining vectors in one matrix as following:

[ ... A ...]

[ ... B ...]

[ ... C ...]

[ ... D ...]

Then applying gauss elimination process to acchive most reduced form of the system.

"""

بعد ما نعمل العملية السابقة لو لقينا ان اخر صف يساوي صفر اذا اجابة السؤال yes لكن لو اخر صف مش بيساوي صفر اذا اجابة السؤال لا ..... دا بالظبط اللي هنعمله مع البروبليم الاصلية !
