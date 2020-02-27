---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mazat, jak lze použít třídy výčtu namísto výčtů jako způsob, jak vyřešit některá omezení.
ms.date: 10/08/2018
ms.openlocfilehash: 82bd80d19b3b73eb2f45ede8cc7ad4593c688277
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628459"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="84f52-103">Použijte třídy výčtu místo typů Enum.</span><span class="sxs-lookup"><span data-stu-id="84f52-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="84f52-104">[Výčty](../../../csharp/language-reference/builtin-types/enum.md) (nebo *výčtové typy* pro Short) jsou obálka s dynamickým jazykem kolem integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="84f52-104">[Enumerations](../../../csharp/language-reference/builtin-types/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="84f52-105">Můžete chtít omezit jejich použití na, pokud ukládáte jednu hodnotu z uzavřené sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="84f52-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="84f52-106">Dobrým příkladem je klasifikace založená na velikostech (malá, střední, Velká).</span><span class="sxs-lookup"><span data-stu-id="84f52-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="84f52-107">Používání výčtů pro tok řízení nebo robustnější abstrakce může být [zápach kódu](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="84f52-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="84f52-108">Tento typ použití vede k křehkému kódu s mnoha příkazy toku řízení, které kontrolují hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="84f52-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="84f52-109">Místo toho můžete vytvořit třídy výčtu, které umožňují všechny bohatě orientované funkce pro objektově orientovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="84f52-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="84f52-110">Nejedná se však o důležité téma a v mnoha případech pro jednoduchost můžete i nadále používat běžné [typy výčtu](../../../csharp/language-reference/builtin-types/enum.md) , pokud je to vaše preference.</span><span class="sxs-lookup"><span data-stu-id="84f52-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/builtin-types/enum.md) if that's your preference.</span></span> <span data-ttu-id="84f52-111">Přesto se použití tříd výčtu podrobněji týká konceptů souvisejících s firmou.</span><span class="sxs-lookup"><span data-stu-id="84f52-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="84f52-112">Implementace základní třídy výčtu</span><span class="sxs-lookup"><span data-stu-id="84f52-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="84f52-113">Dořazení mikroslužeb v eShopOnContainers poskytuje ukázkovou implementaci základní třídy výčtu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="84f52-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="84f52-114">Tuto třídu můžete použít jako typ v jakémkoli objektu entity nebo hodnoty, jako u následujících `CardType`: `Enumeration` třídy:</span><span class="sxs-lookup"><span data-stu-id="84f52-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="84f52-115">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="84f52-115">Additional resources</span></span>

- <span data-ttu-id="84f52-116">**Jimmy Bogard. \ třídy výčtu**</span><span class="sxs-lookup"><span data-stu-id="84f52-116">**Jimmy Bogard. Enumeration classes** \</span></span>
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="84f52-117">**Steve Smith. Alternativy výčtu v C#**  </span><span class="sxs-lookup"><span data-stu-id="84f52-117">**Steve Smith. Enum Alternatives in C#** </span></span>\
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="84f52-118">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="84f52-118">**Enumeration.cs.**</span></span> <span data-ttu-id="84f52-119">Základní třída výčtu v eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="84f52-119">Base Enumeration class in eShopOnContainers </span></span>\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="84f52-120">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="84f52-120">**CardType.cs**.</span></span> <span data-ttu-id="84f52-121">Ukázková třída výčtu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="84f52-121">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- <span data-ttu-id="84f52-122">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="84f52-122">**SmartEnum**.</span></span> <span data-ttu-id="84f52-123">Ardalis – třídy, které vám pomůžou vydávat silné typy inteligentnějších výčtů v .NET.</span><span class="sxs-lookup"><span data-stu-id="84f52-123">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="84f52-124">[Předchozí](implement-value-objects.md)
>[Další](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="84f52-124">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
