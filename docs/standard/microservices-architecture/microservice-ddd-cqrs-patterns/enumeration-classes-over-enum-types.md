---
title: Pomocí třídy výčtu místo typy výčtu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí třídy výčtu místo typy výčtu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: eff87dbfad84ba5521f029064115a5fc54ee574b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106107"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="75f35-103">Pomocí třídy výčtu místo typy výčtu</span><span class="sxs-lookup"><span data-stu-id="75f35-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="75f35-104">[Výčty](../../../../docs/csharp/language-reference/keywords/enum.md) (nebo *typy výčtu* pro zkrácení) jsou dynamické jazyk obálku kolem integrální typu.</span><span class="sxs-lookup"><span data-stu-id="75f35-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="75f35-105">Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="75f35-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="75f35-106">Klasifikace podle velikosti (malé, střední, velký) je dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="75f35-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="75f35-107">Pomocí výčty pro tok řízení nebo robustnější abstrakce může být [code pach](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="75f35-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="75f35-108">Tento typ využití vede k křehké kód s mnoha příkazy toku řízení kontrola hodnoty výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="75f35-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="75f35-109">Místo toho můžete vytvořit výčet tříd, které povolit všechny bohaté funkce jazyka objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="75f35-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="75f35-110">Ale to není důležité téma a v mnoha případech pro jednoduchost, můžete pořád použít regular [typy výčtu](../../../../docs/csharp/language-reference/keywords/enum.md) , pokud vaši volbu.</span><span class="sxs-lookup"><span data-stu-id="75f35-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="75f35-111">Implementace základní třídu – výčet</span><span class="sxs-lookup"><span data-stu-id="75f35-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="75f35-112">Řazení mikroslužbu v eShopOnContainers poskytuje implementaci základní třída výčtu ukázka, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="75f35-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="75f35-113">Tuto třídu můžete použít jako typ v žádné entity nebo hodnota objektu jako následující CardType výčet tříd:</span><span class="sxs-lookup"><span data-stu-id="75f35-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="75f35-114">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="75f35-114">Additional resources</span></span>

-   <span data-ttu-id="75f35-115">**Na výčtu jsou evil – aktualizace**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="75f35-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="75f35-116">**ADAM Hardman. Jak výčty šíří nákazy – A jak ho Vytvrdit**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="75f35-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="75f35-117">**Jimmy Bogard. Třídy – výčet**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="75f35-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="75f35-118">**Steve Smith. Výčet alternativy v jazyce C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="75f35-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="75f35-119">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="75f35-119">**Enumeration.cs.**</span></span> <span data-ttu-id="75f35-120">Základní třída výčet v eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="75f35-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="75f35-121">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="75f35-121">**CardType.cs**.</span></span> <span data-ttu-id="75f35-122">Ukázka třídy výčet v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="75f35-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="75f35-123">[Předchozí](implement-value-objects.md)
[další](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="75f35-123">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>
