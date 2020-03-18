---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Lear, jak můžete použít výčtu třídy, namísto výčtů, jako způsob, jak vyřešit některá omezení druhé.
ms.date: 10/08/2018
ms.openlocfilehash: fb2cbcd744f29c70a86e6f3300721934192eb752
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847177"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>Místo typů výčtu použijte třídy výčtu.

[Výčty](../../../csharp/language-reference/builtin-types/enum.md) (nebo *výčtu typy* pro krátké) jsou tenké jazyk obálky kolem integrální typ. Jejich použití můžete omezit při ukládání jedné hodnoty z uzavřené sady hodnot. Klasifikace založená na velikostech (malé, střední, velké) je dobrým příkladem. Použití výčty pro řízení toku nebo robustnější abstrakce může být [zápach kódu](https://deviq.com/code-smells/). Tento typ použití vede k křehké kód s mnoha příkazy toku řízení kontrolu hodnot výčtu.

Místo toho můžete vytvořit třídy výčtu, které umožňují všechny bohaté funkce objektově orientovaného jazyka.

To však není kritické téma a v mnoha případech pro jednoduchost můžete stále používat běžné [typy výčtu,](../../../csharp/language-reference/builtin-types/enum.md) pokud je to vaše preference. Každopádně použití výčtu tříd je více souvisí s obchodní koncepty.

## <a name="implement-an-enumeration-base-class"></a>Implementace základní třídy výčtu

Řazení mikroslužby v eShopOnContainers poskytuje ukázkovou implementaci základní třídy výčtu, jak je znázorněno v následujícím příkladu:

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

Tuto třídu můžete použít jako typ v libovolné entitě `Enumeration` nebo objektu hodnoty, jako pro následující: `CardType` třída:

```csharp
public class CardType : Enumeration
{
    public static readonly CardType Amex = new CardType(1, "Amex");
    public static readonly CardType Visa = new CardType(2, "Visa");
    public static readonly CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>Další zdroje

- **Jimmyho Bogarda. Třídy výčtu** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steva Smithe. Enum Alternativy v C #** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** Základní třída výčtu v eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. Ukázková třída výčtu v eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis - Třídy, které pomáhají vyrábět silně typizované chytřejší výčty v rozhraní .NET. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[Předchozí](implement-value-objects.md)
>[další](domain-model-layer-validations.md)
