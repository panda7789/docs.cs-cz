---
title: Implementace objektů hodnot
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Získejte informace a možnosti pro implementaci objektů hodnot pomocí nových funkcí Entity Framework.
ms.date: 10/08/2018
ms.openlocfilehash: 70c92fe86fda20ed4e909b945b843e8e71092f09
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899778"
---
# <a name="implement-value-objects"></a><span data-ttu-id="86cdc-103">Implementace objektů hodnot</span><span class="sxs-lookup"><span data-stu-id="86cdc-103">Implement value objects</span></span>

<span data-ttu-id="86cdc-104">Jak je popsáno výše v části informace o entitách a agregacích, je identita pro entity zásadní.</span><span class="sxs-lookup"><span data-stu-id="86cdc-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="86cdc-105">V systému je však mnoho objektů a datových položek, které nevyžadují sledování identity a identity, jako jsou například objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="86cdc-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="86cdc-106">Objekt hodnoty může odkazovat na jiné entity.</span><span class="sxs-lookup"><span data-stu-id="86cdc-106">A value object can reference other entities.</span></span> <span data-ttu-id="86cdc-107">Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do druhého, by tento postup představoval objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="86cdc-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="86cdc-108">Může to být snímek bodů na konkrétní trase, ale tato navrhovaná trasa by nemusela mít identitu, i když interně by se mohla vztahovat na entity jako City, Road atd.</span><span class="sxs-lookup"><span data-stu-id="86cdc-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="86cdc-109">Obrázek 7-13 ukazuje objekt hodnoty adresy v rámci agregace pořadí.</span><span class="sxs-lookup"><span data-stu-id="86cdc-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagram znázorňující hodnotu adresa – objekt uvnitř agregace objednávky](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="86cdc-111">**Obrázek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="86cdc-111">**Figure 7-13**.</span></span> <span data-ttu-id="86cdc-112">Hodnota objektu adresy v rámci agregace objednávky</span><span class="sxs-lookup"><span data-stu-id="86cdc-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="86cdc-113">Jak je znázorněno na obrázku 7-13, entita se obvykle skládá z více atributů.</span><span class="sxs-lookup"><span data-stu-id="86cdc-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="86cdc-114">Například entita `Order` může být modelována jako entita s identitou a složená interně ze sady atributů, jako je například ČísloObjednávky, DatumObjednávky, OrderItems atd. Ale adresa, která je prostě složitou hodnotu složenou ze země/oblasti, ulice, města atd. a nemá v této doméně žádnou identitu, musí být modelována a zpracována jako objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="86cdc-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="86cdc-115">Důležité vlastnosti objektů hodnot</span><span class="sxs-lookup"><span data-stu-id="86cdc-115">Important characteristics of value objects</span></span>

<span data-ttu-id="86cdc-116">Existují dvě hlavní vlastnosti pro objekty hodnot:</span><span class="sxs-lookup"><span data-stu-id="86cdc-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="86cdc-117">Nemají žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="86cdc-117">They have no identity.</span></span>

- <span data-ttu-id="86cdc-118">Jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="86cdc-118">They are immutable.</span></span>

<span data-ttu-id="86cdc-119">První charakterizace již byla diskutována.</span><span class="sxs-lookup"><span data-stu-id="86cdc-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="86cdc-120">Neměnnosti je důležitým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="86cdc-120">Immutability is an important requirement.</span></span> <span data-ttu-id="86cdc-121">Hodnoty objektu hodnoty musí být po vytvoření objektu neměnné.</span><span class="sxs-lookup"><span data-stu-id="86cdc-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="86cdc-122">Proto je-li objekt vytvořen, je nutné zadat požadované hodnoty, ale je nutné, aby se během životnosti objektu nepovolily měnit.</span><span class="sxs-lookup"><span data-stu-id="86cdc-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="86cdc-123">Objekty hodnot umožňují provádět určité štychy pro výkon, a to díky jejich neměnnému charakteru.</span><span class="sxs-lookup"><span data-stu-id="86cdc-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="86cdc-124">To je obzvláště pravdivé v systémech, kde může existovat tisíce instancí objektů hodnot, mnoho z nich má stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="86cdc-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="86cdc-125">Jejich neproměnlivá povaha umožňuje jejich použití znovu; můžou se jednat o objekty, které mají být zaměnitelné, protože jejich hodnoty jsou stejné a nemají žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="86cdc-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="86cdc-126">Tento typ optimalizace může někdy způsobit rozdíl mezi softwarem, který běží pomalu, a softwarem s dobrým výkonem.</span><span class="sxs-lookup"><span data-stu-id="86cdc-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="86cdc-127">Všechny tyto případy jsou samozřejmě závislé na prostředí aplikace a kontextu nasazení.</span><span class="sxs-lookup"><span data-stu-id="86cdc-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="86cdc-128">Implementace objektu hodnoty v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="86cdc-128">Value object implementation in C\#</span></span>

