---
title: Znalost, kdy použít nová klíčová slova – a přepsání C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: b1d99b0c5241a99ba7f621faff7c39d20776b2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646147"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="1264a-102">Znalost, kdy použít klíčová slova override a new (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1264a-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="1264a-103">V jazyce C# metoda v odvozené třídě, může mít stejný název jako metodu v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="1264a-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="1264a-104">Můžete určit, jak interagovat pomocí metody [nové](../../../csharp/language-reference/keywords/new.md) a [přepsat](../../../csharp/language-reference/keywords/override.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="1264a-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="1264a-105">`override` Modifikátor *rozšiřuje* metodu základní třídy a `new` modifikátor *skryje* ho.</span><span class="sxs-lookup"><span data-stu-id="1264a-105">The `override` modifier *extends* the base class method, and the `new` modifier *hides* it.</span></span> <span data-ttu-id="1264a-106">Rozdíl je znázorněn v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1264a-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="1264a-107">V konzolové aplikaci, deklarujte následující dvě třídy `BaseClass` a `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="1264a-108">`DerivedClass` dědí z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="1264a-109">V `Main` metody deklarovat proměnné `bc`, `dc`, a `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="1264a-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="1264a-110">`bc` je typu `BaseClass`, a její hodnota je typu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="1264a-111">`dc` je typu `DerivedClass`, a její hodnota je typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="1264a-112">`bcdc` je typu `BaseClass`, a její hodnota je typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="1264a-113">Jedná se o proměnnou je potřeba věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="1264a-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="1264a-114">Protože `bc` a `bcdc` mít typ `BaseClass`, bude moct pouze přímo `Method1`, pokud nechcete použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="1264a-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="1264a-115">Proměnné `dc` přístup i k `Method1` a `Method2`.</span><span class="sxs-lookup"><span data-stu-id="1264a-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="1264a-116">Tyto vztahy jsou uvedeny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1264a-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="1264a-117">V dalším kroku přidejte následující `Method2` metodu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="1264a-118">Signatura této metody shoduje se signaturou `Method2` metoda ve `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="1264a-119">Protože `BaseClass` má teď `Method2` metoda, je možné přidat druhý volání příkazu pro `BaseClass` proměnné `bc` a `bcdc`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1264a-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="1264a-120">Když vytvoříte projekt, uvidíte, že přidání `Method2` metoda ve `BaseClass` způsobí, že upozornění.</span><span class="sxs-lookup"><span data-stu-id="1264a-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="1264a-121">Upozornění, která `Method2` metoda ve `DerivedClass` skryje `Method2` metoda ve `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="1264a-122">Doporučujeme použít `new` – klíčové slovo v `Method2` definice, pokud máte v úmyslu způsobovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="1264a-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="1264a-123">Můžete také přejmenovat některou `Method2` metody k vyřešení upozornění, ale to není vždy reálné.</span><span class="sxs-lookup"><span data-stu-id="1264a-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="1264a-124">Před přidáním `new`, spusťte program, který se zobrazí výstup vytvářených další volání příkazů.</span><span class="sxs-lookup"><span data-stu-id="1264a-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="1264a-125">Zobrazí se následující výsledky.</span><span class="sxs-lookup"><span data-stu-id="1264a-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="1264a-126">`new` – Klíčové slovo uchovává vztahy, které tento výstup, ale potlačí upozornění.</span><span class="sxs-lookup"><span data-stu-id="1264a-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="1264a-127">Proměnné, které mají typ `BaseClass` i nadále přístup ke členům `BaseClass`a proměnné, která má typ `DerivedClass` i nadále přístup ke členům v `DerivedClass` první a potom zvážit členy zděděné z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="1264a-128">Chcete-li potlačit upozornění, přidejte `new` modifikátor definici typu `Method2` v `DerivedClass`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1264a-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="1264a-129">Modifikátor se dají přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="1264a-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="1264a-130">Spusťte program znovu k ověření, že nedošlo ke změně ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="1264a-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="1264a-131">Dál ověřte, že už se zobrazí upozornění.</span><span class="sxs-lookup"><span data-stu-id="1264a-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="1264a-132">S použitím `new`, jsou potvrzující, že jste si vědomi, že člen, který upravuje skryje člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1264a-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="1264a-133">Další informace o skrytí názvu prostřednictvím dědičnosti, naleznete v tématu [new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="1264a-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="1264a-134">Porovnání toto chování účinky použití `override`, přidejte následující metodu do `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="1264a-135">`override` Modifikátor se dají přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="1264a-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="1264a-136">Přidat `virtual` modifikátor definici typu `Method1` v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="1264a-137">`virtual` Modifikátor se dají přidat před nebo po `public`.</span><span class="sxs-lookup"><span data-stu-id="1264a-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="1264a-138">Spusťte projekt znovu.</span><span class="sxs-lookup"><span data-stu-id="1264a-138">Run the project again.</span></span> <span data-ttu-id="1264a-139">Všimněte si zejména poslední dva řádky následující výstup.</span><span class="sxs-lookup"><span data-stu-id="1264a-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="1264a-140">Použití `override` modifikátor umožňuje `bcdc` přístup `Method1` metodu, která je definována v `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="1264a-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="1264a-141">Obvykle se jedná o požadované chování v hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="1264a-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="1264a-142">Chcete, aby objekty, které obsahují hodnoty, které jsou vytvořeny z odvozené třídy použít metody, které jsou definovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="1264a-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="1264a-143">Dosažení tohoto chování pomocí `override` rozšířit metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1264a-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="1264a-144">Následující kód obsahuje úplný příklad.</span><span class="sxs-lookup"><span data-stu-id="1264a-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="1264a-145">Následující příklad ukazuje podobné chování v jiném kontextu.</span><span class="sxs-lookup"><span data-stu-id="1264a-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="1264a-146">Příklad definuje tři třídy: základní třídu s názvem `Car` a dvě třídy, které jsou odvozeny z něj, `ConvertibleCar` a `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="1264a-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="1264a-147">Obsahuje základní třídy `DescribeCar` metoda.</span><span class="sxs-lookup"><span data-stu-id="1264a-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="1264a-148">Metoda zobrazuje základní popis automobilu a pak zavolá `ShowDetails` k poskytnutí dalších informací.</span><span class="sxs-lookup"><span data-stu-id="1264a-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="1264a-149">Všechny tři třídy definuje `ShowDetails` metoda.</span><span class="sxs-lookup"><span data-stu-id="1264a-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="1264a-150">`new` Modifikátor se používá k definování `ShowDetails` v `ConvertibleCar` třídy.</span><span class="sxs-lookup"><span data-stu-id="1264a-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="1264a-151">`override` Modifikátor se používá k definování `ShowDetails` v `Minivan` třídy.</span><span class="sxs-lookup"><span data-stu-id="1264a-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="1264a-152">Příklad testuje, kterou verzi `ShowDetails` je volána.</span><span class="sxs-lookup"><span data-stu-id="1264a-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="1264a-153">Následující metoda `TestCars1`deklaruje instancí každé třídy a pak zavolá `DescribeCar` pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="1264a-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="1264a-154">`TestCars1` vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="1264a-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="1264a-155">Všimněte si zejména výsledky `car2`, které jsou pravděpodobně není co jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="1264a-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="1264a-156">Typ objektu je `ConvertibleCar`, ale `DescribeCar` není přístup k verzi `ShowDetails` , která je definována v `ConvertibleCar` třídy, protože tato metoda je deklarován s `new` modifikátor, ne `override` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="1264a-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="1264a-157">V důsledku toho `ConvertibleCar` objekt zobrazí popis stejné jako `Car` objektu.</span><span class="sxs-lookup"><span data-stu-id="1264a-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="1264a-158">Porovnejte výsledky `car3`, což je `Minivan` objektu.</span><span class="sxs-lookup"><span data-stu-id="1264a-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="1264a-159">V takovém případě `ShowDetails` metodu, která je deklarována v `Minivan` třídy přepsání `ShowDetails` metodu, která je deklarována v `Car` minivan popisuje třídy a popis, který se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="1264a-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="1264a-160">`TestCars2` Vytvoří seznam objektů, které mají typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="1264a-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="1264a-161">Hodnoty objekty jsou instancemi `Car`, `ConvertibleCar`, a `Minivan` třídy.</span><span class="sxs-lookup"><span data-stu-id="1264a-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="1264a-162">`DescribeCar` je volána na každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="1264a-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="1264a-163">Následující kód ukazuje definici `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="1264a-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="1264a-164">Zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="1264a-164">The following output is displayed.</span></span> <span data-ttu-id="1264a-165">Všimněte si, že je stejný jako výstup, který se zobrazí při `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="1264a-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="1264a-166">`ShowDetails` Metodu `ConvertibleCar` třídy není volána, bez ohledu na to, zda je typ objektu `ConvertibleCar`, například `TestCars1`, nebo `Car`, například `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="1264a-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="1264a-167">Naopak `car3` volání `ShowDetails` metodu z `Minivan` třídy v obou případech se, zda má typ `Minivan` nebo typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="1264a-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="1264a-168">Metody `TestCars3` a `TestCars4` dokončení příkladu.</span><span class="sxs-lookup"><span data-stu-id="1264a-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="1264a-169">Tyto metody volat `ShowDetails` přímo, nejprve z objektů deklarován mít typ `ConvertibleCar` a `Minivan` (`TestCars3`), pak z objekty deklarované typu `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="1264a-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="1264a-170">Následující kód definuje tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="1264a-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="1264a-171">Metody vytvoří následující výstup, který odpovídá výsledky z prvního příkladu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1264a-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="1264a-172">Následující kód ukazuje celý projekt a její výstup.</span><span class="sxs-lookup"><span data-stu-id="1264a-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1264a-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1264a-173">See also</span></span>

- [<span data-ttu-id="1264a-174">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1264a-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1264a-175">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="1264a-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="1264a-176">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="1264a-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="1264a-177">base</span><span class="sxs-lookup"><span data-stu-id="1264a-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="1264a-178">abstract</span><span class="sxs-lookup"><span data-stu-id="1264a-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
