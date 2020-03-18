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
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="fba26-103">Místo typů výčtu použijte třídy výčtu.</span><span class="sxs-lookup"><span data-stu-id="fba26-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="fba26-104">[Výčty](../../../csharp/language-reference/builtin-types/enum.md) (nebo *výčtu typy* pro krátké) jsou tenké jazyk obálky kolem integrální typ.</span><span class="sxs-lookup"><span data-stu-id="fba26-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="fba26-105">Jejich použití můžete omezit při ukládání jedné hodnoty z uzavřené sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="fba26-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="fba26-106">Klasifikace založená na velikostech (malé, střední, velké) je dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="fba26-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="fba26-107">Použití výčty pro řízení toku nebo robustnější abstrakce může být [zápach kódu](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="fba26-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="fba26-108">Tento typ použití vede k křehké kód s mnoha příkazy toku řízení kontrolu hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="fba26-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="fba26-109">Místo toho můžete vytvořit třídy výčtu, které umožňují všechny bohaté funkce objektově orientovaného jazyka.</span><span class="sxs-lookup"><span data-stu-id="fba26-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="fba26-110">To však není kritické téma a v mnoha případech pro jednoduchost můžete stále používat běžné [typy výčtu,](../../../csharp/language-reference/builtin-types/enum.md) pokud je to vaše preference.</span><span class="sxs-lookup"><span data-stu-id="fba26-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="fba26-111">Každopádně použití výčtu tříd je více souvisí s obchodní koncepty.</span><span class="sxs-lookup"><span data-stu-id="fba26-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="fba26-112">Implementace základní třídy výčtu</span><span class="sxs-lookup"><span data-stu-id="fba26-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="fba26-113">Řazení mikroslužby v eShopOnContainers poskytuje ukázkovou implementaci základní třídy výčtu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fba26-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="fba26-114">Tuto třídu můžete použít jako typ v libovolné entitě `Enumeration` nebo objektu hodnoty, jako pro následující: `CardType` třída:</span><span class="sxs-lookup"><span data-stu-id="fba26-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="fba26-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="fba26-115">Additional resources</span></span>

- <span data-ttu-id="fba26-116">**Jimmyho Bogarda. Třídy výčtu** </span><span class="sxs-lookup"><span data-stu-id="fba26-116">**Jimmy Bogard. Enumeration classes** </span></span>\
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="fba26-117">**Steva Smithe. Enum Alternativy v C #** </span><span class="sxs-lookup"><span data-stu-id="fba26-117">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="fba26-118">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="fba26-118">**Enumeration.cs.**</span></span> <span data-ttu-id="fba26-119">Základní třída výčtu v eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="fba26-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="fba26-120">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="fba26-120">**CardType.cs**.</span></span> <span data-ttu-id="fba26-121">Ukázková třída výčtu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="fba26-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="fba26-122">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="fba26-122">**SmartEnum**.</span></span> <span data-ttu-id="fba26-123">Ardalis - Třídy, které pomáhají vyrábět silně typizované chytřejší výčty v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="fba26-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="fba26-124">[Předchozí](implement-value-objects.md)
>[další](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="fba26-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
