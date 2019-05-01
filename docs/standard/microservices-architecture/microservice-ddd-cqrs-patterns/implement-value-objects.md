---
title: Implementace objektů hodnot
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Získejte podrobnosti a možnosti, které implementují objekty hodnotu pomocí nové funkce Entity Framework.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 64ffd600468124439986b0d1949dc048ef245c78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019786"
---
# <a name="implement-value-objects"></a><span data-ttu-id="aa219-103">Implementace objektů hodnot</span><span class="sxs-lookup"><span data-stu-id="aa219-103">Implement value objects</span></span>

<span data-ttu-id="aa219-104">Jak je popsáno v předchozích částech o entit a agregace, je nezbytné pro entity identity.</span><span class="sxs-lookup"><span data-stu-id="aa219-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="aa219-105">Existují však mnoho objektů a dat položky v systému, které nevyžadují identit a identity, jako je například hodnota objektů pro sledování.</span><span class="sxs-lookup"><span data-stu-id="aa219-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="aa219-106">Objekt hodnoty, který může odkazovat na jiné entity.</span><span class="sxs-lookup"><span data-stu-id="aa219-106">A value object can reference other entities.</span></span> <span data-ttu-id="aa219-107">Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho místa do jiného směrující by být objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aa219-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="aa219-108">Bylo by snímek body na konkrétní trase, ale tato trasa navrhované nemusí identitu, i když interně může odkazovat na entitami, jako jsou Město, silniční atd.</span><span class="sxs-lookup"><span data-stu-id="aa219-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="aa219-109">Obrázek 7-13 zobrazuje objekt hodnoty adres v rámci pořadí agregace.</span><span class="sxs-lookup"><span data-stu-id="aa219-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Adresa-objekt hodnoty uvnitř agregace pořadí.](./media/image14.png)

<span data-ttu-id="aa219-111">**Obrázek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="aa219-111">**Figure 7-13**.</span></span> <span data-ttu-id="aa219-112">Adresa objektu hodnot v rámci pořadí agregace</span><span class="sxs-lookup"><span data-stu-id="aa219-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="aa219-113">Jak je znázorněno v obrázek 7-13, entity se obvykle skládá z více atributů.</span><span class="sxs-lookup"><span data-stu-id="aa219-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="aa219-114">Například `Order` entity můžete modelovat jako entity s identitou a interně skládá ze sady atributů, jako je například OrderId, OrderDate, OrderItems atd. Ale adresu, která je jednoduše komplexní – hodnota složený ze země, ulici, Město atd. a nemá žádná identita v této doméně, musí být modelovat a považován za hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="aa219-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="aa219-115">Důležité charakteristiky hodnotu objektů</span><span class="sxs-lookup"><span data-stu-id="aa219-115">Important characteristics of value objects</span></span>

<span data-ttu-id="aa219-116">Existují dva hlavní vlastnosti pro objekty hodnotu:</span><span class="sxs-lookup"><span data-stu-id="aa219-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="aa219-117">Nemají žádné identity.</span><span class="sxs-lookup"><span data-stu-id="aa219-117">They have no identity.</span></span>

- <span data-ttu-id="aa219-118">Jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="aa219-118">They are immutable.</span></span>

<span data-ttu-id="aa219-119">O první charakteristiku bylo už popsáno.</span><span class="sxs-lookup"><span data-stu-id="aa219-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="aa219-120">Neměnnost je důležité požadavek.</span><span class="sxs-lookup"><span data-stu-id="aa219-120">Immutability is an important requirement.</span></span> <span data-ttu-id="aa219-121">Hodnoty objekt hodnoty musí být neměnný po vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="aa219-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="aa219-122">Při vytvoření objektu, proto je nutné zadat požadované hodnoty, ale nesmí zajistí, aby změnit během životního cyklu objektu.</span><span class="sxs-lookup"><span data-stu-id="aa219-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="aa219-123">Hodnota objekty umožňují provádět některé tipy pro výkon díky jejich povaze neměnné.</span><span class="sxs-lookup"><span data-stu-id="aa219-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="aa219-124">To platí zejména v systémech tam, kde můžou existovat tisíce hodnotu instance objektů, z nichž mají stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aa219-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="aa219-125">Jejich neměnné podstatu umožňuje jejich opětovné používání; je možné zaměnitelné objekty, protože jejich hodnoty jsou stejné, a nemají žádné identity.</span><span class="sxs-lookup"><span data-stu-id="aa219-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="aa219-126">Tento typ optimalizace někdy možné zvýšit rozdíl mezi softwarem, který běží pomalu a software s dobrého výkonu.</span><span class="sxs-lookup"><span data-stu-id="aa219-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="aa219-127">Všech těchto případech samozřejmě závisí na prostředí aplikací a nasazení kontext.</span><span class="sxs-lookup"><span data-stu-id="aa219-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="aa219-128">Implementace objektu hodnoty v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="aa219-128">Value object implementation in C\#</span></span>

