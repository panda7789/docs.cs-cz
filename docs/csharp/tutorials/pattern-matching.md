---
title: Použití funkcí pro porovnávání vzorů k rozšiřování datových typů
description: Tento rozšířený kurz ukazuje, jak používat techniky porovnávání vzorů k vytváření funkcionality pomocí dat a algoritmů, které se vytvářejí samostatně.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: fd08e707402bfcd552997111a9c3fa58841a5466
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240051"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="329ad-103">Kurz: použití funkcí pro porovnávání vzorů k rozšiřování datových typů</span><span class="sxs-lookup"><span data-stu-id="329ad-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="329ad-104">C#7 představil základní funkce pro porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="329ad-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="329ad-105">Tyto funkce se v C# 8 rozšiřují novými výrazy a vzorci.</span><span class="sxs-lookup"><span data-stu-id="329ad-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="329ad-106">Můžete napsat funkčnost, která se chová, jako byste rozšířili typy, které mohou být v jiných knihovnách.</span><span class="sxs-lookup"><span data-stu-id="329ad-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="329ad-107">Další možností použití vzorů je vytvořit funkce, které vaše aplikace vyžaduje, nejedná se o základní funkci typu, který se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="329ad-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="329ad-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="329ad-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="329ad-109">Rozpoznává situace, kde by se měla použít porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="329ad-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="329ad-110">Použijte výrazy porovnávání vzorů k implementaci chování založeného na typech a hodnotách vlastností.</span><span class="sxs-lookup"><span data-stu-id="329ad-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="329ad-111">Kombinací porovnávání vzorů s jinými technikami vytvoříte kompletní algoritmy.</span><span class="sxs-lookup"><span data-stu-id="329ad-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="329ad-112">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="329ad-112">Prerequisites</span></span>

