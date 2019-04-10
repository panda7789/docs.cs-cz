---
title: Použít porovnávání vzorů funkce k rozšíření datových typů
description: V tomto kurzu pokročilé ukazuje, jak použít porovnávání vzorů techniky k vytvoření funkce pomocí dat a algoritmy, které se vytvářejí zvlášť.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 5fdd65fdb96cce05f15872969bbdd401095b59e5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308598"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="8af35-103">Kurz: Použití porovnávání vzorů funkce k rozšíření datových typů</span><span class="sxs-lookup"><span data-stu-id="8af35-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="8af35-104">C#7 zavedené základní vzor odpovídající funkce.</span><span class="sxs-lookup"><span data-stu-id="8af35-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="8af35-105">Tyto funkce jsou rozšířeny v C# 8 s výrazy typu new a vzory.</span><span class="sxs-lookup"><span data-stu-id="8af35-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="8af35-106">Můžete napsat funkci, která se chová, jako jste rozšířili typy, které mohou být v jiných knihovnách.</span><span class="sxs-lookup"><span data-stu-id="8af35-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="8af35-107">Další možností použití vzorců je vytvoření funkce, které vaše aplikace vyžaduje, která nejsou základní funkce rozšiřovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8af35-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="8af35-108">V tomto kurzu se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="8af35-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8af35-109">Rozpoznat situacích, kdy porovnávání vzorů by měl být použít.</span><span class="sxs-lookup"><span data-stu-id="8af35-109">Recognize situations where pattern matching should be used.</span></span>
> * <span data-ttu-id="8af35-110">Použití vzoru porovnávání výrazů k implementaci chování na základě typů a hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="8af35-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> * <span data-ttu-id="8af35-111">Kombinovat porovnávání vzorů s dalšími technikami, chcete-li vytvořit kompletní algoritmy.</span><span class="sxs-lookup"><span data-stu-id="8af35-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8af35-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8af35-112">Prerequisites</span></span>

