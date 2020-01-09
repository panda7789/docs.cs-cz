---
title: Znalost, kdy použít klíčová slova override a C# New – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 0a209b9522202649765654013fdc3a468913c6b1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714783"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)

V C#rozhraní může mít metoda v odvozené třídě stejný název jako metoda v základní třídě. Můžete určit způsob interakce metod pomocí klíčových slov [New](../../language-reference/keywords/new-modifier.md) a [override](../../language-reference/keywords/override.md) . Modifikátor `override` *rozšiřuje* metodu `virtual` základní třídy a modifikátor `new` *skrývá* přístupnou metodu základní třídy. Rozdíl je znázorněn v příkladech v tomto tématu.  
  
 V konzolové aplikaci deklarujte následující dvě třídy `BaseClass` a `DerivedClass`. `DerivedClass` dědí z `BaseClass`.  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 V metodě `Main` deklarujte proměnné `bc`, `dc`a `bcdc`.  
  
- `bc` je typu `BaseClass`a jeho hodnota je typu `BaseClass`.  
  
- `dc` je typu `DerivedClass`a jeho hodnota je typu `DerivedClass`.  
  
- `bcdc` je typu `BaseClass`a jeho hodnota je typu `DerivedClass`. Toto je proměnná, na kterou se má věnovat pozornost.  
  
 Vzhledem k tomu, že `bc` a `bcdc` mají typ `BaseClass`, mohou přímo přistupovat k `Method1`, pokud nepoužíváte přetypování. Proměnná `dc` má přístup k `Method1` i `Method2`. Tyto vztahy jsou uvedeny v následujícím kódu.  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 Dále přidejte následující metodu `Method2` k `BaseClass`. Signatura této metody odpovídá podpisu metody `Method2` v `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Vzhledem k tomu, že `BaseClass` nyní má metodu `Method2`, lze přidat druhý volající příkaz pro `BaseClass` proměnné `bc` a `bcdc`, jak je znázorněno v následujícím kódu.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Při sestavování projektu se zobrazí, že přidání metody `Method2` v `BaseClass` způsobí upozornění. Upozornění říká, že metoda `Method2` v `DerivedClass` skrývá `Method2` metodu v `BaseClass`. Pokud chcete tento výsledek způsobit, doporučujeme použít klíčové slovo `new` v definici `Method2`. Alternativně můžete přejmenovat jednu z `Method2` metod pro vyřešení upozornění, ale to není vždy praktické.  
  
 Před přidáním `new`spusťte program, aby se zobrazil výstup vyprodukovaný dalšími příkazy volání. Zobrazí se následující výsledky.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 Klíčové slovo `new` zachovává vztahy, které tvoří tento výstup, ale potlačí upozornění. Proměnné, které mají typ `BaseClass` nadále mají přístup k členům `BaseClass`a proměnná, která má typ `DerivedClass`, nadále přistupuje k členům v `DerivedClass` jako první a následně ke zvážení členů zděděných z `BaseClass`.  
  
 Chcete-li potlačit upozornění, přidejte modifikátor `new` do definice `Method2` v `DerivedClass`, jak je znázorněno v následujícím kódu. Modifikátor lze přidat před nebo po `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Spusťte program znovu a ověřte, zda se výstup nezměnil. Ověřte také, že se upozornění již nezobrazuje. Pomocí `new`uplatňujete, že jste si vědomi, že člen, který upravuje, skrývá člena, který je zděděn ze základní třídy. Další informace o skrývání názvů prostřednictvím dědičnosti naleznete v tématu [new modifikátor](../../language-reference/keywords/new-modifier.md).  
  
 Chcete-li toto chování kontrastovat s účinky použití `override`, přidejte následující metodu pro `DerivedClass`. Modifikátor `override` lze přidat před nebo po `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Přidejte modifikátor `virtual` do definice `Method1` v `BaseClass`. Modifikátor `virtual` lze přidat před nebo po `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Spusťte projekt znovu. Všimněte si zejména posledních dvou řádků následujícího výstupu.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Použití modifikátoru `override` umožňuje `bcdc` přístup k metodě `Method1`, která je definována v `DerivedClass`. Obvykle to je požadované chování v hierarchiích dědičnosti. Chcete, aby objekty, které mají hodnoty vytvořené z odvozené třídy, používaly metody, které jsou definovány v odvozené třídě. Toto chování dosáhnete použitím `override` k rozšiřování metody základní třídy.  
  
 Následující kód obsahuje úplný příklad.  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 Následující příklad ilustruje podobné chování v jiném kontextu. Příklad definuje tři třídy: základní třídu s názvem `Car` a dvě třídy, které jsou odvozeny z ní, `ConvertibleCar` a `Minivan`. Základní třída obsahuje metodu `DescribeCar`. Metoda zobrazí základní popis auta a potom zavolá `ShowDetails` k poskytnutí dalších informací. Každá ze tří tříd definuje metodu `ShowDetails`. Modifikátor `new` slouží k definování `ShowDetails` ve třídě `ConvertibleCar`. Modifikátor `override` slouží k definování `ShowDetails` ve třídě `Minivan`.  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 Příklad testuje, která verze `ShowDetails` je volána. Následující metoda, `TestCars1`, deklaruje instanci každé třídy a poté volá `DescribeCar` na každé instanci.  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 `TestCars1` generuje následující výstup. Všimněte si zejména výsledků `car2`, což pravděpodobně neočekáváte, co jste očekávali. Typ objektu je `ConvertibleCar`, ale `DescribeCar` nemá přístup k verzi `ShowDetails`, která je definována v `ConvertibleCar` třídě, protože tato metoda je deklarována s modifikátorem `new`, nikoli s modifikátorem `override`. V důsledku toho `ConvertibleCar` objekt zobrazuje stejný popis jako objekt `Car`. Porovnejte výsledky pro `car3`, což je objekt `Minivan`. V tomto případě metoda `ShowDetails` deklarovaná v `Minivan` třídy přepíše metodu `ShowDetails`, která je deklarována v třídě `Car` a popis, který se zobrazí, popisuje minivan.  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 `TestCars2` vytvoří seznam objektů, které mají typ `Car`. Hodnoty objektů jsou vytvořeny z tříd `Car`, `ConvertibleCar`a `Minivan`. `DescribeCar` je volána u každého prvku seznamu. Následující kód ukazuje definici `TestCars2`.  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 Zobrazí se následující výstup. Všimněte si, že je stejný jako výstup, který je zobrazen `TestCars1`. Metoda `ShowDetails` třídy `ConvertibleCar` není volána, bez ohledu na to, zda je typ objektu `ConvertibleCar`, jako v `TestCars1`nebo `Car`, jako v `TestCars2`. Naopak `car3` volá metodu `ShowDetails` z třídy `Minivan` v obou případech bez ohledu na to, zda má typ `Minivan` nebo typ `Car`.  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 Metody `TestCars3` a `TestCars4` dokončí příklad. Tyto metody volají `ShowDetails` přímo, nejprve z objektů deklarovaných jako typ `ConvertibleCar` a `Minivan` (`TestCars3`), a poté z objektů deklarovaných jako typ `Car` (`TestCars4`). Následující kód definuje tyto dvě metody.  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 Metody vyvolávají následující výstup, který odpovídá výsledkům z prvního příkladu v tomto tématu.  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 Následující kód ukazuje kompletní projekt a jeho výstup.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Správa verzí pomocí klíčových slov override a new](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [abstract](../../language-reference/keywords/abstract.md)
