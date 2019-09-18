---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mazat, jak lze použít třídy výčtu namísto výčtů jako způsob, jak vyřešit některá omezení.
ms.date: 10/08/2018
ms.openlocfilehash: 575757b6022a9e7468c0ffc5d576dd16de3018f5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039933"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Použijte třídy výčtu místo typů Enum.

[Výčty](../../../csharp/language-reference/keywords/enum.md) (nebo *výčtové typy* pro Short) jsou obálka s dynamickým jazykem kolem integrálního typu. Můžete chtít omezit jejich použití na, pokud ukládáte jednu hodnotu z uzavřené sady hodnot. Dobrým příkladem je klasifikace založená na velikostech (malá, střední, Velká). Používání výčtů pro tok řízení nebo robustnější abstrakce může být [zápach kódu](https://deviq.com/code-smells/). Tento typ použití vede k křehkému kódu s mnoha příkazy toku řízení, které kontrolují hodnoty výčtu.

Místo toho můžete vytvořit třídy výčtu, které umožňují všechny bohatě orientované funkce pro objektově orientovaný jazyk.

Nejedná se však o důležité téma a v mnoha případech pro jednoduchost můžete i nadále používat běžné [typy výčtu](../../../csharp/language-reference/keywords/enum.md) , pokud je to vaše preference. Přesto se použití tříd výčtu podrobněji týká konceptů souvisejících s firmou.

## <a name="implement-an-enumeration-base-class"></a>Implementace základní třídy výčtu

Dořazení mikroslužeb v eShopOnContainers poskytuje ukázkovou implementaci základní třídy výčtu, jak je znázorněno v následujícím příkladu:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) 
    {
        Id = id; 
        Name = name; 
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | 
                                         BindingFlags.Static | 
                                         BindingFlags.DeclaredOnly); 

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj) 
    {
        var otherValue = obj as Enumeration; 

        if (otherValue == null) 
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id); 

    // Other utility methods ... 
}
```

Tuto třídu můžete použít jako typ v jakémkoli objektu entity nebo hodnoty, jako u následující `CardType` třídy: `Enumeration`

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Další zdroje

- **Výčet je Evil – Update** \
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- **Daniel Jak výčty rozšíří chorobu – a jak ji vyřídit** \
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- **Jimmy Bogard. Třídy výčtu** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. Alternativy výčtu vC#**  \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Základní třída výčtu v eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Ukázková třída výčtu v eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis – třídy, které vám pomůžou vydávat silné typy inteligentnějších výčtů v .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Předchozí](implement-value-objects.md)Další
>[](domain-model-layer-validations.md)
