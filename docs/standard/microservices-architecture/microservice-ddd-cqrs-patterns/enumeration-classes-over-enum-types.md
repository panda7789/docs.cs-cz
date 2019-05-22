---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vymazat použití tříd enumeration místo výčty, jako způsob, jak vyřešit některá omezení.
ms.date: 10/08/2018
ms.openlocfilehash: 10b4c2f7b9f079ed535111e65b8154791f6575cd
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003827"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Použití tříd enumeration místo typů výčtů

[Výčty](../../../../docs/csharp/language-reference/keywords/enum.md) (nebo *typy výčtu* zkráceně) jsou dynamického zajišťování jazyk obálku celočíselného typu. Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot. Klasifikace na základě velikostí (malá, střední, velká) je typickým příkladem. Použití výčty pro tok řízení nebo robustnější abstrakce může být [kódu pach](https://deviq.com/code-smells/). Tento typ využití vede k křehké kódu s mnoha příkazech toku řízení kontrolu hodnoty výčtu.

Místo toho můžete vytvořit výčet tříd, které umožňují bohaté funkce objektově orientovaný jazyk.

Ale to není důležité tématu a v mnoha případech se pro jednoduchost, stále můžete pravidelně [typy výčtu](../../../csharp/language-reference/keywords/enum.md) Pokud tomu dáváte přednost. Použití tříd enumeration je i přesto, více souvisí se obchodních konceptů.

## <a name="implement-an-enumeration-base-class"></a>Implementace základní třídy výčtu

Pořadí mikroslužeb v aplikaci eShopOnContainers poskytuje implementaci základní třídy výčtu ukázka, jak je znázorněno v následujícím příkladu:

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

Tuto třídu můžete použít jako typ v libovolném entity nebo hodnota objektu, jako u následujících `CardType` : `Enumeration` třídy:

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

- **Výčtového jsou evil – aktualizovat** \
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- **Daniel Hardman. Jak rozložit výčty stádiu – A jak ho Vytvrdit** \
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- **Jimmy Bogard. Výčet tříd** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. Alternativy výčtu v jazyce C#** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Základní třída výčtu v aplikaci eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Ukázka třídy výčtu v aplikaci eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- **SmartEnum**. Ardalis – třídy, které pomáhají vytvářet chytřejší výčty se silnými typy v rozhraní .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Předchozí](implement-value-objects.md)
>[další](domain-model-layer-validations.md)
