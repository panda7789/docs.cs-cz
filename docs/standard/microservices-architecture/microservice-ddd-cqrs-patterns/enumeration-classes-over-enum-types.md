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
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="e5066-104">Pomocí třídy výčtu místo typy výčtu</span><span class="sxs-lookup"><span data-stu-id="e5066-104">Using Enumeration classes instead of enum types</span></span>

<span data-ttu-id="e5066-105">[Výčty](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*výčty* pro zkrácení) jsou dynamické jazyk obálku kolem integrální typu.</span><span class="sxs-lookup"><span data-stu-id="e5066-105">[Enumerations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="e5066-106">Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="e5066-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="e5066-107">Klasifikace podle pohlaví (například mužského, samičího neznámé), nebo velikosti (S, M, L, XL) jsou dobrými příklady.</span><span class="sxs-lookup"><span data-stu-id="e5066-107">Classification based on gender (for example, male, female, unknown), or sizes (S, M, L, XL) are good examples.</span></span> <span data-ttu-id="e5066-108">Pomocí výčty pro tok řízení nebo robustnější abstrakce může být [code pach](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="e5066-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="e5066-109">Tento typ využití povede k křehké kód s mnoha příkazy toku řízení kontrola hodnoty výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="e5066-109">This type of usage will lead to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="e5066-110">Místo toho můžete vytvořit výčet tříd, které povolit všechny bohaté funkce jazyka objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="e5066-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span> <span data-ttu-id="e5066-111">Ale nejedná se o kritický problém a v mnoha případech pro jednoduchost, stále můžete regulární výčty, pokud vaši volbu.</span><span class="sxs-lookup"><span data-stu-id="e5066-111">However, this is not a critical issue and in many cases, for simplicity, you can still use regular enums if that is your preference.</span></span>

## <a name="implementing-enumeration-classes"></a><span data-ttu-id="e5066-112">Implementace tříd – výčet</span><span class="sxs-lookup"><span data-stu-id="e5066-112">Implementing Enumeration classes</span></span>

<span data-ttu-id="e5066-113">Řazení mikroslužbu v eShopOnContainers poskytuje implementaci základní třída výčtu ukázka, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e5066-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="e5066-114">Tuto třídu můžete použít jako typ v žádné entity nebo hodnota objektu jako následující třídy CardType výčtu.</span><span class="sxs-lookup"><span data-stu-id="e5066-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="e5066-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e5066-115">Additional resources</span></span>

-   <span data-ttu-id="e5066-116">**Na výčtu jsou evil – aktualizovat**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="e5066-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="e5066-117">**ADAM Hardman. Jak výčty šíří nákazy – A jak ho Vytvrdit**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="e5066-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="e5066-118">**Jimmy Bogard. Výčet tříd**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="e5066-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="e5066-119">**Steve Smith. Výčet alternativy v jazyce C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="e5066-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="e5066-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="e5066-120">**Enumeration.cs.**</span></span> <span data-ttu-id="e5066-121">Základní třída výčet v eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="e5066-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="e5066-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="e5066-122">**CardType.cs**.</span></span> <span data-ttu-id="e5066-123">Ukázka třídy výčet v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e5066-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="e5066-124">*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span><span class="sxs-lookup"><span data-stu-id="e5066-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="e5066-125">[Předchozí] (implementace – hodnota objects.md) [Další] (domain modelu layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="e5066-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
