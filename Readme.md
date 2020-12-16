# CouponWithOCP

Aplikasi ini merupakan console untuk mempelajari Open Closed Principle.
Aplikasi ini menerapkan Open Closed principle.

## Scope & Functionalities
* User dapat mempelajari abstraction.
* User dapat mempelajari penerapan polymorphism.
* User dapat mempelajari penerapan Open Closed principle.

## How does it works?
Pada class `Program.cs` terdapat kode berikut:
```c#
static void Main(string[] args)
        {
            Coupon coupon1 = new CouponWithNominal(2000);
            Console.WriteLine(coupon1.calculate(10000));

            Coupon coupon2 = new CouponWithPercentage(25);
            Console.WriteLine(coupon2.calculate(10000));

            Coupon coupon3 = new CouponWithMaxNominal(90, 3000);
            Console.WriteLine(coupon3.calculate(10000));

            Coupon coupon4 = new CouponWithCashback(500);
            Console.WriteLine(coupon4.calculate(10000));

        }
```
Kode di atas digunakan untuk menjalankan aplikasi pada perhitungan kupon dan memasukkan nilai **discNominal** yang dimasukkan.
Semua perhitungan terdapat dalam class `Coupun.cs`.

```C#
public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
```
Kode di atas digunakan untuk menghitung nilai total kupon dengan **discNominal**.

```C#
public override double calculate(double originPrice)
        {
            return (100 - discPercentage) * originPrice / 100;
        }
```
Kode di atas digunakan untuk menghitung nilai total kupon dengan **discPercentage**.

```C#
public override double calculate(double originPrice)
        {
            double discPercentageInRupiah = discPercentage * originPrice / 100;
            double finalPrice = 0;
            if (discPercentageInRupiah > discNominal)
            {
                finalPrice = originPrice - discNominal;
            }
            else
            {
                finalPrice = originPrice - discPercentageInRupiah;
            }
            return finalPrice;
        }
```
Kode di atas digunakan untuk menghitung nilai total kupon dengan nilai maksimum **discNominal**.

```C#
public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
```
Kode di atas digunakan untuk menghitung nilai total kupon dengan cashback.