<span data-ttu-id="8af35-113">Budete muset nastavit počítač pro spuštění .NET Core, včetně C# kompilátoru 8.0 ve verzi preview.</span><span class="sxs-lookup"><span data-stu-id="8af35-113">You'll need to set up your machine to run .NET Core, including the C# 8.0 preview compiler.</span></span> <span data-ttu-id="8af35-114">C# 8 kompilátoru ve verzi preview jsou k dispozici nejnovější [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), nebo si prohlédnout nejnovější [ve verzi preview rozhraní .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="8af35-114">The C# 8 preview compiler is available with the latest [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="8af35-115">Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8af35-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="8af35-116">Scénáře pro porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="8af35-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="8af35-117">Moderní vývoj často zahrnuje integraci dat z více zdrojů a vám informace a přehledy na základě těchto dat v jedné aplikaci získá na ucelenosti.</span><span class="sxs-lookup"><span data-stu-id="8af35-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="8af35-118">Vy a váš tým nebude mít ovládací prvek nebo přístupu pro všechny typy, které představují příchozí data.</span><span class="sxs-lookup"><span data-stu-id="8af35-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="8af35-119">Pro vytváření typů ve vaší aplikaci, které představují jednotlivé typy dat z těchto různých zdrojů dat by volat klasické objektově orientovaný návrh.</span><span class="sxs-lookup"><span data-stu-id="8af35-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="8af35-120">Aplikace by pak pracovat s těmito novými typy, vytváření hierarchie dědičnosti, vytvoření virtuální metody a implementaci abstrakcí.</span><span class="sxs-lookup"><span data-stu-id="8af35-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="8af35-121">Tyto techniky fungují a někdy jsou ty nejlepší nástroje.</span><span class="sxs-lookup"><span data-stu-id="8af35-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="8af35-122">Jindy můžete napsat menším množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="8af35-122">Other times you can write less code.</span></span> <span data-ttu-id="8af35-123">Můžete napsat další kód zrušte pomocí technik, které oddělují data od operací, které zpracovávají data.</span><span class="sxs-lookup"><span data-stu-id="8af35-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="8af35-124">V tomto kurzu vytvoříte a prozkoumejte aplikaci, která přebere příchozí data z několika externích zdrojů pro jeden scénář.</span><span class="sxs-lookup"><span data-stu-id="8af35-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="8af35-125">Uvidíte jak **porovnávání vzorů** poskytuje efektivní způsob, jak spotřebovat a zpracovat data způsoby, které nebyly součástí původního systému.</span><span class="sxs-lookup"><span data-stu-id="8af35-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="8af35-126">Vezměte v úvahu hlavní metro oblast, která používá ke správě přenosů dat mýtné a ceny za dobu ve špičce.</span><span class="sxs-lookup"><span data-stu-id="8af35-126">Consider a major metro area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="8af35-127">Můžete napsat aplikaci, která vypočítá mýtné vozidla na základě jeho typu.</span><span class="sxs-lookup"><span data-stu-id="8af35-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="8af35-128">Novější vylepšení zahrnují ceny na základě počtu osob ve vozidle.</span><span class="sxs-lookup"><span data-stu-id="8af35-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="8af35-129">Dále přidejte ceny založené na čas a den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="8af35-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="8af35-130">Z tohoto stručný popis vám může mít rychle šrafují si hierarchii objektů modelování tohoto systému.</span><span class="sxs-lookup"><span data-stu-id="8af35-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="8af35-131">Však vaše data pochází z více zdrojů, jako jsou jinými systémy pro správu registrace vozidlo.</span><span class="sxs-lookup"><span data-stu-id="8af35-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="8af35-132">Tyto systémy poskytují různé třídy k modelování dat a není nutné jeden objekt modelu, která vám pomůže.</span><span class="sxs-lookup"><span data-stu-id="8af35-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="8af35-133">V tomto kurzu použijete tyto zjednodušené třídy k modelování dat vozidla mezi těmito externími systémy, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8af35-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="8af35-134">Můžete stáhnout počáteční kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="8af35-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="8af35-135">Uvidíte, že třídy vozidlo jsou z různých systémů a jsou v různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="8af35-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="8af35-136">Žádné společné základní třídy, jiné než `System.Object` můžete využít.</span><span class="sxs-lookup"><span data-stu-id="8af35-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="8af35-137">Vzor odpovídající návrhy</span><span class="sxs-lookup"><span data-stu-id="8af35-137">Pattern matching designs</span></span>

