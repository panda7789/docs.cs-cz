---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Použití tříd Enumeration místo typů výčtů
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: f1b88d160d6532c2a768684b55cd236417699322
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194991"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Použití tříd enumeration místo typů výčtů

[Výčty](../../../../docs/csharp/language-reference/keywords/enum.md) (nebo *typy výčtu* zkráceně) jsou dynamického zajišťování jazyk obálku celočíselného typu. Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot. Klasifikace na základě velikostí (malá, střední, velká) je typickým příkladem. Použití výčty pro tok řízení nebo robustnější abstrakce může být [kódu pach](http://deviq.com/code-smells/). Tento typ využití vede k křehké kódu s mnoha příkazech toku řízení kontrolu hodnoty výčtu.

Místo toho můžete vytvořit výčet tříd, které umožňují bohaté funkce objektově orientovaný jazyk.

Ale to není důležité tématu a v mnoha případech se pro jednoduchost, stále můžete pravidelně [typy výčtu](../../../../docs/csharp/language-reference/keywords/enum.md) Pokud tomu dáváte přednost.

## <a name="implementing-an-enumeration-base-class"></a>Implementace základní třídy výčtu

Pořadí mikroslužeb v aplikaci eShopOnContainers poskytuje implementaci základní třídy výčtu ukázka, jak je znázorněno v následujícím příkladu:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }
    
    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | BindingFlags.Static | BindingFlags.DeclaredOnly);

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

Použijte tuto třídu jako typ v libovolném entity nebo hodnotu objektu, jako u následující třídy výčtu CardType:

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    {
    }

    private class AmexCardType : CardType
    {
        public AmexCardType(): base(1, "Amex")
        { }
    }
    
    private class VisaCardType : CardType
    {
        public VisaCardType(): base(2, "Visa")
        { }
    }
    
    private class MasterCardType : CardType
    {
        public MasterCardType(): base(3, "MasterCard")
        { }
    }
}
```

## <a name="additional-resources"></a>Další zdroje

-   **Výčtového jsou evil – aktualizovat**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Daniel Hardman. Jak rozložit výčty stádiu – A jak ho Vytvrdit**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Výčet tříd**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Alternativy výčtu v jazyce C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Základní třída výčtu v aplikaci eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Ukázka třídy výčtu v aplikaci eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Předchozí](implement-value-objects.md)
[další](domain-model-layer-validations.md)
