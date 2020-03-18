---
title: Vědět, kdy použít přepsat a nová klíčová slova - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 493c6c5f5bf47c6b2cd140ac0f6922f91ca4252b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170257"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)

V C# metoda v odvozené třídě může mít stejný název jako metoda v základní třídě. Můžete určit, jak se metody vzájemně ovlivňují pomocí [nových](../../language-reference/keywords/new-modifier.md) a [přepsat](../../language-reference/keywords/override.md) klíčová slova. Modifikátor `override` rozšiřuje metodu základní `new` *třídy* `virtual` a modifikátor skryje přístupnou metodu základní *třídy.* Rozdíl je znázorněn v příkladech v tomto tématu.  
  
 V konzolové aplikaci deklarujte následující dvě třídy `BaseClass` a `DerivedClass`. `DerivedClass`dědí `BaseClass`od .  
  
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
  
 V `Main` metodě deklarujte proměnné `bc`, `dc`a `bcdc`.  
  
- `bc`je typu `BaseClass`a jeho hodnota `BaseClass`je typu .  
  
- `dc`je typu `DerivedClass`a jeho hodnota `DerivedClass`je typu .  
  
- `bcdc`je typu `BaseClass`a jeho hodnota `DerivedClass`je typu . To je proměnná věnovat pozornost.  
  
 Vzhledem `bcdc` k `BaseClass`tomu, `bc` a `Method1`mají typ , mohou pouze přímý přístup , pokud používáte odtypování. Proměnná `dc` může `Method1` `Method2`přistupovat k oběma a . Tyto vztahy jsou uvedeny v následujícím kódu.  
  
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
  
 Dále přidejte `Method2` následující `BaseClass`metodu do . Podpis této metody odpovídá podpisu `Method2` metody `DerivedClass`v .  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Protože `BaseClass` nyní `Method2` má metodu, druhý příkaz `BaseClass` volání `bc` lze `bcdc`přidat pro proměnné a , jak je znázorněno v následujícím kódu.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Při vytváření projektu uvidíte, že přidání `Method2` metody `BaseClass` v způsobí upozornění. Upozornění říká, `Method2` že `DerivedClass` metoda v `Method2` skryje metodu v `BaseClass`. Doporučujeme použít `new` klíčové slovo `Method2` v definici, pokud máte v úmyslu způsobit tento výsledek. Alternativně můžete přejmenovat jednu `Method2` z metod k vyřešení upozornění, ale to není vždy praktické.  
  
 Před `new`přidáním spusťte program a zosakažte výstup emitovaná dalšími příkazy volání. Zobrazí se následující výsledky.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 Klíčové `new` slovo zachová vztahy, které vytvářejí tento výstup, ale potlačí upozornění. Proměnné, které mají `BaseClass` typ nadále `BaseClass`přístup k členům `DerivedClass` , a proměnná, která má typ nadále přístup členů v `DerivedClass` první a pak zvážit členy zděděné z `BaseClass`.  
  
 Chcete-li upozornění potlačit, přidejte `new` modifikátor k definici `Method2` v `DerivedClass`, jak je znázorněno v následujícím kódu. Modifikátor lze přidat `public`před nebo za .  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Spusťte program znovu a ověřte, zda se výstup nezměnil. Ověřte také, že se upozornění již nezobrazuje. Pomocí `new`, tvrdíte, že jste si vědomi, že člen, který upravuje skryje člen, který je zděděn ze základní třídy. Další informace o skrytí názvu prostřednictvím dědičnosti naleznete v [tématu new Modifier](../../language-reference/keywords/new-modifier.md).  
  
 Chcete-li toto chování `override`narozdíloddůsledků použití `DerivedClass`, přidejte do aplikace následující metodu . Modifikátor `override` lze přidat `public`před nebo za .  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Přidejte `virtual` modifikátor `Method1` k `BaseClass`definici v . Modifikátor `virtual` lze přidat `public`před nebo za .  
  
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
  
 Použití `override` modifikátoru `bcdc` umožňuje `Method1` přístup k metodě, která je definována v aplikaci `DerivedClass`. To je obvykle požadované chování v hierarchiích dědičnosti. Chcete, aby objekty, které mají hodnoty, které jsou vytvořeny z odvozené třídy používat metody, které jsou definovány v odvozené třídě. Tohoto chování lze `override` dosáhnout pomocí rozšířit metodu základní třídy.  
  
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
  
 Následující příklad ilustruje podobné chování v jiném kontextu. Příklad definuje tři třídy: základní `Car` třídu s názvem a `ConvertibleCar` dvě `Minivan`třídy, které jsou odvozeny z něj a . Základní třída obsahuje `DescribeCar` metodu. Metoda zobrazí základní popis vozu a pak `ShowDetails` volá poskytnout další informace. Každá ze tří tříd `ShowDetails` definuje metodu. Modifikátor `new` se `ShowDetails` používá `ConvertibleCar` k definování ve třídě. Modifikátor `override` se `ShowDetails` používá `Minivan` k definování ve třídě.  
  
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
  
 Příklad testuje, která `ShowDetails` verze je volána. Následující metoda `TestCars1`, deklaruje instanci `DescribeCar` každé třídy a potom volá každou instanci.  
  
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
  
 `TestCars1`vytvoří následující výstup. Všimněte si `car2`zejména výsledky pro , které pravděpodobně nejsou to, co jste očekávali. Typ objektu je `ConvertibleCar`, `DescribeCar` ale nemá přístup `ShowDetails` k verzi, `ConvertibleCar` která je definována `new` ve třídě, `override` protože tato metoda je deklarována modifikátorem, nikoli modifikátorem. V důsledku toho `ConvertibleCar` objekt zobrazí stejný `Car` popis jako objekt. Porovnejte `car3`výsledky pro `Minivan` , což je objekt. V tomto případě `ShowDetails` metoda, která `Minivan` je deklarována ve třídě přepíše metodu, `ShowDetails` která je deklarována ve `Car` třídě a popis, který je zobrazen, popisuje minivan.  
  
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
  
 `TestCars2`vytvoří seznam objektů, které `Car`mají typ . Hodnoty objektů jsou vytvářeny z `Car`, `ConvertibleCar`a `Minivan` třídy. `DescribeCar`je volána na každý prvek seznamu. Následující kód ukazuje definici `TestCars2`.  
  
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
  
 Zobrazí se následující výstup. Všimněte si, že je stejný jako `TestCars1`výstup, který je zobrazen . Metoda `ShowDetails` `ConvertibleCar` třídy není volána, bez ohledu na to, `ConvertibleCar`zda `TestCars1`je `Car`typ objektu , jako v , nebo , jako v `TestCars2`. `car3` Naopak volá metodu `ShowDetails` z `Minivan` třídy v obou případech, zda má typ `Minivan` nebo typ `Car`.  
  
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
  
 Metody `TestCars3` `TestCars4` a dokončit příklad. Tyto metody `ShowDetails` volání přímo, nejprve `ConvertibleCar` z `Minivan` `TestCars3`objektů deklarovaných za `Car` `TestCars4`typ a ( ), pak z objektů deklarovaných typu ( ). Následující kód definuje tyto dvě metody.  
  
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
  
 Metody vytvářejí následující výstup, který odpovídá výsledkům z prvního příkladu v tomto tématu.  
  
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
  
 Následující kód ukazuje celý projekt a jeho výstup.  
  
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
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Správa verzí pomocí klíčových slov override a new](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [Abstraktní](../../language-reference/keywords/abstract.md)
