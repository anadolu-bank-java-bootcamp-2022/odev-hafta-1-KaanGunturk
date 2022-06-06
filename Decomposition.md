Bu sayfada decomposition hakkında yaptığım araştırmayı paylaşacağım.

Decompositon ,karmaşık bir problemi veya sistemi daha yönetilebilir hale getirmek için anlaşılması daha kolay olan küçük parçalara ayırmayı aynı zamanda programlama ve bakım yapılması için kolaylık sağlayan bilgisayar bilimidir.Daha sonra,küçük paröalar inccelenip çözülebilir veya üzerinde çalışılması daha kolay olduğu için ayrı ayrı tasarlanabilir.

Decomposition kullanma nedenimiz eğer problem ayrıştırılmazsa çözülmesi çok daha zordur.Aynı zamanda birçok farklı aşamayla uğraşmak,bir problemi birkaç küçük probleme bölüp her birinin teker teker çözmekten çok daha zordur.Problemi daha küçük parçalara bölmek, her küçük problemin detaylı incenebileceği anlamına gelir.

Bu kısımda bir problemin nasıl alınacağını,ayrıştırılacağını ve onu çözmek için bir algoritmanın nasıl tasarlanacağını inceleyeceğiz.

Bir çalışanın haftalık ücreti, ücret oranına ve haftada çalışılan saat sayısına bağlıdır. Çalışanlar haftada en az bir saat, en fazla 60 saat çalışırlar. 40 saatten fazla çalışan bir çalışana, 40'ın üzerinde çalışılan tüm saatler için normal ücretin 1,5 katı ödenir. Normal ücret, saat başına 10 sterlindir. Herhangi bir çalışanın haftalık ücretini hesaplamak ve çıktısını almak için bir program gereklidir.

    Problemi Decompositon yöntemi kullanarak ayrıştırma;

1-Kaç saat çalışıldığını öğrenin.

2-Bu saatlerden kaçının normal oranda ödeneceğini öğrenin.

3-Bu saatlerden kaçının, varsa, fazla mesai oranında ödeneceğini öğrenin.

4-Normal saatler için ödemeyi hesaplayın Fazla mesai saatleri için ödemeyi hesaplayın.

5-Normal ve fazla mesai saatleri için toplam ödemeyi hesaplayın.

6-Sonucu yazın.

    Variables ve Constants

Yukarıdaki çözüm aşağıdakı variables değerleri gerektirecektir.Program çalıştırıldığında bu değerler değişecektir.

Variable Data type

hours_worked Float
overtime_hours Float
normal_pay Float
overtime_pay Float
total_pay Float

Asağıdaki constant değerler kullanılacaktır.Program çalıştırıldığında bu değerler değişmeyecektir.

Constant Data type
HOURLY_RATE Float
OVERTIME_RATE Float
MAX_HOURS Integer
MIN_HOURS Integer
NORMAL_HOURS Integer

#variable ve constant tanımlama

Set HOURLY_RATE = 10.00

Set OVERTIME_RATE = 15.00

Set MAX_HOURS = 60

Set MIN_HOURS = 1

Set NORMAL_HOURS = 40

Set hours_worked = 0

Set overtime_hours = 0

Set normal_pay = 0

Set overtime_pay = 0

total_pay = 0

{input number of hours worked}

while hours_worked < MIN_HOURS OR hours_worked > MAX_HOURS

output "Enter the number of hours worked"
input hours_worked

end while

{calculate overtime hours}

if hours_worked > NORMAL_HOURS then

overtime_hours = hours_worked - NORMAL_HOURS

hours_worked = NORMAL_HOURS

end if

{calculate pay}

normal*pay = hours_worked * HOURLY\*RATE

overtime_pay = overtime_hours \* OVERTIME_RATE

total_pay = normal_pay + overtime_pay

{output result}
Output "Normal pay rate: £" < HOURLY_RATE

Output "Overtime pay rate: £" < OVERTIME_RATE

Output "Hours worked: " < hours_worked

Output "Overtime hours worked: " < overtime_hours

Output "Total pay: £" < total_pay

End

Çıkış değerleri

Girillen değerlere göre çıktı aşağıdaki gibi olacaktır.

Örnek 1: 4 hours

Enter the number of hours worked: 4

Normal pay rate: £10

Overtime pay rate: £15

Hours worked: 4

Overtime hours worked: 0

Total pay: £40

Örnek 2: 45 hours

Enter the number of hours worked: 45

Normal pay rate: £10

Overtime pay rate: £15

Hours worked: 40

Overtime hours worked: 5

Total pay: £475

Problem decomposition kullanılarak tamamen ayrıştırıldı ve algotitma tasarlandı.
