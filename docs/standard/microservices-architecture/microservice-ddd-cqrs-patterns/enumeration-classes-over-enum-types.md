---
title: "Pomocí třídy výčtu místo typy výčtu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí třídy výčtu místo typy výčtu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1745198720fd12a9d26aab2d2afb2c5dd6b6b49d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>Pomocí třídy výčtu místo typy výčtu

[Výčty](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*výčty* pro zkrácení) jsou dynamické jazyk obálku kolem integrální typu. Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot. Klasifikace podle pohlaví (například mužského, samičího neznámé), nebo velikosti (S, M, L, XL) jsou dobrými příklady. Pomocí výčty pro tok řízení nebo robustnější abstrakce může být [code pach](http://deviq.com/code-smells/). Tento typ využití povede k křehké kód s mnoha příkazy toku řízení kontrola hodnoty výčtového typu.

Místo toho můžete vytvořit výčet tříd, které povolit všechny bohaté funkce jazyka objektově orientovaný. Ale nejedná se o kritický problém a v mnoha případech pro jednoduchost, stále můžete regulární výčty, pokud vaši volbu.

## <a name="implementing-enumeration-classes"></a>Implementace tříd – výčet

Řazení mikroslužbu v eShopOnContainers poskytuje implementaci základní třída výčtu ukázka, jak je znázorněno v následujícím příkladu:

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

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

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
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

Tuto třídu můžete použít jako typ v žádné entity nebo hodnota objektu jako následující třídy CardType výčtu.

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }


    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a>Další zdroje

-   **Na výčtu jsou evil – aktualizovat**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **ADAM Hardman. Jak výčty šíří nákazy – A jak ho Vytvrdit**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Výčet tříd**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Výčet alternativy v jazyce C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Základní třída výčet v eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Ukázka třídy výčet v eShopOnContainers.
    [*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Předchozí] (implementace – hodnota objects.md) [Další] (domain modelu layer-validations.md)
