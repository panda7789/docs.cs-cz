---
title: Implementace hodnota objekty
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace hodnota objekty
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 4ba2e48e742e580a1c96743fa89e413c488b8dc7
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106720"
---
# <a name="implementing-value-objects"></a><span data-ttu-id="cb3c3-103">Implementace hodnota objekty</span><span class="sxs-lookup"><span data-stu-id="cb3c3-103">Implementing value objects</span></span>

<span data-ttu-id="cb3c3-104">Jak je popsáno v předchozích částech o entity a agregace, identita je zásadní pro entity.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="cb3c3-105">Existují však mnoho objektů a dat položky v rámci systému, které nevyžadují, aby identita a identity, jako je například hodnota objektů pro sledování.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="cb3c3-106">Objekt hodnoty můžete odkazovat ostatní entity.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-106">A value object can reference other entities.</span></span> <span data-ttu-id="cb3c3-107">Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do jiného že směrování by objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="cb3c3-108">Je snímek body na konkrétní trase, ale tato trasa navrhované neměli svou identitu, i když interně může odkazovat na entity města, silniční, atd.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="cb3c3-109">Obrázek 9 – 13 ukazuje objekt hodnoty adres v rámci agregace pořadí.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-109">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="cb3c3-110">**Obrázek 9 – 13**.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-110">**Figure 9-13**.</span></span> <span data-ttu-id="cb3c3-111">Adresa hodnota objekt v rámci agregace pořadí</span><span class="sxs-lookup"><span data-stu-id="cb3c3-111">Address value object within the Order aggregate</span></span>

<span data-ttu-id="cb3c3-112">Jak znázorňuje obrázek 9 – 13, entity se obvykle skládá z více atributů.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-112">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="cb3c3-113">Například `Order` entity můžete modelován jako entity s identity a složené interně sady atributů, například OrderId, OrderDate, OrderItems atd. Ale na adresu, což je jednoduše komplexní hodnota tvořený země, ulici, Město, atd. a je žádná identita v této doméně, musí být modelovány a považován za objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-113">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. and has no identity in this domain,  must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="cb3c3-114">Důležité charakteristiky hodnota objektů</span><span class="sxs-lookup"><span data-stu-id="cb3c3-114">Important characteristics of value objects</span></span>

<span data-ttu-id="cb3c3-115">Existují dvě hlavní vlastnosti pro objekty, hodnota:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-115">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="cb3c3-116">Nemají žádné identity.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-116">They have no identity.</span></span>

-   <span data-ttu-id="cb3c3-117">Jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-117">They are immutable.</span></span>

<span data-ttu-id="cb3c3-118">První vlastnosti už byl popsané.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-118">The first characteristic was already discussed.</span></span> <span data-ttu-id="cb3c3-119">Neměnitelnosti je důležité požadavek.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-119">Immutability is an important requirement.</span></span> <span data-ttu-id="cb3c3-120">Hodnoty objektu. hodnota musí být neměnné po vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-120">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="cb3c3-121">Když se objekt, proto je nutné zadat požadované hodnoty, ale nesmí umožňovat, aby změnit v průběhu životnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-121">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="cb3c3-122">Hodnota objekty umožňují provádět určité triky pro výkon díky jejich neměnné povahy.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-122">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="cb3c3-123">To platí hlavně v systémech kde může být tisíce hodnotu instance objektů, které mnoho má stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-123">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="cb3c3-124">Svou povahou neměnné umožňuje, aby znovu použít; může se jednat zaměňovat objekty, protože jejich hodnoty jsou stejné a mají žádná identita.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-124">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="cb3c3-125">Tento typ optimalizace někdy mohou být rozdíl mezi software, který běží pomalu a software s dobrý výkon.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-125">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="cb3c3-126">Všech těchto případech samozřejmě závisí na prostředí aplikace a nasazení kontextu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-126">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="cb3c3-127">Hodnota objektu implementace v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="cb3c3-127">Value object implementation in C\#</span></span>

