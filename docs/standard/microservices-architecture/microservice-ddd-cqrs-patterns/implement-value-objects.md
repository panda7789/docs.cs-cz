---
title: Implementace hodnota objekty
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace hodnota objekty"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a><span data-ttu-id="f25d3-104">Implementace hodnota objekty</span><span class="sxs-lookup"><span data-stu-id="f25d3-104">Implementing value objects</span></span>

<span data-ttu-id="f25d3-105">Jak je popsáno v předchozích částech o entity a agregace, identita je zásadní pro entity.</span><span class="sxs-lookup"><span data-stu-id="f25d3-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="f25d3-106">Existují však mnoho objektů a dat položky v rámci systému, které nevyžadují, aby identita a identity, jako je například hodnota objektů pro sledování.</span><span class="sxs-lookup"><span data-stu-id="f25d3-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="f25d3-107">Objekt hodnoty můžete odkazovat ostatní entity.</span><span class="sxs-lookup"><span data-stu-id="f25d3-107">A value object can reference other entities.</span></span> <span data-ttu-id="f25d3-108">Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do jiného že směrování by objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f25d3-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="f25d3-109">Je snímek body na konkrétní trase, ale tato trasa navrhované neměli svou identitu, i když interně může odkazovat na entity města, silniční, atd.</span><span class="sxs-lookup"><span data-stu-id="f25d3-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="f25d3-110">Obrázek 9 – 13 ukazuje objekt hodnoty adres v rámci agregace pořadí.</span><span class="sxs-lookup"><span data-stu-id="f25d3-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="f25d3-111">**Obrázek 9 – 13**.</span><span class="sxs-lookup"><span data-stu-id="f25d3-111">**Figure 9-13**.</span></span> <span data-ttu-id="f25d3-112">Adresa hodnota objekt v rámci agregace pořadí</span><span class="sxs-lookup"><span data-stu-id="f25d3-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="f25d3-113">Jak znázorňuje obrázek 9 – 13, entity se obvykle skládá z více atributů.</span><span class="sxs-lookup"><span data-stu-id="f25d3-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="f25d3-114">Například pořadí můžete modelován jako entity s identitou a interně tvořený sadu atributů například OrderId, OrderDate, OrderItems atd. Ale na adresu, což je jednoduše komplexní hodnota skládá z země, ulici, města, musí být modelovány a považován za objekt hodnoty atd.</span><span class="sxs-lookup"><span data-stu-id="f25d3-114">For example, Order can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="f25d3-115">Důležité charakteristiky hodnota objektů</span><span class="sxs-lookup"><span data-stu-id="f25d3-115">Important characteristics of value objects</span></span>

<span data-ttu-id="f25d3-116">Existují dvě hlavní vlastnosti pro objekty, hodnota:</span><span class="sxs-lookup"><span data-stu-id="f25d3-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="f25d3-117">Nemají žádné identity.</span><span class="sxs-lookup"><span data-stu-id="f25d3-117">They have no identity.</span></span>

-   <span data-ttu-id="f25d3-118">Jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="f25d3-118">They are immutable.</span></span>

<span data-ttu-id="f25d3-119">První vlastnosti už byl popsané.</span><span class="sxs-lookup"><span data-stu-id="f25d3-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="f25d3-120">Neměnitelnosti je důležité požadavek.</span><span class="sxs-lookup"><span data-stu-id="f25d3-120">Immutability is an important requirement.</span></span> <span data-ttu-id="f25d3-121">Hodnoty objektu. hodnota musí být neměnné po vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="f25d3-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="f25d3-122">Když se objekt, proto je nutné zadat požadované hodnoty, ale nesmí umožňovat, aby změnit v průběhu životnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="f25d3-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="f25d3-123">Hodnota objekty umožňují provádět určité triky pro výkon díky jejich neměnné povahy.</span><span class="sxs-lookup"><span data-stu-id="f25d3-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="f25d3-124">To platí hlavně v systémech kde může být tisíce hodnotu instance objektů, které mnoho má stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f25d3-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="f25d3-125">Svou povahou neměnné umožňuje, aby znovu použít; může se jednat zaměňovat objekty, protože jejich hodnoty jsou stejné a mají žádná identita.</span><span class="sxs-lookup"><span data-stu-id="f25d3-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="f25d3-126">Tento typ optimalizace někdy mohou být rozdíl mezi software, který běží pomalu a software s dobrý výkon.</span><span class="sxs-lookup"><span data-stu-id="f25d3-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="f25d3-127">Všech těchto případech samozřejmě závisí na prostředí aplikace a nasazení kontextu.</span><span class="sxs-lookup"><span data-stu-id="f25d3-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="f25d3-128">Hodnota objektu implementace v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="f25d3-128">Value object implementation in C\#</span></span>

