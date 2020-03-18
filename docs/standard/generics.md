---
title: Obecný přehled typů (obecných typů)
description: Zjistěte, jak obecné typy fungují jako šablony kódu, které umožňují definovat datové struktury bezpečné pro daný typ bez potvrzení skutečného datového typu.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 3c1181f5be717f328ae906c6009fc8a34b904c89
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61923848"
---
# <a name="generic-types-overview"></a><span data-ttu-id="c631e-103">Obecný přehled typů</span><span class="sxs-lookup"><span data-stu-id="c631e-103">Generic types overview</span></span>

<span data-ttu-id="c631e-104">Vývojáři používají obecné typy po celou dobu v rozhraní .NET, implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="c631e-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="c631e-105">Při použití LINQ v rozhraní .NET jste si všimli, že pracujete s <xref:System.Collections.Generic.IEnumerable%601>?</span><span class="sxs-lookup"><span data-stu-id="c631e-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="c631e-106">Nebo pokud jste někdy viděli online vzorek "obecného úložiště" pro rozhovor s databázemi pomocí entity\<frameworku, viděli jste, že většina metod vrací IQueryable T>?</span><span class="sxs-lookup"><span data-stu-id="c631e-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable\<T>?</span></span> <span data-ttu-id="c631e-107">Možná jste se divili, co **t** je v těchto příkladech a proč je to tam.</span><span class="sxs-lookup"><span data-stu-id="c631e-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="c631e-108">**Nejprve** zavedena v rozhraní .NET Framework 2.0, obecné typy jsou v podstatě "šablona kódu", který umožňuje vývojářům definovat datové struktury [bezpečné pro typ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) bez potvrzení skutečného datového typu.</span><span class="sxs-lookup"><span data-stu-id="c631e-108">First introduced in the .NET Framework 2.0, **generics** are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="c631e-109">Například <xref:System.Collections.Generic.List%601> je [obecná kolekce,](xref:System.Collections.Generic) která může být deklarována a použita s libovolným typem, například `List<int>`, `List<string>`nebo `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="c631e-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="c631e-110">Chcete-li pochopit, proč jsou generika užitečná, podívejme se na <xref:System.Collections.ArrayList>konkrétní třídu před a po přidání generik: .</span><span class="sxs-lookup"><span data-stu-id="c631e-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c631e-111">V rozhraní .NET Framework `ArrayList` 1.0 <xref:System.Object>byly prvky typu .</span><span class="sxs-lookup"><span data-stu-id="c631e-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="c631e-112">To znamenalo, že každý přidaný prvek `Object`byl tiše převeden na .</span><span class="sxs-lookup"><span data-stu-id="c631e-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="c631e-113">Totéž by se stalo při čtení prvků ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="c631e-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="c631e-114">Tento proces se označuje jako [zabalení a rozbalení](../csharp/programming-guide/types/boxing-and-unboxing.md)a má vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="c631e-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="c631e-115">Více než to však neexistuje žádný způsob, jak určit typ dat v seznamu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c631e-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="c631e-116">To je pro některé křehké kód.</span><span class="sxs-lookup"><span data-stu-id="c631e-116">This makes for some fragile code.</span></span> <span data-ttu-id="c631e-117">Obecné typy řeší tento problém definováním typu dat, která budou obsahovat jednotlivé instance seznamu.</span><span class="sxs-lookup"><span data-stu-id="c631e-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="c631e-118">Můžete například přidávat pouze celá čísla `List<int>` a přidávat pouze `List<Person>`osoby do .</span><span class="sxs-lookup"><span data-stu-id="c631e-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="c631e-119">Obecné typy jsou také k dispozici za běhu.</span><span class="sxs-lookup"><span data-stu-id="c631e-119">Generics are also available at runtime.</span></span> <span data-ttu-id="c631e-120">To znamená, že runtime ví, jaký typ datové struktury používáte, a může ji efektivněji ukládat do paměti.</span><span class="sxs-lookup"><span data-stu-id="c631e-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="c631e-121">Následující příklad je malý program, který ilustruje efektivitu znalosti typu datové struktury za běhu:</span><span class="sxs-lookup"><span data-stu-id="c631e-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="c631e-122">Tento program vytváří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="c631e-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="c631e-123">První věc, kterou si můžete všimnout, je, že řazení obecného seznamu je výrazně rychlejší než řazení neobecného seznamu.</span><span class="sxs-lookup"><span data-stu-id="c631e-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="c631e-124">Můžete si také všimnout, že typ pro obecný seznam je odlišný ([System.Int32]), zatímco typ pro neobecný seznam je zobecněn.</span><span class="sxs-lookup"><span data-stu-id="c631e-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="c631e-125">Vzhledem k tomu, `List<int>` že <xref:System.Int32>runtime zná obecný typ , může ukládat prvky seznamu `ArrayList` do základního celočíselného pole v paměti, zatímco neobecný musí přetypovat každý prvek seznamu do objektu.</span><span class="sxs-lookup"><span data-stu-id="c631e-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="c631e-126">Jak ukazuje tento příklad, extra přetypovávání zabírají čas a zpomalují řazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="c631e-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="c631e-127">Další výhodou běhu, který ví typ obecného prostředí, je lepší ladění.</span><span class="sxs-lookup"><span data-stu-id="c631e-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="c631e-128">Při ladění obecné v C#, víte, jaký typ každý prvek je ve vaší datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="c631e-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="c631e-129">Bez obecných typů byste neměli ponětí, jaký typ byl každý prvek.</span><span class="sxs-lookup"><span data-stu-id="c631e-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="c631e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c631e-130">See also</span></span>

- [<span data-ttu-id="c631e-131">Průvodce programováním jazyka C# – obecné typy</span><span class="sxs-lookup"><span data-stu-id="c631e-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
