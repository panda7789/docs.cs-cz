---
title: "Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b4d53f16f046839d56bc1dc37f7b2d8816c5956f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)
V jazyce C# metoda v odvozené třídě, může mít stejný název jako metodu v základní třídě. Můžete určit, jak používat metody pomocí [nové](../../../csharp/language-reference/keywords/new.md) a [přepsat](../../../csharp/language-reference/keywords/override.md) klíčová slova. `override` Modifikátor *rozšiřuje* metodu základní třídy a `new` modifikátor *skryje* ho. Rozdíl je předvedené v příkladech v tomto tématu.  
  
 V konzolové aplikaci, deklarovat následující dvě třídy `BaseClass` a `DerivedClass`. `DerivedClass`dědí z `BaseClass`.  
  
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
  
 V `Main` metody deklarujte proměnné `bc`, `dc`, a `bcdc`.  
  
-   `bc`je typu `BaseClass`, a jeho hodnota je typu `BaseClass`.  
  
-   `dc`je typu `DerivedClass`, a jeho hodnota je typu `DerivedClass`.  
  
-   `bcdc`je typu `BaseClass`, a jeho hodnota je typu `DerivedClass`. Jedná se o proměnnou věnovat pozornost.  
  
 Protože `bc` a `bcdc` mít typ `BaseClass`, pouze přímo přístupem `Method1`, pokud nechcete použít přetypování. Proměnné `dc` k dispozici obě `Method1` a `Method2`. Tyto relace jsou uvedené v následující kód.  
  
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
  
 V dalším kroku přidejte následující `Method2` metodu `BaseClass`. Tato metoda podpis neodpovídá podpisu `Method2` metoda v `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Protože `BaseClass` má teď `Method2` metoda, druhé volání příkazu lze přidat pro `BaseClass` proměnné `bc` a `bcdc`, jak je znázorněno v následujícím kódu.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Při sestavování projektu zobrazí přidání `Method2` metoda v `BaseClass` způsobí, že upozornění. Upozornění, která `Method2` metoda v `DerivedClass` skryje `Method2` metoda v `BaseClass`. Doporučujeme používat `new` – klíčové slovo v `Method2` definice, pokud máte v úmyslu způsobit, že výsledek. Alternativně může přejmenujte jeden z `Method2` metody k vyřešení upozornění, ale není vždy reálné.  
  
 Před přidáním `new`, spusťte program, který chcete zobrazit výstup vyprodukované další volání příkazy. Zobrazí se následující výsledky.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` – Klíčové slovo uchovává vztahy, které vytvářejí tento výstup, ale jeho potlačí upozornění. Proměnné, které mají typ `BaseClass` nadále přístup ke členům v `BaseClass`a proměnné, která má typ `DerivedClass` nadále přístup ke členům v `DerivedClass` první a pak zvažte členy zděděno z `BaseClass`.  
  
 Chcete-li potlačit upozornění, přidejte `new` modifikátor definici `Method2` v `DerivedClass`, jak je znázorněno v následujícím kódu. Modifikátor lze přidat před nebo po `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Spusťte program znovu k ověření, že se nezměnil výstup. Také ověřte, že už se zobrazí upozornění. Pomocí `new`, uplatňujete, že jste si vědomi, že člena, který upravuje skryje člena, který je zděděn ze základní třídy. Další informace o skrývání název prostřednictvím dědičnosti najdete v tématu [new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 K kontrastu tohoto chování důsledky použití `override`, přidejte následující metodu do `DerivedClass`. `override` Modifikátor lze přidat před nebo po `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Přidat `virtual` modifikátor definici `Method1` v `BaseClass`. `virtual` Modifikátor lze přidat před nebo po `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Spusťte projekt znovu. Všimněte si, zejména poslední dva řádky následující výstup.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Použití `override` modifikátor umožňuje `bcdc` pro přístup k `Method1` metoda, která je definována v `DerivedClass`. Obvykle, který je toto chování žádoucí v hierarchie dědičnosti. Chcete objekty, které mají hodnoty, které jsou vytvořené z odvozené třídy používat metody, které jsou definovány v odvozené třídě. Dosažení tohoto chování pomocí `override` rozšířit metoda základní třídy.  
  
 Následující kód obsahuje kompletní příklad.  
  
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
  
 Následující příklad ukazuje podobné chování v jiném kontextu. V příkladu definuje tří tříd: základní třídu s názvem `Car` a dvě třídy, které jsou odvozeny od, `ConvertibleCar` a `Minivan`. Obsahuje základní třídy `DescribeCar` metoda. Metoda zobrazí základní popis automobilu a pak zavolá `ShowDetails` můžete poskytnout dodatečné informace. Všechny tři třídy definuje `ShowDetails` metoda. `new` Modifikátor se používá k definování `ShowDetails` v `ConvertibleCar` třídy. `override` Modifikátor se používá k definování `ShowDetails` v `Minivan` třídy.  
  
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
  
 V příkladu testuje, kterou verzi `ShowDetails` je volána. Následující metoda `TestCars1`, deklaruje instancí každé třídy a pak zavolá `DescribeCar` na každou instanci.  
  
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
  
 `TestCars1`vytvoří následující výstup. Všimněte si, zejména výsledky pro `car2`, které jsou pravděpodobně není co očekává. Typ objektu je `ConvertibleCar`, ale `DescribeCar` nepřistoupí verzi `ShowDetails` která je definovaná v `ConvertibleCar` třídy vzhledem k tomu, že metoda je deklarovaný s `new` modifikátor, není `override` modifikátor. V důsledku toho `ConvertibleCar` objekt zobrazí popis stejné jako `Car` objektu. Porovnejte výsledky pro `car3`, který je `Minivan` objektu. V takovém případě `ShowDetails` metoda, která je definována v `Minivan` třídy přepsání `ShowDetails` metoda, která je definována v `Car` třídy a popis, který se zobrazí popisuje minivan.  
  
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
  
 `TestCars2`Vytvoří seznam objektů, které mají typ `Car`. Instance hodnoty objekty z `Car`, `ConvertibleCar`, a `Minivan` třídy. `DescribeCar`je volána pro každý element seznamu. Následující kód ukazuje definici `TestCars2`.  
  
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
  
 Zobrazí se následující výstup. Všimněte si, že je stejný jako výstup, který se zobrazí při `TestCars1`. `ShowDetails` Metodu `ConvertibleCar` třída není volána bez ohledu na to, jestli je typ objektu `ConvertibleCar`jako v `TestCars1`, nebo `Car`jako v `TestCars2`. Naopak `car3` volání `ShowDetails` metoda z `Minivan` třídy v obou případech, zda má typ `Minivan` nebo typ `Car`.  
  
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
  
 Metody `TestCars3` a `TestCars4` dokončit v příkladu. Tyto metody volání `ShowDetails` přímo, nejprve z objektů deklarovaný tak, aby měl typ `ConvertibleCar` a `Minivan` (`TestCars3`), pak z objektů deklarovaný tak, aby měl typ `Car` (`TestCars4`). Následující kód definuje tyto dvě metody.  
  
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
  
 Metody vytvořit následující výstup, který odpovídá výsledky z prvního příkladu v tomto tématu.  
  
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
  
 Následující kód ukazuje dokončený projekt a její výstup.  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [základní](../../../csharp/language-reference/keywords/base.md)  
 [abstraktní](../../../csharp/language-reference/keywords/abstract.md)
