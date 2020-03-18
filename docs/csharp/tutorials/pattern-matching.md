---
title: Použití prvků porovnávání vzorů k rozšíření datových typů
description: Tento pokročilý kurz ukazuje, jak používat techniky porovnávání vzorů k vytvoření funkce pomocí dat a algoritmů, které jsou vytvořeny samostatně.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: df1054d8e0ec2b2539e6a1d00bf353d8ca927397
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156529"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="4736a-103">Kurz: Použití funkcí porovnávání vzorů k rozšíření datových typů</span><span class="sxs-lookup"><span data-stu-id="4736a-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="4736a-104">C# 7 představil základní funkce odpovídající vzor.</span><span class="sxs-lookup"><span data-stu-id="4736a-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="4736a-105">Tyto funkce jsou rozšířeny v C# 8 s novými výrazy a vzory.</span><span class="sxs-lookup"><span data-stu-id="4736a-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="4736a-106">Můžete psát funkce, které se chová, jako byste rozšířené typy, které mohou být v jiných knihovnách.</span><span class="sxs-lookup"><span data-stu-id="4736a-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="4736a-107">Další použití pro vzory je vytvořit funkce, které vaše aplikace vyžaduje, že není základní funkce typu, který je rozšířen.</span><span class="sxs-lookup"><span data-stu-id="4736a-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="4736a-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="4736a-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="4736a-109">Rozpoznat situace, kde by měl být použit porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="4736a-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="4736a-110">K implementaci chování na základě typů a hodnot vlastností použijte výrazy porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="4736a-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="4736a-111">Zkombinujte porovnávání vzorů s jinými technikami a vytvořte úplné algoritmy.</span><span class="sxs-lookup"><span data-stu-id="4736a-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4736a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4736a-112">Prerequisites</span></span>

<span data-ttu-id="4736a-113">Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="4736a-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="4736a-114">Kompilátor Jazyka C# 8 je k dispozici počínaje [sadou Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="4736a-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="4736a-115">Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně Visual Studio nebo .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="4736a-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="4736a-116">Scénáře pro porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="4736a-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="4736a-117">Moderní vývoj často zahrnuje integraci dat z více zdrojů a prezentaci informací a poznatků z nich v jedné soudržné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4736a-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="4736a-118">Vy a váš tým nebudete mít kontrolu nebo přístup pro všechny typy, které představují příchozí data.</span><span class="sxs-lookup"><span data-stu-id="4736a-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="4736a-119">Klasický objektově orientovaný návrh by volal pro vytváření typů ve vaší aplikaci, které představují každý datový typ z těchto více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="4736a-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="4736a-120">Potom aplikace bude pracovat s těmito novými typy, sestavení hierarchie dědičnosti, vytvářet virtuální metody a implementovat abstrakce.</span><span class="sxs-lookup"><span data-stu-id="4736a-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="4736a-121">Tyto techniky fungují, a někdy jsou nejlepší nástroje.</span><span class="sxs-lookup"><span data-stu-id="4736a-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="4736a-122">Jindy můžete napsat méně kódu.</span><span class="sxs-lookup"><span data-stu-id="4736a-122">Other times you can write less code.</span></span> <span data-ttu-id="4736a-123">Můžete napsat více jasný kód pomocí technik, které oddělují data z operací, které pracují s daty.</span><span class="sxs-lookup"><span data-stu-id="4736a-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="4736a-124">V tomto kurzu vytvoříte a prozkoumáte aplikaci, která přebírá příchozí data z několika externích zdrojů pro jeden scénář.</span><span class="sxs-lookup"><span data-stu-id="4736a-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="4736a-125">Uvidíte, jak **porovnávání vzorů** poskytuje efektivní způsob, jak využívat a zpracovávat tato data způsoby, které nebyly součástí původního systému.</span><span class="sxs-lookup"><span data-stu-id="4736a-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="4736a-126">Vezměme si hlavní metropolitní oblast, která používá mýtné a ceny ve špičce pro správu provozu.</span><span class="sxs-lookup"><span data-stu-id="4736a-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="4736a-127">Napíšete aplikaci, která vypočítá mýtné pro vozidlo na základě jeho typu.</span><span class="sxs-lookup"><span data-stu-id="4736a-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="4736a-128">Pozdější vylepšení zahrnují ceny na základě počtu cestujících ve vozidle.</span><span class="sxs-lookup"><span data-stu-id="4736a-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="4736a-129">Další vylepšení přidávají ceny na základě času a dne v týdnu.</span><span class="sxs-lookup"><span data-stu-id="4736a-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="4736a-130">Z tohoto stručného popisu jste možná rychle načrtli hierarchii objektů, abyste tento systém modelovali.</span><span class="sxs-lookup"><span data-stu-id="4736a-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="4736a-131">Vaše data však pocházejí z více zdrojů, jako jsou jiné systémy řízení registrace vozidel.</span><span class="sxs-lookup"><span data-stu-id="4736a-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="4736a-132">Tyto systémy poskytují různé třídy pro modelování dat a nemáte jeden objektový model, který můžete použít.</span><span class="sxs-lookup"><span data-stu-id="4736a-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="4736a-133">V tomto kurzu budete používat tyto zjednodušené třídy k modelování dat vozidel z těchto externích systémů, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4736a-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="4736a-134">Startovací kód si můžete stáhnout z úložiště [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start)</span><span class="sxs-lookup"><span data-stu-id="4736a-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="4736a-135">Můžete vidět, že třídy vozidel jsou z různých systémů a jsou v různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="4736a-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="4736a-136">Žádná společná základní třída, kromě `System.Object` toho, že může být využita.</span><span class="sxs-lookup"><span data-stu-id="4736a-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="4736a-137">Vzory odpovídající návrhy</span><span class="sxs-lookup"><span data-stu-id="4736a-137">Pattern matching designs</span></span>