<span data-ttu-id="329ad-113">Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="329ad-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="329ad-114">Kompilátor C# 8 je k dispozici počínaje [verzí Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="329ad-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="329ad-115">V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="329ad-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="329ad-116">Scénáře pro porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="329ad-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="329ad-117">Moderní vývoj často zahrnuje integraci dat z více zdrojů a prezentování informací a přehledů z těchto dat v jediné soudržné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="329ad-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="329ad-118">Vy a váš tým nebude mít kontrolu ani přístup pro všechny typy, které reprezentují příchozí data.</span><span class="sxs-lookup"><span data-stu-id="329ad-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="329ad-119">Klasický objektově orientovaný návrh by volal pro vytváření typů ve vaší aplikaci, které reprezentují každý datový typ z těchto více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="329ad-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="329ad-120">Vaše aplikace pak bude pracovat s těmito novými typy, vytvořit Hierarchie dědičnosti, vytvářet virtuální metody a implementovat abstrakce.</span><span class="sxs-lookup"><span data-stu-id="329ad-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="329ad-121">Tyto techniky fungují a někdy jsou nejlepšími nástroji.</span><span class="sxs-lookup"><span data-stu-id="329ad-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="329ad-122">Jindy můžete psát méně kódu.</span><span class="sxs-lookup"><span data-stu-id="329ad-122">Other times you can write less code.</span></span> <span data-ttu-id="329ad-123">Můžete psát více jasných kódů pomocí technik, které oddělují data z operací, které manipulují s těmito daty.</span><span class="sxs-lookup"><span data-stu-id="329ad-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="329ad-124">V tomto kurzu vytvoříte a prozkoumáte aplikaci, která bude v jednom scénáři přijímat příchozí data z několika externích zdrojů.</span><span class="sxs-lookup"><span data-stu-id="329ad-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="329ad-125">Uvidíte, jak **porovnávání vzorů** poskytuje efektivní způsob, jak spotřebovávat a zpracovávat tato data způsobem, který nebyl součástí původního systému.</span><span class="sxs-lookup"><span data-stu-id="329ad-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="329ad-126">Vezměte v úvahu hlavní metropolitní oblast, která využívá mýtné a ceny za špičku ke správě provozu.</span><span class="sxs-lookup"><span data-stu-id="329ad-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="329ad-127">Napíšete aplikaci, která vypočítá mýtné pro vozidlo na základě jeho typu.</span><span class="sxs-lookup"><span data-stu-id="329ad-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="329ad-128">Pozdější vylepšení zahrnují ceny na základě počtu uživatelů v rámci vozidla.</span><span class="sxs-lookup"><span data-stu-id="329ad-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="329ad-129">Další vylepšení přidávají ceny na základě času a dne v týdnu.</span><span class="sxs-lookup"><span data-stu-id="329ad-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="329ad-130">Z tohoto krátkého popisu jste mohli rychle vykreslit hierarchii objektů k modelování tohoto systému.</span><span class="sxs-lookup"><span data-stu-id="329ad-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="329ad-131">Vaše data ale pocházejí z několika zdrojů, jako jsou jiné systémy pro správu registrace vozidel.</span><span class="sxs-lookup"><span data-stu-id="329ad-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="329ad-132">Tyto systémy poskytují různé třídy pro modelování dat a nemáte jeden objektový model, který můžete použít.</span><span class="sxs-lookup"><span data-stu-id="329ad-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="329ad-133">V tomto kurzu použijete tyto zjednodušené třídy pro modelování dat vozidel z těchto externích systémů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="329ad-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="329ad-134">Počáteční kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub.</span><span class="sxs-lookup"><span data-stu-id="329ad-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="329ad-135">Můžete vidět, že třídy vozidel jsou z různých systémů a jsou v různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="329ad-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="329ad-136">Není možné využít žádnou společnou základní třídu, kromě `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="329ad-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="329ad-137">Vzory porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="329ad-137">Pattern matching designs</span></span>

<span data-ttu-id="329ad-138">Scénář použitý v tomto kurzu zvýrazňuje druhy problémů, které porovnávání vzorů je vhodné pro řešení:</span><span class="sxs-lookup"><span data-stu-id="329ad-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="329ad-139">Objekty, se kterými potřebujete pracovat, nejsou v hierarchii objektů, které odpovídají vašim cílům.</span><span class="sxs-lookup"><span data-stu-id="329ad-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="329ad-140">Možná budete pracovat s třídami, které jsou součástí nesouvisejících systémů.</span><span class="sxs-lookup"><span data-stu-id="329ad-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="329ad-141">Funkce, kterou přidáváte, není součástí základní abstrakce pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="329ad-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="329ad-142">Telefonní linka *placená změnou vozidla pro různé* typy vozidel, ale placená linka není základní funkcí vozidla.</span><span class="sxs-lookup"><span data-stu-id="329ad-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="329ad-143">Pokud *tvar* dat a *operace* na těchto datech nejsou popsány společně, funkce pro porovnávání vzorů v C# nástroji usnadňuje práci s.</span><span class="sxs-lookup"><span data-stu-id="329ad-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="329ad-144">Implementace základních výpočtů mýtné</span><span class="sxs-lookup"><span data-stu-id="329ad-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="329ad-145">Základní výpočet placená linka se spoléhá jenom na typ vozidla:</span><span class="sxs-lookup"><span data-stu-id="329ad-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="329ad-146">`Car` je $2,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="329ad-147">`Taxi` je $3,50.</span><span class="sxs-lookup"><span data-stu-id="329ad-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="329ad-148">`Bus` je $5,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="329ad-149">`DeliveryTruck` je $10,00</span><span class="sxs-lookup"><span data-stu-id="329ad-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="329ad-150">Vytvořte novou třídu `TollCalculator` a implementujte porovnávání vzorů pro typ vozidla, abyste získali hodnotu mýtné.</span><span class="sxs-lookup"><span data-stu-id="329ad-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="329ad-151">Následující kód ukazuje počáteční implementaci `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="329ad-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

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