<span data-ttu-id="f25d3-129">Z hlediska implementace může mít základní třídy hodnotu objektu, která má základní pomocné metody jako rovnosti na základě porovnání mezi všechny atributy (protože objekt hodnota nesmí být na základě identity) a dalších základních vlastností.</span><span class="sxs-lookup"><span data-stu-id="f25d3-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="f25d3-130">Následující příklad ukazuje hodnotu objektu základní třída používaná v řazení mikroslužbu z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f25d3-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

<span data-ttu-id="f25d3-131">Tuto třídu můžete použít při implementaci skutečnou hodnotu objektu, stejně jako u adres objekt hodnoty vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f25d3-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a><span data-ttu-id="f25d3-132">Skrytí vlastnosti identity při použití EF základní udržení hodnota objekty</span><span class="sxs-lookup"><span data-stu-id="f25d3-132">Hiding the identity characteristic when using EF Core to persist value objects</span></span>

<span data-ttu-id="f25d3-133">Omezení při použití EF základní je, že v jeho aktuální verze (EF základní 1.1) nelze použít [komplexní typy](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) definovaným v EF 6.x.</span><span class="sxs-lookup"><span data-stu-id="f25d3-133">A limitation when using EF Core is that in its current version (EF Core 1.1) you cannot use [complex types](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) as defined in EF 6.x.</span></span> <span data-ttu-id="f25d3-134">Proto musíte uložit hodnotu objektu jako EF entity.</span><span class="sxs-lookup"><span data-stu-id="f25d3-134">Therefore, you must store your value object as an EF entity.</span></span> <span data-ttu-id="f25d3-135">Však můžete skrýt jeho ID, takže byste měli vytvořit jasné, že identita není důležité v modelu, který je součástí objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f25d3-135">However, you can hide its ID so you make clear that the identity is not important in the model that the value object is part of.</span></span> <span data-ttu-id="f25d3-136">Skrýt ID je pomocí ID jako vlastnost stínové.</span><span class="sxs-lookup"><span data-stu-id="f25d3-136">You hide the ID is by using the ID as a shadow property.</span></span> <span data-ttu-id="f25d3-137">Vzhledem k tomu, že tato konfigurace pro skrytí ID v modelu je nastaven na úrovni infrastruktury, je transparentní pro váš model domény a jeho implementace infrastruktury může v budoucnu změnit.</span><span class="sxs-lookup"><span data-stu-id="f25d3-137">Since that configuration for hiding the ID in the model is set up in the infrastructure level, it will be transparent for your domain model, and its infrastructure implementation could change in the future.</span></span>

<span data-ttu-id="f25d3-138">Skrytá ID vyžaduje EF základní infrastruktury je v eShopOnContainers, implementovaná tímto způsobem na úrovni DbContext pomocí rozhraní Fluent API v projektu OMI.</span><span class="sxs-lookup"><span data-stu-id="f25d3-138">In eShopOnContainers, the hidden ID needed by EF Core infrastructure is implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span>

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

<span data-ttu-id="f25d3-139">Proto ID je skrytý z hlediska domény modelu a v budoucnu infrastruktury objekt hodnotu lze také implementovat jako komplexní typ nebo jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f25d3-139">Therefore, the ID is hidden from the domain model point of view, and in the future, the value object infrastructure could also be implemented as a complex type or another way.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f25d3-140">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="f25d3-140">Additional resources</span></span>

-   <span data-ttu-id="f25d3-141">**Martin Fowler. Vzor ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="f25d3-141">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="f25d3-142">**Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru.**</span><span class="sxs-lookup"><span data-stu-id="f25d3-142">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="f25d3-143">(Sešit; zahrnuje diskuzi o hodnotu objekty) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="f25d3-143">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="f25d3-144">**Vaughn Vernon. Implementace návrhu řízené domény.**</span><span class="sxs-lookup"><span data-stu-id="f25d3-144">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="f25d3-145">(Sešit; zahrnuje diskuzi o hodnotu objekty) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="f25d3-145">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="f25d3-146">**Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="f25d3-146">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="f25d3-147">**Komplexní typy nebo hodnoty objekty**.</span><span class="sxs-lookup"><span data-stu-id="f25d3-147">**Complex types and/or value objects**.</span></span> <span data-ttu-id="f25d3-148">Diskusi do úložiště GitHub základní EF (karta problémy) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="f25d3-148">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="f25d3-149">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="f25d3-149">**ValueObject.cs.**</span></span> <span data-ttu-id="f25d3-150">Základní hodnota třída objektu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f25d3-150">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="f25d3-151">*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span><span class="sxs-lookup"><span data-stu-id="f25d3-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="f25d3-152">**Třídy adres.**</span><span class="sxs-lookup"><span data-stu-id="f25d3-152">**Address class.**</span></span> <span data-ttu-id="f25d3-153">Ukázka třídy objektu hodnotu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f25d3-153">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="f25d3-154">*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span><span class="sxs-lookup"><span data-stu-id="f25d3-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
<span data-ttu-id="f25d3-155">[Předchozí] (seedwork-domain-model-base-classes-interfaces.md) [Další] (výčet třídy over výčtu types.md)</span><span class="sxs-lookup"><span data-stu-id="f25d3-155">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
