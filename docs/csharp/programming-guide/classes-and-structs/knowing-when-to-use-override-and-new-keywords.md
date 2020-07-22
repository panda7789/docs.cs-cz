---
title: Znalost, kdy použít klíčová slova override a New – Průvodce programováním v C#
description: Pomocí klíčového slova New a override v jazyce C# určete, jak budou metody se stejným názvem v základní a odvozené třídě spolupracovat.
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 732a37c08b4c7bb998a7cc5dcfbd00d4e706b06c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864537"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="36b62-103">Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="36b62-103">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="36b62-104">V jazyce C# může mít metoda v odvozené třídě stejný název jako metoda v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="36b62-104">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="36b62-105">Můžete určit způsob interakce metod pomocí klíčových slov [New](../../language-reference/keywords/new-modifier.md) a [override](../../language-reference/keywords/override.md) .</span><span class="sxs-lookup"><span data-stu-id="36b62-105">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="36b62-106">`override`Modifikátor *rozšiřuje* metodu základní třídy `virtual` a `new` Modifikátor *skrývá* přístupnou metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="36b62-106">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="36b62-107">Rozdíl je znázorněn v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="36b62-107">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="36b62-108">V konzolové aplikaci deklarujte následující dvě třídy `BaseClass` a `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-108">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="36b62-109">`DerivedClass`dědí z `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-109">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="36b62-110">V `Main` metodě deklarujte proměnné `bc` , `dc` a `bcdc` .</span><span class="sxs-lookup"><span data-stu-id="36b62-110">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="36b62-111">`bc`je typu `BaseClass` a jeho hodnota je typu `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-111">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="36b62-112">`dc`je typu `DerivedClass` a jeho hodnota je typu `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-112">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="36b62-113">`bcdc`je typu `BaseClass` a jeho hodnota je typu `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-113">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="36b62-114">Toto je proměnná, na kterou se má věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="36b62-114">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="36b62-115">Vzhledem k tomu, že `bc` a `bcdc` mají typ `BaseClass` , mohou přistupovat pouze k `Method1` , pokud nepoužíváte přetypování.</span><span class="sxs-lookup"><span data-stu-id="36b62-115">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="36b62-116">Proměnná `dc` má přístup k oběma `Method1` i `Method2` .</span><span class="sxs-lookup"><span data-stu-id="36b62-116">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="36b62-117">Tyto vztahy jsou uvedeny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="36b62-117">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="36b62-118">Dále přidejte následující `Method2` metodu do `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-118">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="36b62-119">Signatura této metody odpovídá signatuře `Method2` metody v `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-119">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="36b62-120">Vzhledem k tomu `BaseClass` , že nyní má `Method2` metodu, lze přidat druhý volající příkaz pro `BaseClass` proměnné `bc` a `bcdc` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="36b62-120">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="36b62-121">Při sestavování projektu vidíte, že přidání `Method2` metody v `BaseClass` způsobuje upozornění.</span><span class="sxs-lookup"><span data-stu-id="36b62-121">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="36b62-122">Upozornění říká, že `Method2` metoda v nástroji `DerivedClass` skrývá `Method2` metodu v `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-122">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="36b62-123">`new`Pokud máte v `Method2` úmyslu tento výsledek způsobit, doporučujeme použít klíčové slovo v definici.</span><span class="sxs-lookup"><span data-stu-id="36b62-123">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="36b62-124">Alternativně můžete přejmenovat jednu z `Method2` metod a vyřešit tak upozornění, ale to není vždy praktické.</span><span class="sxs-lookup"><span data-stu-id="36b62-124">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="36b62-125">Před přidáním `new` Spusťte program, aby se zobrazil výstup vyprodukovaný dalšími příkazy volání.</span><span class="sxs-lookup"><span data-stu-id="36b62-125">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="36b62-126">Zobrazí se následující výsledky.</span><span class="sxs-lookup"><span data-stu-id="36b62-126">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="36b62-127">`new`Klíčové slovo zachovává vztahy, které tvoří tento výstup, ale potlačí upozornění.</span><span class="sxs-lookup"><span data-stu-id="36b62-127">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="36b62-128">Proměnné, které mají typ `BaseClass` , budou mít i nadále přístup ke členům `BaseClass` a proměnná, která má typ, `DerivedClass` nadále přistupuje k členům v `DerivedClass` prvním a pak pro účely zvážení členů zděděných z `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-128">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="36b62-129">Chcete-li potlačit upozornění, přidejte `new` modifikátor do definice `Method2` v `DerivedClass` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="36b62-129">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="36b62-130">Modifikátor lze přidat před nebo po `public` .</span><span class="sxs-lookup"><span data-stu-id="36b62-130">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="36b62-131">Spusťte program znovu a ověřte, zda se výstup nezměnil.</span><span class="sxs-lookup"><span data-stu-id="36b62-131">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="36b62-132">Ověřte také, že se upozornění již nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="36b62-132">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="36b62-133">Pomocí můžete vyhodnotit, že jste `new` si vědomi, že člen, který upravuje, skrývá člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="36b62-133">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="36b62-134">Další informace o skrývání názvů prostřednictvím dědičnosti naleznete v tématu [new modifikátor](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="36b62-134">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="36b62-135">Chcete-li toto chování kontrastit na efekty použití `override` , přidejte následující metodu do `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-135">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="36b62-136">`override`Modifikátor lze přidat před nebo po `public` .</span><span class="sxs-lookup"><span data-stu-id="36b62-136">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="36b62-137">Přidejte `virtual` modifikátor do definice `Method1` v `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-137">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="36b62-138">`virtual`Modifikátor lze přidat před nebo po `public` .</span><span class="sxs-lookup"><span data-stu-id="36b62-138">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="36b62-139">Spusťte projekt znovu.</span><span class="sxs-lookup"><span data-stu-id="36b62-139">Run the project again.</span></span> <span data-ttu-id="36b62-140">Všimněte si zejména posledních dvou řádků následujícího výstupu.</span><span class="sxs-lookup"><span data-stu-id="36b62-140">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="36b62-141">Použití `override` modifikátoru umožňuje přístup k `bcdc` `Method1` metodě, která je definována v `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="36b62-141">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="36b62-142">Obvykle to je požadované chování v hierarchiích dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="36b62-142">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="36b62-143">Chcete, aby objekty, které mají hodnoty vytvořené z odvozené třídy, používaly metody, které jsou definovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="36b62-143">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="36b62-144">Toto chování dosáhnete použitím `override` k rozšiřování metody základní třídy.</span><span class="sxs-lookup"><span data-stu-id="36b62-144">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="36b62-145">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="36b62-145">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="36b62-146">Následující příklad ilustruje podobné chování v jiném kontextu.</span><span class="sxs-lookup"><span data-stu-id="36b62-146">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="36b62-147">Příklad definuje tři třídy: základní třídu s názvem `Car` a dvě třídy, které jsou odvozeny z ní `ConvertibleCar` a `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="36b62-147">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="36b62-148">Základní třída obsahuje `DescribeCar` metodu.</span><span class="sxs-lookup"><span data-stu-id="36b62-148">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="36b62-149">Metoda zobrazí základní popis auta a potom zavolá `ShowDetails` k poskytnutí dalších informací.</span><span class="sxs-lookup"><span data-stu-id="36b62-149">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="36b62-150">Každá ze tří tříd definuje `ShowDetails` metodu.</span><span class="sxs-lookup"><span data-stu-id="36b62-150">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="36b62-151">`new`Modifikátor slouží k definování `ShowDetails` ve `ConvertibleCar` třídě.</span><span class="sxs-lookup"><span data-stu-id="36b62-151">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="36b62-152">`override`Modifikátor slouží k definování `ShowDetails` ve `Minivan` třídě.</span><span class="sxs-lookup"><span data-stu-id="36b62-152">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="36b62-153">Příklad testuje, která verze `ShowDetails` je volána.</span><span class="sxs-lookup"><span data-stu-id="36b62-153">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="36b62-154">Následující metoda `TestCars1` deklaruje instanci každé třídy a poté volá `DescribeCar` každou instanci.</span><span class="sxs-lookup"><span data-stu-id="36b62-154">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="36b62-155">`TestCars1`Vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="36b62-155">`TestCars1` produces the following output.</span></span> <span data-ttu-id="36b62-156">Všimněte si zejména výsledků pro `car2` , což pravděpodobně není to, co jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="36b62-156">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="36b62-157">Typ objektu je `ConvertibleCar` , ale nemá přístup k `DescribeCar` verzi `ShowDetails` , která je definována ve `ConvertibleCar` třídě, protože tato metoda je deklarována s `new` modifikátorem, nikoli `override` modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="36b62-157">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="36b62-158">V důsledku toho `ConvertibleCar` objekt zobrazí stejný popis jako `Car` objekt.</span><span class="sxs-lookup"><span data-stu-id="36b62-158">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="36b62-159">Kontrastování výsledků pro `car3` , což je `Minivan` objekt.</span><span class="sxs-lookup"><span data-stu-id="36b62-159">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="36b62-160">V tomto případě `ShowDetails` metoda, která je deklarována v `Minivan` třídě `ShowDetails` , přepisuje metodu, která je deklarována ve `Car` třídě, a popis, který je zobrazen, popisuje minivan.</span><span class="sxs-lookup"><span data-stu-id="36b62-160">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="36b62-161">`TestCars2`Vytvoří seznam objektů, které mají typ `Car` .</span><span class="sxs-lookup"><span data-stu-id="36b62-161">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="36b62-162">Hodnoty objektů jsou vytvořeny z `Car` `ConvertibleCar` tříd, a `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="36b62-162">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="36b62-163">`DescribeCar`je volána u každého prvku seznamu.</span><span class="sxs-lookup"><span data-stu-id="36b62-163">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="36b62-164">Následující kód ukazuje definici `TestCars2` .</span><span class="sxs-lookup"><span data-stu-id="36b62-164">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="36b62-165">Zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="36b62-165">The following output is displayed.</span></span> <span data-ttu-id="36b62-166">Všimněte si, že je stejný jako výstup, který je zobrazen pomocí `TestCars1` .</span><span class="sxs-lookup"><span data-stu-id="36b62-166">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="36b62-167">`ShowDetails`Metoda `ConvertibleCar` třídy není volána, bez ohledu na to, zda je typ objektu `ConvertibleCar` , jako v `TestCars1` nebo `Car` , jako v `TestCars2` .</span><span class="sxs-lookup"><span data-stu-id="36b62-167">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="36b62-168">Naopak `car3` volá `ShowDetails` metodu z `Minivan` třídy v obou případech bez ohledu na to, zda obsahuje typ `Minivan` nebo typ `Car` .</span><span class="sxs-lookup"><span data-stu-id="36b62-168">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="36b62-169">Metody `TestCars3` a `TestCars4` dokončete příklad.</span><span class="sxs-lookup"><span data-stu-id="36b62-169">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="36b62-170">Tyto metody volají `ShowDetails` přímo, nejprve z objektů deklarovaných jako typ `ConvertibleCar` a `Minivan` ( `TestCars3` ), poté z objektů deklarovaných jako typ `Car` ( `TestCars4` ).</span><span class="sxs-lookup"><span data-stu-id="36b62-170">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="36b62-171">Následující kód definuje tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="36b62-171">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="36b62-172">Metody vyvolávají následující výstup, který odpovídá výsledkům z prvního příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="36b62-172">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="36b62-173">Následující kód ukazuje kompletní projekt a jeho výstup.</span><span class="sxs-lookup"><span data-stu-id="36b62-173">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36b62-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="36b62-174">See also</span></span>

- [<span data-ttu-id="36b62-175">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="36b62-175">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36b62-176">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="36b62-176">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="36b62-177">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="36b62-177">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="36b62-178">base</span><span class="sxs-lookup"><span data-stu-id="36b62-178">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="36b62-179">Výtah</span><span class="sxs-lookup"><span data-stu-id="36b62-179">abstract</span></span>](../../language-reference/keywords/abstract.md)
