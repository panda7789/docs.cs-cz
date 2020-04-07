---
title: Implementace objektů hodnot
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Získejte do podrobností a možností implementovat objekty hodnoty pomocí nových funkcí entity framework.
ms.date: 01/30/2020
ms.openlocfilehash: 4a8a92a8dabcf09654ecd0e5dea2a7df25d7abf7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805734"
---
# <a name="implement-value-objects"></a><span data-ttu-id="55912-103">Implementace hodnotových objektů</span><span class="sxs-lookup"><span data-stu-id="55912-103">Implement value objects</span></span>

<span data-ttu-id="55912-104">Jak je popsáno v předchozích částech o entitách a agregaci, identita je zásadní pro entity.</span><span class="sxs-lookup"><span data-stu-id="55912-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="55912-105">Existuje však mnoho objektů a datových položek v systému, které nevyžadují sledování identity a identity, jako jsou například objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="55912-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="55912-106">Objekt hodnoty může odkazovat na jiné entity.</span><span class="sxs-lookup"><span data-stu-id="55912-106">A value object can reference other entities.</span></span> <span data-ttu-id="55912-107">Například v aplikaci, která generuje trasu, která popisuje, jak se dostat z jednoho bodu do druhého, by tato trasa byla hodnotovým objektem.</span><span class="sxs-lookup"><span data-stu-id="55912-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="55912-108">Jednalo by se o snímek bodů na konkrétní trase, ale tato navrhovaná trasa by neměla identitu, i když interně by se mohla vztahovat na subjekty, jako je Město, Silnice atd.</span><span class="sxs-lookup"><span data-stu-id="55912-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="55912-109">Obrázek 7-13 znázorňuje objekt hodnoty Adresa v rámci agregace Pořadí.</span><span class="sxs-lookup"><span data-stu-id="55912-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagram znázorňující hodnotu adresy-objekt uvnitř agregace pořadí.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="55912-111">**Obrázek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="55912-111">**Figure 7-13**.</span></span> <span data-ttu-id="55912-112">Objekt hodnoty adresy v rámci agregace Objednávka</span><span class="sxs-lookup"><span data-stu-id="55912-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="55912-113">Jak je znázorněno na obrázku 7-13, entita se obvykle skládá z více atributů.</span><span class="sxs-lookup"><span data-stu-id="55912-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="55912-114">Entita `Order` může být například modelována jako entita s identitou a tvořena interně sadou atributů, jako je OrderId, OrderDate, OrderItems atd. Ale adresa, která je jednoduše komplexní hodnota složená z země nebo oblasti, ulice, města atd.</span><span class="sxs-lookup"><span data-stu-id="55912-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="55912-115">Důležité vlastnosti hodnotových objektů</span><span class="sxs-lookup"><span data-stu-id="55912-115">Important characteristics of value objects</span></span>

<span data-ttu-id="55912-116">Existují dvě hlavní charakteristiky pro hodnotové objekty:</span><span class="sxs-lookup"><span data-stu-id="55912-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="55912-117">Nemají žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="55912-117">They have no identity.</span></span>

- <span data-ttu-id="55912-118">Jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="55912-118">They are immutable.</span></span>

<span data-ttu-id="55912-119">První charakteristika byla již diskutována.</span><span class="sxs-lookup"><span data-stu-id="55912-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="55912-120">Neměnnost je důležitým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="55912-120">Immutability is an important requirement.</span></span> <span data-ttu-id="55912-121">Hodnoty objektu hodnoty musí být neměnné, jakmile je objekt vytvořen.</span><span class="sxs-lookup"><span data-stu-id="55912-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="55912-122">Proto při vytvoření objektu je nutné zadat požadované hodnoty, ale nesmíte povolit jejich změny během životnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="55912-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="55912-123">Hodnotové objekty vám umožní provádět určité triky pro výkon, díky své neměnné povaze.</span><span class="sxs-lookup"><span data-stu-id="55912-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="55912-124">To platí zejména v systémech, kde mohou existovat tisíce instancí objektu hodnoty, z nichž mnohé mají stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="55912-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="55912-125">Jejich neměnná povaha umožňuje jejich opětovné použití; mohou být zaměnitelné objekty, protože jejich hodnoty jsou stejné a nemají žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="55912-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="55912-126">Tento typ optimalizace může někdy dělat rozdíl mezi softwarem, který běží pomalu a software s dobrým výkonem.</span><span class="sxs-lookup"><span data-stu-id="55912-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="55912-127">Samozřejmě všechny tyto případy závisí na prostředí aplikace a kontextu nasazení.</span><span class="sxs-lookup"><span data-stu-id="55912-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="55912-128">Implementace objektu hodnoty v C\#</span><span class="sxs-lookup"><span data-stu-id="55912-128">Value object implementation in C\#</span></span>

