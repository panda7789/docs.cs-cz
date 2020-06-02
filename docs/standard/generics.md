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
# <a name="generic-types-overview"></a>Přehled obecných typů

Vývojáři používají obecné typy v rozhraní .NET, ať už implicitně nebo explicitně. Pokud používáte LINQ v .NET, někdy jste si všimli, že pracujete s <xref:System.Collections.Generic.IEnumerable%601> ? Pokud jste někdy viděli online ukázku obecného úložiště pro komunikaci s databázemi pomocí Entity Framework, vidíte, že se většina metod vrátí `IQueryable<T>` ? Možná jste přemýšlelii, co je **T** v těchto příkladech, a proč tam tam je.

Jako první představená v .NET Framework 2,0, obecné jsou v podstatě "Šablona kódu", která vývojářům umožňuje definovat [typově bezpečné](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) datové struktury bez potvrzení skutečného datového typu. Například <xref:System.Collections.Generic.List%601> je [Obecná kolekce](xref:System.Collections.Generic) , kterou lze deklarovat a použít s libovolným typem, například, `List<int>` `List<string>` nebo `List<Person>` .

Aby bylo možné pochopit, proč jsou obecné výrazy užitečné, Podívejme se na konkrétní třídu před a po přidání obecných typů: <xref:System.Collections.ArrayList> . V .NET Framework 1,0 `ArrayList` prvky byly typu <xref:System.Object> . Libovolný prvek přidaný do kolekce byl tiše převeden na `Object` . Totéž by se stalo při čtení prvků ze seznamu. Tento proces se označuje jako [zabalení a rozbalení](../csharp/programming-guide/types/boxing-and-unboxing.md)a má dopad na výkon. Kromě výkonu ale neexistuje žádný způsob, jak určit typ dat v seznamu v době kompilace, který je pro nějaký křehký kód. Obecné vyřeší tento problém definováním typu dat, který bude obsahovat každá instance seznamu. Například můžete přidat pouze celá čísla do `List<int>` a pouze přidat osoby `List<Person>` .

Obecné typy jsou také k dispozici v době běhu. Modul runtime ví, jaký typ datové struktury používáte, a je možné ho v paměti efektivněji Uložit.

Následující příklad je malý program, který znázorňuje efektivitu znalosti typu struktury dat za běhu:

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

První věc, kterou si můžete všimnout, je, že řazení obecného seznamu je výrazně rychlejší než řazení neobecného seznamu. Můžete si také všimnout, že typ pro obecný seznam je odlišný ([System. Int32]), zatímco typ pro neobecný seznam je zobecněný. Vzhledem k tomu, že modul runtime ví, že `List<int>` je obecný typ <xref:System.Int32> , může uložit prvky seznamu v podkladovém poli typu Integer v paměti, zatímco neobecné `ArrayList` musí přetypování každého prvku seznamu na objekt. Jak ukazuje tento příklad, nadbytečné přetypování zabírají čas a zpomalují řazení seznamu.

Další výhodou modulu runtime, který se znalostí typu vašeho obecného, je lepší ladění. Při ladění obecného v jazyce C# víte, jaký typ každého prvku je v datové struktuře. Bez obecných typů byste nemuseli mít žádný nápad, který typ každého elementu byl.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C# – obecné typy](../csharp/programming-guide/generics/index.md)
