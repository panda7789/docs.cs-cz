---
title: "Obecné typy (Obecné) – přehled"
description: "Zjistěte, jak obecné fungovat jako kód šablony, které umožňují definovat bezpečnost typů datové struktury bez potvrzení typ skutečná data."
keywords: "Rozhraní .NET, .NET core"
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: acd6f1cc3a6200140f25fc31e4f6fb0f8da5a6e3
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="generic-types-generics-overview"></a><span data-ttu-id="7ac53-104">Obecné typy (Obecné) – přehled</span><span class="sxs-lookup"><span data-stu-id="7ac53-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="7ac53-105">Používáme obecné vždy v jazyce C#, ať už implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="7ac53-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="7ac53-106">Při použití LINQ v jazyku C#, se někdy zjistíte, že pracujete s rozhraní IEnumerable<T>?</span><span class="sxs-lookup"><span data-stu-id="7ac53-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="7ac53-107">Nebo pokud jste viděli někdy online ukázka "Obecné úložiště" pro rozhovoru s databází pomocí rozhraní Entity Framework, se zobrazí, většina metody vrací IQueryable<T>?</span><span class="sxs-lookup"><span data-stu-id="7ac53-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="7ac53-108">Vám může mít zajímalo co **T** se v těchto příkladech a proč je zde?</span><span class="sxs-lookup"><span data-stu-id="7ac53-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="7ac53-109">Poprvé rozhraní .NET Framework 2.0, obecné typy související se situací změny jazyka C# a Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7ac53-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="7ac53-110">**Obecné typy** jsou v podstatě "kód šablonu", který umožňuje vývojářům definovat [bezpečnost typů](https://msdn.microsoft.com/library/hbzz1a9a.aspx) datové struktury bez potvrzení typ skutečná data.</span><span class="sxs-lookup"><span data-stu-id="7ac53-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="7ac53-111">Například `List<T>` je [obecnou kolekci](xref:System.Collections.Generic) , lze deklarovat a použít s žádným typem: `List<int>`, `List<string>`, `List<Person>`atd.</span><span class="sxs-lookup"><span data-stu-id="7ac53-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="7ac53-112">Ano co je bod?</span><span class="sxs-lookup"><span data-stu-id="7ac53-112">So, what’s the point?</span></span> <span data-ttu-id="7ac53-113">Obecné typy jsou užitečné</span><span class="sxs-lookup"><span data-stu-id="7ac53-113">Why are generics useful?</span></span> <span data-ttu-id="7ac53-114">Chcete-li to porozumět, musíme si prohlédněte určité třídy před a po přidání obecné typy.</span><span class="sxs-lookup"><span data-stu-id="7ac53-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="7ac53-115">Podívejme se na `ArrayList`.</span><span class="sxs-lookup"><span data-stu-id="7ac53-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="7ac53-116">V jazyce C# 1.0 `ArrayList` elementy byly typu `object`.</span><span class="sxs-lookup"><span data-stu-id="7ac53-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="7ac53-117">To znamenalo, že byl libovolný element, který byl přidán bezobslužně převeden do `object`; stejné co se stane na čtení elementy ze seznamu (Tento proces se označuje jako [zabalení](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) a rozbalení v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="7ac53-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) and unboxing respectively).</span></span> <span data-ttu-id="7ac53-118">Zabalení a rozbalení mít vliv výkonu.</span><span class="sxs-lookup"><span data-stu-id="7ac53-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="7ac53-119">Více než ale není v době kompilace zjistit, co je skutečný typ dat v seznamu.</span><span class="sxs-lookup"><span data-stu-id="7ac53-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="7ac53-120">Díky tomu pro některé křehké kód.</span><span class="sxs-lookup"><span data-stu-id="7ac53-120">This makes for some fragile code.</span></span> <span data-ttu-id="7ac53-121">Obecné typy tento problém vyřešit tím, že poskytuje další informace o typu dat, které bude obsahovat každou instanci seznamu.</span><span class="sxs-lookup"><span data-stu-id="7ac53-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="7ac53-122">Jednoduše PUT, lze přidat pouze celých čísel na `List<int>` a přidat pouze osoby, aby `List<Person>`atd.</span><span class="sxs-lookup"><span data-stu-id="7ac53-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="7ac53-123">Obecné typy jsou také k dispozici v době běhu nebo **reified**.</span><span class="sxs-lookup"><span data-stu-id="7ac53-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="7ac53-124">To znamená, že modul runtime ví, jaký typ dat struktura používáte a můžete ho uložit v paměti efektivněji.</span><span class="sxs-lookup"><span data-stu-id="7ac53-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="7ac53-125">Tady je malý program, který ukazuje efektivitu znalost data struktury typu za běhu:</span><span class="sxs-lookup"><span data-stu-id="7ac53-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="7ac53-126">Tento program vypočítá následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7ac53-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="7ac53-127">První věcí, kterou jste si všimli, že je zde řazení seznamu Obecné je mnohem rychlejší než neobecnou seznam.</span><span class="sxs-lookup"><span data-stu-id="7ac53-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="7ac53-128">Také můžete si všimnout, že typ pro obecné seznamu je odlišné ([System.Int32]), zatímco typ seznamu neobecnou je zobecněn.</span><span class="sxs-lookup"><span data-stu-id="7ac53-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="7ac53-129">Vzhledem k tomu, že modul runtime zná obecná `List<int>` je typu int, může ukládat prvky seznamu v základní pole celé číslo v paměti, zatímco neobecnou `ArrayList` má přetypovat každý element seznamu jako objekt uložen v objektu pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="7ac53-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="7ac53-130">Jak je znázorněno prostřednictvím v tomto příkladu, navíc odlitků trvat až čas a zpomalit řazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="7ac53-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="7ac53-131">Užitečné věc o běhu znalost typ vaší obecného je lépe ladění prostředí.</span><span class="sxs-lookup"><span data-stu-id="7ac53-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="7ac53-132">Když ladíte obecný v jazyce C#, víte, jaký typ každého elementu je datová struktura.</span><span class="sxs-lookup"><span data-stu-id="7ac53-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="7ac53-133">Bez obecné typy byste měli žádné nápad jaký typ každý element.</span><span class="sxs-lookup"><span data-stu-id="7ac53-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="7ac53-134">Další čtení a prostředky</span><span class="sxs-lookup"><span data-stu-id="7ac53-134">Further reading and resources</span></span>

*   [<span data-ttu-id="7ac53-135">Úvod do obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="7ac53-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="7ac53-136">C# Průvodce programováním – obecné typy</span><span class="sxs-lookup"><span data-stu-id="7ac53-136">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