<span data-ttu-id="329ad-152">Předchozí kód používá **výraz Switch** (není stejný jako příkaz [`switch`](../language-reference/keywords/switch.md) ), který testuje **vzor typu**.</span><span class="sxs-lookup"><span data-stu-id="329ad-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="329ad-153">**Výraz Switch** začíná proměnnou, `vehicle` v předchozím kódu následovaný klíčovým slovem `switch`.</span><span class="sxs-lookup"><span data-stu-id="329ad-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="329ad-154">Dál přijde všechna **ramena přepínače** uvnitř složených závorek.</span><span class="sxs-lookup"><span data-stu-id="329ad-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="329ad-155">Výraz `switch` umožňuje další upřesnění syntaxe, která obklopuje příkaz `switch`.</span><span class="sxs-lookup"><span data-stu-id="329ad-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="329ad-156">Klíčové slovo `case` je vynecháno a výsledek každého ARM je výraz.</span><span class="sxs-lookup"><span data-stu-id="329ad-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="329ad-157">Poslední dvě paže zobrazují novou funkci jazyka.</span><span class="sxs-lookup"><span data-stu-id="329ad-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="329ad-158">`{ }` Case odpovídá jakémukoli objektu, který není null, který se neshodoval s dřívějším procesorem ARM.</span><span class="sxs-lookup"><span data-stu-id="329ad-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="329ad-159">Tato ARM zachytí všechny nesprávné typy předané do této metody.</span><span class="sxs-lookup"><span data-stu-id="329ad-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="329ad-160">`{ }` případ musí splňovat jednotlivé typy vozidel.</span><span class="sxs-lookup"><span data-stu-id="329ad-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="329ad-161">Pokud byla objednávka stornována, má `{ }` případ přednost.</span><span class="sxs-lookup"><span data-stu-id="329ad-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="329ad-162">A konečně, `null` vzor detekuje, když se do této metody předává `null`.</span><span class="sxs-lookup"><span data-stu-id="329ad-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="329ad-163">Vzor `null` může být poslední, protože jiné vzorce typu odpovídají pouze nenulovému objektu správného typu.</span><span class="sxs-lookup"><span data-stu-id="329ad-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="329ad-164">Tento kód můžete otestovat pomocí následujícího kódu v `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="329ad-164">You can test this code using the following code in `Program.cs`:</span></span>

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

<span data-ttu-id="329ad-165">Tento kód je obsažen v projektu Starter, ale je označen jako komentář. Odstraňte komentáře a můžete testovat, co jste napsali.</span><span class="sxs-lookup"><span data-stu-id="329ad-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="329ad-166">Začínáte, jak vzory vám pomohou vytvořit algoritmy, kde je kód a data odděleny.</span><span class="sxs-lookup"><span data-stu-id="329ad-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="329ad-167">Výraz `switch` testuje typ a vytváří různé hodnoty na základě výsledků.</span><span class="sxs-lookup"><span data-stu-id="329ad-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="329ad-168">To je jenom začátek.</span><span class="sxs-lookup"><span data-stu-id="329ad-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="329ad-169">Přidat ceny obsazení</span><span class="sxs-lookup"><span data-stu-id="329ad-169">Add occupancy pricing</span></span>

<span data-ttu-id="329ad-170">Autorita pro telefonní linky chce, aby dokázala povzbudit kapacitu vozidel při maximální kapacitě.</span><span class="sxs-lookup"><span data-stu-id="329ad-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="329ad-171">Rozhodla se doúčtovat více, pokud vozidlo má méně cestujících, a podporuje plná vozidla tím, že nabízí nižší ceny:</span><span class="sxs-lookup"><span data-stu-id="329ad-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="329ad-172">Automobily a Taxis bez cestujících platíte navíc $0,50.</span><span class="sxs-lookup"><span data-stu-id="329ad-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="329ad-173">Automobily a Taxis se dvěma cestujícími získají slevu $0,50.</span><span class="sxs-lookup"><span data-stu-id="329ad-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="329ad-174">Automobily a Taxis se třemi nebo více cestujícími získají slevu $1,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="329ad-175">Na sběrnicích, které jsou menší než 50%, se zaplatí extra $2,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="329ad-176">Pro autobusy, které jsou v plném rozsahu 90%, se zobrazí sleva $1,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="329ad-177">Tato pravidla lze implementovat pomocí **vzoru vlastnosti** ve stejném výrazu přepínače.</span><span class="sxs-lookup"><span data-stu-id="329ad-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="329ad-178">Po určení typu se vzorek vlastnosti prověřuje vlastnostmi objektu.</span><span class="sxs-lookup"><span data-stu-id="329ad-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="329ad-179">Jednotlivý případ `Car` se rozšíří na čtyři různé případy:</span><span class="sxs-lookup"><span data-stu-id="329ad-179">The single case for a `Car` expands to four different cases:</span></span>

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

<span data-ttu-id="329ad-180">První tři případy testují typ jako `Car`a pak zkontrolují hodnotu vlastnosti `Passengers`.</span><span class="sxs-lookup"><span data-stu-id="329ad-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="329ad-181">Pokud oba odpovídají, vyhodnotí se tento výraz a vrátí se.</span><span class="sxs-lookup"><span data-stu-id="329ad-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="329ad-182">Také rozšíříte případy pro Taxis podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="329ad-182">You would also expand the cases for taxis in a similar manner:</span></span>

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

<span data-ttu-id="329ad-183">V předchozím příkladu byla klauzule `when` v konečném případě vynechána.</span><span class="sxs-lookup"><span data-stu-id="329ad-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="329ad-184">Dále implementujte pravidla obsazení rozšířením případů pro autobusy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="329ad-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

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

<span data-ttu-id="329ad-185">Autorita pro telefonní linky se netýká počtu cestujících v dodacích vozíkech.</span><span class="sxs-lookup"><span data-stu-id="329ad-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="329ad-186">Místo toho upraví hodnotu mýtné na základě váhy třídy nákladových vozíků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="329ad-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="329ad-187">Za vozíky nad 5000 kg se účtuje extra $5,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="329ad-188">Lehkými nákladními za 3000 kg se předává sleva $2,00.</span><span class="sxs-lookup"><span data-stu-id="329ad-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="329ad-189">Toto pravidlo je implementováno s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="329ad-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="329ad-190">Předchozí kód ukazuje klauzuli `when` ARM přepínače.</span><span class="sxs-lookup"><span data-stu-id="329ad-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="329ad-191">Použijte klauzuli `when` pro testování jiných podmínek než rovnosti u vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="329ad-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="329ad-192">Až budete hotovi, budete mít metodu, která vypadá podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="329ad-192">When you've finished, you'll have a method that looks much like the following:</span></span>

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
    
    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

<span data-ttu-id="329ad-193">Mnohé z těchto palných zbraní jsou příklady **rekurzivních vzorů**.</span><span class="sxs-lookup"><span data-stu-id="329ad-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="329ad-194">Například `Car { Passengers: 1}` zobrazuje v rámci vzoru vlastnosti konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="329ad-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="329ad-195">Pomocí vnořených přepínačů můžete tento kód méně vyměnit.</span><span class="sxs-lookup"><span data-stu-id="329ad-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="329ad-196">V předchozích příkladech mají `Car` a `Taxi` obě různé zbraně.</span><span class="sxs-lookup"><span data-stu-id="329ad-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="329ad-197">V obou případech můžete vytvořit vzor typu, který bude informační kanál do vzoru vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="329ad-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="329ad-198">Tato technika je znázorněna v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="329ad-198">This technique is shown in the following code:</span></span>

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

<span data-ttu-id="329ad-199">V předchozím příkladu použití rekurzivního výrazu znamená, že neopakujete `Car` a `Taxi` zbraně obsahující podřízená ramena, která testují hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="329ad-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="329ad-200">Tato technika se nepoužívá pro `Bus` a `DeliveryTruck` zbraně, protože tyto zbraně jsou testovací rozsahy pro vlastnost, nikoli diskrétní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="329ad-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="329ad-201">Přidat ceny ve špičce</span><span class="sxs-lookup"><span data-stu-id="329ad-201">Add peak pricing</span></span>

<span data-ttu-id="329ad-202">U konečné funkce chce autorita pro telefonní linky přidat ceny za špičku v časově citlivém čase.</span><span class="sxs-lookup"><span data-stu-id="329ad-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="329ad-203">Během ráno a večer nespěcháte hodin se telefonní linky zdvojnásobí.</span><span class="sxs-lookup"><span data-stu-id="329ad-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="329ad-204">Toto pravidlo má vliv pouze na provoz v jednom směru: příchozí na město v ráno a odchozí v večer nespěcháte hodinu.</span><span class="sxs-lookup"><span data-stu-id="329ad-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="329ad-205">Během jiné doby během pracovního dne se telefonní linky zvyšují o 50%.</span><span class="sxs-lookup"><span data-stu-id="329ad-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="329ad-206">Pozdě v noci a včas ráno se telefonní linky snižují o 25%.</span><span class="sxs-lookup"><span data-stu-id="329ad-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="329ad-207">Během víkendu se jedná o normální sazbu bez ohledu na čas.</span><span class="sxs-lookup"><span data-stu-id="329ad-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="329ad-208">Pro tuto funkci použijete porovnávání vzorů, ale budete je integrovat s jinými technikami.</span><span class="sxs-lookup"><span data-stu-id="329ad-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="329ad-209">Můžete sestavit výraz porovnávání s jednou maskou, který by měl být v souladu se všemi kombinacemi směr, den v týdnu a čas.</span><span class="sxs-lookup"><span data-stu-id="329ad-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="329ad-210">Výsledkem by byl složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="329ad-210">The result would be a complicated expression.</span></span> <span data-ttu-id="329ad-211">Bylo těžké ho přečíst a obtížně pochopit.</span><span class="sxs-lookup"><span data-stu-id="329ad-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="329ad-212">Díky tomu je obtížné zajistit správnost.</span><span class="sxs-lookup"><span data-stu-id="329ad-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="329ad-213">Místo toho Zkombinujte tyto metody pro sestavení řazené kolekce členů hodnot, které stručně popisují všechny tyto stavy.</span><span class="sxs-lookup"><span data-stu-id="329ad-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="329ad-214">Pak použijte porovnávání vzorů k výpočtu násobitele pro mýtné.</span><span class="sxs-lookup"><span data-stu-id="329ad-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="329ad-215">Řazená kolekce členů obsahuje tři diskrétní podmínky:</span><span class="sxs-lookup"><span data-stu-id="329ad-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="329ad-216">Den je buď den v týdnu, nebo víkend.</span><span class="sxs-lookup"><span data-stu-id="329ad-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="329ad-217">Časové pásmo, ve kterém se má linka nashromáždit.</span><span class="sxs-lookup"><span data-stu-id="329ad-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="329ad-218">Směr je na město nebo od města.</span><span class="sxs-lookup"><span data-stu-id="329ad-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="329ad-219">V následující tabulce jsou uvedeny kombinace vstupních hodnot a násobitele cen ve špičce:</span><span class="sxs-lookup"><span data-stu-id="329ad-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="329ad-220">Day</span><span class="sxs-lookup"><span data-stu-id="329ad-220">Day</span></span>        | <span data-ttu-id="329ad-221">Čas</span><span class="sxs-lookup"><span data-stu-id="329ad-221">Time</span></span>         | <span data-ttu-id="329ad-222">Směr</span><span class="sxs-lookup"><span data-stu-id="329ad-222">Direction</span></span> | <span data-ttu-id="329ad-223">Premium</span><span class="sxs-lookup"><span data-stu-id="329ad-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="329ad-224">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-224">Weekday</span></span>    | <span data-ttu-id="329ad-225">ráno nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-225">morning rush</span></span> | <span data-ttu-id="329ad-226">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-226">inbound</span></span>   | <span data-ttu-id="329ad-227">× 2,00</span><span class="sxs-lookup"><span data-stu-id="329ad-227">x 2.00</span></span>  |
| <span data-ttu-id="329ad-228">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-228">Weekday</span></span>    | <span data-ttu-id="329ad-229">ráno nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-229">morning rush</span></span> | <span data-ttu-id="329ad-230">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-230">outbound</span></span>  | <span data-ttu-id="329ad-231">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-231">x 1.00</span></span>  |
| <span data-ttu-id="329ad-232">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-232">Weekday</span></span>    | <span data-ttu-id="329ad-233">Daytime</span><span class="sxs-lookup"><span data-stu-id="329ad-233">daytime</span></span>      | <span data-ttu-id="329ad-234">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-234">inbound</span></span>   | <span data-ttu-id="329ad-235">× 1,50</span><span class="sxs-lookup"><span data-stu-id="329ad-235">x 1.50</span></span>  |
| <span data-ttu-id="329ad-236">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-236">Weekday</span></span>    | <span data-ttu-id="329ad-237">Daytime</span><span class="sxs-lookup"><span data-stu-id="329ad-237">daytime</span></span>      | <span data-ttu-id="329ad-238">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-238">outbound</span></span>  | <span data-ttu-id="329ad-239">× 1,50</span><span class="sxs-lookup"><span data-stu-id="329ad-239">x 1.50</span></span>  |
| <span data-ttu-id="329ad-240">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-240">Weekday</span></span>    | <span data-ttu-id="329ad-241">večerní nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-241">evening rush</span></span> | <span data-ttu-id="329ad-242">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-242">inbound</span></span>   | <span data-ttu-id="329ad-243">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-243">x 1.00</span></span>  |
| <span data-ttu-id="329ad-244">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-244">Weekday</span></span>    | <span data-ttu-id="329ad-245">večerní nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-245">evening rush</span></span> | <span data-ttu-id="329ad-246">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-246">outbound</span></span>  | <span data-ttu-id="329ad-247">× 2,00</span><span class="sxs-lookup"><span data-stu-id="329ad-247">x 2.00</span></span>  |
| <span data-ttu-id="329ad-248">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-248">Weekday</span></span>    | <span data-ttu-id="329ad-249">přes noc</span><span class="sxs-lookup"><span data-stu-id="329ad-249">overnight</span></span>    | <span data-ttu-id="329ad-250">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-250">inbound</span></span>   | <span data-ttu-id="329ad-251">× 0,75</span><span class="sxs-lookup"><span data-stu-id="329ad-251">x 0.75</span></span>  |
| <span data-ttu-id="329ad-252">Názvy</span><span class="sxs-lookup"><span data-stu-id="329ad-252">Weekday</span></span>    | <span data-ttu-id="329ad-253">přes noc</span><span class="sxs-lookup"><span data-stu-id="329ad-253">overnight</span></span>    | <span data-ttu-id="329ad-254">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-254">outbound</span></span>  | <span data-ttu-id="329ad-255">× 0,75</span><span class="sxs-lookup"><span data-stu-id="329ad-255">x 0.75</span></span>  |
| <span data-ttu-id="329ad-256">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-256">Weekend</span></span>    | <span data-ttu-id="329ad-257">ráno nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-257">morning rush</span></span> | <span data-ttu-id="329ad-258">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-258">inbound</span></span>   | <span data-ttu-id="329ad-259">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-259">x 1.00</span></span>  |
| <span data-ttu-id="329ad-260">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-260">Weekend</span></span>    | <span data-ttu-id="329ad-261">ráno nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-261">morning rush</span></span> | <span data-ttu-id="329ad-262">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-262">outbound</span></span>  | <span data-ttu-id="329ad-263">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-263">x 1.00</span></span>  |
| <span data-ttu-id="329ad-264">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-264">Weekend</span></span>    | <span data-ttu-id="329ad-265">Daytime</span><span class="sxs-lookup"><span data-stu-id="329ad-265">daytime</span></span>      | <span data-ttu-id="329ad-266">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-266">inbound</span></span>   | <span data-ttu-id="329ad-267">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-267">x 1.00</span></span>  |
| <span data-ttu-id="329ad-268">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-268">Weekend</span></span>    | <span data-ttu-id="329ad-269">Daytime</span><span class="sxs-lookup"><span data-stu-id="329ad-269">daytime</span></span>      | <span data-ttu-id="329ad-270">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-270">outbound</span></span>  | <span data-ttu-id="329ad-271">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-271">x 1.00</span></span>  |
| <span data-ttu-id="329ad-272">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-272">Weekend</span></span>    | <span data-ttu-id="329ad-273">večerní nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-273">evening rush</span></span> | <span data-ttu-id="329ad-274">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-274">inbound</span></span>   | <span data-ttu-id="329ad-275">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-275">x 1.00</span></span>  |
| <span data-ttu-id="329ad-276">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-276">Weekend</span></span>    | <span data-ttu-id="329ad-277">večerní nespěcháte</span><span class="sxs-lookup"><span data-stu-id="329ad-277">evening rush</span></span> | <span data-ttu-id="329ad-278">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-278">outbound</span></span>  | <span data-ttu-id="329ad-279">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-279">x 1.00</span></span>  |
| <span data-ttu-id="329ad-280">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-280">Weekend</span></span>    | <span data-ttu-id="329ad-281">přes noc</span><span class="sxs-lookup"><span data-stu-id="329ad-281">overnight</span></span>    | <span data-ttu-id="329ad-282">příjem</span><span class="sxs-lookup"><span data-stu-id="329ad-282">inbound</span></span>   | <span data-ttu-id="329ad-283">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-283">x 1.00</span></span>  |
| <span data-ttu-id="329ad-284">Volné</span><span class="sxs-lookup"><span data-stu-id="329ad-284">Weekend</span></span>    | <span data-ttu-id="329ad-285">přes noc</span><span class="sxs-lookup"><span data-stu-id="329ad-285">overnight</span></span>    | <span data-ttu-id="329ad-286">komunikace</span><span class="sxs-lookup"><span data-stu-id="329ad-286">outbound</span></span>  | <span data-ttu-id="329ad-287">× 1,00</span><span class="sxs-lookup"><span data-stu-id="329ad-287">x 1.00</span></span>  |

<span data-ttu-id="329ad-288">Existují 16 různých kombinací tří proměnných.</span><span class="sxs-lookup"><span data-stu-id="329ad-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="329ad-289">Kombinací některých podmínek zjednodušete výraz finálního přepínače.</span><span class="sxs-lookup"><span data-stu-id="329ad-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="329ad-290">Systém, který shromažďuje mýtné, používá strukturu <xref:System.DateTime> pro čas, kdy byla placená linka shromažďována.</span><span class="sxs-lookup"><span data-stu-id="329ad-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="329ad-291">Sestavujte členské metody, které vytvoří proměnné z předchozí tabulky.</span><span class="sxs-lookup"><span data-stu-id="329ad-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="329ad-292">Následující funkce používá výraz porovnávání vzorů k vyjádření, zda <xref:System.DateTime> představuje víkend nebo den v týdnu:</span><span class="sxs-lookup"><span data-stu-id="329ad-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

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

<span data-ttu-id="329ad-293">Tato metoda funguje, ale je repetitious.</span><span class="sxs-lookup"><span data-stu-id="329ad-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="329ad-294">Můžete ho zjednodušit, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="329ad-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="329ad-295">Dále přidejte podobnou funkci pro kategorizaci času do bloků:</span><span class="sxs-lookup"><span data-stu-id="329ad-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="329ad-296">Předchozí metoda nepoužívá porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="329ad-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="329ad-297">Je jasné, že se seznámíte s `if`mi příkazy.</span><span class="sxs-lookup"><span data-stu-id="329ad-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="329ad-298">Můžete přidat privátní `enum` pro převod jednotlivých časových úseků na samostatnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="329ad-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="329ad-299">Po vytvoření těchto metod můžete použít jiný výraz `switch` se **vzorem řazené kolekce členů** pro výpočet cenové úrovně Premium.</span><span class="sxs-lookup"><span data-stu-id="329ad-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="329ad-300">Můžete sestavit výraz `switch` se všemi 16 opěrkami rukou:</span><span class="sxs-lookup"><span data-stu-id="329ad-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="329ad-301">Výše uvedený kód funguje, ale může být zjednodušený.</span><span class="sxs-lookup"><span data-stu-id="329ad-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="329ad-302">Všechny osm kombinací pro daný víkend mají stejnou mýtné.</span><span class="sxs-lookup"><span data-stu-id="329ad-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="329ad-303">Všechna osm můžete nahradit následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="329ad-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="329ad-304">Příchozí i odchozí provoz mají stejný násobitel během dne v týdnu denní a jednodenních hodin.</span><span class="sxs-lookup"><span data-stu-id="329ad-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="329ad-305">Tyto čtyři paže s přepínačem lze nahradit následujícími dvěma řádky:</span><span class="sxs-lookup"><span data-stu-id="329ad-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="329ad-306">Kód by měl vypadat jako následující kód po těchto dvou změnách:</span><span class="sxs-lookup"><span data-stu-id="329ad-306">The code should look like the following code after those two changes:</span></span>

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

<span data-ttu-id="329ad-307">Nakonec můžete odebrat dvě nespěcháte hodiny, které platí pro běžnou cenu.</span><span class="sxs-lookup"><span data-stu-id="329ad-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="329ad-308">Po odebrání těchto zbraní můžete `false` nahradit pomocí zahození (`_`) v konečném přepínači ARM.</span><span class="sxs-lookup"><span data-stu-id="329ad-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="329ad-309">Budete mít následující metodu, kterou jste dokončili:</span><span class="sxs-lookup"><span data-stu-id="329ad-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="329ad-310">Tento příklad zvýrazňuje jednu z výhod porovnávání vzorů: větve vzorů jsou vyhodnocovány v pořadí.</span><span class="sxs-lookup"><span data-stu-id="329ad-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="329ad-311">V případě, že je změníte jejich uspořádání tak, aby předchozí větev zpracovává jeden z vašich pozdějších případů, kompilátor vás upozorní na nedosažitelný kód.</span><span class="sxs-lookup"><span data-stu-id="329ad-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="329ad-312">Tato jazyková pravidla usnadňují provádění předchozích zjednodušení s jistotou, že se kód nezměnil.</span><span class="sxs-lookup"><span data-stu-id="329ad-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="329ad-313">Porovnávání vzorů usnadňuje čtení některých typů kódu a nabízí alternativu k objektově orientovaným technikám, když nemůžete přidat kód do tříd.</span><span class="sxs-lookup"><span data-stu-id="329ad-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="329ad-314">Cloud způsobuje živá data a funkce.</span><span class="sxs-lookup"><span data-stu-id="329ad-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="329ad-315">*Tvar* dat a jeho *operace* nejsou nutně popsány společně.</span><span class="sxs-lookup"><span data-stu-id="329ad-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="329ad-316">V tomto kurzu jste ze své původní funkce využili stávající data zcela různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="329ad-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="329ad-317">Porovnávání vzorů vám dává možnost psát funkce, které tyto typy overrode, i když je nemůžete roztáhnout.</span><span class="sxs-lookup"><span data-stu-id="329ad-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="329ad-318">Další kroky</span><span class="sxs-lookup"><span data-stu-id="329ad-318">Next steps</span></span>

<span data-ttu-id="329ad-319">Hotový kód si můžete stáhnout z úložiště GitHub [/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub.</span><span class="sxs-lookup"><span data-stu-id="329ad-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="329ad-320">Prozkoumejte vlastní modely a přidejte tuto techniku do vašich běžných kódovacích aktivit.</span><span class="sxs-lookup"><span data-stu-id="329ad-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="329ad-321">Výukové postupy poskytují další způsob přístupu k problémům a vytváření nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="329ad-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
