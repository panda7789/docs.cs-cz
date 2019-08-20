---
title: Znalost, kdy použít klíčová slova override a C# New – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 00751cd8eac7979fe94d890ddeb7d13edb233f9e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596469"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="7a02f-102">Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7a02f-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="7a02f-103">V C#rozhraní může mít metoda v odvozené třídě stejný název jako metoda v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="7a02f-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="7a02f-104">Můžete určit způsob interakce metod pomocí klíčových slov [New](../../language-reference/keywords/new-modifier.md) a [override](../../language-reference/keywords/override.md) .</span><span class="sxs-lookup"><span data-stu-id="7a02f-104">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="7a02f-105">`new` `virtual` Modifikátor rozšiřuje metodu základní třídy a modifikátor skrývá přístupnou metodu základní třídy. `override`</span><span class="sxs-lookup"><span data-stu-id="7a02f-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="7a02f-106">Rozdíl je znázorněn v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="7a02f-107">V konzolové aplikaci deklarujte následující dvě třídy `BaseClass` a. `DerivedClass`</span><span class="sxs-lookup"><span data-stu-id="7a02f-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="7a02f-108">`DerivedClass`dědí z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-109">V metodě deklarujte proměnné `bc`, `dc`a `bcdc`. `Main`</span><span class="sxs-lookup"><span data-stu-id="7a02f-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="7a02f-110">`bc`je typu `BaseClass`a jeho hodnota je typu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="7a02f-111">`dc`je typu `DerivedClass`a jeho hodnota je typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="7a02f-112">`bcdc`je typu `BaseClass`a jeho hodnota je typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="7a02f-113">Toto je proměnná, na kterou se má věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="7a02f-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="7a02f-114">Vzhledem `bc` k `bcdc` tomu, `BaseClass`že a mají typ, mohou `Method1`přistupovat pouze k, pokud nepoužíváte přetypování.</span><span class="sxs-lookup"><span data-stu-id="7a02f-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="7a02f-115">Proměnná `dc` má přístup k `Method1` oběma `Method2`i.</span><span class="sxs-lookup"><span data-stu-id="7a02f-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="7a02f-116">Tyto vztahy jsou uvedeny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-117">Dále přidejte následující `Method2` metodu do `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="7a02f-118">Signatura této metody odpovídá signatuře `Method2` metody v. `DerivedClass`</span><span class="sxs-lookup"><span data-stu-id="7a02f-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="7a02f-119">Vzhledem `BaseClass` k tomu, `Method2` že nyní má metodu, lze přidat druhý volající příkaz `BaseClass` pro `bc` proměnné `bcdc`a, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="7a02f-120">Při sestavování projektu vidíte, že přidání `Method2` metody v `BaseClass` způsobuje upozornění.</span><span class="sxs-lookup"><span data-stu-id="7a02f-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="7a02f-121">Upozornění `Method2` říká, že metoda v `DerivedClass` nástroji skrývá `Method2` metodu v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="7a02f-122">Pokud máte `new` `Method2` v úmyslu tento výsledek způsobit, doporučujeme použít klíčové slovo v definici.</span><span class="sxs-lookup"><span data-stu-id="7a02f-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="7a02f-123">Alternativně můžete přejmenovat jednu z `Method2` metod a vyřešit tak upozornění, ale to není vždy praktické.</span><span class="sxs-lookup"><span data-stu-id="7a02f-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="7a02f-124">Před přidáním `new`spusťte program, aby se zobrazil výstup vyprodukovaný dalšími příkazy volání.</span><span class="sxs-lookup"><span data-stu-id="7a02f-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="7a02f-125">Zobrazí se následující výsledky.</span><span class="sxs-lookup"><span data-stu-id="7a02f-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="7a02f-126">`new` Klíčové slovo zachovává vztahy, které tvoří tento výstup, ale potlačí upozornění.</span><span class="sxs-lookup"><span data-stu-id="7a02f-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="7a02f-127">Proměnné, které mají typ `BaseClass` `BaseClass`, budou mít i nadále přístup ke členům a proměnná, která má `DerivedClass` typ, nadále přistupuje k `DerivedClass` členům v prvním a pak pro účely zvážení `BaseClass`členů zděděných z.</span><span class="sxs-lookup"><span data-stu-id="7a02f-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="7a02f-128">Chcete-li potlačit upozornění, `new` přidejte modifikátor do `Method2` definice v `DerivedClass`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="7a02f-129">Modifikátor lze přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="7a02f-130">Spusťte program znovu a ověřte, zda se výstup nezměnil.</span><span class="sxs-lookup"><span data-stu-id="7a02f-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="7a02f-131">Ověřte také, že se upozornění již nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="7a02f-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="7a02f-132">Pomocí `new`můžete vyhodnotit, že jste si vědomi, že člen, který upravuje, skrývá člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="7a02f-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="7a02f-133">Další informace o skrývání názvů prostřednictvím dědičnosti naleznete v tématu [new modifikátor](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="7a02f-133">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="7a02f-134">Chcete-li toto chování kontrastit na efekty `override`použití, přidejte následující metodu do `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="7a02f-135">Modifikátor lze přidat před nebo po `public`. `override`</span><span class="sxs-lookup"><span data-stu-id="7a02f-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="7a02f-136">Přidejte modifikátor do `Method1` definice v `BaseClass`. `virtual`</span><span class="sxs-lookup"><span data-stu-id="7a02f-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="7a02f-137">Modifikátor lze přidat před nebo po `public`. `virtual`</span><span class="sxs-lookup"><span data-stu-id="7a02f-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="7a02f-138">Spusťte projekt znovu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-138">Run the project again.</span></span> <span data-ttu-id="7a02f-139">Všimněte si zejména posledních dvou řádků následujícího výstupu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="7a02f-140">Použití `override` modifikátoru umožňuje `bcdc` přístup `Method1` k metodě, která je definována v `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="7a02f-141">Obvykle to je požadované chování v hierarchiích dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="7a02f-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="7a02f-142">Chcete, aby objekty, které mají hodnoty vytvořené z odvozené třídy, používaly metody, které jsou definovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="7a02f-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="7a02f-143">Toto chování dosáhnete použitím `override` k rozšiřování metody základní třídy.</span><span class="sxs-lookup"><span data-stu-id="7a02f-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="7a02f-144">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="7a02f-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-145">Následující příklad ilustruje podobné chování v jiném kontextu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="7a02f-146">Příklad definuje tři třídy: základní třídu s názvem `Car` a dvě třídy, které jsou odvozeny z `ConvertibleCar` ní a `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="7a02f-147">Základní třída obsahuje `DescribeCar` metodu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="7a02f-148">Metoda zobrazí základní popis auta a potom zavolá `ShowDetails` k poskytnutí dalších informací.</span><span class="sxs-lookup"><span data-stu-id="7a02f-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="7a02f-149">Každá ze tří tříd definuje `ShowDetails` metodu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="7a02f-150">Modifikátor slouží k definování `ShowDetails` ve `ConvertibleCar` třídě. `new`</span><span class="sxs-lookup"><span data-stu-id="7a02f-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="7a02f-151">Modifikátor slouží k definování `ShowDetails` ve `Minivan` třídě. `override`</span><span class="sxs-lookup"><span data-stu-id="7a02f-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-152">Příklad testuje, která verze `ShowDetails` je volána.</span><span class="sxs-lookup"><span data-stu-id="7a02f-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="7a02f-153">Následující metoda `TestCars1`deklaruje instanci každé třídy a poté volá `DescribeCar` každou instanci.</span><span class="sxs-lookup"><span data-stu-id="7a02f-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-154">`TestCars1`Vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="7a02f-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="7a02f-155">Všimněte si zejména výsledků pro `car2`, což pravděpodobně není to, co jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="7a02f-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="7a02f-156">Typ `ConvertibleCar`objektu je, ale `DescribeCar` nemá přístup k verzi `ShowDetails` , která je definována ve `ConvertibleCar` třídě, `override` protože tato metoda je deklarována s `new` modifikátorem, nikoli modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="7a02f-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="7a02f-157">V důsledku toho `ConvertibleCar` objekt zobrazí stejný popis `Car` jako objekt.</span><span class="sxs-lookup"><span data-stu-id="7a02f-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="7a02f-158">Kontrastování výsledků pro `car3`, což `Minivan` je objekt.</span><span class="sxs-lookup"><span data-stu-id="7a02f-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="7a02f-159">V tomto případě `ShowDetails` metoda, která je deklarována `Minivan` v třídě, Přepisuje `ShowDetails` metodu, která je deklarována ve `Car` třídě, a popis, který je zobrazen, popisuje minivan.</span><span class="sxs-lookup"><span data-stu-id="7a02f-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-160">`TestCars2`Vytvoří seznam objektů, které mají typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="7a02f-161">Hodnoty objektů jsou vytvořeny z `Car`tříd, `ConvertibleCar`a `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="7a02f-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="7a02f-162">`DescribeCar`je volána u každého prvku seznamu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="7a02f-163">Následující kód ukazuje definici `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-164">Zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="7a02f-164">The following output is displayed.</span></span> <span data-ttu-id="7a02f-165">Všimněte si, že je stejný jako výstup, který je zobrazen pomocí `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="7a02f-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="7a02f-166">`TestCars1` `ConvertibleCar` `Car` `TestCars2`Metoda třídy není volána, bez ohledu na to, zda je typ objektu, jako v nebo, jako v. `ConvertibleCar` `ShowDetails`</span><span class="sxs-lookup"><span data-stu-id="7a02f-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="7a02f-167">`car3` Naopak `Minivan` volá metodu z `Minivan` třídy v obou případech bez ohledu na to, zda obsahuje typ nebo typ `Car`. `ShowDetails`</span><span class="sxs-lookup"><span data-stu-id="7a02f-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-168">Metody `TestCars3` a`TestCars4` dokončete příklad.</span><span class="sxs-lookup"><span data-stu-id="7a02f-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="7a02f-169">Tyto metody volají `ShowDetails` přímo, nejprve z objektů deklarovaných jako typ `ConvertibleCar` a `Minivan` (`TestCars3`), poté z objektů deklarovaných jako typ `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="7a02f-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="7a02f-170">Následující kód definuje tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="7a02f-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-171">Metody vyvolávají následující výstup, který odpovídá výsledkům z prvního příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7a02f-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="7a02f-172">Následující kód ukazuje kompletní projekt a jeho výstup.</span><span class="sxs-lookup"><span data-stu-id="7a02f-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a02f-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a02f-173">See also</span></span>

- [<span data-ttu-id="7a02f-174">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7a02f-174">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7a02f-175">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="7a02f-175">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7a02f-176">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="7a02f-176">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="7a02f-177">base</span><span class="sxs-lookup"><span data-stu-id="7a02f-177">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="7a02f-178">abstract</span><span class="sxs-lookup"><span data-stu-id="7a02f-178">abstract</span></span>](../../language-reference/keywords/abstract.md)
