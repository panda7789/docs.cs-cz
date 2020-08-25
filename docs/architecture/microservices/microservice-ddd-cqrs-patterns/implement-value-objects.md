---
title: Implementace objektů hodnot
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Získejte informace a možnosti pro implementaci objektů hodnot pomocí nových funkcí Entity Framework.
ms.date: 08/21/2020
ms.openlocfilehash: 02eed7baaa364c62aa2df599f1d8b0e700dd215f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811116"
---
# <a name="implement-value-objects"></a><span data-ttu-id="4f02a-103">Implementace objektů hodnot</span><span class="sxs-lookup"><span data-stu-id="4f02a-103">Implement value objects</span></span>

<span data-ttu-id="4f02a-104">Jak je popsáno výše v části informace o entitách a agregacích, je identita pro entity zásadní.</span><span class="sxs-lookup"><span data-stu-id="4f02a-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="4f02a-105">V systému je však mnoho objektů a datových položek, které nevyžadují sledování identity a identity, jako jsou například objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="4f02a-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="4f02a-106">Objekt hodnoty může odkazovat na jiné entity.</span><span class="sxs-lookup"><span data-stu-id="4f02a-106">A value object can reference other entities.</span></span> <span data-ttu-id="4f02a-107">Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do druhého, by tento postup představoval objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f02a-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="4f02a-108">Může to být snímek bodů na konkrétní trase, ale tato navrhovaná trasa by nemusela mít identitu, i když interně by se mohla vztahovat na entity jako City, Road atd.</span><span class="sxs-lookup"><span data-stu-id="4f02a-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="4f02a-109">Obrázek 7-13 ukazuje objekt hodnoty adresy v rámci agregace pořadí.</span><span class="sxs-lookup"><span data-stu-id="4f02a-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagram znázorňující hodnotu adresa – objekt uvnitř agregace objednávky](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="4f02a-111">**Obrázek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="4f02a-111">**Figure 7-13**.</span></span> <span data-ttu-id="4f02a-112">Hodnota objektu adresy v rámci agregace objednávky</span><span class="sxs-lookup"><span data-stu-id="4f02a-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="4f02a-113">Jak je znázorněno na obrázku 7-13, entita se obvykle skládá z více atributů.</span><span class="sxs-lookup"><span data-stu-id="4f02a-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="4f02a-114">`Order`Entita může být například modelována jako entita s identitou a složená interně ze sady atributů, jako je například ČísloObjednávky, DatumObjednávky, OrderItems atd. Ale adresa, která je prostě složitou hodnotu složenou ze země/oblasti, ulice, města atd. a nemá v této doméně žádnou identitu, musí být modelována a zpracována jako objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f02a-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="4f02a-115">Důležité vlastnosti objektů hodnot</span><span class="sxs-lookup"><span data-stu-id="4f02a-115">Important characteristics of value objects</span></span>

<span data-ttu-id="4f02a-116">Existují dvě hlavní vlastnosti pro objekty hodnot:</span><span class="sxs-lookup"><span data-stu-id="4f02a-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="4f02a-117">Nemají žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="4f02a-117">They have no identity.</span></span>

- <span data-ttu-id="4f02a-118">Jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="4f02a-118">They are immutable.</span></span>

<span data-ttu-id="4f02a-119">První charakterizace již byla diskutována.</span><span class="sxs-lookup"><span data-stu-id="4f02a-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="4f02a-120">Neměnnosti je důležitým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="4f02a-120">Immutability is an important requirement.</span></span> <span data-ttu-id="4f02a-121">Hodnoty objektu hodnoty musí být po vytvoření objektu neměnné.</span><span class="sxs-lookup"><span data-stu-id="4f02a-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="4f02a-122">Proto je-li objekt vytvořen, je nutné zadat požadované hodnoty, ale je nutné, aby se během životnosti objektu nepovolily měnit.</span><span class="sxs-lookup"><span data-stu-id="4f02a-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="4f02a-123">Objekty hodnot umožňují provádět určité štychy pro výkon, a to díky jejich neměnnému charakteru.</span><span class="sxs-lookup"><span data-stu-id="4f02a-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="4f02a-124">To je obzvláště pravdivé v systémech, kde může existovat tisíce instancí objektů hodnot, mnoho z nich má stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f02a-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="4f02a-125">Jejich neproměnlivá povaha umožňuje jejich použití znovu; můžou se jednat o objekty, které mají být zaměnitelné, protože jejich hodnoty jsou stejné a nemají žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="4f02a-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="4f02a-126">Tento typ optimalizace může někdy způsobit rozdíl mezi softwarem, který běží pomalu, a softwarem s dobrým výkonem.</span><span class="sxs-lookup"><span data-stu-id="4f02a-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="4f02a-127">Všechny tyto případy jsou samozřejmě závislé na prostředí aplikace a kontextu nasazení.</span><span class="sxs-lookup"><span data-stu-id="4f02a-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="4f02a-128">Implementace objektu hodnoty v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="4f02a-128">Value object implementation in C\#</span></span>

<span data-ttu-id="4f02a-129">V souvislosti s implementací můžete mít základní třídu objektu hodnoty, která má základní obslužné metody, jako je rovnost, na základě porovnání všech atributů (vzhledem k tomu, že objekt hodnoty nesmí být založen na identitě) a další základní charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="4f02a-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on the comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="4f02a-130">Následující příklad ukazuje základní třídu hodnotového objektu použitou při řazení mikroslužby z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4f02a-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    protected abstract IEnumerable<object> GetEqualityComponents();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        var other = (ValueObject)obj;

        return this.GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
            .Select(x => x != null ? x.GetHashCode() : 0)
            .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

<span data-ttu-id="4f02a-131">Tuto třídu můžete použít při implementaci vlastního objektu Value, stejně jako objekt hodnoty adresy zobrazený v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4f02a-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetEqualityComponents()
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

<span data-ttu-id="4f02a-132">Můžete zjistit, jak tato implementace objektu hodnoty nemá žádnou identitu, a proto žádné pole ID není ani na třídě Address ani na třídě ValueObject.</span><span class="sxs-lookup"><span data-stu-id="4f02a-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="4f02a-133">Neexistence pole ID ve třídě, která má být použita Entity Framework (EF), nebylo možné, dokud EF Core 2,0, což významně pomáhá implementovat lépe vícehodnotové objekty bez ID.</span><span class="sxs-lookup"><span data-stu-id="4f02a-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="4f02a-134">To je přesně vysvětlení další části.</span><span class="sxs-lookup"><span data-stu-id="4f02a-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="4f02a-135">Může být namítáno, že objekty hodnot, které jsou neměnné, by měly být jen pro čtení (to znamená, že mají vlastnosti jen pro získání) a které jsou skutečně pravdivé.</span><span class="sxs-lookup"><span data-stu-id="4f02a-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="4f02a-136">Objekty hodnot jsou však obvykle serializovány a deserializovány, aby procházely přes fronty zpráv a byly jen pro čtení, které zabrání deserializaci v přiřazení hodnot, takže je stačí jen pro to, aby bylo jen `private set` pro čtení praktické.</span><span class="sxs-lookup"><span data-stu-id="4f02a-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so you just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="4f02a-137">Jak zachovat objekty hodnot v databázi pomocí EF Core 2,0 a novějších</span><span class="sxs-lookup"><span data-stu-id="4f02a-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="4f02a-138">Právě jste viděli, jak v doménovém modelu definovat objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f02a-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="4f02a-139">Ale jak je můžete ve skutečnosti uchovávat v databázi pomocí Entity Framework Core, protože obvykle cílí na entity s identitou?</span><span class="sxs-lookup"><span data-stu-id="4f02a-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="4f02a-140">Pozadí a starší přístupy pomocí EF Core 1,1</span><span class="sxs-lookup"><span data-stu-id="4f02a-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="4f02a-141">Jako pozadí omezení při použití EF Core 1,0 a 1,1 bylo, že nemůžete použít [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) definované v EF 6. x v tradičním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f02a-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="4f02a-142">Proto pokud používáte EF Core 1,0 nebo 1,1, je třeba uložit objekt hodnoty jako entitu EF s polem ID.</span><span class="sxs-lookup"><span data-stu-id="4f02a-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="4f02a-143">Proto, aby vypadala podobně jako objekt hodnoty bez identity, mohli byste skrýt jeho ID, aby bylo jasné, že identita objektu value není v doménovém modelu důležitá.</span><span class="sxs-lookup"><span data-stu-id="4f02a-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="4f02a-144">Toto ID můžete skrýt pomocí ID jako [vlastnosti Shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="4f02a-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="4f02a-145">Vzhledem k tomu, že konfigurace pro skrývání ID v modelu je nastavená na úrovni infrastruktury EF, bude to pro váš doménový model transparentní.</span><span class="sxs-lookup"><span data-stu-id="4f02a-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="4f02a-146">V počáteční verzi eShopOnContainers (.NET Core 1,1) se skryté ID, které potřebuje infrastruktura EF Core, implementovalo následujícím způsobem na úrovni DbContext, pomocí rozhraní Fluent API v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="4f02a-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="4f02a-147">Z tohoto důvodu bylo ID z hlediska doménového modelu skryté, ale stále přítomné v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="4f02a-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="4f02a-148">Trvalost tohoto objektu Value do databáze se ale prováděla jako regulární entita v jiné tabulce.</span><span class="sxs-lookup"><span data-stu-id="4f02a-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="4f02a-149">V EF Core 2,0 a novějších existují nové a lepší způsoby, jak zachovat objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="4f02a-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="4f02a-150">Zachovat objekty hodnot jako vlastněné typy entit v EF Core 2,0 a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="4f02a-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="4f02a-151">I s některými mezerami mezi vzorem objektu kanonické hodnoty v DDD a vlastněnou entitou typu v EF Core je aktuálně nejlepším způsobem, jak zachovat objekty hodnot pomocí EF Core 2,0 a novějších.</span><span class="sxs-lookup"><span data-stu-id="4f02a-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="4f02a-152">Na konci této části můžete vidět omezení.</span><span class="sxs-lookup"><span data-stu-id="4f02a-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="4f02a-153">Do EF Core od verze 2,0 byla přidána funkce typu vlastněné entity.</span><span class="sxs-lookup"><span data-stu-id="4f02a-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="4f02a-154">Vlastněný typ entity umožňuje mapovat typy, které nemají vlastní identitu explicitně definované v doménovém modelu a jsou používány jako vlastnosti, jako je například objekt hodnoty, v rámci kterékoli z entit.</span><span class="sxs-lookup"><span data-stu-id="4f02a-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="4f02a-155">Vlastněný typ entity sdílí stejný typ CLR s jiným typem entity (to znamená pouze regulární třída).</span><span class="sxs-lookup"><span data-stu-id="4f02a-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="4f02a-156">Entita obsahující definici navigace je entitou vlastníka.</span><span class="sxs-lookup"><span data-stu-id="4f02a-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="4f02a-157">Při dotazování vlastníka jsou ve výchozím nastavení zahrnuty vlastní typy.</span><span class="sxs-lookup"><span data-stu-id="4f02a-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="4f02a-158">Podobně jako při prohlížení doménového modelu vypadá vlastněný typ, který nemá žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="4f02a-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="4f02a-159">Nicméně v rámci pokrývání mají vlastněné typy identitu, ale vlastnost navigace vlastníka je součástí této identity.</span><span class="sxs-lookup"><span data-stu-id="4f02a-159">However, under the covers, owned types do have the identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="4f02a-160">Identita instancí vlastněných typů není zcela vlastní.</span><span class="sxs-lookup"><span data-stu-id="4f02a-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="4f02a-161">Skládá se ze tří součástí:</span><span class="sxs-lookup"><span data-stu-id="4f02a-161">It consists of three components:</span></span>

- <span data-ttu-id="4f02a-162">Identita vlastníka</span><span class="sxs-lookup"><span data-stu-id="4f02a-162">The identity of the owner</span></span>

- <span data-ttu-id="4f02a-163">Navigační vlastnost, na kterou se odkazuje</span><span class="sxs-lookup"><span data-stu-id="4f02a-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="4f02a-164">V případě kolekcí vlastněných typů, nezávislé komponenty (podporované v EF Core 2,2 a novější).</span><span class="sxs-lookup"><span data-stu-id="4f02a-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="4f02a-165">Například v modelu domény řazení na eShopOnContainers jako součást entity Order je objekt hodnoty adresy implementován jako vlastněný typ entity v rámci entity Owner, která je objednávka.</span><span class="sxs-lookup"><span data-stu-id="4f02a-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="4f02a-166">`Address` je typ bez vlastnosti identity definované v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="4f02a-166">`Address` is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="4f02a-167">Slouží jako vlastnost typu objednávky k určení dodací adresy pro konkrétní objednávku.</span><span class="sxs-lookup"><span data-stu-id="4f02a-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="4f02a-168">Podle konvence se vytvoří stínový primární klíč pro vlastní typ a bude namapován na stejnou tabulku jako vlastník pomocí rozdělení tabulky.</span><span class="sxs-lookup"><span data-stu-id="4f02a-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="4f02a-169">To umožňuje použít vlastněné typy podobně jako složité typy používané v EF6 v tradičním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f02a-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="4f02a-170">Je důležité si uvědomit, že vlastní typy nejsou nikdy zjištěny v konvenci v EF Core, takže je musíte deklarovat explicitně.</span><span class="sxs-lookup"><span data-stu-id="4f02a-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="4f02a-171">V eShopOnContainers je v souboru OrderingContext.cs v rámci `OnModelCreating()` metody použito více konfigurací infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="4f02a-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="4f02a-172">Jedna z nich se vztahuje k entitě Order.</span><span class="sxs-lookup"><span data-stu-id="4f02a-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="4f02a-173">V následujícím kódu je pro entitu pro objednávku definována infrastruktura trvalosti:</span><span class="sxs-lookup"><span data-stu-id="4f02a-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="4f02a-174">V předchozím kódu `orderConfiguration.OwnsOne(o => o.Address)` Metoda určuje, že `Address` vlastnost je vlastněná entitou `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="4f02a-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="4f02a-175">Ve výchozím nastavení EF Core konvence pojmenují sloupce databáze pro vlastnosti typu vlastněné entity jako `EntityProperty_OwnedEntityProperty` .</span><span class="sxs-lookup"><span data-stu-id="4f02a-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="4f02a-176">Proto se vnitřní vlastnosti nástroje `Address` zobrazí v `Orders` tabulce s názvy `Address_Street` `Address_City` (a tak dále pro `State` , a `Country` `ZipCode` ).</span><span class="sxs-lookup"><span data-stu-id="4f02a-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="4f02a-177">`Property().HasColumnName()`K přejmenování těchto sloupců můžete připojit metodu Fluent.</span><span class="sxs-lookup"><span data-stu-id="4f02a-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="4f02a-178">V případě `Address` veřejné vlastnosti by mapování vypadalo takto:</span><span class="sxs-lookup"><span data-stu-id="4f02a-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="4f02a-179">Je možné řetězit `OwnsOne` metodu v mapování Fluent.</span><span class="sxs-lookup"><span data-stu-id="4f02a-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="4f02a-180">V následujícím hypotetickém příkladu `OrderDetails` vlastní `BillingAddress` a `ShippingAddress` , které jsou oba `Address` typy.</span><span class="sxs-lookup"><span data-stu-id="4f02a-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="4f02a-181">Pak `OrderDetails` vlastní `Order` typ.</span><span class="sxs-lookup"><span data-stu-id="4f02a-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="4f02a-182">Další podrobnosti o vlastněných typech entit</span><span class="sxs-lookup"><span data-stu-id="4f02a-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="4f02a-183">Vlastněné typy jsou definovány při konfiguraci navigační vlastnosti na konkrétní typ pomocí rozhraní OwnsOne Fluent API.</span><span class="sxs-lookup"><span data-stu-id="4f02a-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="4f02a-184">Definice vlastněného typu v našem modelu metadat je složená z: typ vlastníka, navigační vlastnost a typ CLR vlastněných typů.</span><span class="sxs-lookup"><span data-stu-id="4f02a-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="4f02a-185">Identita (klíč) instance vlastního typu v našem zásobníku je složena z identity typu vlastníka a definice vlastněného typu.</span><span class="sxs-lookup"><span data-stu-id="4f02a-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="4f02a-186">Možnosti vlastněných entit</span><span class="sxs-lookup"><span data-stu-id="4f02a-186">Owned entities capabilities</span></span>

- <span data-ttu-id="4f02a-187">Vlastněné typy mohou odkazovat na jiné entity, buď vlastněné (vnořené vlastněné typy), nebo nevlastní (standardní referenční vlastnosti navigace jiným entitám).</span><span class="sxs-lookup"><span data-stu-id="4f02a-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="4f02a-188">Stejný typ CLR můžete mapovat jako jiné vlastněné typy ve stejné entitě Owner prostřednictvím samostatných vlastností navigace.</span><span class="sxs-lookup"><span data-stu-id="4f02a-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="4f02a-189">Rozdělení tabulky se nastavuje podle konvence, ale můžete si ji vyfiltrovat tak, že namapujete vlastněný typ na jinou tabulku pomocí ToTable.</span><span class="sxs-lookup"><span data-stu-id="4f02a-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="4f02a-190">Načítání Eager se provádí automaticky na vlastněných typech, to znamená, že není nutné volat `.Include()` dotaz.</span><span class="sxs-lookup"><span data-stu-id="4f02a-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="4f02a-191">Lze nakonfigurovat s atributem `[Owned]` pomocí EF Core 2,1 a novějším.</span><span class="sxs-lookup"><span data-stu-id="4f02a-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="4f02a-192">Může zpracovávat kolekce vlastněných typů (pomocí verze 2,2 a novější).</span><span class="sxs-lookup"><span data-stu-id="4f02a-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="4f02a-193">Omezení entit vlastněných společností</span><span class="sxs-lookup"><span data-stu-id="4f02a-193">Owned entities limitations</span></span>

- <span data-ttu-id="4f02a-194">Nemůžete vytvořit `DbSet<T>` vlastní typ (podle návrhu).</span><span class="sxs-lookup"><span data-stu-id="4f02a-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="4f02a-195">Nemůžete volat `ModelBuilder.Entity<T>()` na vlastněné typy (aktuálně podle návrhu).</span><span class="sxs-lookup"><span data-stu-id="4f02a-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="4f02a-196">Není podporována podpora volitelného typu (to znamená Nullable), který je namapován s vlastníkem ve stejné tabulce (tj. pomocí rozdělení tabulky).</span><span class="sxs-lookup"><span data-stu-id="4f02a-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="4f02a-197">Důvodem je to, že mapování je provedeno pro každou vlastnost, neexistuje žádná samostatná ověřovací hodnota pro hodnotu null Complex jako celek.</span><span class="sxs-lookup"><span data-stu-id="4f02a-197">This is because mapping is done for each property, there is no  separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="4f02a-198">Žádná podpora mapování dědění pro vlastní typy, ale měli byste být schopni mapovat dva typy listů stejných hierarchií dědičnosti jako jiné vlastněné typy.</span><span class="sxs-lookup"><span data-stu-id="4f02a-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="4f02a-199">EF Core nebude mít důvod k tomu, že jsou součástí stejné hierarchie.</span><span class="sxs-lookup"><span data-stu-id="4f02a-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="4f02a-200">Hlavní rozdíly s EF6's komplexními typy</span><span class="sxs-lookup"><span data-stu-id="4f02a-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="4f02a-201">Rozdělení tabulky je volitelné, to znamená, že mohou být případně mapovány na samostatnou tabulku a stále mají vlastní typy.</span><span class="sxs-lookup"><span data-stu-id="4f02a-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="4f02a-202">Můžou odkazovat na jiné entity (to znamená, že můžou fungovat jako závislá strana na vztazích s jinými nevlastními typy).</span><span class="sxs-lookup"><span data-stu-id="4f02a-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4f02a-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="4f02a-203">Additional resources</span></span>

- <span data-ttu-id="4f02a-204">**Martin Fowlera. Vzor ValueObject** </span><span class="sxs-lookup"><span data-stu-id="4f02a-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="4f02a-205">**Eric Evans. Návrh založený na doméně: řešení složitosti na srdce softwaru.**</span><span class="sxs-lookup"><span data-stu-id="4f02a-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="4f02a-206">(Kniha; obsahuje diskuzi o objektech hodnot) </span><span class="sxs-lookup"><span data-stu-id="4f02a-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="4f02a-207">**Vaughn Vernon. Implementace návrhu založeného na doméně.**</span><span class="sxs-lookup"><span data-stu-id="4f02a-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="4f02a-208">(Kniha; obsahuje diskuzi o objektech hodnot) </span><span class="sxs-lookup"><span data-stu-id="4f02a-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="4f02a-209">**Vlastněné typy entit** </span><span class="sxs-lookup"><span data-stu-id="4f02a-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="4f02a-210">**Vlastnosti stínu** </span><span class="sxs-lookup"><span data-stu-id="4f02a-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="4f02a-211">**Komplexní typy a/nebo hodnotové objekty**.</span><span class="sxs-lookup"><span data-stu-id="4f02a-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="4f02a-212">Diskuze v úložišti GitHubu EF Core (karta problémy) </span><span class="sxs-lookup"><span data-stu-id="4f02a-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="4f02a-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="4f02a-213">**ValueObject.cs.**</span></span> <span data-ttu-id="4f02a-214">Třída objektů základní hodnoty v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="4f02a-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="4f02a-215">**Adresa třídy.**</span><span class="sxs-lookup"><span data-stu-id="4f02a-215">**Address class.**</span></span> <span data-ttu-id="4f02a-216">Ukázková hodnota třídy objektu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4f02a-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="4f02a-217">[Předchozí](seedwork-domain-model-base-classes-interfaces.md) 
>  [Další](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="4f02a-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