<span data-ttu-id="8af35-138">Scénář používaných pro tento kurz stručný přehled druhy problémů, které vzorovou shodu je vhodná pro řešení:</span><span class="sxs-lookup"><span data-stu-id="8af35-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="8af35-139">Objekty, které potřebujete k práci s nejsou v hierarchii objektů, který odpovídá vaše cíle.</span><span class="sxs-lookup"><span data-stu-id="8af35-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="8af35-140">Pracujete s třídami, které jsou součástí nesouvisejících systémy.</span><span class="sxs-lookup"><span data-stu-id="8af35-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="8af35-141">Funkce, které přidáváte, které nejsou součástí základní abstrakce pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="8af35-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="8af35-142">Linka zaplaceno vozidla *změny* pro různé typy vozidel, ale linka není základní funkce vozidlo.</span><span class="sxs-lookup"><span data-stu-id="8af35-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="8af35-143">Když *tvar* dat a *operace* zabývat data nejsou společně popsané porovnávání vzorů funkce v C# usnadňují práci s.</span><span class="sxs-lookup"><span data-stu-id="8af35-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="8af35-144">Provádění výpočtů základní linka</span><span class="sxs-lookup"><span data-stu-id="8af35-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="8af35-145">Pouze na typ, který využívá nejzákladnější výpočtu linka:</span><span class="sxs-lookup"><span data-stu-id="8af35-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="8af35-146">A `Car` je $2.00.</span><span class="sxs-lookup"><span data-stu-id="8af35-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="8af35-147">A `Taxi` je 3.50 $.</span><span class="sxs-lookup"><span data-stu-id="8af35-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="8af35-148">A `Bus` je 5.00 $.</span><span class="sxs-lookup"><span data-stu-id="8af35-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="8af35-149">A `DeliveryTruck` je 10,00 USD</span><span class="sxs-lookup"><span data-stu-id="8af35-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="8af35-150">Vytvořte nový `TollCalculator` třídy a implementovat vzorce pro porovnávání na typ, který má získat velikost linka.</span><span class="sxs-lookup"><span data-stu-id="8af35-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="8af35-151">Následující kód ukazuje počáteční implementace `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8af35-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="8af35-152">Předchozí kód používá **výraz switch** (není stejný jako [ `switch` ](../language-reference/keywords/switch.md) příkaz), který testuje **vzor typu**.</span><span class="sxs-lookup"><span data-stu-id="8af35-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="8af35-153">A **výraz switch** začíná proměnnou, `vehicle` v předchozím kódu, za nímž následuje `switch` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8af35-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="8af35-154">Dále obsahuje všechny **přepnout arms** uvnitř složených závorek.</span><span class="sxs-lookup"><span data-stu-id="8af35-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="8af35-155">`switch` Výraz vytvoří další upřesnění zpráv o syntaxi, která obklopuje `switch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8af35-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="8af35-156">`case` – Klíčové slovo je vynechán, a výsledek každého arm je výraz.</span><span class="sxs-lookup"><span data-stu-id="8af35-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="8af35-157">Poslední dva arms zobrazit novou funkci jazyka.</span><span class="sxs-lookup"><span data-stu-id="8af35-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="8af35-158">`{ }` Případ odpovídá libovolný nenulový objekt, který neodpovídal starší arm.</span><span class="sxs-lookup"><span data-stu-id="8af35-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="8af35-159">Tato arm zachytí nesprávné typy předaný této metodě.</span><span class="sxs-lookup"><span data-stu-id="8af35-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="8af35-160">`{ }` Případu musí následovat případů pro každý typ vozidlo.</span><span class="sxs-lookup"><span data-stu-id="8af35-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="8af35-161">Pokud pořadí byly vráceny zpět, `{ }` případ má přednost.</span><span class="sxs-lookup"><span data-stu-id="8af35-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="8af35-162">Nakonec `null` zjistí vzor, kdy `null` je předaný této metodě.</span><span class="sxs-lookup"><span data-stu-id="8af35-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="8af35-163">`null` Model může být poslední, protože jiné vzory typ shodný s pouze nenulový objekt nesprávného typu.</span><span class="sxs-lookup"><span data-stu-id="8af35-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="8af35-164">Můžete otestovat tento kód, pomocí následujícího kódu v `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="8af35-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="8af35-165">Tento kód je součástí počáteční projekt, ale je označené jako komentář. Odstranit znaky komentářů, a budete moci otestovat, co jste napsali.</span><span class="sxs-lookup"><span data-stu-id="8af35-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="8af35-166">Začínáte naleznete v tématu Jak vzory vám může pomoci vytvořit algoritmy, kde jsou oddělené kód a data.</span><span class="sxs-lookup"><span data-stu-id="8af35-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="8af35-167">`switch` Výraz testuje typ a vytváří různé hodnoty na základě výsledků.</span><span class="sxs-lookup"><span data-stu-id="8af35-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="8af35-168">To je jenom začátek.</span><span class="sxs-lookup"><span data-stu-id="8af35-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="8af35-169">Přidat obsazení ceny</span><span class="sxs-lookup"><span data-stu-id="8af35-169">Add occupancy pricing</span></span>

