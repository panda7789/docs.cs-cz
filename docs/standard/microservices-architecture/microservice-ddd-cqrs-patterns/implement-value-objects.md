---
title: Implementace objektů hodnot
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Získejte podrobnosti a možnosti, které implementují objekty hodnotu pomocí nové funkce Entity Framework.
ms.date: 10/08/2018
ms.openlocfilehash: 850d571ffb92f2d200e24430a9611fb13b64e635
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644300"
---
# <a name="implement-value-objects"></a>Implementace objektů hodnot

Jak je popsáno v předchozích částech o entit a agregace, je nezbytné pro entity identity. Existují však mnoho objektů a dat položky v systému, které nevyžadují identit a identity, jako je například hodnota objektů pro sledování.

Objekt hodnoty, který může odkazovat na jiné entity. Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho místa do jiného směrující by být objekt hodnoty. Bylo by snímek body na konkrétní trase, ale tato trasa navrhované nemusí identitu, i když interně může odkazovat na entitami, jako jsou Město, silniční atd.

Obrázek 7-13 zobrazuje objekt hodnoty adres v rámci pořadí agregace.

![Adresa-objekt hodnoty uvnitř agregace pořadí.](./media/image14.png)

**Obrázek 7-13**. Adresa objektu hodnot v rámci pořadí agregace

Jak je znázorněno v obrázek 7-13, entity se obvykle skládá z více atributů. Například `Order` entity můžete modelovat jako entity s identitou a interně skládá ze sady atributů, jako je například OrderId, OrderDate, OrderItems atd. Ale adresu, která je jednoduše komplexní – hodnota složený ze země, ulici, Město atd. a nemá žádná identita v této doméně, musí být modelovat a považován za hodnotu objektu.

## <a name="important-characteristics-of-value-objects"></a>Důležité charakteristiky hodnotu objektů

Existují dva hlavní vlastnosti pro objekty hodnotu:

- Nemají žádné identity.

- Jsou neměnné.

O první charakteristiku bylo už popsáno. Neměnnost je důležité požadavek. Hodnoty objekt hodnoty musí být neměnný po vytvoření objektu. Při vytvoření objektu, proto je nutné zadat požadované hodnoty, ale nesmí zajistí, aby změnit během životního cyklu objektu.

Hodnota objekty umožňují provádět některé tipy pro výkon díky jejich povaze neměnné. To platí zejména v systémech tam, kde můžou existovat tisíce hodnotu instance objektů, z nichž mají stejné hodnoty. Jejich neměnné podstatu umožňuje jejich opětovné používání; je možné zaměnitelné objekty, protože jejich hodnoty jsou stejné, a nemají žádné identity. Tento typ optimalizace někdy možné zvýšit rozdíl mezi softwarem, který běží pomalu a software s dobrého výkonu. Všech těchto případech samozřejmě závisí na prostředí aplikací a nasazení kontext.

## <a name="value-object-implementation-in-c"></a>Implementace objektu hodnoty v jazyce C\#

Z hlediska implementace může mít hodnotu základní třídu objektu, který má metody základní nástroje, jako je rovnost na základě porovnání mezi všechny atributy (protože hodnota objektu nesmí být na základě identity) a další základní vlastnosti. Následující příklad ukazuje základní třídu hodnotu objektu používá v pořadí mikroslužeb v aplikaci eShopOnContainers.

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

Tuto třídu můžete použít při implementaci skutečnou hodnotu objektu, stejně jako u adres objekt hodnoty je znázorněno v následujícím příkladu:

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

Uvidíte jak implementovaný objekt hodnotu adresy má žádná identita a proto žádné pole ID, ani na třídu adresu ani na třídu ValueObject.

Žádné ID pole třídy používané Entity Framework s nebylo možné, dokud EF Core 2.0, což značně pomáhá implementovat lepší hodnotu objekty s žádné ID. To je přesně vysvětlení další části.

Může být uvedl, že hodnota objekty, budou nezměnitelný, by měla být jen pro čtení (například get jen vlastnosti), a to je ve skutečnosti hodnotu true. Však hodnoty objekty jsou obvykle serializaci a deserializaci absolvovat fronty zpráv a je jen pro čtení zastaví deserializátor v přiřazení hodnoty, takže jsme právě nechat jako privátní sada, která je jen pro čtení dostatečně bude praktické.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Zachování hodnotu objektů v databázi s EF Core 2.0

