---
title: Obecné typy (obecné typy) – přehled
description: Naučte se, jak obecné typy fungují jako šablony kódu, které umožňují definovat typově bezpečné datové struktury bez potvrzení skutečného datového typu.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 99e3b589cd67c9d7026966d3d48d0e06a91fcc86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287542"
---
# <a name="generic-types-overview"></a><span data-ttu-id="09bc0-103">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="09bc0-103">Generic types overview</span></span>

<span data-ttu-id="09bc0-104">Vývojáři používají obecné typy v rozhraní .NET, ať už implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="09bc0-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="09bc0-105">Pokud používáte LINQ v .NET, někdy jste si všimli, že pracujete s <xref:System.Collections.Generic.IEnumerable%601> ?</span><span class="sxs-lookup"><span data-stu-id="09bc0-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="09bc0-106">Pokud jste někdy viděli online ukázku obecného úložiště pro komunikaci s databázemi pomocí Entity Framework, vidíte, že se většina metod vrátí `IQueryable<T>` ?</span><span class="sxs-lookup"><span data-stu-id="09bc0-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="09bc0-107">Možná jste přemýšlelii, co je **T** v těchto příkladech, a proč tam tam je.</span><span class="sxs-lookup"><span data-stu-id="09bc0-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="09bc0-108">Jako první představená v .NET Framework 2,0, obecné jsou v podstatě "Šablona kódu", která vývojářům umožňuje definovat [typově bezpečné](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) datové struktury bez potvrzení skutečného datového typu.</span><span class="sxs-lookup"><span data-stu-id="09bc0-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="09bc0-109">Například <xref:System.Collections.Generic.List%601> je [Obecná kolekce](xref:System.Collections.Generic) , kterou lze deklarovat a použít s libovolným typem, například, `List<int>` `List<string>` nebo `List<Person>` .</span><span class="sxs-lookup"><span data-stu-id="09bc0-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="09bc0-110">Aby bylo možné pochopit, proč jsou obecné výrazy užitečné, Podívejme se na konkrétní třídu před a po přidání obecných typů: <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="09bc0-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="09bc0-111">V .NET Framework 1,0 `ArrayList` prvky byly typu <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="09bc0-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="09bc0-112">Libovolný prvek přidaný do kolekce byl tiše převeden na `Object` .</span><span class="sxs-lookup"><span data-stu-id="09bc0-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="09bc0-113">Totéž by se stalo při čtení prvků ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="09bc0-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="09bc0-114">Tento proces se označuje jako [zabalení a rozbalení](../csharp/programming-guide/types/boxing-and-unboxing.md)a má dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="09bc0-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="09bc0-115">Kromě výkonu ale neexistuje žádný způsob, jak určit typ dat v seznamu v době kompilace, který je pro nějaký křehký kód.</span><span class="sxs-lookup"><span data-stu-id="09bc0-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="09bc0-116">Obecné vyřeší tento problém definováním typu dat, který bude obsahovat každá instance seznamu.</span><span class="sxs-lookup"><span data-stu-id="09bc0-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="09bc0-117">Například můžete přidat pouze celá čísla do `List<int>` a pouze přidat osoby `List<Person>` .</span><span class="sxs-lookup"><span data-stu-id="09bc0-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="09bc0-118">Obecné typy jsou také k dispozici v době běhu.</span><span class="sxs-lookup"><span data-stu-id="09bc0-118">Generics are also available at run time.</span></span> <span data-ttu-id="09bc0-119">Modul runtime ví, jaký typ datové struktury používáte, a je možné ho v paměti efektivněji Uložit.</span><span class="sxs-lookup"><span data-stu-id="09bc0-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="09bc0-120">Následující příklad je malý program, který znázorňuje efektivitu znalosti typu struktury dat za běhu:</span><span class="sxs-lookup"><span data-stu-id="09bc0-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

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

<span data-ttu-id="09bc0-121">Tento program vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="09bc0-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="09bc0-122">První věc, kterou si můžete všimnout, je, že řazení obecného seznamu je výrazně rychlejší než řazení neobecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="09bc0-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="09bc0-123">Můžete si také všimnout, že typ pro obecný seznam je odlišný ([System. Int32]), zatímco typ pro neobecný seznam je zobecněný.</span><span class="sxs-lookup"><span data-stu-id="09bc0-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="09bc0-124">Vzhledem k tomu, že modul runtime ví, že `List<int>` je obecný typ <xref:System.Int32> , může uložit prvky seznamu v podkladovém poli typu Integer v paměti, zatímco neobecné `ArrayList` musí přetypování každého prvku seznamu na objekt.</span><span class="sxs-lookup"><span data-stu-id="09bc0-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="09bc0-125">Jak ukazuje tento příklad, nadbytečné přetypování zabírají čas a zpomalují řazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="09bc0-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="09bc0-126">Další výhodou modulu runtime, který se znalostí typu vašeho obecného, je lepší ladění.</span><span class="sxs-lookup"><span data-stu-id="09bc0-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="09bc0-127">Při ladění obecného v jazyce C# víte, jaký typ každého prvku je v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="09bc0-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="09bc0-128">Bez obecných typů byste nemuseli mít žádný nápad, který typ každého elementu byl.</span><span class="sxs-lookup"><span data-stu-id="09bc0-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="09bc0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="09bc0-129">See also</span></span>

- [<span data-ttu-id="09bc0-130">Průvodce programováním v C# – obecné typy</span><span class="sxs-lookup"><span data-stu-id="09bc0-130">C# Programming Guide - Generics</span></span>](../csharp/programming-guide/generics/index.md)