<span data-ttu-id="8af35-170">Autorita linka se chce podporovat vozidel projít využívá maximální kapacitu.</span><span class="sxs-lookup"><span data-stu-id="8af35-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="8af35-171">Jste se rozhodli účtovat více při vozidel mají menší počet cestujících a podporovat plnou vozidel tím, že nabízí nižší ceny:</span><span class="sxs-lookup"><span data-stu-id="8af35-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="8af35-172">Auta nebo taxi s žádné cestujících platit navíc 0,50 USD.</span><span class="sxs-lookup"><span data-stu-id="8af35-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="8af35-173">Auta nebo taxi s dvěma cestujících získat 0,50 slevu.</span><span class="sxs-lookup"><span data-stu-id="8af35-173">Cars and taxis with two passengers get a 0.50 discount.</span></span>
- <span data-ttu-id="8af35-174">Auta nebo taxi se třemi nebo více cestujících získat slevu 1,00 $.</span><span class="sxs-lookup"><span data-stu-id="8af35-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="8af35-175">Sběrnice, které jsou kratší než 50 % úplné platit navíc 2.00 $.</span><span class="sxs-lookup"><span data-stu-id="8af35-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="8af35-176">Sběrnice, které jsou více než 90 % úplné získat slevu 1,00 $.</span><span class="sxs-lookup"><span data-stu-id="8af35-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="8af35-177">Tato pravidla je možné implementovat pomocí **vlastnost vzor** ve stejném výrazu přepínače.</span><span class="sxs-lookup"><span data-stu-id="8af35-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="8af35-178">Vzor pro vlastnost prozkoumá vlastností objektu po určil typ.</span><span class="sxs-lookup"><span data-stu-id="8af35-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="8af35-179">Jeden případ `Car` rozšíří na čtyři různé případy:</span><span class="sxs-lookup"><span data-stu-id="8af35-179">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="8af35-180">První tři případy typ jako testu `Car`, zkontrolujte hodnotu `Passengers` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8af35-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="8af35-181">Pokud se obě shodovat, tento výraz je vyhodnocen a vrácena.</span><span class="sxs-lookup"><span data-stu-id="8af35-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="8af35-182">By bylo třeba rozbalit také případy taxi podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="8af35-182">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="8af35-183">V předchozím příkladu `when` na posledním případě vynechání klauzule.</span><span class="sxs-lookup"><span data-stu-id="8af35-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="8af35-184">V dalším kroku implementujte obsazení pravidla tak, že rozbalíte případů pro sběrnice, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8af35-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="8af35-185">Autorita linka není problémem počet cestujících v trucks doručování.</span><span class="sxs-lookup"><span data-stu-id="8af35-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="8af35-186">Místo toho že účtovat více založené na třídě váha nákladních vozů.</span><span class="sxs-lookup"><span data-stu-id="8af35-186">Instead, they charge more based on the weight class of the trucks.</span></span> <span data-ttu-id="8af35-187">Trucks víc než 5000 lbs se účtují další 5.00 $.</span><span class="sxs-lookup"><span data-stu-id="8af35-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span> <span data-ttu-id="8af35-188">Světle trucks v části 3000 lbs disponují $2.00 slevy.</span><span class="sxs-lookup"><span data-stu-id="8af35-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span> <span data-ttu-id="8af35-189">Toto pravidlo je implementováno s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8af35-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="8af35-190">Předchozí kód ukazuje `when` klauzule přepínače arm.</span><span class="sxs-lookup"><span data-stu-id="8af35-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="8af35-191">Můžete použít `when` klauzule k testování podmínek jiné než rovnost pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8af35-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="8af35-192">Po dokončení budete mít metodu, která vypadá podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="8af35-192">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="8af35-193">Mnohé z nich přepnout arms jsou příklady **rekurzivní vzory**.</span><span class="sxs-lookup"><span data-stu-id="8af35-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="8af35-194">Například `Car { Passengers: 1}` zobrazuje konstantní vzorek uvnitř vlastnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="8af35-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="8af35-195">Méně opakované tento kód můžete provést pomocí vnořených přepínače.</span><span class="sxs-lookup"><span data-stu-id="8af35-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="8af35-196">`Car` a `Taxi` mají čtyři různé arms v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="8af35-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="8af35-197">V obou případech můžete vytvořit typ vzor, který se předají do vlastnosti modelu.</span><span class="sxs-lookup"><span data-stu-id="8af35-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="8af35-198">Tato technika je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8af35-198">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="8af35-199">V předchozím příkladu, pomocí výrazu rekurzivní znamená, že nemusíte opakovat `Car` a `Taxi` arms obsahující arms podřízený, které testují hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8af35-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="8af35-200">Tato technika se nepoužívá pro `Bus` a `DeliveryTruck` zbraní protože zbraně testování rozsahy pro vlastnost, nikoli jednotlivých hodnot.</span><span class="sxs-lookup"><span data-stu-id="8af35-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="8af35-201">Přidat ceny ve špičce</span><span class="sxs-lookup"><span data-stu-id="8af35-201">Add peak pricing</span></span>

