Explanation of SQL Queries and Challenges
1. Ən çətin hesab etdiyiniz SQL sorğusu hansı oldu?
Mənim üçün ən çox baş yoran sorğu 3.15(a) oldu. Çünki burada WHERE və HAVING bəndlərini birgə işlətmək lazımdır. WHERE sətirləri qruplaşdırmadan öncə süzür, HAVING isə GROUP BY-dan sonra şərt qoyur. Brooklyn-dəki bütün filiallarda hesabı olan müştəriləri taparkən əvvəlcə WHERE ilə həmin şəhərin filiallarını seçdim. Sonra HAVING daxilində COUNT(...) yazaraq müştərinin hesabı olan filial sayını Brooklyn-dəki filial sayına bərabər tutdum.

2. Hansı sorğu üçün alt sorğu (subquery) istifadə etdiniz?
Alt sorğudan 3.15(a) tapşırığında istifadə etdim. Məqsəd Brooklyn-dəki filiallarda hesabı olan müştəriləri tapmaq idi. Filial sayını əllə yazmaq olmazdı. Ona görə HAVING daxilində alt sorğu yazdım: (SELECT COUNT(*) FROM branch WHERE branch_city = 'Brooklyn'). Bu alt sorğu filial sayını bazadan hesablayıb əsas sorğuya ötürür. Beləliklə, bazada dəyişiklik olsa belə sorğu işləyir.

3. JOIN istifadə etdiyiniz bir nümunəni izah edin.
JOIN əməliyyatını 3.11(a) tapşırığında tətbiq etdim. Comp. Sci. kursunu alan tələbələrin adını tapırdıq. Tələbə adı student, aldığı kurslar takes, kursun departamenti course cədvəlindədir. Məlumatlar 3 cədvəldə olduğu üçün onları JOIN ilə bağladım. student ilə takes cədvəlini tələbə ID-sinə, takes ilə course cədvəlini isə kurs koduna görə əlaqələndirdim.

4. SQL sorğularını yazarkən qarşılaşdığınız bir problemi və onun həllini izah edin.
Ən çox ilişdiyim məqam COUNT() funksiyasını WHERE içində yazmağım oldu. Məsələn, WHERE COUNT(*) > 2 yazırdım və baza xəta verirdi. Sonra anladım ki, SQL əvvəlcə WHERE-i icra etdiyi üçün həmin an qruplaşma olmur. Problemi həll etmək üçün GROUP BY istifadə edib şərti HAVING daxilinə keçirdim: sətirlərə WHERE, qruplara HAVING tətbiq olunur.