<span data-ttu-id="cb3c3-128">Z hlediska implementace může mít základní třídy hodnotu objektu, která má základní pomocné metody jako rovnosti na základě porovnání mezi všechny atributy (protože objekt hodnota nesmí být na základě identity) a dalších základních vlastností.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-128">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="cb3c3-129">Následující příklad ukazuje hodnotu objektu základní třída používaná v řazení mikroslužbu z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-129">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }        
    // Other utilility methods
}
```

<span data-ttu-id="cb3c3-130">Tuto třídu můžete použít při implementaci skutečnou hodnotu objektu, stejně jako u adres objekt hodnoty vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-130">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; }
    public String City { get; }
    public String State { get; }
    public String Country { get; }
    public String ZipCode { get; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="cb3c3-131">Postup zachovat hodnotu objekty v databázi s EF základní 2.0</span><span class="sxs-lookup"><span data-stu-id="cb3c3-131">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="cb3c3-132">Právě jste viděli, jak definovat objekt hodnoty v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-132">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="cb3c3-133">Ale, jak můžete je ve skutečnosti zachovat ji do databáze prostřednictvím základní Entity Framework (EF), které se obvykle týká entity s identity?</span><span class="sxs-lookup"><span data-stu-id="cb3c3-133">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="cb3c3-134">Pozadí a starší přístupů pomocí EF základní 1.1</span><span class="sxs-lookup"><span data-stu-id="cb3c3-134">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="cb3c3-135">Jako pozadí, byl omezení při použití EF základní 1.0 a 1.1, nelze použít [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) definovaným v EF 6.x v tradiční rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-135">As background, a limitation when using EF Core 1.0 and 1.1 was that you cannot use  [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="cb3c3-136">Proto pokud používáte EF základní 1.0 nebo 1.1, je potřebný k uložení objektu hodnotu jako entity EF s pole ID.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-136">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="cb3c3-137">A, vypadal další jako objekt hodnoty pomocí žádná identita, může skrýt jeho ID, takže byste měli vytvořit jasné, že identita objekt hodnoty není důležité v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-137">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="cb3c3-138">Toto ID může skrýt pomocí ID jako [stínové vlastnost](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-138">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="cb3c3-139">Vzhledem k tomu, že konfigurace pro skrytí ID v modelu je nastaven na úrovni infrastruktury EF, bylo by druh transparentní pro modelu domény.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-139">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="cb3c3-140">Skrytá ID vyžaduje EF základní infrastruktury byla v původní verzi eShopOnContainers (.NET Core 1.1), implementovaná tímto způsobem na úrovni DbContext pomocí rozhraní Fluent API v projektu OMI.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-140">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="cb3c3-141">Proto se ID skrytá z hlediska domény modelu, ale stále přítomen v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-141">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration) 
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA); 

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

<span data-ttu-id="cb3c3-142">Však trvalost hodnotu objektu do databáze byla provedena jako regulární entity v jiné tabulky.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-142">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="cb3c3-143">S EF základní 2.0, je nový a lepší způsoby zachovat objekty hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-143">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="cb3c3-144">Zachovat objekty hodnotu jako ve vlastnictví entity typy v EF základní 2.0</span><span class="sxs-lookup"><span data-stu-id="cb3c3-144">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="cb3c3-145">I když některé mezery mezi vzor objektu kanonické hodnoty v DDD a typ vlastní entity v základní EF je aktuálně nejlepší způsob, jak zachovat objekty hodnotu s EF základní 2.0.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-145">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="cb3c3-146">Zobrazí se omezeních na konci této části.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-146">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="cb3c3-147">Funkci typu vlastněná entita byla přidána do základní EF od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-147">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="cb3c3-148">Typ entity ve vlastnictví umožňuje mapovat typy, které nemají své vlastní identity explicitně definované v modelu domény a jsou použity jako vlastnosti, například objekt hodnoty v některé z vaší entity.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-148">An owned entity type allows you to map types that do not have their own identity explicitely defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="cb3c3-149">Typ entity ve vlastnictví sdílí stejný typ CLR s jiným typem entity.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-149">An owned entity type shares the same CLR type with another entity type.</span></span> <span data-ttu-id="cb3c3-150">Entita obsahující definující navigační je vlastníka.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-150">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="cb3c3-151">Při dotazování vlastník, vlastní typy jsou zahrnuté ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-151">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="cb3c3-152">Podle vzhledu modelu domény, vlastní typ vypadá nemá žádné identity.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-152">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span>
<span data-ttu-id="cb3c3-153">V pozadí, vlastní typy mají identity, ale je součástí tuto identitu vlastníka navigační vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-153">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="cb3c3-154">Identita instance vlastní typy není úplně svoje vlastní.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-154">The identity of instances of own types is not completely their own.</span></span> <span data-ttu-id="cb3c3-155">Obsahuje tři komponenty:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-155">It consists of three components:</span></span>

- <span data-ttu-id="cb3c3-156">Identitu vlastníka</span><span class="sxs-lookup"><span data-stu-id="cb3c3-156">The identity of the owner</span></span>

- <span data-ttu-id="cb3c3-157">Vlastnost navigace na ně odkazují</span><span class="sxs-lookup"><span data-stu-id="cb3c3-157">The navigation property pointing to them</span></span>

- <span data-ttu-id="cb3c3-158">V případě kolekce vlastní typy komponentu nezávislé (není dosud podporován v EF základní 2.0).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-158">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0).</span></span>

<span data-ttu-id="cb3c3-159">V modelu domény řazení v eShopOnContainers jako součást pořadí entity, například objekt hodnoty adresa je implementovaný jako typ entity ve vlastnictví v rámci entity vlastníka, který je entita pořadí.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-159">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="cb3c3-160">Adresa je typu s žádná vlastnost identity, které jsou definované v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-160">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="cb3c3-161">Jako vlastnost typu pořadí slouží k určení adresy příjemce pro konkrétní pořadí.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-161">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="cb3c3-162">Podle konvence stínové primární klíč se vytvoří pro vlastní typ a bude být namapované na stejné tabulce jako vlastník pomocí rozdělení tabulky.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-162">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="cb3c3-163">To umožňuje použití vlastní typy podobně jako na tom, jak komplexní typy, které se používají v EF6 v tradiční rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-163">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="cb3c3-164">Je důležité si uvědomit, že který vlastněných typy nikdy zjištění podle konvence v EF jádra, musíte je výslovně deklarovat.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-164">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="cb3c3-165">V eShopOnContainers v OrderingContext.cs, v rámci metody OnModelCreating(), existuje více konfigurace infrastruktury, které bylo použito.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-165">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="cb3c3-166">Jeden z nich se týká entity pořadí.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-166">One of them is related to the Order entity.</span></span>

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
// 
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

<span data-ttu-id="cb3c3-167">V následujícím kódu je definováno infrastruktury trvalosti pro entitu pořadí:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-167">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

```csharp
// Part of the OrderEntityTypeConfiguration.cs class 
// 
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    
    //...Additional validations, constraints and code...
    //...
}
```

<span data-ttu-id="cb3c3-168">V předchozí kód `orderConfiguration.OwnsOne(o => o.Address)` metoda určuje, že `Address` vlastnost je vlastní entita `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-168">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="cb3c3-169">Ve výchozím nastavení, konvence EF základní název sloupce databáze pro vlastnosti typu entity ve vlastnictví jako `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-169">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="cb3c3-170">Proto vnitřní vlastnosti `Address` se objeví v `Orders` tabulku s názvy `Address_Street`, `Address_City` (a tak dále pro `State`, `Country` a `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-170">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="cb3c3-171">Můžete připojit `Property().HasColumnName()` fluent metoda přejmenovat tyto sloupce.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-171">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="cb3c3-172">V případě, kde `Address` veřejná vlastnost mapování by bylo třeba takto:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-172">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="cb3c3-173">Je možné řetězec `OwnsOne` metoda fluent mapování.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-173">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="cb3c3-174">V následujícím příkladu hypotetický `OrderDetails` vlastní `BillingAddress` a `ShippingAddress`, které jsou obě `Address` typy.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-174">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="cb3c3-175">Potom `OrderDetails` vlastníkem je `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-175">Then `OrderDetails` is owned by the `Order` type.</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="cb3c3-176">Další informace o typy vlastní entit</span><span class="sxs-lookup"><span data-stu-id="cb3c3-176">Additional details on owned entity types</span></span>

<span data-ttu-id="cb3c3-177">• Vlastní typy jsou definovány při konfiguraci navigační vlastnost pro konkrétní typ pomocí rozhraní fluent API OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-177">•   Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

<span data-ttu-id="cb3c3-178">• Definici vlastní typu v našem model metadat je složené: Typ vlastníka, navigační vlastnost a typ CLR vlastní typu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-178">•   The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

<span data-ttu-id="cb3c3-179">• Identity (klíč) vlastní typ instance v našem zásobníku je složené identity typu vlastníka a definicí typu vlastní.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-179">•   The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="cb3c3-180">Vlastní entity možnosti:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-180">Owned entities capabilities:</span></span>

<span data-ttu-id="cb3c3-181">•, Že typ, můžete odkazovat jinými entitami, buď ve vlastnictví (vnořené vlastní typy) bez vlastněné nebo (navigační vlastnosti regulární odkazu na ostatní entity).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-181">•   Owned type can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

<span data-ttu-id="cb3c3-182">• Můžete mapovat stejný typ CLR jako ve vlastnictví různého stejné entity vlastníka prostřednictvím samostatné navigační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-182">•   You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

<span data-ttu-id="cb3c3-183">• Rozdělení tabulky je nastavená podle konvence, ale můžete chodit tak, že mapuje vlastní typ do jiné tabulky pomocí ToTable.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-183">•   Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

<span data-ttu-id="cb3c3-184">• Přes načtení je prováděno automaticky pro vlastní typy, tj. není třeba volat Include() na dotaz.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-184">•   Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="cb3c3-185">Vlastní entity omezení:</span><span class="sxs-lookup"><span data-stu-id="cb3c3-185">Owned entities limitations:</span></span>

<span data-ttu-id="cb3c3-186">• Nelze vytvořit DbSet<T> vlastní typu (záměrně).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-186">•   You cannot create a DbSet<T> of an owned type (by design).</span></span>

<span data-ttu-id="cb3c3-187">• Nelze volat ModelBuilder.Entity<T>() pro vlastní typy (aktuálně podle návrhu).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-187">•   You cannot call ModelBuilder.Entity<T>() on owned types (currently by design).</span></span>

<span data-ttu-id="cb3c3-188">• Žádné kolekce vlastní typy ještě (ale bude se podporovány ve verzích po EF základní 2.0).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-188">•   No collections of owned types yet (but they will be supported in versions after EF Core 2.0).</span></span>

<span data-ttu-id="cb3c3-189">• Žádná podpora pro jejich konfigurací prostřednictvím atributu.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-189">•   No support for configuring them via an attribute.</span></span>

<span data-ttu-id="cb3c3-190">• Žádná podpora pro volitelné (tj. připouštějící hodnotu Null) vlastní typy, které jsou mapovány s vlastníkem ve stejné tabulce (tj. pomocí rozdělení tabulky).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-190">•   No support for optional (i.e. nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="cb3c3-191">To je proto nemáme samostatné sentinel pro hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-191">This is because we don't have a separate sentinel for the null.</span></span>

<span data-ttu-id="cb3c3-192">• Podpora mapování dědičnosti pro vlastní typy, ale byste měli mít k mapování dva typy na stejné hierarchie dědičnosti jako ve vlastnictví různého typu list.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-192">•   No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="cb3c3-193">Základní EF nebude důvodu o tom, že jsou součástí stejné hierarchie.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-193">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="cb3c3-194">Hlavní rozdíly mezi EF6 je komplexní typy</span><span class="sxs-lookup"><span data-stu-id="cb3c3-194">Main differences with EF6's complex types</span></span>

<span data-ttu-id="cb3c3-195">• Rozdělení tabulky je volitelné, tj. jejich může volitelně mapovat do samostatné tabulky a přesto být vlastní typy.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-195">•   Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

<span data-ttu-id="cb3c3-196">• Mohou odkazovat ostatní entity (tj. jejich může fungovat jako závislé straně u relací na jiné typy bez vlastněných).</span><span class="sxs-lookup"><span data-stu-id="cb3c3-196">•   They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>


## <a name="additional-resources"></a><span data-ttu-id="cb3c3-197">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cb3c3-197">Additional resources</span></span>

-   <span data-ttu-id="cb3c3-198">**Martin Fowler. Vzor ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="cb3c3-198">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="cb3c3-199">**Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru.**</span><span class="sxs-lookup"><span data-stu-id="cb3c3-199">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="cb3c3-200">(Sešit; zahrnuje diskuzi o hodnotu objekty) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="cb3c3-200">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="cb3c3-201">**Vaughn Vernon. Implementace návrhu řízené domény.**</span><span class="sxs-lookup"><span data-stu-id="cb3c3-201">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="cb3c3-202">(Sešit; zahrnuje diskuzi o hodnotu objekty) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="cb3c3-202">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="cb3c3-203">**Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="cb3c3-203">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="cb3c3-204">**Komplexní typy nebo hodnoty objekty**.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-204">**Complex types and/or value objects**.</span></span> <span data-ttu-id="cb3c3-205">Diskusi do úložiště GitHub základní EF (karta problémů) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="cb3c3-205">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="cb3c3-206">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="cb3c3-206">**ValueObject.cs.**</span></span> <span data-ttu-id="cb3c3-207">Základní hodnota třída objektu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-207">Base value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="cb3c3-208">**Třídy adres.**</span><span class="sxs-lookup"><span data-stu-id="cb3c3-208">**Address class.**</span></span> <span data-ttu-id="cb3c3-209">Ukázka třídy objektu hodnotu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="cb3c3-209">Sample value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
<span data-ttu-id="cb3c3-210">[Předchozí](seedwork-domain-model-base-classes-interfaces.md)
[další](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="cb3c3-210">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
