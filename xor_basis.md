لو معاك array of n integers as input  واديتلك عدد من الqueries كل مرة بديلك رقم واسالك, هل الرقم ده اقدر اعمله عن طريق xor operations على اي ارقام من ال input array ؟ 


الحل الbrute force هو انك تكون كل subsets الممكنة وتعملهم لكل واحدة xor. ولكن الحل ده time complexity 2^n فاكيد هيجيب TLE.

وهنا بيظهر analogy with linear algebra بالتحديد gauss elimination (: 




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

Then applying gauss elimination process to achieve most reduced form of the system.

"""

بعد ما نعمل العملية السابقة لو لقينا ان اخر صف يساوي صفر اذا اجابة السؤال yes لكن لو اخر صف مش بيساوي صفر اذا اجابة السؤال لا ..... دا بالظبط اللي هنعمله مع البروبليم الاصلية !

اللي احنا عملناه فوق هو اننا بندور على basis of the system  او بمعنى اخر ال vectors الاساسية واللي منها اقدر اكون اي vecotr تاني

"""

suppose you have 3 numbers: 2, 1 and 3

the binary representation : 10, 01 and 11

these numbers can be put in a matrix as follow:

[ 1 0 ]

[ 0 1 ]

[ 1 1 ]

"""

هنا هنعمل gauss elimination  على الماتركس دي ولكن بطريقة مختلفة شوية.

بنمشي على كل صف من الشمال وندور على اول pivot , ودلوقتي نصفر كل الصفوف اللى تحتيه عن طريق اننا نعمل xor لاي صف فيه واحد مكان الpivot اللي احنا واقفين عنده.

يعني مثلا هنشوف اول صف هنلاقي ان اول pivot في المكان (1,1) , دلوقتي ندور في الصفوف اللي تحتيه لو في 1 مكان الpivot , هنلاقي انه في الصف التالت.... فهنعمل xor للصف الاول والتالت وبالتالي ده الناتج:

"""

[ 1 0 ]

[ 0 1 ]

[ 0 1 ]

"""

ودلوقتي نشوف تاني pivot هنلاقيه في المكان (2,2) ونشوف تحته هنلاقي ان في واحد في الصف التالت.. فهنعمل xor للصف التاني والتالت وهيبقى دا الناتج:


"""

[ 1 0 ]

[ 0 1 ]

[ 0 0 ]

"""

اخر صف بيساوي صفر,

بكده قدرنا بسهولة نقول ان 3 ممكن نكونها عن طريق عملية xor  بين مجموعة ارقام تانية .

ده بالظبط اللي هنعمله مع البروبليم الاصلية بتاعتنا 

"""

given an array of n integers we will form the XOR - space basis of the array , hence. we will be able to answer the queries.

"""

وده الكود اللي نقدر نعمل بيه كده

    const int LOG = 60;

    long long basis[LOG]; // basis[i] keeps the number with the i-th bit set

    void insert(long long x) {
    for (int i = LOG - 1; i >= 0; --i) {
    
        if (!(x & (1LL << i))) continue;
        
        if (!basis[i]) {
        
            basis[i] = x;
            
            break;
        }
        
        x ^= basis[i];
        
    }
    }



ref:

https://www.youtube.com/watch?v=qIXg9vJ6hZM&t=1566s

https://codeforces.com/blog/entry/68953