<span data-ttu-id="8af35-202">Pro poslední funkci autority linka chce přidat dobu ve špičce citlivé ceny.</span><span class="sxs-lookup"><span data-stu-id="8af35-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="8af35-203">Během ráno a špičce hodin večer jsou mýtné dvojitá.</span><span class="sxs-lookup"><span data-stu-id="8af35-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="8af35-204">Toto pravidlo ovlivní pouze provoz v jednom směru: Město ráno příchozí a odchozí ve špičce hodině večer.</span><span class="sxs-lookup"><span data-stu-id="8af35-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="8af35-205">Během jindy během pracovního dne mýtné zvýšit o 50 %.</span><span class="sxs-lookup"><span data-stu-id="8af35-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="8af35-206">Noční pozdní a časná ráno, mýtné jsou sníženy o 25 %.</span><span class="sxs-lookup"><span data-stu-id="8af35-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="8af35-207">Během víkendu je normální rychlosti, bez ohledu na čas.</span><span class="sxs-lookup"><span data-stu-id="8af35-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="8af35-208">Porovnávání vzorů pro tuto funkci použijete, ale budete ji integrovat s dalšími technikami.</span><span class="sxs-lookup"><span data-stu-id="8af35-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="8af35-209">Může vytvořit jeden vzor odpovídající výraz, který by účet pro všechny kombinace směr, den v týdnu a čas.</span><span class="sxs-lookup"><span data-stu-id="8af35-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="8af35-210">Výsledek by byl složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="8af35-210">The result would be a complicated expression.</span></span> <span data-ttu-id="8af35-211">By bylo obtížné číst a obtížně srozumitelné.</span><span class="sxs-lookup"><span data-stu-id="8af35-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="8af35-212">Díky tomu se obtížně zajistili její správnost.</span><span class="sxs-lookup"><span data-stu-id="8af35-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="8af35-213">Místo toho sloučit tyto metody pro vytvoření n-tice hodnot, která stručně popisuje tyto stavy.</span><span class="sxs-lookup"><span data-stu-id="8af35-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="8af35-214">Pak pomocí porovnávání vzorů pro výpočet multiplikátor pro placená linka.</span><span class="sxs-lookup"><span data-stu-id="8af35-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="8af35-215">Řazené kolekce členů obsahuje tři samostatné podmínky:</span><span class="sxs-lookup"><span data-stu-id="8af35-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="8af35-216">Den je jeden den v týdnu nebo víkendech.</span><span class="sxs-lookup"><span data-stu-id="8af35-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="8af35-217">Vzdálené čas, kdy se shromažďují linka.</span><span class="sxs-lookup"><span data-stu-id="8af35-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="8af35-218">Směr je do město nebo z něj Město</span><span class="sxs-lookup"><span data-stu-id="8af35-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="8af35-219">Následující tabulka uvádí kombinace vstupních hodnot a ceny multiplikátor ve špičce:</span><span class="sxs-lookup"><span data-stu-id="8af35-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="8af35-220">Den</span><span class="sxs-lookup"><span data-stu-id="8af35-220">Day</span></span>        | <span data-ttu-id="8af35-221">Čas</span><span class="sxs-lookup"><span data-stu-id="8af35-221">Time</span></span>         | <span data-ttu-id="8af35-222">Směr</span><span class="sxs-lookup"><span data-stu-id="8af35-222">Direction</span></span> | <span data-ttu-id="8af35-223">Premium</span><span class="sxs-lookup"><span data-stu-id="8af35-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="8af35-224">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-224">Weekday</span></span>    | <span data-ttu-id="8af35-225">naléhavá ráno</span><span class="sxs-lookup"><span data-stu-id="8af35-225">morning rush</span></span> | <span data-ttu-id="8af35-226">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-226">inbound</span></span>   | <span data-ttu-id="8af35-227">x 2.00</span><span class="sxs-lookup"><span data-stu-id="8af35-227">x 2.00</span></span>  |
| <span data-ttu-id="8af35-228">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-228">Weekday</span></span>    | <span data-ttu-id="8af35-229">naléhavá ráno</span><span class="sxs-lookup"><span data-stu-id="8af35-229">morning rush</span></span> | <span data-ttu-id="8af35-230">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-230">outbound</span></span>  | <span data-ttu-id="8af35-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-231">x 1.00</span></span>  |
| <span data-ttu-id="8af35-232">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-232">Weekday</span></span>    | <span data-ttu-id="8af35-233">denní</span><span class="sxs-lookup"><span data-stu-id="8af35-233">daytime</span></span>      | <span data-ttu-id="8af35-234">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-234">inbound</span></span>   | <span data-ttu-id="8af35-235">x 1.50</span><span class="sxs-lookup"><span data-stu-id="8af35-235">x 1.50</span></span>  |
| <span data-ttu-id="8af35-236">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-236">Weekday</span></span>    | <span data-ttu-id="8af35-237">denní</span><span class="sxs-lookup"><span data-stu-id="8af35-237">daytime</span></span>      | <span data-ttu-id="8af35-238">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-238">outbound</span></span>  | <span data-ttu-id="8af35-239">x 1.50</span><span class="sxs-lookup"><span data-stu-id="8af35-239">x 1.50</span></span>  |
| <span data-ttu-id="8af35-240">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-240">Weekday</span></span>    | <span data-ttu-id="8af35-241">večer špičce</span><span class="sxs-lookup"><span data-stu-id="8af35-241">evening rush</span></span> | <span data-ttu-id="8af35-242">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-242">inbound</span></span>   | <span data-ttu-id="8af35-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-243">x 1.00</span></span>  |
| <span data-ttu-id="8af35-244">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-244">Weekday</span></span>    | <span data-ttu-id="8af35-245">večer špičce</span><span class="sxs-lookup"><span data-stu-id="8af35-245">evening rush</span></span> | <span data-ttu-id="8af35-246">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-246">outbound</span></span>  | <span data-ttu-id="8af35-247">x 2.00</span><span class="sxs-lookup"><span data-stu-id="8af35-247">x 2.00</span></span>  |
| <span data-ttu-id="8af35-248">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-248">Weekday</span></span>    | <span data-ttu-id="8af35-249">přes noc</span><span class="sxs-lookup"><span data-stu-id="8af35-249">overnight</span></span>    | <span data-ttu-id="8af35-250">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-250">inbound</span></span>   | <span data-ttu-id="8af35-251">x 0,75.</span><span class="sxs-lookup"><span data-stu-id="8af35-251">x 0.75</span></span>  |
| <span data-ttu-id="8af35-252">Den v týdnu</span><span class="sxs-lookup"><span data-stu-id="8af35-252">Weekday</span></span>    | <span data-ttu-id="8af35-253">přes noc</span><span class="sxs-lookup"><span data-stu-id="8af35-253">overnight</span></span>    | <span data-ttu-id="8af35-254">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-254">outbound</span></span>  | <span data-ttu-id="8af35-255">x 0,75.</span><span class="sxs-lookup"><span data-stu-id="8af35-255">x 0.75</span></span>  |
| <span data-ttu-id="8af35-256">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-256">Weekend</span></span>    | <span data-ttu-id="8af35-257">naléhavá ráno</span><span class="sxs-lookup"><span data-stu-id="8af35-257">morning rush</span></span> | <span data-ttu-id="8af35-258">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-258">inbound</span></span>   | <span data-ttu-id="8af35-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-259">x 1.00</span></span>  |
| <span data-ttu-id="8af35-260">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-260">Weekend</span></span>    | <span data-ttu-id="8af35-261">naléhavá ráno</span><span class="sxs-lookup"><span data-stu-id="8af35-261">morning rush</span></span> | <span data-ttu-id="8af35-262">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-262">outbound</span></span>  | <span data-ttu-id="8af35-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-263">x 1.00</span></span>  |
| <span data-ttu-id="8af35-264">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-264">Weekend</span></span>    | <span data-ttu-id="8af35-265">denní</span><span class="sxs-lookup"><span data-stu-id="8af35-265">daytime</span></span>      | <span data-ttu-id="8af35-266">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-266">inbound</span></span>   | <span data-ttu-id="8af35-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-267">x 1.00</span></span>  |
| <span data-ttu-id="8af35-268">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-268">Weekend</span></span>    | <span data-ttu-id="8af35-269">denní</span><span class="sxs-lookup"><span data-stu-id="8af35-269">daytime</span></span>      | <span data-ttu-id="8af35-270">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-270">outbound</span></span>  | <span data-ttu-id="8af35-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-271">x 1.00</span></span>  |
| <span data-ttu-id="8af35-272">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-272">Weekend</span></span>    | <span data-ttu-id="8af35-273">večer špičce</span><span class="sxs-lookup"><span data-stu-id="8af35-273">evening rush</span></span> | <span data-ttu-id="8af35-274">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-274">inbound</span></span>   | <span data-ttu-id="8af35-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-275">x 1.00</span></span>  |
| <span data-ttu-id="8af35-276">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-276">Weekend</span></span>    | <span data-ttu-id="8af35-277">večer špičce</span><span class="sxs-lookup"><span data-stu-id="8af35-277">evening rush</span></span> | <span data-ttu-id="8af35-278">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-278">outbound</span></span>  | <span data-ttu-id="8af35-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-279">x 1.00</span></span>  |
| <span data-ttu-id="8af35-280">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-280">Weekend</span></span>    | <span data-ttu-id="8af35-281">přes noc</span><span class="sxs-lookup"><span data-stu-id="8af35-281">overnight</span></span>    | <span data-ttu-id="8af35-282">Příchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-282">inbound</span></span>   | <span data-ttu-id="8af35-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-283">x 1.00</span></span>  |
| <span data-ttu-id="8af35-284">Víkendu</span><span class="sxs-lookup"><span data-stu-id="8af35-284">Weekend</span></span>    | <span data-ttu-id="8af35-285">přes noc</span><span class="sxs-lookup"><span data-stu-id="8af35-285">overnight</span></span>    | <span data-ttu-id="8af35-286">Odchozí</span><span class="sxs-lookup"><span data-stu-id="8af35-286">outbound</span></span>  | <span data-ttu-id="8af35-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="8af35-287">x 1.00</span></span>  |