<span data-ttu-id="aa219-129">Z hlediska implementace může mít hodnotu základní třídu objektu, který má metody základní nástroje, jako je rovnost na základě porovnání mezi všechny atributy (protože hodnota objektu nesmí být na základě identity) a další základní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa219-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="aa219-130">Následující příklad ukazuje základní třídu hodnotu objektu používá v pořadí mikroslužeb v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="aa219-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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
    // Other utility methods
}
```

<span data-ttu-id="aa219-131">Tuto třídu můžete použít při implementaci skutečnou hodnotu objektu, stejně jako u adres objekt hodnoty je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aa219-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

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

<span data-ttu-id="aa219-132">Uvidíte jak implementovaný objekt hodnotu adresy má žádná identita a proto žádné pole ID, ani na třídu adresu ani na třídu ValueObject.</span><span class="sxs-lookup"><span data-stu-id="aa219-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="aa219-133">Žádné ID pole třídy používané Entity Framework s nebylo možné, dokud EF Core 2.0, což značně pomáhá implementovat lepší hodnotu objekty s žádné ID.</span><span class="sxs-lookup"><span data-stu-id="aa219-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="aa219-134">To je přesně vysvětlení další části.</span><span class="sxs-lookup"><span data-stu-id="aa219-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="aa219-135">Může být uvedl, že hodnota objekty, budou nezměnitelný, by měla být jen pro čtení (například get jen vlastnosti), a to je ve skutečnosti hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="aa219-135">It could be argued that value objects, being immutable, should be read-only (i.e. get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="aa219-136">Však hodnoty objekty jsou obvykle serializaci a deserializaci absolvovat fronty zpráv a je jen pro čtení zastaví deserializátor v přiřazení hodnoty, takže jsme právě nechat jako privátní sada, která je jen pro čtení dostatečně bude praktické.</span><span class="sxs-lookup"><span data-stu-id="aa219-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="aa219-137">Zachování hodnotu objektů v databázi s EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="aa219-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="aa219-138">Právě jste viděli, jak definovat objekt hodnoty v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="aa219-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="aa219-139">Ale jak můžete ve skutečnosti trvale uložíte ho do databáze prostřednictvím základní Entity Framework (EF), která se obvykle týká entity, které identity?</span><span class="sxs-lookup"><span data-stu-id="aa219-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="aa219-140">Na pozadí a starší přístupy s použitím EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="aa219-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="aa219-141">Jako pozadí, byla nelze použít omezení při použití EF Core 1.0 a 1.1 [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) jak jsou definovány v EF 6.x v tradiční rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa219-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="aa219-142">Proto pokud pomocí EF Core 1.0 a 1.1, museli jste k uložení hodnoty objektu jako entita EF se pole ID.</span><span class="sxs-lookup"><span data-stu-id="aa219-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="aa219-143">Pak, aby vypadal podobně objekt hodnoty pomocí žádná identita, může skrýt jeho ID, takže jasně, že identita hodnota objektu není důležité v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="aa219-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="aa219-144">Toto ID může skrýt pomocí ID jako [stínové vlastnosti](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="aa219-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="aa219-145">Protože tuto konfiguraci pro skrytí ID v modelu je nastaven na úrovni infrastruktury EF, bylo by druh transparentní pro doménový model.</span><span class="sxs-lookup"><span data-stu-id="aa219-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="aa219-146">Skrytá ID vyžadované EF Core infrastruktury byl v počáteční verzi aplikaci eShopOnContainers (.NET Core 1.1), implementované v úrovni DbContext, následujícím způsobem pomocí rozhraní Fluent API v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="aa219-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="aa219-147">Proto se ID skryté z hlediska domény modelu, ale stále k dispozici v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="aa219-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="aa219-148">Ale trvalost hodnotu objektu do databáze byla provedena jako regulární entity v jiné tabulce.</span><span class="sxs-lookup"><span data-stu-id="aa219-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="aa219-149">S EF Core 2.0, existují nové a lepší způsoby, jak zachovat hodnotu objektů.</span><span class="sxs-lookup"><span data-stu-id="aa219-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="aa219-150">Zachovat hodnotu objektů jako vlastněné typy entit v EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="aa219-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="aa219-151">I při některých mezery mezi vzor objektu Kanonická hodnota v DDD a typ vlastnictví entity v EF Core je aktuálně nejlepší způsob, jak zachovat hodnotu objekty s EF Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="aa219-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="aa219-152">Zobrazí se omezení na konci této části.</span><span class="sxs-lookup"><span data-stu-id="aa219-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="aa219-153">Typ funkce vlastnictví entity byl přidán do EF Core od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="aa219-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="aa219-154">Typ vlastnictví entity umožňuje mapování typů, které nemají vlastní identity explicitně definované v modelu domény a slouží jako vlastnosti, jako je například objekt hodnoty v rámci všech entit.</span><span class="sxs-lookup"><span data-stu-id="aa219-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="aa219-155">Typ vlastnictví entity sdílí stejný typ CLR s jiným typem entity (to znamená, je právě běžné třídy).</span><span class="sxs-lookup"><span data-stu-id="aa219-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="aa219-156">Entita obsahující definující navigace je entita, vlastníka.</span><span class="sxs-lookup"><span data-stu-id="aa219-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="aa219-157">Při dotazování na vlastníka, vlastněné typy jsou zahrnuté ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="aa219-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="aa219-158">Právě zobrazením doménový model, vlastní typ, který vypadá to, nemá žádné identity.</span><span class="sxs-lookup"><span data-stu-id="aa219-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="aa219-159">Pod pokličkou, vlastněné typy mít identitu, ale vlastník navigační vlastnost je součástí této identity.</span><span class="sxs-lookup"><span data-stu-id="aa219-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="aa219-160">Identita instance typů vlastnictví není zcela vlastní.</span><span class="sxs-lookup"><span data-stu-id="aa219-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="aa219-161">Skládá se ze tří komponent:</span><span class="sxs-lookup"><span data-stu-id="aa219-161">It consists of three components:</span></span>

- <span data-ttu-id="aa219-162">Identita vlastníka</span><span class="sxs-lookup"><span data-stu-id="aa219-162">The identity of the owner</span></span>

- <span data-ttu-id="aa219-163">Navigační vlastnost odkazuje na ně</span><span class="sxs-lookup"><span data-stu-id="aa219-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="aa219-164">V případě kolekcí vlastněné typy, jako nezávislé součást (ještě není podporované v EF Core 2.0, naráželi na 2.2).</span><span class="sxs-lookup"><span data-stu-id="aa219-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="aa219-165">V doménovém modelu řazení v aplikaci eShopOnContainers jako součást pořadí entity, například objekt hodnoty adres je implementovaný jako typ vlastnictví entity v rámci entity vlastník, což je entita pořadí.</span><span class="sxs-lookup"><span data-stu-id="aa219-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="aa219-166">Adresa je typ s žádnou vlastnost identity definován v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="aa219-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="aa219-167">Jako vlastnost typu pořadí slouží k určení dodací adresu pro konkrétní objednávku.</span><span class="sxs-lookup"><span data-stu-id="aa219-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="aa219-168">Podle konvence stínové primární klíč je vytvořen pro typ vlastnictví a bude ji namapovat na stejnou tabulku jako vlastník pomocí rozdělení tabulky.</span><span class="sxs-lookup"><span data-stu-id="aa219-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="aa219-169">To umožňuje použití vlastní typy podobně jako na tom, jak komplexní typy, které se používají v EF6 v tradiční rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa219-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="aa219-170">Je důležité si uvědomit, že, který vlastní, že typy nikdy zjištění konvencí v EF Core, takže je nutné je explicitně deklarovat.</span><span class="sxs-lookup"><span data-stu-id="aa219-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="aa219-171">V aplikaci eShopOnContainers v OrderingContext.cs, v rámci metody OnModelCreating() existují více konfiguraci infrastruktury, které jsou právě používá.</span><span class="sxs-lookup"><span data-stu-id="aa219-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="aa219-172">Jeden z nich souvisí s entitou objednávky.</span><span class="sxs-lookup"><span data-stu-id="aa219-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="aa219-173">V následujícím kódu je definována infrastruktury trvalosti pro entitu pořadí:</span><span class="sxs-lookup"><span data-stu-id="aa219-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="aa219-174">V předchozím kódu `orderConfiguration.OwnsOne(o => o.Address)` metody Určuje, že `Address` vlastností je vlastní entity `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="aa219-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="aa219-175">Ve výchozím nastavení, EF Core konvence název sloupce databáze pro vlastnosti typu vlastnictví entity jako `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="aa219-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="aa219-176">Proto vnitřní vlastnosti `Address` se zobrazí v `Orders` tabulky s názvy `Address_Street`, `Address_City` (a podobně pro `State`, `Country` a `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="aa219-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="aa219-177">Můžete připojit `Property().HasColumnName()` fluent metoda přejmenování sloupců.</span><span class="sxs-lookup"><span data-stu-id="aa219-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="aa219-178">V případě, kdy `Address` je veřejná vlastnost mapování bude podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="aa219-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="aa219-179">Je možné řetězec `OwnsOne` metoda v mapování fluent.</span><span class="sxs-lookup"><span data-stu-id="aa219-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="aa219-180">V následujícím příkladu hypotetické `OrderDetails` vlastní `BillingAddress` a `ShippingAddress`, které jsou obě `Address` typy.</span><span class="sxs-lookup"><span data-stu-id="aa219-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="aa219-181">Potom `OrderDetails` není ve vlastnictví `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="aa219-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="aa219-182">Další podrobnosti o vlastněné typy entit</span><span class="sxs-lookup"><span data-stu-id="aa219-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="aa219-183">Vlastněné typy jsou definovány, když konfigurujete navigační vlastnost pro určitý typ pomocí rozhraní API fluent OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="aa219-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="aa219-184">Definice typu vlastnictví v našich metadat modelu je složené: Typ vlastníka, navigační vlastnost a typ CLR vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="aa219-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="aa219-185">Identita (klíč) vlastnictví typu instance v našich zásobníku je složené identity typu vlastníka a definice typu vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="aa219-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="aa219-186">Vlastnictví entity funkce:</span><span class="sxs-lookup"><span data-stu-id="aa219-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="aa219-187">Vlastní typy mohou odkazovat na jiné entity, buď vlastní (vnořené vlastněné typy) nebo není ve vlastnictví (pravidelných odkaz navigačních vlastností pro ostatní entity).</span><span class="sxs-lookup"><span data-stu-id="aa219-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="aa219-188">Můžete namapovat stejný typ CLR jako vlastněné typy v rámci stejné entity vlastníka prostřednictvím samostatný navigační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa219-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="aa219-189">Rozdělení tabulky se nastavení podle konvence, ale můžete odhlásit pomocí mapování typ vlastnictví na jinou tabulku pomocí ToTable.</span><span class="sxs-lookup"><span data-stu-id="aa219-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="aa219-190">Předběžné načítání se provádí automaticky na vlastní typy, tedy není nutné volat Include() na dotazu.</span><span class="sxs-lookup"><span data-stu-id="aa219-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="aa219-191">Můžete nakonfigurovat pomocí atributu \[vlastněno\], protože EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="aa219-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="aa219-192">Vlastnictví entity omezení:</span><span class="sxs-lookup"><span data-stu-id="aa219-192">Owned entities limitations:</span></span>

- <span data-ttu-id="aa219-193">Nelze vytvořit DbSet\<T\> vlastnictví typu (záměrně).</span><span class="sxs-lookup"><span data-stu-id="aa219-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="aa219-194">Nejde volat ModelBuilder.Entity\<T\>() pro vlastní typy (aktuálně záměrné).</span><span class="sxs-lookup"><span data-stu-id="aa219-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="aa219-195">Žádné kolekce vlastněné typy, ale (od verze EF Core 2.1, ale podporovaly v 2.2).</span><span class="sxs-lookup"><span data-stu-id="aa219-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="aa219-196">Žádná podpora pro volitelné (tedy s možnou hodnotou Null) vlastní typy, které jsou mapovány s vlastníkem ve stejné tabulce (například pomocí rozdělení tabulky).</span><span class="sxs-lookup"><span data-stu-id="aa219-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="aa219-197">Důvodem je, že mapování se provádí pro každou vlastnost, nemáme samostatné sentinel pro komplexní hodnota null jako celé.</span><span class="sxs-lookup"><span data-stu-id="aa219-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="aa219-198">Žádná podpora dědičnosti mapování pro vlastní typy, ale byste měli namapovat dva typy listu stejné hierarchie dědičnosti jako různé typy vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="aa219-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="aa219-199">EF Core nebude odůvodnitelný fakt, že jsou součástí stejné hierarchie.</span><span class="sxs-lookup"><span data-stu-id="aa219-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="aa219-200">Hlavní rozdíly s EF6 pro komplexní typy</span><span class="sxs-lookup"><span data-stu-id="aa219-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="aa219-201">Rozdělení tabulky je volitelné, to znamená, že je volitelně možné mapovat na samostatnou tabulku a nadále jeho vlastníkem typy.</span><span class="sxs-lookup"><span data-stu-id="aa219-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="aa219-202">Odkazují jiné entity (například jejich může fungovat jako závislé straně u relací na jiné typy než vlastnictví).</span><span class="sxs-lookup"><span data-stu-id="aa219-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="aa219-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="aa219-203">Additional resources</span></span>

- <span data-ttu-id="aa219-204">**Martina Fowlera. Vzor ValueObject** \\</span><span class="sxs-lookup"><span data-stu-id="aa219-204">**Martin Fowler. ValueObject pattern** \\</span></span>
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="aa219-205">**Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru.**</span><span class="sxs-lookup"><span data-stu-id="aa219-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="aa219-206">(Kniha; obsahuje diskusi hodnotu objektů) \\</span><span class="sxs-lookup"><span data-stu-id="aa219-206">(Book; includes a discussion of value objects) \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="aa219-207">**Vaughn Vernon. Implementace návrhu řízeného doménou.**</span><span class="sxs-lookup"><span data-stu-id="aa219-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="aa219-208">(Kniha; obsahuje diskusi hodnotu objektů) \\</span><span class="sxs-lookup"><span data-stu-id="aa219-208">(Book; includes a discussion of value objects) \\</span></span>
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="aa219-209">**Stínové vlastnosti** \\</span><span class="sxs-lookup"><span data-stu-id="aa219-209">**Shadow Properties** \\</span></span>
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="aa219-210">**Komplexní typy nebo hodnoty objekty**.</span><span class="sxs-lookup"><span data-stu-id="aa219-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="aa219-211">Diskuze v úložišti Githubu EF Core (stiskněte klávesu tab problémy) \\</span><span class="sxs-lookup"><span data-stu-id="aa219-211">Discussion in the EF Core GitHub repo (Issues tab) \\</span></span>
  <https://github.com/aspnet/EntityFramework/issues/246>

- <span data-ttu-id="aa219-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="aa219-212">**ValueObject.cs.**</span></span> <span data-ttu-id="aa219-213">Základní třída objektu hodnotu v eShopOnContainers.* * \\</span><span class="sxs-lookup"><span data-stu-id="aa219-213">Base value object class in eShopOnContainers.**  \\</span></span>
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="aa219-214">**Třída adresy**</span><span class="sxs-lookup"><span data-stu-id="aa219-214">**Address class.**</span></span> <span data-ttu-id="aa219-215">Ukázka hodnotová třída objektu v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="aa219-215">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="aa219-216">[Předchozí](seedwork-domain-model-base-classes-interfaces.md)
> [další](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="aa219-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
