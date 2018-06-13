---
title: Implementace hodnota objekty
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace hodnota objekty
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 04a0def5fbadcc39220d9dc8daa9c9341fe66b26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579299"
---
# <a name="implementing-value-objects"></a>Implementace hodnota objekty

Jak je popsáno v předchozích částech o entity a agregace, identita je zásadní pro entity. Existují však mnoho objektů a dat položky v rámci systému, které nevyžadují, aby identita a identity, jako je například hodnota objektů pro sledování.

Objekt hodnoty můžete odkazovat ostatní entity. Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do jiného že směrování by objekt hodnoty. Je snímek body na konkrétní trase, ale tato trasa navrhované neměli svou identitu, i když interně může odkazovat na entity města, silniční, atd.

Obrázek 9 – 13 ukazuje objekt hodnoty adres v rámci agregace pořadí.

![](./media/image14.png)

**Obrázek 9 – 13**. Adresa hodnota objekt v rámci agregace pořadí

Jak znázorňuje obrázek 9 – 13, entity se obvykle skládá z více atributů. Například `Order` entity můžete modelován jako entity s identity a složené interně sady atributů, například OrderId, OrderDate, OrderItems atd. Ale na adresu, což je jednoduše komplexní hodnota tvořený země, ulici, Město, atd. a je žádná identita v této doméně, musí být modelovány a považován za objekt hodnoty.

## <a name="important-characteristics-of-value-objects"></a>Důležité charakteristiky hodnota objektů

Existují dvě hlavní vlastnosti pro objekty, hodnota:

-   Nemají žádné identity.

-   Jsou neměnné.

První vlastnosti už byl popsané. Neměnitelnosti je důležité požadavek. Hodnoty objektu. hodnota musí být neměnné po vytvoření objektu. Když se objekt, proto je nutné zadat požadované hodnoty, ale nesmí umožňovat, aby změnit v průběhu životnosti objektu.

Hodnota objekty umožňují provádět určité triky pro výkon díky jejich neměnné povahy. To platí hlavně v systémech kde může být tisíce hodnotu instance objektů, které mnoho má stejné hodnoty. Svou povahou neměnné umožňuje, aby znovu použít; může se jednat zaměňovat objekty, protože jejich hodnoty jsou stejné a mají žádná identita. Tento typ optimalizace někdy mohou být rozdíl mezi software, který běží pomalu a software s dobrý výkon. Všech těchto případech samozřejmě závisí na prostředí aplikace a nasazení kontextu.

## <a name="value-object-implementation-in-c"></a>Hodnota objektu implementace v jazyce C\#

Z hlediska implementace může mít základní třídy hodnotu objektu, která má základní pomocné metody jako rovnosti na základě porovnání mezi všechny atributy (protože objekt hodnota nesmí být na základě identity) a dalších základních vlastností. Následující příklad ukazuje hodnotu objektu základní třída používaná v řazení mikroslužbu z eShopOnContainers.

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

Tuto třídu můžete použít při implementaci skutečnou hodnotu objektu, stejně jako u adres objekt hodnoty vidět v následujícím příkladu:

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

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Postup zachovat hodnotu objekty v databázi s EF základní 2.0

Právě jste viděli, jak definovat objekt hodnoty v modelu domény. Ale, jak můžete je ve skutečnosti zachovat ji do databáze prostřednictvím základní Entity Framework (EF), které se obvykle týká entity s identity?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Pozadí a starší přístupů pomocí EF základní 1.1

