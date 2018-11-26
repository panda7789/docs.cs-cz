---
title: Použití tříd Enumeration místo typů výčtů
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vymazat použití tříd enumeration místo výčty, jako způsob, jak vyřešit některá omezení.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 57c4af55bab9b17da5809f912d7c2d0b76eba40b
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296708"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="ad9ad-103">Použití tříd enumeration místo typů výčtů</span><span class="sxs-lookup"><span data-stu-id="ad9ad-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="ad9ad-104">[Výčty](../../../../docs/csharp/language-reference/keywords/enum.md) (nebo *typy výčtu* zkráceně) jsou dynamického zajišťování jazyk obálku celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="ad9ad-105">Můžete chtít omezit jejich použití k když ukládáte jednu hodnotu z uzavřených sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="ad9ad-106">Klasifikace na základě velikostí (malá, střední, velká) je typickým příkladem.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="ad9ad-107">Použití výčty pro tok řízení nebo robustnější abstrakce může být [kódu pach](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="ad9ad-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="ad9ad-108">Tento typ využití vede k křehké kódu s mnoha příkazech toku řízení kontrolu hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="ad9ad-109">Místo toho můžete vytvořit výčet tříd, které umožňují bohaté funkce objektově orientovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="ad9ad-110">Ale to není důležité tématu a v mnoha případech se pro jednoduchost, stále můžete pravidelně [typy výčtu](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/enum) Pokud tomu dáváte přednost.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/enum) if that's your preference.</span></span> <span data-ttu-id="ad9ad-111">Použití tříd enumeration je i přesto, více souvisí se obchodních konceptů.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="ad9ad-112">Implementace základní třídy výčtu</span><span class="sxs-lookup"><span data-stu-id="ad9ad-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="ad9ad-113">Pořadí mikroslužeb v aplikaci eShopOnContainers poskytuje implementaci základní třídy výčtu ukázka, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ad9ad-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration()
    { }

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

<span data-ttu-id="ad9ad-114">Tuto třídu můžete použít jako typ v libovolném entity nebo hodnota objektu, jako u následujících `CardType` : `Enumeration` třídy:</span><span class="sxs-lookup"><span data-stu-id="ad9ad-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    { }

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

## <a name="additional-resources"></a><span data-ttu-id="ad9ad-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ad9ad-115">Additional resources</span></span>

- <span data-ttu-id="ad9ad-116">**Výčtového jsou evil – aktualizovat** \\</span><span class="sxs-lookup"><span data-stu-id="ad9ad-116">**Enum’s are evil—update** \\</span></span>
  [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

- <span data-ttu-id="ad9ad-117">**Daniel Hardman. Jak rozložit výčty stádiu – A jak ho Vytvrdit** \\</span><span class="sxs-lookup"><span data-stu-id="ad9ad-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** \\</span></span>
  [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

- <span data-ttu-id="ad9ad-118">**Jimmy Bogard. Výčet tříd** \\</span><span class="sxs-lookup"><span data-stu-id="ad9ad-118">**Jimmy Bogard. Enumeration classes** \\</span></span>
  [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

- <span data-ttu-id="ad9ad-119">**Steve Smith. Alternativy výčtu v jazyce C#** \\</span><span class="sxs-lookup"><span data-stu-id="ad9ad-119">**Steve Smith. Enum Alternatives in C#** \\</span></span>
  [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

- <span data-ttu-id="ad9ad-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="ad9ad-120">**Enumeration.cs.**</span></span> <span data-ttu-id="ad9ad-121">Základní třída výčtu v aplikaci eShopOnContainers \\</span><span class="sxs-lookup"><span data-stu-id="ad9ad-121">Base Enumeration class in eShopOnContainers \\</span></span>
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

- <span data-ttu-id="ad9ad-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-122">**CardType.cs**.</span></span> <span data-ttu-id="ad9ad-123">Ukázka třídy výčtu v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)
    
- <span data-ttu-id="ad9ad-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-124">**SmartEnum**.</span></span> <span data-ttu-id="ad9ad-125">Ardalis – třídy, které pomáhají vytvářet chytřejší výčty se silnými typy v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ad9ad-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  [*https://www.nuget.org/packages/Ardalis.SmartEnum/*](https://www.nuget.org/packages/Ardalis.SmartEnum/)


>[!div class="step-by-step"]
<span data-ttu-id="ad9ad-126">[Předchozí](implement-value-objects.md)
[další](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="ad9ad-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>