<span data-ttu-id="55912-129">Pokud jde o implementaci, můžete mít základní třídu objektu hodnoty, která má základní metody nástroje, jako je rovnost, na základě porovnání mezi všemi atributy (protože objekt hodnoty nesmí být založen na identitě) a dalšízákladní charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="55912-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="55912-130">Následující příklad ukazuje základní třídu objektu hodnoty použitou v objednávání mikroslužby z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="55912-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="55912-131">Tuto třídu můžete použít při implementaci objektu skutečné hodnoty, stejně jako u objektu hodnoty Adresa zobrazeném v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="55912-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="55912-132">Můžete vidět, jak tato implementace objektu hodnoty Address nemá žádnou identitu a proto žádné pole ID, ani na Address třídy ani na ValueObject třídy.</span><span class="sxs-lookup"><span data-stu-id="55912-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="55912-133">Bez ID pole ve třídě, které mají být použity entity Framework (EF) nebylo možné až EF Core 2.0, což výrazně pomáhá implementovat lepší hodnotu objekty bez ID.</span><span class="sxs-lookup"><span data-stu-id="55912-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="55912-134">To je přesně vysvětlení další části.</span><span class="sxs-lookup"><span data-stu-id="55912-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="55912-135">To by mohlo být argumentoval, že hodnota objekty, je neměnný, by měl být jen pro čtení (to znamená, že mají vlastnosti pouze pro získání), a to je opravdu pravda.</span><span class="sxs-lookup"><span data-stu-id="55912-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="55912-136">Však hodnoty objekty jsou obvykle serializovány a rekonstruovat projít fronty zpráv a je jen pro čtení zastaví deserializer z přiřazení hodnot, takže jsme jen tak nechat jako `private set`, což je jen pro čtení dost být praktické.</span><span class="sxs-lookup"><span data-stu-id="55912-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="55912-137">Jak zachovat hodnotové objekty v databázi s EF Core 2.0 a novější</span><span class="sxs-lookup"><span data-stu-id="55912-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="55912-138">Právě jste viděli, jak definovat objekt hodnoty v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="55912-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="55912-139">Ale jak můžete skutečně zachovat do databáze pomocí entity framework core, protože obvykle cílí na entity s identitou?</span><span class="sxs-lookup"><span data-stu-id="55912-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="55912-140">Souvislosti a starší přístupy využívající EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="55912-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="55912-141">Jako pozadí omezení při použití EF Core 1.0 a 1.1 bylo, že nelze použít [složité typy,](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) jak je definováno v EF 6.x v tradiční rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55912-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="55912-142">Proto pokud používáte EF Core 1.0 nebo 1.1, je třeba uložit objekt hodnoty jako entitu EF s polem ID.</span><span class="sxs-lookup"><span data-stu-id="55912-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="55912-143">Pak, takže to vypadalo spíše jako objekt hodnoty bez identity, můžete skrýt jeho ID, takže si můžete jasně, že identita objektu hodnoty není důležité v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="55912-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="55912-144">Toto ID můžete skrýt pomocí ID jako [vlastnosti stín](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="55912-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="55912-145">Vzhledem k tomu, že konfigurace pro skrytí ID v modelu je nastavena na úrovni infrastruktury EF, by bylo trochu transparentní pro model domény.</span><span class="sxs-lookup"><span data-stu-id="55912-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="55912-146">V počáteční verzi eShopOnContainers (.NET Core 1.1) skryté ID potřebné infrastruktury EF Core bylo implementováno následujícím způsobem na úrovni DbContext pomocí fluent api v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="55912-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="55912-147">Proto ID byla skryta z hlediska modelu domény, ale stále k dispozici v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="55912-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="55912-148">Trvalost tohoto objektu hodnoty do databáze však byla provedena jako normální entita v jiné tabulce.</span><span class="sxs-lookup"><span data-stu-id="55912-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="55912-149">S EF Core 2.0 a novější, existují nové a lepší způsoby, jak zachovat hodnoty objektů.</span><span class="sxs-lookup"><span data-stu-id="55912-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="55912-150">Zachovat objekty hodnoty jako typy vlastněných entit v EF Core 2.0 a novějším</span><span class="sxs-lookup"><span data-stu-id="55912-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="55912-151">I s některými mezerami mezi vzorem objektu kanonické hodnoty v DDD a typem vlastněné entity v EF Core je aktuálně nejlepším způsobem, jak zachovat hodnotové objekty s EF Core 2.0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="55912-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="55912-152">Omezení naleznete na konci této části.</span><span class="sxs-lookup"><span data-stu-id="55912-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="55912-153">Funkce typu vlastněné entity byla přidána do EF Core od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="55912-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="55912-154">Typ vlastní entity umožňuje mapovat typy, které nemají vlastní identitu explicitně definovanou v modelu domény a používají se jako vlastnosti, jako je například objekt hodnoty, v rámci libovolné entity.</span><span class="sxs-lookup"><span data-stu-id="55912-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="55912-155">Vlastněný typ entity sdílí stejný typ CLR s jiným typem entity (to znamená, že je to pouze běžná třída).</span><span class="sxs-lookup"><span data-stu-id="55912-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="55912-156">Entita obsahující definující navigaci je entita vlastníka.</span><span class="sxs-lookup"><span data-stu-id="55912-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="55912-157">Při dotazování vlastníka jsou ve výchozím nastavení zahrnuty vlastněné typy.</span><span class="sxs-lookup"><span data-stu-id="55912-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="55912-158">Jen při pohledu na model domény, vlastněný typ vypadá, že nemá žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="55912-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="55912-159">Však pod kryty, vlastněné typy mají identitu, ale vlastnost navigace vlastníka je součástí této identity.</span><span class="sxs-lookup"><span data-stu-id="55912-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="55912-160">Identita instancí vlastněných typů není zcela vlastní.</span><span class="sxs-lookup"><span data-stu-id="55912-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="55912-161">Skládá se ze tří složek:</span><span class="sxs-lookup"><span data-stu-id="55912-161">It consists of three components:</span></span>

- <span data-ttu-id="55912-162">Totožnost vlastníka</span><span class="sxs-lookup"><span data-stu-id="55912-162">The identity of the owner</span></span>

- <span data-ttu-id="55912-163">Vlastnost navigace směřující k nim</span><span class="sxs-lookup"><span data-stu-id="55912-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="55912-164">V případě kolekcí vlastněných typů, nezávislá komponenta (podporována v EF Core 2.2 a novější).</span><span class="sxs-lookup"><span data-stu-id="55912-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="55912-165">Například v modelu objednávací domény v eShopOnContainers jako součást entity Order je objekt hodnoty Adresa implementován jako typ vlastněné entity v rámci entity vlastníka, což je entita Objednávka.</span><span class="sxs-lookup"><span data-stu-id="55912-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="55912-166">Adresa je typ bez vlastnosti identity definované v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="55912-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="55912-167">Používá se jako vlastnost typu Objednávka k určení dodací adresy pro konkrétní objednávku.</span><span class="sxs-lookup"><span data-stu-id="55912-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="55912-168">Podle konvence je vytvořen stínový primární klíč pro vlastněný typ a bude mapován na stejnou tabulku jako vlastník pomocí rozdělení tabulky.</span><span class="sxs-lookup"><span data-stu-id="55912-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="55912-169">To umožňuje použít vlastněné typy podobně jako složité typy se používají v EF6 v tradiční rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55912-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="55912-170">Je důležité si uvědomit, že vlastněné typy nejsou nikdy zjištěny podle konvence v EF Core, takže je nutné deklarovat explicitně.</span><span class="sxs-lookup"><span data-stu-id="55912-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="55912-171">V eShopOnContainers, v souboru `OnModelCreating()` OrderingContext.cs v rámci metody, jsou použity více konfigurací infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="55912-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="55912-172">Jeden z nich souvisí s entitou Objednávka.</span><span class="sxs-lookup"><span data-stu-id="55912-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="55912-173">V následujícím kódu je pro entitu Objednávka definována infrastruktura trvalosti:</span><span class="sxs-lookup"><span data-stu-id="55912-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="55912-174">V předchozím kódu `orderConfiguration.OwnsOne(o => o.Address)` metoda určuje, `Address` že vlastnost je vlastněnou entitou `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="55912-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="55912-175">Ve výchozím nastavení ef základní konvence název sloupce databáze pro `EntityProperty_OwnedEntityProperty`vlastnosti typu vlastní entity jako .</span><span class="sxs-lookup"><span data-stu-id="55912-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="55912-176">`Address` Proto se v `Orders` tabulce s názvy `Address_Street` `Address_City` (a tak dále `State`pro `Country`, `ZipCode`a ).</span><span class="sxs-lookup"><span data-stu-id="55912-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="55912-177">Můžete připojit plynulou metodu `Property().HasColumnName()` přejmenovat tyto sloupce.</span><span class="sxs-lookup"><span data-stu-id="55912-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="55912-178">V případě, `Address` kdy je veřejná vlastnost, mapování by bylo následující:</span><span class="sxs-lookup"><span data-stu-id="55912-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="55912-179">Je možné zřetězit `OwnsOne` metodu plynulým mapováním.</span><span class="sxs-lookup"><span data-stu-id="55912-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="55912-180">V následujícím `OrderDetails` hypotetickém `BillingAddress` příkladu vlastní `ShippingAddress` `Address` a , které jsou oba typy.</span><span class="sxs-lookup"><span data-stu-id="55912-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="55912-181">Potom `OrderDetails` je vlastněn typem. `Order`</span><span class="sxs-lookup"><span data-stu-id="55912-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="55912-182">Další podrobnosti o typech vlastněných entit</span><span class="sxs-lookup"><span data-stu-id="55912-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="55912-183">Vlastní typy jsou definovány při konfiguraci navigační vlastnost i pro určitý typ pomocí OwnsOne fluent API.</span><span class="sxs-lookup"><span data-stu-id="55912-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="55912-184">Definice vlastněného typu v našem modelu metadat je složena z: typ vlastníka, navigační vlastnost a typ CLR vlastněného typu.</span><span class="sxs-lookup"><span data-stu-id="55912-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="55912-185">Identita (klíč) instance vlastněného typu v našem zásobníku je složený z identity typu vlastníka a definice vlastněného typu.</span><span class="sxs-lookup"><span data-stu-id="55912-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="55912-186">Možnosti vlastněných entit</span><span class="sxs-lookup"><span data-stu-id="55912-186">Owned entities capabilities</span></span>

- <span data-ttu-id="55912-187">Vlastněné typy mohou odkazovat na jiné entity, buď vlastněné (vnořené vlastněné typy) nebo nevlastněné (vlastnosti navigace s pravidelným odkazem na jiné entity).</span><span class="sxs-lookup"><span data-stu-id="55912-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="55912-188">Můžete mapovat stejný typ CLR jako různé vlastněné typy ve stejné entitě vlastníka prostřednictvím samostatných navigačních vlastností.</span><span class="sxs-lookup"><span data-stu-id="55912-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="55912-189">Rozdělení tabulky je nastaveno podle konvence, ale můžete se odhlásit mapováním vlastněného typu na jinou tabulku pomocí ToTable.</span><span class="sxs-lookup"><span data-stu-id="55912-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="55912-190">Eager načítání se provádí automaticky na vlastněné typy, to `.Include()` znamená, že není nutné volat na dotaz.</span><span class="sxs-lookup"><span data-stu-id="55912-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="55912-191">Lze konfigurovat s `[Owned]`atributem , pomocí EF Core 2.1 a novější.</span><span class="sxs-lookup"><span data-stu-id="55912-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="55912-192">Zvládne kolekce vlastněných typů (pomocí verze 2.2 a novější).</span><span class="sxs-lookup"><span data-stu-id="55912-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="55912-193">Omezení vlastněných subjektů</span><span class="sxs-lookup"><span data-stu-id="55912-193">Owned entities limitations</span></span>

- <span data-ttu-id="55912-194">Nelze vytvořit `DbSet<T>` typ vlastněného (záměrně).</span><span class="sxs-lookup"><span data-stu-id="55912-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="55912-195">Nelze volat `ModelBuilder.Entity<T>()` na vlastněné typy (aktuálně záměrné).</span><span class="sxs-lookup"><span data-stu-id="55912-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="55912-196">Žádná podpora pro volitelné (to znamená, nullable) vlastněné typy, které jsou mapovány s vlastníkem ve stejné tabulce (to znamená pomocí rozdělení tabulky).</span><span class="sxs-lookup"><span data-stu-id="55912-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="55912-197">Důvodem je, že mapování se provádí pro každou vlastnost, nemáme samostatný sentinel pro komplexní hodnotu null jako celek.</span><span class="sxs-lookup"><span data-stu-id="55912-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="55912-198">Žádná podpora mapování dědičnosti pro vlastněné typy, ale měli byste být schopni mapovat dva typy listů stejné hierarchie dědičnosti jako různé vlastněné typy.</span><span class="sxs-lookup"><span data-stu-id="55912-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="55912-199">EF Core nebude důvod o tom, že jsou součástí stejné hierarchie.</span><span class="sxs-lookup"><span data-stu-id="55912-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="55912-200">Hlavní rozdíly s komplexními typy EF6</span><span class="sxs-lookup"><span data-stu-id="55912-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="55912-201">Rozdělení tabulky je volitelné, to znamená, že mohou být volitelně mapovány na samostatnou tabulku a stále vlastněné typy.</span><span class="sxs-lookup"><span data-stu-id="55912-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="55912-202">Mohou odkazovat na jiné entity (to znamená, že mohou působit jako závislá strana na vztazích s jinými nevlastněnými typy).</span><span class="sxs-lookup"><span data-stu-id="55912-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="55912-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="55912-203">Additional resources</span></span>

- <span data-ttu-id="55912-204">**Martin Fowler. Vzor ValueObject** </span><span class="sxs-lookup"><span data-stu-id="55912-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="55912-205">**Eric Evans. Návrh řízený doménou: Řešení složitosti v srdci softwaru.**</span><span class="sxs-lookup"><span data-stu-id="55912-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="55912-206">(Kniha; obsahuje diskusi o hodnotových objektech) </span><span class="sxs-lookup"><span data-stu-id="55912-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="55912-207">**Vaughn Vernon, to je můj zástupce. Implementace návrhu řízeného doménou.**</span><span class="sxs-lookup"><span data-stu-id="55912-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="55912-208">(Kniha; obsahuje diskusi o hodnotových objektech) </span><span class="sxs-lookup"><span data-stu-id="55912-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="55912-209">**Typy vlastněných entit** </span><span class="sxs-lookup"><span data-stu-id="55912-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="55912-210">**Vlastnosti stínu** </span><span class="sxs-lookup"><span data-stu-id="55912-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="55912-211">**Komplexní typy a/nebo hodnotové objekty**.</span><span class="sxs-lookup"><span data-stu-id="55912-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="55912-212">Diskuse v úložišti EF Core GitHub (karta Problémy) </span><span class="sxs-lookup"><span data-stu-id="55912-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="55912-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="55912-213">**ValueObject.cs.**</span></span> <span data-ttu-id="55912-214">Třída objektu základní hodnoty v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="55912-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="55912-215">**Třída adres.**</span><span class="sxs-lookup"><span data-stu-id="55912-215">**Address class.**</span></span> <span data-ttu-id="55912-216">Ukázková třída objektu hodnoty v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="55912-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="55912-217">[Předchozí](seedwork-domain-model-base-classes-interfaces.md)
> [další](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="55912-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