Právě jste viděli, jak definovat objekt hodnoty v doménovém modelu. Ale jak můžete ve skutečnosti trvale uložíte ho do databáze prostřednictvím základní Entity Framework (EF), která se obvykle týká entity, které identity?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Na pozadí a starší přístupy s použitím EF Core 1.1

Jako pozadí, byla nelze použít omezení při použití EF Core 1.0 a 1.1 [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) jak jsou definovány v EF 6.x v tradiční rozhraní .NET Framework. Proto pokud pomocí EF Core 1.0 a 1.1, museli jste k uložení hodnoty objektu jako entita EF se pole ID. Pak, aby vypadal podobně objekt hodnoty pomocí žádná identita, může skrýt jeho ID, takže jasně, že identita hodnota objektu není důležité v doménovém modelu. Toto ID může skrýt pomocí ID jako [stínové vlastnosti](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Protože tuto konfiguraci pro skrytí ID v modelu je nastaven na úrovni infrastruktury EF, bylo by druh transparentní pro doménový model.

Skrytá ID vyžadované EF Core infrastruktury byl v počáteční verzi aplikaci eShopOnContainers (.NET Core 1.1), implementované v úrovni DbContext, následujícím způsobem pomocí rozhraní Fluent API v projektu infrastruktury. Proto se ID skryté z hlediska domény modelu, ale stále k dispozici v infrastruktuře.

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

Ale trvalost hodnotu objektu do databáze byla provedena jako regulární entity v jiné tabulce.

S EF Core 2.0, existují nové a lepší způsoby, jak zachovat hodnotu objektů.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Zachovat hodnotu objektů jako vlastněné typy entit v EF Core 2.0

I při některých mezery mezi vzor objektu Kanonická hodnota v DDD a typ vlastnictví entity v EF Core je aktuálně nejlepší způsob, jak zachovat hodnotu objekty s EF Core 2.0. Zobrazí se omezení na konci této části.

Typ funkce vlastnictví entity byl přidán do EF Core od verze 2.0.

Typ vlastnictví entity umožňuje mapování typů, které nemají vlastní identity explicitně definované v modelu domény a slouží jako vlastnosti, jako je například objekt hodnoty v rámci všech entit. Typ vlastnictví entity sdílí stejný typ CLR s jiným typem entity (to znamená, je právě běžné třídy). Entita obsahující definující navigace je entita, vlastníka. Při dotazování na vlastníka, vlastněné typy jsou zahrnuté ve výchozím nastavení.

Právě zobrazením doménový model, vlastní typ, který vypadá to, nemá žádné identity. Pod pokličkou, vlastněné typy mít identitu, ale vlastník navigační vlastnost je součástí této identity.

Identita instance typů vlastnictví není zcela vlastní. Skládá se ze tří komponent:

- Identita vlastníka

- Navigační vlastnost odkazuje na ně

- V případě kolekcí vlastněné typy, jako nezávislé součást (ještě není podporované v EF Core 2.0, naráželi na 2.2).

V doménovém modelu řazení v aplikaci eShopOnContainers jako součást pořadí entity, například objekt hodnoty adres je implementovaný jako typ vlastnictví entity v rámci entity vlastník, což je entita pořadí. Adresa je typ s žádnou vlastnost identity definován v doménovém modelu. Jako vlastnost typu pořadí slouží k určení dodací adresu pro konkrétní objednávku.

Podle konvence stínové primární klíč je vytvořen pro typ vlastnictví a bude ji namapovat na stejnou tabulku jako vlastník pomocí rozdělení tabulky. To umožňuje použití vlastní typy podobně jako na tom, jak komplexní typy, které se používají v EF6 v tradiční rozhraní .NET Framework.

Je důležité si uvědomit, že, který vlastní, že typy nikdy zjištění konvencí v EF Core, takže je nutné je explicitně deklarovat.

V aplikaci eShopOnContainers v OrderingContext.cs, v rámci metody OnModelCreating() existují více konfiguraci infrastruktury, které jsou právě používá. Jeden z nich souvisí s entitou objednávky.

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

V následujícím kódu je definována infrastruktury trvalosti pro entitu pořadí:

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

V předchozím kódu `orderConfiguration.OwnsOne(o => o.Address)` metody Určuje, že `Address` vlastností je vlastní entity `Order` typu.

Ve výchozím nastavení, EF Core konvence název sloupce databáze pro vlastnosti typu vlastnictví entity jako `EntityProperty_OwnedEntityProperty`. Proto vnitřní vlastnosti `Address` se zobrazí v `Orders` tabulky s názvy `Address_Street`, `Address_City` (a podobně pro `State`, `Country` a `ZipCode`).

Můžete připojit `Property().HasColumnName()` fluent metoda přejmenování sloupců. V případě, kdy `Address` je veřejná vlastnost mapování bude podobný tomuto:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Je možné řetězec `OwnsOne` metoda v mapování fluent. V následujícím příkladu hypotetické `OrderDetails` vlastní `BillingAddress` a `ShippingAddress`, které jsou obě `Address` typy. Potom `OrderDetails` není ve vlastnictví `Order` typu.

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

### <a name="additional-details-on-owned-entity-types"></a>Další podrobnosti o vlastněné typy entit

- Vlastněné typy jsou definovány, když konfigurujete navigační vlastnost pro určitý typ pomocí rozhraní API fluent OwnsOne.

- Definice typu vlastnictví v našich metadat modelu je složené: Typ vlastníka, navigační vlastnost a typ CLR vlastnictví.

- Identita (klíč) vlastnictví typu instance v našich zásobníku je složené identity typu vlastníka a definice typu vlastnictví.

#### <a name="owned-entities-capabilities"></a>Vlastnictví entity funkce:

- Vlastní typy mohou odkazovat na jiné entity, buď vlastní (vnořené vlastněné typy) nebo není ve vlastnictví (pravidelných odkaz navigačních vlastností pro ostatní entity).

- Můžete namapovat stejný typ CLR jako vlastněné typy v rámci stejné entity vlastníka prostřednictvím samostatný navigační vlastnosti.

- Rozdělení tabulky se nastavení podle konvence, ale můžete odhlásit pomocí mapování typ vlastnictví na jinou tabulku pomocí ToTable.

- Předběžné načítání se provádí automaticky na vlastní typy, tedy není nutné volat Include() na dotazu.

- Můžete nakonfigurovat pomocí atributu \[vlastněno\], protože EF Core 2.1

#### <a name="owned-entities-limitations"></a>Vlastnictví entity omezení:

- Nelze vytvořit DbSet\<T\> vlastnictví typu (záměrně).

- Nejde volat ModelBuilder.Entity\<T\>() pro vlastní typy (aktuálně záměrné).

- Žádné kolekce vlastněné typy, ale (od verze EF Core 2.1, ale podporovaly v 2.2).

- Žádná podpora pro volitelné (tedy s možnou hodnotou Null) vlastní typy, které jsou mapovány s vlastníkem ve stejné tabulce (například pomocí rozdělení tabulky). Důvodem je, že mapování se provádí pro každou vlastnost, nemáme samostatné sentinel pro komplexní hodnota null jako celé.

- Žádná podpora dědičnosti mapování pro vlastní typy, ale byste měli namapovat dva typy listu stejné hierarchie dědičnosti jako různé typy vlastnictví. EF Core nebude odůvodnitelný fakt, že jsou součástí stejné hierarchie.

#### <a name="main-differences-with-ef6s-complex-types"></a>Hlavní rozdíly s EF6 pro komplexní typy

- Rozdělení tabulky je volitelné, to znamená, že je volitelně možné mapovat na samostatnou tabulku a nadále jeho vlastníkem typy.

- Odkazují jiné entity (například jejich může fungovat jako závislé straně u relací na jiné typy než vlastnictví).

## <a name="additional-resources"></a>Další zdroje

- **Martina Fowlera. Vzor ValueObject** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru.** (Kniha; obsahuje diskusi hodnotu objektů) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon. Implementace návrhu řízeného doménou.** (Kniha; obsahuje diskusi hodnotu objektů) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Stínové vlastnosti** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Komplexní typy nebo hodnoty objekty**. Diskuze v úložišti Githubu EF Core (stiskněte klávesu tab problémy) \
  <https://github.com/aspnet/EntityFramework/issues/246>

- **ValueObject.cs.** Třída objektu základní hodnoty v aplikaci eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Třída adresy** Ukázka hodnotová třída objektu v aplikaci eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Předchozí](seedwork-domain-model-base-classes-interfaces.md)
> [další](enumeration-classes-over-enum-types.md)