<span data-ttu-id="86cdc-129">V souvislosti s implementací můžete mít základní třídu objektu hodnoty, která má základní obslužné metody, jako je rovnost na základě porovnání všech atributů (vzhledem k tomu, že objekt hodnoty nesmí být založen na identitě) a další základní charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="86cdc-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="86cdc-130">Následující příklad ukazuje základní třídu hodnotového objektu použitou při řazení mikroslužby z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="86cdc-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="86cdc-131">Tuto třídu můžete použít při implementaci vlastního objektu Value, stejně jako objekt hodnoty adresy zobrazený v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="86cdc-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="86cdc-132">Můžete zjistit, jak tato implementace objektu hodnoty nemá žádnou identitu, a proto žádné pole ID není ani na třídě Address ani na třídě ValueObject.</span><span class="sxs-lookup"><span data-stu-id="86cdc-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="86cdc-133">Neexistence pole ID ve třídě, která má být použita Entity Framework nebyla možná, dokud EF Core 2,0, což významně pomáhá implementovat lépe vícehodnotové objekty bez ID.</span><span class="sxs-lookup"><span data-stu-id="86cdc-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="86cdc-134">To je přesně vysvětlení další části.</span><span class="sxs-lookup"><span data-stu-id="86cdc-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="86cdc-135">Může být namítáno, že objekty hodnot, které jsou neměnné, by měly být jen pro čtení (tj. vlastnosti jen pro získání), a to vlastně pravdivé.</span><span class="sxs-lookup"><span data-stu-id="86cdc-135">It could be argued that value objects, being immutable, should be read-only (i.e. get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="86cdc-136">Objekty hodnot se ale obvykle serializovat a deserializovat, aby procházely přes fronty zpráv a jen pro čtení zastaví deserializaci, aby bylo možné přiřadit hodnoty, takže je pouze máme soukromá sada, která je dostatečně čitelná, aby mohla být praktická.</span><span class="sxs-lookup"><span data-stu-id="86cdc-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="86cdc-137">Jak zachovat objekty hodnot v databázi pomocí EF Core 2,0</span><span class="sxs-lookup"><span data-stu-id="86cdc-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="86cdc-138">Právě jste viděli, jak v doménovém modelu definovat objekt hodnoty.</span><span class="sxs-lookup"><span data-stu-id="86cdc-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="86cdc-139">Ale jak můžete ve skutečnosti uchovávat v databázi prostřednictvím jádra Entity Framework (EF), která obvykle cílí na entity s identitou?</span><span class="sxs-lookup"><span data-stu-id="86cdc-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="86cdc-140">Pozadí a starší přístupy pomocí EF Core 1,1</span><span class="sxs-lookup"><span data-stu-id="86cdc-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="86cdc-141">Jako pozadí omezení při použití EF Core 1,0 a 1,1 bylo, že nemůžete použít [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) definované v EF 6. x v tradičním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86cdc-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="86cdc-142">Proto pokud používáte EF Core 1,0 nebo 1,1, je třeba uložit objekt hodnoty jako entitu EF s polem ID.</span><span class="sxs-lookup"><span data-stu-id="86cdc-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="86cdc-143">Proto, aby vypadala podobně jako objekt hodnoty bez identity, mohli byste skrýt jeho ID, aby bylo jasné, že identita objektu value není v doménovém modelu důležitá.</span><span class="sxs-lookup"><span data-stu-id="86cdc-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="86cdc-144">Toto ID můžete skrýt pomocí ID jako [vlastnosti Shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="86cdc-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="86cdc-145">Vzhledem k tomu, že konfigurace pro skrývání ID v modelu je nastavená na úrovni infrastruktury EF, bude to pro váš doménový model transparentní.</span><span class="sxs-lookup"><span data-stu-id="86cdc-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="86cdc-146">V počáteční verzi eShopOnContainers (.NET Core 1,1) se skryté ID, které potřebuje infrastruktura EF Core, implementovalo následujícím způsobem na úrovni DbContext, pomocí rozhraní Fluent API v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="86cdc-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="86cdc-147">Z tohoto důvodu bylo ID z hlediska doménového modelu skryté, ale stále přítomné v infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="86cdc-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="86cdc-148">Trvalost tohoto objektu Value do databáze se ale prováděla jako regulární entita v jiné tabulce.</span><span class="sxs-lookup"><span data-stu-id="86cdc-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="86cdc-149">S EF Core 2,0 existují nové a lepší způsoby, jak zachovat objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="86cdc-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="86cdc-150">Zachovat objekty hodnot jako vlastněné typy entit v EF Core 2,0</span><span class="sxs-lookup"><span data-stu-id="86cdc-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="86cdc-151">I s některými mezerami mezi vzorem objektu kanonické hodnoty v DDD a vlastněnou entitou typu v EF Core je aktuálně nejlepším způsobem, jak zachovat objekty hodnot pomocí EF Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="86cdc-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="86cdc-152">Na konci této části můžete vidět omezení.</span><span class="sxs-lookup"><span data-stu-id="86cdc-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="86cdc-153">Do EF Core od verze 2,0 byla přidána funkce typu vlastněné entity.</span><span class="sxs-lookup"><span data-stu-id="86cdc-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="86cdc-154">Vlastněný typ entity umožňuje mapovat typy, které nemají vlastní identitu explicitně definované v doménovém modelu a jsou používány jako vlastnosti, jako je například objekt hodnoty, v rámci kterékoli z entit.</span><span class="sxs-lookup"><span data-stu-id="86cdc-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="86cdc-155">Vlastněný typ entity sdílí stejný typ CLR s jiným typem entity (to znamená pouze regulární třída).</span><span class="sxs-lookup"><span data-stu-id="86cdc-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="86cdc-156">Entita obsahující definici navigace je entitou vlastníka.</span><span class="sxs-lookup"><span data-stu-id="86cdc-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="86cdc-157">Při dotazování vlastníka jsou ve výchozím nastavení zahrnuty vlastní typy.</span><span class="sxs-lookup"><span data-stu-id="86cdc-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="86cdc-158">Podobně jako při prohlížení doménového modelu vypadá vlastněný typ, který nemá žádnou identitu.</span><span class="sxs-lookup"><span data-stu-id="86cdc-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="86cdc-159">Nicméně v rámci pokrývání mají vlastněné typy identitu, ale vlastnost navigace vlastníka je součástí této identity.</span><span class="sxs-lookup"><span data-stu-id="86cdc-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="86cdc-160">Identita instancí vlastněných typů není zcela vlastní.</span><span class="sxs-lookup"><span data-stu-id="86cdc-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="86cdc-161">Skládá se ze tří součástí:</span><span class="sxs-lookup"><span data-stu-id="86cdc-161">It consists of three components:</span></span>

- <span data-ttu-id="86cdc-162">Identita vlastníka</span><span class="sxs-lookup"><span data-stu-id="86cdc-162">The identity of the owner</span></span>

- <span data-ttu-id="86cdc-163">Navigační vlastnost, na kterou se odkazuje</span><span class="sxs-lookup"><span data-stu-id="86cdc-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="86cdc-164">V případě kolekcí vlastněných typů se nezávislá komponenta (zatím nepodporovaná v EF Core 2,0, která se nachází na 2,2).</span><span class="sxs-lookup"><span data-stu-id="86cdc-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="86cdc-165">Například v modelu domény řazení na eShopOnContainers jako součást entity Order je objekt hodnoty adresy implementován jako vlastněný typ entity v rámci entity Owner, která je objednávka.</span><span class="sxs-lookup"><span data-stu-id="86cdc-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="86cdc-166">Adresa je typ bez vlastnosti identity definované v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="86cdc-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="86cdc-167">Slouží jako vlastnost typu objednávky k určení dodací adresy pro konkrétní objednávku.</span><span class="sxs-lookup"><span data-stu-id="86cdc-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="86cdc-168">Podle konvence se vytvoří stínový primární klíč pro vlastní typ a bude namapován na stejnou tabulku jako vlastník pomocí rozdělení tabulky.</span><span class="sxs-lookup"><span data-stu-id="86cdc-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="86cdc-169">To umožňuje použít vlastněné typy podobně jako složité typy používané v EF6 v tradičním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86cdc-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="86cdc-170">Je důležité si uvědomit, že vlastní typy nejsou nikdy zjištěny v konvenci v EF Core, takže je musíte deklarovat explicitně.</span><span class="sxs-lookup"><span data-stu-id="86cdc-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="86cdc-171">V eShopOnContainers platí, že v OrderingContext.cs v rámci metody OnModelCreating () existuje více konfigurací infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="86cdc-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="86cdc-172">Jedna z nich se vztahuje k entitě Order.</span><span class="sxs-lookup"><span data-stu-id="86cdc-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="86cdc-173">V následujícím kódu je pro entitu pro objednávku definována infrastruktura trvalosti:</span><span class="sxs-lookup"><span data-stu-id="86cdc-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="86cdc-174">V předchozím kódu metoda `orderConfiguration.OwnsOne(o => o.Address)` určuje, že vlastnost `Address` je vlastněnou entitou typu `Order`.</span><span class="sxs-lookup"><span data-stu-id="86cdc-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="86cdc-175">Ve výchozím nastavení EF Core konvence pojmenují sloupce databáze pro vlastnosti typu vlastněné entity jako `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="86cdc-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="86cdc-176">Proto se vnitřní vlastnosti `Address` zobrazí v tabulce `Orders` s názvy `Address_Street``Address_City` (atd. `State``Country` a `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="86cdc-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="86cdc-177">K přejmenování těchto sloupců můžete připojit metodu `Property().HasColumnName()` Fluent.</span><span class="sxs-lookup"><span data-stu-id="86cdc-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="86cdc-178">V případě, kdy `Address` je veřejná vlastnost, by mapování vypadalo takto:</span><span class="sxs-lookup"><span data-stu-id="86cdc-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="86cdc-179">Je možné zřetězit metodu `OwnsOne` v mapování Fluent.</span><span class="sxs-lookup"><span data-stu-id="86cdc-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="86cdc-180">V následujícím hypotetickém příkladu `OrderDetails` vlastní `BillingAddress` a `ShippingAddress`, které jsou oba `Address` typy.</span><span class="sxs-lookup"><span data-stu-id="86cdc-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="86cdc-181">Pak `OrderDetails` vlastní `Order` typ.</span><span class="sxs-lookup"><span data-stu-id="86cdc-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="86cdc-182">Další podrobnosti o vlastněných typech entit</span><span class="sxs-lookup"><span data-stu-id="86cdc-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="86cdc-183">Vlastněné typy jsou definovány při konfiguraci navigační vlastnosti na konkrétní typ pomocí rozhraní OwnsOne Fluent API.</span><span class="sxs-lookup"><span data-stu-id="86cdc-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="86cdc-184">Definice vlastněného typu v našem modelu metadat je složená z: typ vlastníka, navigační vlastnost a typ CLR vlastněných typů.</span><span class="sxs-lookup"><span data-stu-id="86cdc-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="86cdc-185">Identita (klíč) instance vlastního typu v našem zásobníku je složena z identity typu vlastníka a definice vlastněného typu.</span><span class="sxs-lookup"><span data-stu-id="86cdc-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="86cdc-186">Možnosti vlastněných entit:</span><span class="sxs-lookup"><span data-stu-id="86cdc-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="86cdc-187">Vlastněné typy mohou odkazovat na jiné entity, buď vlastněné (vnořené vlastněné typy), nebo nevlastní (standardní referenční vlastnosti navigace jiným entitám).</span><span class="sxs-lookup"><span data-stu-id="86cdc-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="86cdc-188">Stejný typ CLR můžete mapovat jako jiné vlastněné typy ve stejné entitě Owner prostřednictvím samostatných vlastností navigace.</span><span class="sxs-lookup"><span data-stu-id="86cdc-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="86cdc-189">Rozdělení tabulky je nastavení podle konvence, ale můžete si ji vyfiltrovat tak, že namapujete vlastněný typ na jinou tabulku pomocí ToTable.</span><span class="sxs-lookup"><span data-stu-id="86cdc-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="86cdc-190">Načítání Eager se provádí automaticky na vlastněných typech, tj. není nutné volat include () na dotaz.</span><span class="sxs-lookup"><span data-stu-id="86cdc-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="86cdc-191">Dá se nakonfigurovat s atributem \[vlastní\], od EF Core 2,1</span><span class="sxs-lookup"><span data-stu-id="86cdc-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="86cdc-192">Omezení entit vlastněných entitami:</span><span class="sxs-lookup"><span data-stu-id="86cdc-192">Owned entities limitations:</span></span>

- <span data-ttu-id="86cdc-193">Nemůžete vytvořit\> Negenerickými\<T vlastněných typu (podle návrhu).</span><span class="sxs-lookup"><span data-stu-id="86cdc-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="86cdc-194">Nelze volat ModelBuilder. entity\<T\>() na vlastněných typech (aktuálně podle návrhu).</span><span class="sxs-lookup"><span data-stu-id="86cdc-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="86cdc-195">Zatím nejsou žádné kolekce vlastněných typů (od EF Core 2,1, ale budou podporované v 2,2).</span><span class="sxs-lookup"><span data-stu-id="86cdc-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="86cdc-196">Není podporována podpora volitelného typu (to znamená Nullable), který je namapován s vlastníkem ve stejné tabulce (tj. použití rozdělení tabulky).</span><span class="sxs-lookup"><span data-stu-id="86cdc-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="86cdc-197">Důvodem je to, že mapování se provádí pro každou vlastnost, ale nepoužíváme samostatnou sentinelou pro komplexní hodnotu null a jako celek.</span><span class="sxs-lookup"><span data-stu-id="86cdc-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="86cdc-198">Pro vlastněné typy není podporovaná podpora mapování dědičnosti, ale měli byste být schopni mapovat dva typy listů stejných hierarchií dědičnosti jako jiné vlastněné typy.</span><span class="sxs-lookup"><span data-stu-id="86cdc-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="86cdc-199">EF Core nebude mít důvod k tomu, že jsou součástí stejné hierarchie.</span><span class="sxs-lookup"><span data-stu-id="86cdc-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="86cdc-200">Hlavní rozdíly s EF6's komplexními typy</span><span class="sxs-lookup"><span data-stu-id="86cdc-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="86cdc-201">Rozdělení tabulky je volitelné, tj. je možné je volitelně namapovat na samostatnou tabulku a nadále mít vlastní typy.</span><span class="sxs-lookup"><span data-stu-id="86cdc-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="86cdc-202">Můžou odkazovat na jiné entity (to znamená, že můžou fungovat jako závislá strana na vztazích s jinými nevlastními typy).</span><span class="sxs-lookup"><span data-stu-id="86cdc-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="86cdc-203">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="86cdc-203">Additional resources</span></span>

- <span data-ttu-id="86cdc-204">**Martin Fowlera. \ vzor ValueObject**</span><span class="sxs-lookup"><span data-stu-id="86cdc-204">**Martin Fowler. ValueObject pattern** \</span></span>
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="86cdc-205">**Eric Evans. Návrh založený na doméně: řešení složitosti na srdce softwaru.**</span><span class="sxs-lookup"><span data-stu-id="86cdc-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="86cdc-206">(Kniha; obsahuje diskuzi o objektech hodnot) </span><span class="sxs-lookup"><span data-stu-id="86cdc-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="86cdc-207">**Vaughn Vernon. Implementace návrhu založeného na doméně.**</span><span class="sxs-lookup"><span data-stu-id="86cdc-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="86cdc-208">(Kniha; obsahuje diskuzi o objektech hodnot) </span><span class="sxs-lookup"><span data-stu-id="86cdc-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="86cdc-209">**Vlastnosti stínu** </span><span class="sxs-lookup"><span data-stu-id="86cdc-209">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="86cdc-210">**Komplexní typy a/nebo hodnotové objekty**.</span><span class="sxs-lookup"><span data-stu-id="86cdc-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="86cdc-211">Diskuze v úložišti GitHubu EF Core (karta problémy) </span><span class="sxs-lookup"><span data-stu-id="86cdc-211">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="86cdc-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="86cdc-212">**ValueObject.cs.**</span></span> <span data-ttu-id="86cdc-213">Třída objektů základní hodnoty v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="86cdc-213">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="86cdc-214">**Adresa třídy.**</span><span class="sxs-lookup"><span data-stu-id="86cdc-214">**Address class.**</span></span> <span data-ttu-id="86cdc-215">Ukázková hodnota třídy objektu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="86cdc-215">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="86cdc-216">[Předchozí](seedwork-domain-model-base-classes-interfaces.md)
> [Další](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="86cdc-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
