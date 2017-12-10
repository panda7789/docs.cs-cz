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
# <a name="generic-types-generics-overview"></a>Obecné typy (Obecné) – přehled

Používáme obecné vždy v jazyce C#, ať už implicitně nebo explicitně. Při použití LINQ v jazyku C#, se někdy zjistíte, že pracujete s rozhraní IEnumerable<T>? Nebo pokud jste viděli někdy online ukázka "Obecné úložiště" pro rozhovoru s databází pomocí rozhraní Entity Framework, se zobrazí, většina metody vrací IQueryable<T>? Vám může mít zajímalo co **T** se v těchto příkladech a proč je zde?

Poprvé rozhraní .NET Framework 2.0, obecné typy související se situací změny jazyka C# a Common Language Runtime (CLR). **Obecné typy** jsou v podstatě "kód šablonu", který umožňuje vývojářům definovat [bezpečnost typů](https://msdn.microsoft.com/library/hbzz1a9a.aspx) datové struktury bez potvrzení typ skutečná data. Například `List<T>` je [obecnou kolekci](xref:System.Collections.Generic) , lze deklarovat a použít s žádným typem: `List<int>`, `List<string>`, `List<Person>`atd.

Ano co je bod? Obecné typy jsou užitečné Chcete-li to porozumět, musíme si prohlédněte určité třídy před a po přidání obecné typy. Podívejme se na `ArrayList`. V jazyce C# 1.0 `ArrayList` elementy byly typu `object`. To znamenalo, že byl libovolný element, který byl přidán bezobslužně převeden do `object`; stejné co se stane na čtení elementy ze seznamu (Tento proces se označuje jako [zabalení](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) a rozbalení v uvedeném pořadí). Zabalení a rozbalení mít vliv výkonu. Více než ale není v době kompilace zjistit, co je skutečný typ dat v seznamu. Díky tomu pro některé křehké kód. Obecné typy tento problém vyřešit tím, že poskytuje další informace o typu dat, které bude obsahovat každou instanci seznamu. Jednoduše PUT, lze přidat pouze celých čísel na `List<int>` a přidat pouze osoby, aby `List<Person>`atd.

Obecné typy jsou také k dispozici v době běhu nebo **reified**. To znamená, že modul runtime ví, jaký typ dat struktura používáte a můžete ho uložit v paměti efektivněji.

Tady je malý program, který ukazuje efektivitu znalost data struktury typu za běhu:

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

Tento program vypočítá následující výstup:

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

První věcí, kterou jste si všimli, že je zde řazení seznamu Obecné je mnohem rychlejší než neobecnou seznam. Také můžete si všimnout, že typ pro obecné seznamu je odlišné ([System.Int32]), zatímco typ seznamu neobecnou je zobecněn. Vzhledem k tomu, že modul runtime zná obecná `List<int>` je typu int, může ukládat prvky seznamu v základní pole celé číslo v paměti, zatímco neobecnou `ArrayList` má přetypovat každý element seznamu jako objekt uložen v objektu pole v paměti. Jak je znázorněno prostřednictvím v tomto příkladu, navíc odlitků trvat až čas a zpomalit řazení seznamu.

Užitečné věc o běhu znalost typ vaší obecného je lépe ladění prostředí. Když ladíte obecný v jazyce C#, víte, jaký typ každého elementu je datová struktura. Bez obecné typy byste měli žádné nápad jaký typ každý element.

## <a name="further-reading-and-resources"></a>Další čtení a prostředky

*   [Úvod do obecnými typy C#](https://msdn.microsoft.com/library/ms379564.aspx)
*   [C# Průvodce programováním – obecné typy](../../docs/csharp/programming-guide/generics/index.md)
