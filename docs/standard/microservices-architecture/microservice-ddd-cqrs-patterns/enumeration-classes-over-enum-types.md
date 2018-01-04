---
title: "Pomocí třídy výčtu místo typy výčtu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí třídy výčtu místo typy výčtu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4b190ee9dde5628bf16fe9c483d3636539c29361
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="fdc59-104">Pomocí třídy výčtu místo typy výčtu</span><span class="sxs-lookup"><span data-stu-id="fdc59-104">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="fdc59-105">[Výčty](../../../../docs/csharp/language-reference/keywords/enum.md) (nebo *typy výčtu* pro zkrácení) jsou dynamické jazyk obálku kolem integrální typu.</span><span class="sxs-lookup"><span data-stu-id="fdc59-105">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="fdc59-106">Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="fdc59-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="fdc59-107">Klasifikace podle pohlaví (například mužského, samičího neznámý) nebo velikosti (malé, střední, velký) jsou dobrými příklady.</span><span class="sxs-lookup"><span data-stu-id="fdc59-107">Classification based on gender (for example, male, female, unknown) or sizes (small, medium, large) are good examples.</span></span> <span data-ttu-id="fdc59-108">Pomocí výčty pro tok řízení nebo robustnější abstrakce může být [code pach](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="fdc59-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="fdc59-109">Tento typ využití vede k křehké kód s mnoha příkazy toku řízení kontrola hodnoty výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="fdc59-109">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="fdc59-110">Místo toho můžete vytvořit výčet tříd, které povolit všechny bohaté funkce jazyka objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="fdc59-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="fdc59-111">Ale to není důležité téma a v mnoha případech pro jednoduchost, můžete pořád použít regular [typy výčtu](../../../../docs/csharp/language-reference/keywords/enum.md) , pokud vaši volbu.</span><span class="sxs-lookup"><span data-stu-id="fdc59-111">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="fdc59-112">Implementace základní třídu – výčet</span><span class="sxs-lookup"><span data-stu-id="fdc59-112">Implementing an Enumeration base class</span></span>

<span data-ttu-id="fdc59-113">Řazení mikroslužbu v eShopOnContainers poskytuje implementaci základní třída výčtu ukázka, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fdc59-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="fdc59-114">Tuto třídu můžete použít jako typ v žádné entity nebo hodnota objektu jako následující CardType výčet tříd:</span><span class="sxs-lookup"><span data-stu-id="fdc59-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="fdc59-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="fdc59-115">Additional resources</span></span>

-   <span data-ttu-id="fdc59-116">**Na výčtu jsou evil – aktualizovat**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="fdc59-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="fdc59-117">**ADAM Hardman. Jak výčty šíří nákazy – A jak ho Vytvrdit**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="fdc59-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="fdc59-118">**Jimmy Bogard. Výčet tříd**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="fdc59-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="fdc59-119">**Steve Smith. Výčet alternativy v jazyce C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="fdc59-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="fdc59-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="fdc59-120">**Enumeration.cs.**</span></span> <span data-ttu-id="fdc59-121">Základní třída výčet v eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="fdc59-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="fdc59-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="fdc59-122">**CardType.cs**.</span></span> <span data-ttu-id="fdc59-123">Ukázka třídy výčet v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="fdc59-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="fdc59-124">*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span><span class="sxs-lookup"><span data-stu-id="fdc59-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="fdc59-125">[Předchozí] (implementace – hodnota objects.md) [Další] (domain modelu layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="fdc59-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
