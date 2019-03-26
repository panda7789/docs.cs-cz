---
title: Obecné typy (Obecné) – přehled
description: Zjistěte, jak kód šablony, které umožňují definovat typ vláknově bezpečných datových struktur bez potvrzení do skutečný datový typ plnit obecných typů.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 3c1181f5be717f328ae906c6009fc8a34b904c89
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465422"
---
# <a name="generic-types-overview"></a><span data-ttu-id="12f7a-103">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="12f7a-103">Generic types overview</span></span>

<span data-ttu-id="12f7a-104">Vývojáři pomocí obecných typů neustále v .NET, zda implicitně nebo explicitně.</span><span class="sxs-lookup"><span data-stu-id="12f7a-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="12f7a-105">Při použití LINQ v .NET, Všimli jste si někdy, že pracujete s <xref:System.Collections.Generic.IEnumerable%601>?</span><span class="sxs-lookup"><span data-stu-id="12f7a-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="12f7a-106">Nebo pokud jste někdy viděli online ukázky "obecného úložiště" pro komunikaci se databází pomocí Entity Frameworku, nebyla uvidíte, že většina metod vrátí IQueryable\<T >?</span><span class="sxs-lookup"><span data-stu-id="12f7a-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable\<T>?</span></span> <span data-ttu-id="12f7a-107">Vám může mít přemýšleli, co **T** je v těchto příkladech a proč je tady.</span><span class="sxs-lookup"><span data-stu-id="12f7a-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="12f7a-108">Poprvé byla představena v rozhraní .NET Framework 2.0, **obecných typů** jsou v podstatě "kód šablony", který umožňuje vývojářům definovat [zajišťující bezpečnost typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) datové struktury bez potvrzení do skutečný datový typ.</span><span class="sxs-lookup"><span data-stu-id="12f7a-108">First introduced in the .NET Framework 2.0, **generics** are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="12f7a-109">Například <xref:System.Collections.Generic.List%601> je [obecné kolekce](xref:System.Collections.Generic) , který můžete deklarovat a používat s libovolného typu, jako například `List<int>`, `List<string>`, nebo `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="12f7a-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="12f7a-110">Abyste pochopili, proč jsou užitečné obecných typů, Pojďme se podívat na konkrétní třídu před a po přidání obecných typů: <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="12f7a-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="12f7a-111">V rozhraní .NET Framework 1.0 `ArrayList` elementy byly typu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="12f7a-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="12f7a-112">To znamená, že byl tiše převod libovolný prvek přidán `Object`.</span><span class="sxs-lookup"><span data-stu-id="12f7a-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="12f7a-113">Stejné by mohlo dojít při čtení prvky ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="12f7a-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="12f7a-114">Tento proces se označuje jako [zabalení a rozbalení](../csharp/programming-guide/types/boxing-and-unboxing.md), a to má vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="12f7a-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="12f7a-115">A víc než ale neexistuje žádný způsob, jak určit typ dat v seznamu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="12f7a-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="12f7a-116">Díky tomu pro některé křehké kód.</span><span class="sxs-lookup"><span data-stu-id="12f7a-116">This makes for some fragile code.</span></span> <span data-ttu-id="12f7a-117">Obecné typy tento problém vyřešit tak, že definujete typ dat, který bude obsahovat každou instanci seznamu.</span><span class="sxs-lookup"><span data-stu-id="12f7a-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="12f7a-118">Například můžete přidat pouze celých čísel na `List<int>` a přidávat jenom osoby `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="12f7a-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="12f7a-119">Obecné typy jsou také k dispozici za běhu.</span><span class="sxs-lookup"><span data-stu-id="12f7a-119">Generics are also available at runtime.</span></span> <span data-ttu-id="12f7a-120">To znamená, že modul runtime ví, jaký typ struktury dat používáte a můžete ho uložit do paměti efektivněji.</span><span class="sxs-lookup"><span data-stu-id="12f7a-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="12f7a-121">V následujícím příkladu je malý program, který ukazuje efektivitu znalost data strukturovat typu za běhu:</span><span class="sxs-lookup"><span data-stu-id="12f7a-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="12f7a-122">Tento program vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="12f7a-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="12f7a-123">První věc, kterou si všimnete, že je zde řazení obecného seznamu je výrazně rychlejší než řazení seznamu Obecné.</span><span class="sxs-lookup"><span data-stu-id="12f7a-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="12f7a-124">Můžete také všimnout, jestli je typ obecný seznam jedinečných ([System.Int32]), že typ seznamu neobecnou je zobecněný.</span><span class="sxs-lookup"><span data-stu-id="12f7a-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="12f7a-125">Vzhledem k tomu, že modul runtime ví Obecné `List<int>` je typu <xref:System.Int32>, může ukládat prvky seznamu v podkladové pole celé číslo v paměti, zatímco neobecné `ArrayList` má převést každý prvek seznamu na objekt.</span><span class="sxs-lookup"><span data-stu-id="12f7a-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="12f7a-126">Jak ukazuje tento příklad, navíc přetypování trvat až čas a zpomalit řazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="12f7a-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="12f7a-127">Další výhodou znalost typu vaše obecný modul runtime je lepší možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="12f7a-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="12f7a-128">Při ladění obecný v jazyce C#, víte, jaký typ je každý prvek datové struktury.</span><span class="sxs-lookup"><span data-stu-id="12f7a-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="12f7a-129">Bez obecných typů by nemáte představu, jaký typ byl každý prvek.</span><span class="sxs-lookup"><span data-stu-id="12f7a-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="12f7a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12f7a-130">See also</span></span>

- [<span data-ttu-id="12f7a-131">Programování průvodce v C# – obecné typy</span><span class="sxs-lookup"><span data-stu-id="12f7a-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