Jako pozadí, byl omezení při použití EF základní 1.0 a 1.1, nelze použít [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) definovaným v EF 6.x v tradiční rozhraní .NET Framework. Proto pokud používáte EF základní 1.0 nebo 1.1, je potřebný k uložení objektu hodnotu jako entity EF s pole ID. A, vypadal další jako objekt hodnoty pomocí žádná identita, může skrýt jeho ID, takže byste měli vytvořit jasné, že identita objekt hodnoty není důležité v modelu domény. Toto ID může skrýt pomocí ID jako [stínové vlastnost](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Vzhledem k tomu, že konfigurace pro skrytí ID v modelu je nastaven na úrovni infrastruktury EF, bylo by druh transparentní pro modelu domény.

Skrytá ID vyžaduje EF základní infrastruktury byla v původní verzi eShopOnContainers (.NET Core 1.1), implementovaná tímto způsobem na úrovni DbContext pomocí rozhraní Fluent API v projektu OMI. Proto se ID skrytá z hlediska domény modelu, ale stále přítomen v infrastruktuře.

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

Však trvalost hodnotu objektu do databáze byla provedena jako regulární entity v jiné tabulky.

S EF základní 2.0, je nový a lepší způsoby zachovat objekty hodnotu.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Zachovat objekty hodnotu jako ve vlastnictví entity typy v EF základní 2.0

I když některé mezery mezi vzor objektu kanonické hodnoty v DDD a typ vlastní entity v základní EF je aktuálně nejlepší způsob, jak zachovat objekty hodnotu s EF základní 2.0. Zobrazí se omezeních na konci této části.

Funkci typu vlastněná entita byla přidána do základní EF od verze 2.0.

Typ entity ve vlastnictví umožňuje mapovat typy, které nemají své vlastní identity explicitně definované v modelu domény a jsou použity jako vlastnosti, například objekt hodnoty v některé z vaší entity. Typ entity ve vlastnictví sdílí stejný typ CLR s jiným typem entity. Entita obsahující definující navigační je vlastníka. Při dotazování vlastník, vlastní typy jsou zahrnuté ve výchozím nastavení.

Podle vzhledu modelu domény, vlastní typ vypadá nemá žádné identity.
V pozadí, vlastní typy mají identity, ale je součástí tuto identitu vlastníka navigační vlastnost.

Identita instance vlastní typy není úplně svoje vlastní. Obsahuje tři komponenty:

- Identitu vlastníka

- Vlastnost navigace na ně odkazují

- V případě kolekce vlastní typy komponentu nezávislé (není dosud podporován v EF základní 2.0).

V modelu domény řazení v eShopOnContainers jako součást pořadí entity, například objekt hodnoty adresa je implementovaný jako typ entity ve vlastnictví v rámci entity vlastníka, který je entita pořadí. Adresa je typu s žádná vlastnost identity, které jsou definované v modelu domény. Jako vlastnost typu pořadí slouží k určení adresy příjemce pro konkrétní pořadí.

Podle konvence stínové primární klíč se vytvoří pro vlastní typ a bude být namapované na stejné tabulce jako vlastník pomocí rozdělení tabulky. To umožňuje použití vlastní typy podobně jako na tom, jak komplexní typy, které se používají v EF6 v tradiční rozhraní .NET Framework.

Je důležité si uvědomit, že který vlastněných typy nikdy zjištění podle konvence v EF jádra, musíte je výslovně deklarovat.

V eShopOnContainers v OrderingContext.cs, v rámci metody OnModelCreating(), existuje více konfigurace infrastruktury, které bylo použito. Jeden z nich se týká entity pořadí.

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

V následujícím kódu je definováno infrastruktury trvalosti pro entitu pořadí:

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

V předchozí kód `orderConfiguration.OwnsOne(o => o.Address)` metoda určuje, že `Address` vlastnost je vlastní entita `Order` typu.

Ve výchozím nastavení, konvence EF základní název sloupce databáze pro vlastnosti typu entity ve vlastnictví jako `EntityProperty_OwnedEntityProperty`. Proto vnitřní vlastnosti `Address` se objeví v `Orders` tabulku s názvy `Address_Street`, `Address_City` (a tak dále pro `State`, `Country` a `ZipCode`).

Můžete připojit `Property().HasColumnName()` fluent metoda přejmenovat tyto sloupce. V případě, kde `Address` veřejná vlastnost mapování by bylo třeba takto:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Je možné řetězec `OwnsOne` metoda fluent mapování. V následujícím příkladu hypotetický `OrderDetails` vlastní `BillingAddress` a `ShippingAddress`, které jsou obě `Address` typy. Potom `OrderDetails` vlastníkem je `Order` typu.

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

### <a name="additional-details-on-owned-entity-types"></a>Další informace o typy vlastní entit

• Vlastní typy jsou definovány při konfiguraci navigační vlastnost pro konkrétní typ pomocí rozhraní fluent API OwnsOne.

• Definici vlastní typu v našem model metadat je složené: Typ vlastníka, navigační vlastnost a typ CLR vlastní typu.

• Identity (klíč) vlastní typ instance v našem zásobníku je složené identity typu vlastníka a definicí typu vlastní.

#### <a name="owned-entities-capabilities"></a>Vlastní entity možnosti:

•, Že typ, můžete odkazovat jinými entitami, buď ve vlastnictví (vnořené vlastní typy) bez vlastněné nebo (navigační vlastnosti regulární odkazu na ostatní entity).

• Můžete mapovat stejný typ CLR jako ve vlastnictví různého stejné entity vlastníka prostřednictvím samostatné navigační vlastnosti.

• Rozdělení tabulky je nastavená podle konvence, ale můžete chodit tak, že mapuje vlastní typ do jiné tabulky pomocí ToTable.

• Přes načtení je prováděno automaticky pro vlastní typy, tj. není třeba volat Include() na dotaz.

#### <a name="owned-entities-limitations"></a>Vlastní entity omezení:

• Nelze vytvořit DbSet<T> vlastní typu (záměrně).

• Nelze volat ModelBuilder.Entity<T>() pro vlastní typy (aktuálně podle návrhu).

• Žádné kolekce vlastní typy ještě (ale bude se podporovány ve verzích po EF základní 2.0).

• Žádná podpora pro jejich konfigurací prostřednictvím atributu.

• Žádná podpora pro volitelné (tj. připouštějící hodnotu Null) vlastní typy, které jsou mapovány s vlastníkem ve stejné tabulce (tj. pomocí rozdělení tabulky). To je proto nemáme samostatné sentinel pro hodnotu null.

• Podpora mapování dědičnosti pro vlastní typy, ale byste měli mít k mapování dva typy na stejné hierarchie dědičnosti jako ve vlastnictví různého typu list. Základní EF nebude důvodu o tom, že jsou součástí stejné hierarchie.

#### <a name="main-differences-with-ef6s-complex-types"></a>Hlavní rozdíly mezi EF6 je komplexní typy

• Rozdělení tabulky je volitelné, tj. jejich může volitelně mapovat do samostatné tabulky a přesto být vlastní typy.

• Mohou odkazovat ostatní entity (tj. jejich může fungovat jako závislé straně u relací na jiné typy bez vlastněných).


## <a name="additional-resources"></a>Další zdroje

-   **Martin Fowler. Vzor ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru.** (Sešit; zahrnuje diskuzi o hodnotu objekty) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Implementace návrhu řízené domény.** (Sešit; zahrnuje diskuzi o hodnotu objekty) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Komplexní typy nebo hodnoty objekty**. Diskusi do úložiště GitHub základní EF (karta problémů) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Základní hodnota třída objektu v eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Třídy adres.** Ukázka třídy objektu hodnotu v eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
[Předchozí] (seedwork-domain-model-base-classes-interfaces.md) [Další] (výčet třídy over výčtu types.md)
