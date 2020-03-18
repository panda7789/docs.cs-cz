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
# <a name="generic-types-overview"></a>Obecný přehled typů

Vývojáři používají obecné typy po celou dobu v rozhraní .NET, implicitně nebo explicitně. Při použití LINQ v rozhraní .NET jste si všimli, že pracujete s <xref:System.Collections.Generic.IEnumerable%601>? Nebo pokud jste někdy viděli online vzorek "obecného úložiště" pro rozhovor s databázemi pomocí entity\<frameworku, viděli jste, že většina metod vrací IQueryable T>? Možná jste se divili, co **t** je v těchto příkladech a proč je to tam.

**Nejprve** zavedena v rozhraní .NET Framework 2.0, obecné typy jsou v podstatě "šablona kódu", který umožňuje vývojářům definovat datové struktury [bezpečné pro typ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) bez potvrzení skutečného datového typu. Například <xref:System.Collections.Generic.List%601> je [obecná kolekce,](xref:System.Collections.Generic) která může být deklarována a použita s libovolným typem, například `List<int>`, `List<string>`nebo `List<Person>`.

Chcete-li pochopit, proč jsou generika užitečná, podívejme se na <xref:System.Collections.ArrayList>konkrétní třídu před a po přidání generik: . V rozhraní .NET Framework `ArrayList` 1.0 <xref:System.Object>byly prvky typu . To znamenalo, že každý přidaný prvek `Object`byl tiše převeden na . Totéž by se stalo při čtení prvků ze seznamu. Tento proces se označuje jako [zabalení a rozbalení](../csharp/programming-guide/types/boxing-and-unboxing.md)a má vliv na výkon. Více než to však neexistuje žádný způsob, jak určit typ dat v seznamu v době kompilace. To je pro některé křehké kód. Obecné typy řeší tento problém definováním typu dat, která budou obsahovat jednotlivé instance seznamu. Můžete například přidávat pouze celá čísla `List<int>` a přidávat pouze `List<Person>`osoby do .

Obecné typy jsou také k dispozici za běhu. To znamená, že runtime ví, jaký typ datové struktury používáte, a může ji efektivněji ukládat do paměti.

Následující příklad je malý program, který ilustruje efektivitu znalosti typu datové struktury za běhu:

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

Tento program vytváří výstup podobný následujícímu:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

První věc, kterou si můžete všimnout, je, že řazení obecného seznamu je výrazně rychlejší než řazení neobecného seznamu. Můžete si také všimnout, že typ pro obecný seznam je odlišný ([System.Int32]), zatímco typ pro neobecný seznam je zobecněn. Vzhledem k tomu, `List<int>` že <xref:System.Int32>runtime zná obecný typ , může ukládat prvky seznamu `ArrayList` do základního celočíselného pole v paměti, zatímco neobecný musí přetypovat každý prvek seznamu do objektu. Jak ukazuje tento příklad, extra přetypovávání zabírají čas a zpomalují řazení seznamu.

Další výhodou běhu, který ví typ obecného prostředí, je lepší ladění. Při ladění obecné v C#, víte, jaký typ každý prvek je ve vaší datové struktuře. Bez obecných typů byste neměli ponětí, jaký typ byl každý prvek.

## <a name="see-also"></a>Viz také

- [Průvodce programováním jazyka C# – obecné typy](../../docs/csharp/programming-guide/generics/index.md)