<span data-ttu-id="8af35-288">Existují 16 různé kombinace tří proměnných.</span><span class="sxs-lookup"><span data-stu-id="8af35-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="8af35-289">Díky kombinaci některá z podmínek, zjednodušíte výraz konečné přepínače.</span><span class="sxs-lookup"><span data-stu-id="8af35-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="8af35-290">Používá systém, který shromažďuje mýtné <xref:System.DateTime> struktury po dobu, kdy byla shromážděna linka.</span><span class="sxs-lookup"><span data-stu-id="8af35-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="8af35-291">Vytvořte člena metody, které z předchozí tabulky vytvořte proměnné.</span><span class="sxs-lookup"><span data-stu-id="8af35-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="8af35-292">Následující funkce, která používá vzor odpovídající výraz přepínače vyjádřit, jestli <xref:System.DateTime> představuje víkend nebo jeden den v týdnu:</span><span class="sxs-lookup"><span data-stu-id="8af35-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="8af35-293">Tato metoda funguje, ale je automatizujete.</span><span class="sxs-lookup"><span data-stu-id="8af35-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="8af35-294">Nemůžete zjednodušit, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8af35-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="8af35-295">V dalším kroku přidejte podobnou funkci ke kategorizaci času bloky:</span><span class="sxs-lookup"><span data-stu-id="8af35-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="8af35-296">Předchozí metoda nepoužívá porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="8af35-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="8af35-297">Je jasnější, pomocí známých cascade z `if` příkazy.</span><span class="sxs-lookup"><span data-stu-id="8af35-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="8af35-298">Přidat soukromé `enum` převést každý časový rozsah na diskrétní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8af35-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="8af35-299">Po vytvoření tyto metody můžete použít jiné `switch` výraz s **vzor n-tice** k výpočtu cenové úrovně premium.</span><span class="sxs-lookup"><span data-stu-id="8af35-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="8af35-300">Může vytvářet `switch` výraz s všechny 16 arms:</span><span class="sxs-lookup"><span data-stu-id="8af35-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="8af35-301">Výše kód funguje, ale můžete se dá zjednodušit.</span><span class="sxs-lookup"><span data-stu-id="8af35-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="8af35-302">Všechny osm kombinace pro víkendu mají stejné linka.</span><span class="sxs-lookup"><span data-stu-id="8af35-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="8af35-303">Můžete nahradit všechny osm tento řádek:</span><span class="sxs-lookup"><span data-stu-id="8af35-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="8af35-304">Příchozí a odchozí provoz mají stejné multiplikátor během denní den v týdnu a hodiny přes noc.</span><span class="sxs-lookup"><span data-stu-id="8af35-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="8af35-305">Tyto čtyři přepínač arms je možné nahradit následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="8af35-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="8af35-306">Kód by měl vypadat jako v následujícím kódu až tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="8af35-306">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="8af35-307">Nakonec můžete odebrat dvě špičce hodinu případů, kdy platíte běžná cena.</span><span class="sxs-lookup"><span data-stu-id="8af35-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="8af35-308">Po odebrání těchto arms můžete nahradit `false` s zahození (`_`) v posledním přepínač arm.</span><span class="sxs-lookup"><span data-stu-id="8af35-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="8af35-309">Budete mít hotové následující metodu:</span><span class="sxs-lookup"><span data-stu-id="8af35-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="8af35-310">Tento příklad ukazuje, jednou z výhod porovnávání vzorů: větví vzor se vyhodnocují v pořadí.</span><span class="sxs-lookup"><span data-stu-id="8af35-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="8af35-311">Pokud změníte uspořádání, je tak, aby starší větev zpracovává jeden z novějších případy, kompilátor vás upozorní o nedosažitelném kódu.</span><span class="sxs-lookup"><span data-stu-id="8af35-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="8af35-312">Tato pravidla jazyk usnadnili provést předchozí zjednodušení s vědomím, že kód nezměnila.</span><span class="sxs-lookup"><span data-stu-id="8af35-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="8af35-313">Porovnávání vzorů provede některé typy kód lépe čitelný a nabízí alternativu k objektově orientované techniky, když kód nelze přidat do vašich tříd.</span><span class="sxs-lookup"><span data-stu-id="8af35-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="8af35-314">Data a funkce live této doby změny nepublikujete, příčinou je v cloudu.</span><span class="sxs-lookup"><span data-stu-id="8af35-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="8af35-315">*Tvar* dat a *operace* na to nejsou popsané nutně společně.</span><span class="sxs-lookup"><span data-stu-id="8af35-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="8af35-316">V tomto kurzu využívat existující data z jeho původní funkce zcela různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="8af35-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="8af35-317">Porovnávání vzorů přiřadil schopnost psát funkce, které overrode těchto typů, i když nelze rozšířit, je.</span><span class="sxs-lookup"><span data-stu-id="8af35-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8af35-318">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8af35-318">Next steps</span></span>

<span data-ttu-id="8af35-319">Dokončený kód z si můžete stáhnout [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="8af35-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="8af35-320">Prozkoumávání vzorců sami a přidejte tuto techniku regulární kódování aktivit.</span><span class="sxs-lookup"><span data-stu-id="8af35-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="8af35-321">Tyto techniky učení nabízí další způsob, jak přistupovat ke problémy a vytvořit nové funkce.</span><span class="sxs-lookup"><span data-stu-id="8af35-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