<span data-ttu-id="4736a-138">Scénář použitý v tomto kurzu upozorňuje na druhy problémů, které odpovídá vzor je vhodný k řešení:</span><span class="sxs-lookup"><span data-stu-id="4736a-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="4736a-139">Objekty, se kterými potřebujete pracovat, nejsou v hierarchii objektů, která odpovídá vašim cílům.</span><span class="sxs-lookup"><span data-stu-id="4736a-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="4736a-140">Je možné, že pracujete s třídami, které jsou součástí nesouvisejících systémů.</span><span class="sxs-lookup"><span data-stu-id="4736a-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="4736a-141">Funkce, které přidáváte, není součástí základní abstrakce pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="4736a-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="4736a-142">Mýtné placené vozidlem *se mění* pro různé typy vozidel, ale mýtné není základní funkcí vozidla.</span><span class="sxs-lookup"><span data-stu-id="4736a-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="4736a-143">Pokud *tvar* dat a *operace* na těchto datech nejsou popsány společně, funkce porovnávání vzorů v C# usnadňují práci s.</span><span class="sxs-lookup"><span data-stu-id="4736a-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="4736a-144">Provedení základních výpočtů mýtného</span><span class="sxs-lookup"><span data-stu-id="4736a-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="4736a-145">Nejzákladnější výpočet mýtného se opírá pouze o typ vozidla:</span><span class="sxs-lookup"><span data-stu-id="4736a-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="4736a-146">A `Car` je 2,00 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="4736a-147">A `Taxi` je 3,50 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="4736a-148">A `Bus` je 5,00 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="4736a-149">A `DeliveryTruck` je 10,00 dolarů</span><span class="sxs-lookup"><span data-stu-id="4736a-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="4736a-150">Vytvořte `TollCalculator` novou třídu a implementujte odpovídající vzor na typu vozidla, abyste získali částku mýtného.</span><span class="sxs-lookup"><span data-stu-id="4736a-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="4736a-151">Následující kód ukazuje počáteční implementaci `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="4736a-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

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

<span data-ttu-id="4736a-152">Předchozí kód používá **výraz přepínače** (není [`switch`](../language-reference/keywords/switch.md) stejný jako příkaz), který testuje **vzor typu**.</span><span class="sxs-lookup"><span data-stu-id="4736a-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="4736a-153">**Výraz přepínače** začíná proměnnou `vehicle` v předchozím kódu následovaném klíčovým slovem. `switch`</span><span class="sxs-lookup"><span data-stu-id="4736a-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="4736a-154">Dále přicházejí všechny **ramena spínače** uvnitř kudrnatých šle.</span><span class="sxs-lookup"><span data-stu-id="4736a-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="4736a-155">Výraz `switch` provede další vylepšení syntaxe, která `switch` obklopuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="4736a-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="4736a-156">Klíčové `case` slovo je vynecháno a výsledkem každé rameno je výraz.</span><span class="sxs-lookup"><span data-stu-id="4736a-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="4736a-157">Poslední dvě paže ukazují novou jazykovou funkci.</span><span class="sxs-lookup"><span data-stu-id="4736a-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="4736a-158">Případ `{ }` odpovídá všem objektům, které nemají hodnotu null a které neodpovídají předchozí ruce.</span><span class="sxs-lookup"><span data-stu-id="4736a-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="4736a-159">Toto rameno zachytí všechny nesprávné typy předané této metodě.</span><span class="sxs-lookup"><span data-stu-id="4736a-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="4736a-160">Pouzdro `{ }` musí následovat případy pro každý typ vozidla.</span><span class="sxs-lookup"><span data-stu-id="4736a-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="4736a-161">Pokud by bylo pořadí `{ }` obráceno, měl by přednost případ.</span><span class="sxs-lookup"><span data-stu-id="4736a-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="4736a-162">Nakonec `null` vzor detekuje při `null` předání této metodě.</span><span class="sxs-lookup"><span data-stu-id="4736a-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="4736a-163">Vzorek `null` může být poslední, protože jiné vzory typu odpovídají pouze objektu bez hodnoty null správného typu.</span><span class="sxs-lookup"><span data-stu-id="4736a-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="4736a-164">Tento kód můžete otestovat pomocí `Program.cs`následujícího kódu v :</span><span class="sxs-lookup"><span data-stu-id="4736a-164">You can test this code using the following code in `Program.cs`:</span></span>

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

<span data-ttu-id="4736a-165">Tento kód je součástí počátečního projektu, ale je zakomentován. Odeberte komentáře a můžete otestovat, co jste napsali.</span><span class="sxs-lookup"><span data-stu-id="4736a-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="4736a-166">Začínáte vidět, jak vzory vám mohou pomoci vytvořit algoritmy, kde kód a data jsou oddělené.</span><span class="sxs-lookup"><span data-stu-id="4736a-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="4736a-167">Výraz `switch` testuje typ a vytváří různé hodnoty na základě výsledků.</span><span class="sxs-lookup"><span data-stu-id="4736a-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="4736a-168">To je jen začátek.</span><span class="sxs-lookup"><span data-stu-id="4736a-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="4736a-169">Přidání cen obsazenosti</span><span class="sxs-lookup"><span data-stu-id="4736a-169">Add occupancy pricing</span></span>

<span data-ttu-id="4736a-170">Mýtný úřad chce motivovat vozidla k jízdě na maximální kapacitu.</span><span class="sxs-lookup"><span data-stu-id="4736a-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="4736a-171">Rozhodli se účtovat více, když mají vozidla méně cestujících, a podporují plná vozidla tím, že nabízejí nižší ceny:</span><span class="sxs-lookup"><span data-stu-id="4736a-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="4736a-172">Auta a taxíky bez pasažérů zaplatí dalších 0,50 usd.</span><span class="sxs-lookup"><span data-stu-id="4736a-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="4736a-173">Auta a taxíky se dvěma cestujícími získat slevu 0,50 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="4736a-174">Auta a taxíky se třemi nebo více cestujícími získají slevu 1,00 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="4736a-175">Autobusy, které jsou méně než 50% plné platit extra 2,00 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="4736a-176">Autobusy, které jsou více než 90% plné získat slevu 1,00 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="4736a-177">Tato pravidla lze implementovat pomocí **vzoru vlastnosti** ve stejném výrazu přepínač.</span><span class="sxs-lookup"><span data-stu-id="4736a-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="4736a-178">Vzor vlastností zkoumá vlastnosti objektu po určení typu.</span><span class="sxs-lookup"><span data-stu-id="4736a-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="4736a-179">Jediný případ pro `Car` rozšíření na čtyři různé případy:</span><span class="sxs-lookup"><span data-stu-id="4736a-179">The single case for a `Car` expands to four different cases:</span></span>

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

<span data-ttu-id="4736a-180">První tři případy test typu `Car`jako , pak `Passengers` zkontrolujte hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4736a-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="4736a-181">Pokud obě shody, tento výraz je vyhodnocena a vrácena.</span><span class="sxs-lookup"><span data-stu-id="4736a-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="4736a-182">Byste také rozšířit případy pro taxíky podobným způsobem:</span><span class="sxs-lookup"><span data-stu-id="4736a-182">You would also expand the cases for taxis in a similar manner:</span></span>

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

<span data-ttu-id="4736a-183">V předchozím příkladu `when` byla klauzule vynechána v konečném případě.</span><span class="sxs-lookup"><span data-stu-id="4736a-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="4736a-184">Dále implementujte pravidla obsazenosti rozšířením případů pro autobusy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4736a-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

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

<span data-ttu-id="4736a-185">Mýtný úřad se nezabývá počtem cestujících v dodávkách.</span><span class="sxs-lookup"><span data-stu-id="4736a-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="4736a-186">Místo toho upraví výši mýtného na základě hmotnostní třídy nákladních vozidel takto:</span><span class="sxs-lookup"><span data-stu-id="4736a-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="4736a-187">Nákladní vozidla nad 5000 liber jsou účtovány extra 5,00 dolarů.</span><span class="sxs-lookup"><span data-stu-id="4736a-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="4736a-188">Lehké nákladní automobily pod 3000 liber jsou uvedeny 2,00 dolarů slevu.</span><span class="sxs-lookup"><span data-stu-id="4736a-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="4736a-189">Toto pravidlo je implementováno pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4736a-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="4736a-190">Předchozí kód zobrazuje `when` klauzuli ramene switch.</span><span class="sxs-lookup"><span data-stu-id="4736a-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="4736a-191">Klauzule `when` slouží k testování podmínek jiných než rovnost na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4736a-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="4736a-192">Po dokončení budete mít metodu, která vypadá podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="4736a-192">When you've finished, you'll have a method that looks much like the following:</span></span>

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

<span data-ttu-id="4736a-193">Mnohé z těchto přepínačů jsou příklady **rekurzivních vzorů**.</span><span class="sxs-lookup"><span data-stu-id="4736a-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="4736a-194">Například `Car { Passengers: 1}` zobrazuje konstantní vzorek uvnitř vzoru vlastností.</span><span class="sxs-lookup"><span data-stu-id="4736a-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="4736a-195">Tento kód můžete provést méně opakující se pomocí vnořené přepínače.</span><span class="sxs-lookup"><span data-stu-id="4736a-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="4736a-196">`Car` A `Taxi` oba mají čtyři různé zbraně v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="4736a-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="4736a-197">V obou případech můžete vytvořit vzorek textu, který se vkládá do vzoru vlastností.</span><span class="sxs-lookup"><span data-stu-id="4736a-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="4736a-198">Tato technika je uvedena v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4736a-198">This technique is shown in the following code:</span></span>

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

<span data-ttu-id="4736a-199">V předchozí ukázce použití rekurzivního výrazu znamená, že neopakujete `Car` a `Taxi` ramena obsahující podřízené ramena, která testují hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4736a-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="4736a-200">Tato technika se nepoužívá `Bus` pro `DeliveryTruck` a zbraně, protože tyto zbraně jsou testovací rozsahy pro vlastnost, nikoli diskrétní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4736a-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="4736a-201">Přidání špičkových cen</span><span class="sxs-lookup"><span data-stu-id="4736a-201">Add peak pricing</span></span>

<span data-ttu-id="4736a-202">Pro konečnou funkci chce orgán pro výběr mýtného přidat časově citlivé ceny ve špičce.</span><span class="sxs-lookup"><span data-stu-id="4736a-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="4736a-203">Během ranní a večerní špičky se mýtné zdvojnásobí.</span><span class="sxs-lookup"><span data-stu-id="4736a-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="4736a-204">Toto pravidlo ovlivňuje pouze provoz v jednom směru: příchozí do města v dopoledních hodinách, a odchozí ve večerní špičce.</span><span class="sxs-lookup"><span data-stu-id="4736a-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="4736a-205">Během jiných časů během pracovního dne se mýtné zvyšuje o 50 %.</span><span class="sxs-lookup"><span data-stu-id="4736a-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="4736a-206">Pozdě v noci a brzy ráno se mýtné snižuje o 25%.</span><span class="sxs-lookup"><span data-stu-id="4736a-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="4736a-207">Během víkendu je to běžná sazba, bez ohledu na čas.</span><span class="sxs-lookup"><span data-stu-id="4736a-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="4736a-208">Budete používat porovnávání vzorů pro tuto funkci, ale budete integrovat s jinými technikami.</span><span class="sxs-lookup"><span data-stu-id="4736a-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="4736a-209">Můžete vytvořit jeden vzor odpovídající výraz, který by účet pro všechny kombinace směru, den v týdnu a čas.</span><span class="sxs-lookup"><span data-stu-id="4736a-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="4736a-210">Výsledkem by byl složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="4736a-210">The result would be a complicated expression.</span></span> <span data-ttu-id="4736a-211">Bylo by těžké číst a těžko pochopit.</span><span class="sxs-lookup"><span data-stu-id="4736a-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="4736a-212">To ztěžuje zajištění správnosti.</span><span class="sxs-lookup"><span data-stu-id="4736a-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="4736a-213">Místo toho zkombinujte tyto metody k vytvoření řazené kolekce členů s hodnotami, které výstižně popisují všechny tyto stavy.</span><span class="sxs-lookup"><span data-stu-id="4736a-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="4736a-214">Pak použijte porovnávání vzorů k výpočtu multiplikátoru pro mýtné.</span><span class="sxs-lookup"><span data-stu-id="4736a-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="4736a-215">Řazená kolekce členů obsahuje tři diskrétní podmínky:</span><span class="sxs-lookup"><span data-stu-id="4736a-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="4736a-216">Den je buď všední den nebo víkend.</span><span class="sxs-lookup"><span data-stu-id="4736a-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="4736a-217">Pásmo času, kdy se vybírá mýtné.</span><span class="sxs-lookup"><span data-stu-id="4736a-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="4736a-218">Směr je do města nebo mimo město</span><span class="sxs-lookup"><span data-stu-id="4736a-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="4736a-219">V následující tabulce jsou uvedeny kombinace vstupních hodnot a násobitele cen ve špičce:</span><span class="sxs-lookup"><span data-stu-id="4736a-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="4736a-220">Den</span><span class="sxs-lookup"><span data-stu-id="4736a-220">Day</span></span>        | <span data-ttu-id="4736a-221">Time</span><span class="sxs-lookup"><span data-stu-id="4736a-221">Time</span></span>         | <span data-ttu-id="4736a-222">Směr</span><span class="sxs-lookup"><span data-stu-id="4736a-222">Direction</span></span> | <span data-ttu-id="4736a-223">Premium</span><span class="sxs-lookup"><span data-stu-id="4736a-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="4736a-224">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-224">Weekday</span></span>    | <span data-ttu-id="4736a-225">ranní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-225">morning rush</span></span> | <span data-ttu-id="4736a-226">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-226">inbound</span></span>   | <span data-ttu-id="4736a-227">x 2,00</span><span class="sxs-lookup"><span data-stu-id="4736a-227">x 2.00</span></span>  |
| <span data-ttu-id="4736a-228">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-228">Weekday</span></span>    | <span data-ttu-id="4736a-229">ranní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-229">morning rush</span></span> | <span data-ttu-id="4736a-230">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-230">outbound</span></span>  | <span data-ttu-id="4736a-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-231">x 1.00</span></span>  |
| <span data-ttu-id="4736a-232">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-232">Weekday</span></span>    | <span data-ttu-id="4736a-233">Denní</span><span class="sxs-lookup"><span data-stu-id="4736a-233">daytime</span></span>      | <span data-ttu-id="4736a-234">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-234">inbound</span></span>   | <span data-ttu-id="4736a-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="4736a-235">x 1.50</span></span>  |
| <span data-ttu-id="4736a-236">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-236">Weekday</span></span>    | <span data-ttu-id="4736a-237">Denní</span><span class="sxs-lookup"><span data-stu-id="4736a-237">daytime</span></span>      | <span data-ttu-id="4736a-238">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-238">outbound</span></span>  | <span data-ttu-id="4736a-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="4736a-239">x 1.50</span></span>  |
| <span data-ttu-id="4736a-240">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-240">Weekday</span></span>    | <span data-ttu-id="4736a-241">večerní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-241">evening rush</span></span> | <span data-ttu-id="4736a-242">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-242">inbound</span></span>   | <span data-ttu-id="4736a-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-243">x 1.00</span></span>  |
| <span data-ttu-id="4736a-244">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-244">Weekday</span></span>    | <span data-ttu-id="4736a-245">večerní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-245">evening rush</span></span> | <span data-ttu-id="4736a-246">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-246">outbound</span></span>  | <span data-ttu-id="4736a-247">x 2,00</span><span class="sxs-lookup"><span data-stu-id="4736a-247">x 2.00</span></span>  |
| <span data-ttu-id="4736a-248">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-248">Weekday</span></span>    | <span data-ttu-id="4736a-249">Přes noc</span><span class="sxs-lookup"><span data-stu-id="4736a-249">overnight</span></span>    | <span data-ttu-id="4736a-250">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-250">inbound</span></span>   | <span data-ttu-id="4736a-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="4736a-251">x 0.75</span></span>  |
| <span data-ttu-id="4736a-252">Weekday</span><span class="sxs-lookup"><span data-stu-id="4736a-252">Weekday</span></span>    | <span data-ttu-id="4736a-253">Přes noc</span><span class="sxs-lookup"><span data-stu-id="4736a-253">overnight</span></span>    | <span data-ttu-id="4736a-254">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-254">outbound</span></span>  | <span data-ttu-id="4736a-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="4736a-255">x 0.75</span></span>  |
| <span data-ttu-id="4736a-256">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-256">Weekend</span></span>    | <span data-ttu-id="4736a-257">ranní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-257">morning rush</span></span> | <span data-ttu-id="4736a-258">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-258">inbound</span></span>   | <span data-ttu-id="4736a-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-259">x 1.00</span></span>  |
| <span data-ttu-id="4736a-260">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-260">Weekend</span></span>    | <span data-ttu-id="4736a-261">ranní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-261">morning rush</span></span> | <span data-ttu-id="4736a-262">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-262">outbound</span></span>  | <span data-ttu-id="4736a-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-263">x 1.00</span></span>  |
| <span data-ttu-id="4736a-264">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-264">Weekend</span></span>    | <span data-ttu-id="4736a-265">Denní</span><span class="sxs-lookup"><span data-stu-id="4736a-265">daytime</span></span>      | <span data-ttu-id="4736a-266">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-266">inbound</span></span>   | <span data-ttu-id="4736a-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-267">x 1.00</span></span>  |
| <span data-ttu-id="4736a-268">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-268">Weekend</span></span>    | <span data-ttu-id="4736a-269">Denní</span><span class="sxs-lookup"><span data-stu-id="4736a-269">daytime</span></span>      | <span data-ttu-id="4736a-270">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-270">outbound</span></span>  | <span data-ttu-id="4736a-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-271">x 1.00</span></span>  |
| <span data-ttu-id="4736a-272">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-272">Weekend</span></span>    | <span data-ttu-id="4736a-273">večerní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-273">evening rush</span></span> | <span data-ttu-id="4736a-274">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-274">inbound</span></span>   | <span data-ttu-id="4736a-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-275">x 1.00</span></span>  |
| <span data-ttu-id="4736a-276">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-276">Weekend</span></span>    | <span data-ttu-id="4736a-277">večerní spěch</span><span class="sxs-lookup"><span data-stu-id="4736a-277">evening rush</span></span> | <span data-ttu-id="4736a-278">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-278">outbound</span></span>  | <span data-ttu-id="4736a-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-279">x 1.00</span></span>  |
| <span data-ttu-id="4736a-280">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-280">Weekend</span></span>    | <span data-ttu-id="4736a-281">Přes noc</span><span class="sxs-lookup"><span data-stu-id="4736a-281">overnight</span></span>    | <span data-ttu-id="4736a-282">inbound</span><span class="sxs-lookup"><span data-stu-id="4736a-282">inbound</span></span>   | <span data-ttu-id="4736a-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-283">x 1.00</span></span>  |
| <span data-ttu-id="4736a-284">Weekend</span><span class="sxs-lookup"><span data-stu-id="4736a-284">Weekend</span></span>    | <span data-ttu-id="4736a-285">Přes noc</span><span class="sxs-lookup"><span data-stu-id="4736a-285">overnight</span></span>    | <span data-ttu-id="4736a-286">Odchozí</span><span class="sxs-lookup"><span data-stu-id="4736a-286">outbound</span></span>  | <span data-ttu-id="4736a-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="4736a-287">x 1.00</span></span>  |

<span data-ttu-id="4736a-288">Existuje 16 různých kombinací tří proměnných.</span><span class="sxs-lookup"><span data-stu-id="4736a-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="4736a-289">Kombinací některých podmínek zjednodušíte konečný výraz přepínače.</span><span class="sxs-lookup"><span data-stu-id="4736a-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="4736a-290">Systém, který vybírá mýtné, <xref:System.DateTime> používá strukturu pro čas, kdy bylo mýtné vybráno.</span><span class="sxs-lookup"><span data-stu-id="4736a-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="4736a-291">Vytvořte členské metody, které vytvářejí proměnné z předchozí tabulky.</span><span class="sxs-lookup"><span data-stu-id="4736a-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="4736a-292">Následující funkce používá vzor odpovídající přepínač výraz <xref:System.DateTime> vyjádřit, zda představuje víkend nebo den v týdnu:</span><span class="sxs-lookup"><span data-stu-id="4736a-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

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

<span data-ttu-id="4736a-293">Tato metoda funguje, ale je to opakující se.</span><span class="sxs-lookup"><span data-stu-id="4736a-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="4736a-294">Můžete jej zjednodušit, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4736a-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="4736a-295">Dále přidejte podobnou funkci kategorizovat čas do bloků:</span><span class="sxs-lookup"><span data-stu-id="4736a-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="4736a-296">Předchozí metoda nepoužívá porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="4736a-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="4736a-297">Je to jasnější pomocí známé `if` kaskády prohlášení.</span><span class="sxs-lookup"><span data-stu-id="4736a-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="4736a-298">Přidáte soukromé `enum` převést každý rozsah času na diskrétní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4736a-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="4736a-299">Po vytvoření těchto metod můžete `switch` použít jiný výraz se **vzorem řazené kolekce členů** k výpočtu cenové prémie.</span><span class="sxs-lookup"><span data-stu-id="4736a-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="4736a-300">Dalo by `switch` se vytvořit výraz se všemi 16 zbraněmi:</span><span class="sxs-lookup"><span data-stu-id="4736a-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="4736a-301">Výše uvedený kód funguje, ale může být zjednodušen.</span><span class="sxs-lookup"><span data-stu-id="4736a-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="4736a-302">Všech osm kombinací na víkend má stejnou daň.</span><span class="sxs-lookup"><span data-stu-id="4736a-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="4736a-303">Všech osm můžete nahradit následujícím řádkem:</span><span class="sxs-lookup"><span data-stu-id="4736a-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="4736a-304">Příchozí i odchozí provoz mají stejný multiplikátor během denních a nočních hodin ve všední den.</span><span class="sxs-lookup"><span data-stu-id="4736a-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="4736a-305">Tato čtyři ramena spínače mohou být nahrazena těmito dvěma řádky:</span><span class="sxs-lookup"><span data-stu-id="4736a-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="4736a-306">Kód by měl vypadat jako následující kód po těchto dvou změnách:</span><span class="sxs-lookup"><span data-stu-id="4736a-306">The code should look like the following code after those two changes:</span></span>

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

<span data-ttu-id="4736a-307">Nakonec můžete odstranit dvě doby dopravní špičky, které platí běžnou cenu.</span><span class="sxs-lookup"><span data-stu-id="4736a-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="4736a-308">Jakmile tato ramena vyjmete, můžete je v posledním rameni spínače nahradit `false` výmětem (`_`).</span><span class="sxs-lookup"><span data-stu-id="4736a-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="4736a-309">Budete mít následující hotovou metodu:</span><span class="sxs-lookup"><span data-stu-id="4736a-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="4736a-310">Tento příklad zvýrazní jednu z výhod porovnávání vzorů: větve vzoru jsou vyhodnoceny v pořadí.</span><span class="sxs-lookup"><span data-stu-id="4736a-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="4736a-311">Pokud je změníte uspořádání tak, aby starší větev zpracovává jeden z vašich pozdějších případů, kompilátor vás upozorní na nedostupný kód.</span><span class="sxs-lookup"><span data-stu-id="4736a-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="4736a-312">Tato jazyková pravidla usnadnila předchozí zjednodušení s jistotou, že se kód nezměnil.</span><span class="sxs-lookup"><span data-stu-id="4736a-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="4736a-313">Porovnávání vzorů umožňuje některé typy kódu čitelnější a nabízí alternativu k objektově orientované techniky, když nelze přidat kód do tříd.</span><span class="sxs-lookup"><span data-stu-id="4736a-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="4736a-314">Cloud způsobuje, že data a funkce žijí odděleně.</span><span class="sxs-lookup"><span data-stu-id="4736a-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="4736a-315">*Tvar* dat a *operace* na něm nejsou nutně popsány společně.</span><span class="sxs-lookup"><span data-stu-id="4736a-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="4736a-316">V tomto kurzu jste spotřebovávají existující data zcela odlišnými způsoby než původní funkce.</span><span class="sxs-lookup"><span data-stu-id="4736a-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="4736a-317">Porovnávání vzorů vám dalo možnost psát funkce, které tyto typy přeruší, i když je nelze rozšířit.</span><span class="sxs-lookup"><span data-stu-id="4736a-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4736a-318">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4736a-318">Next steps</span></span>

<span data-ttu-id="4736a-319">Hotový kód si můžete stáhnout z úložiště [GitHub dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished)</span><span class="sxs-lookup"><span data-stu-id="4736a-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="4736a-320">Prozkoumejte vzory na vlastní pěst a přidejte tuto techniku do svých pravidelných kódovacích aktivit.</span><span class="sxs-lookup"><span data-stu-id="4736a-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="4736a-321">Učení těchto technik vám dává jiný způsob, jak přistupovat k problémům a vytvářet nové funkce.</span><span class="sxs-lookup"><span data-stu-id="4736a-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
