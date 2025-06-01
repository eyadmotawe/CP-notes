لو معاك array of n integers as input  واديتلك عدد من الqueries كل مرة بديلك رقم واسالك, هل الرقم ده اقدر اعمله عن طريق xor operations على اي ارقام من ال input array ؟ 


الحل الbrute force هو انك تكون كل subsets الممكنة وتعملهم xor. ولكن الحل ده time complexity 2^n فاكيد هيجيب TLE.

وهنا بيظهر analogy with linear algebra بالتحديد gauss elimination .  (لو مكنتش بتحب الكورس دا زيي, متقلقش مش هنطزل هنا (: ).


