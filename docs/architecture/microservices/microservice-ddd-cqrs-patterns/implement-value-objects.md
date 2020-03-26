---
title: Implementace objektů hodnot
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Získejte do podrobností a možností implementovat objekty hodnoty pomocí nových funkcí entity framework.
ms.date: 01/30/2020
ms.openlocfilehash: 919b23f7c1a0cd0aec8c4417f3af98469a0743dd
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249419"
---
# <a name="implement-value-objects"></a>Implementace hodnotových objektů

Jak je popsáno v předchozích částech o entitách a agregaci, identita je zásadní pro entity. Existuje však mnoho objektů a datových položek v systému, které nevyžadují sledování identity a identity, jako jsou například objekty hodnot.

Objekt hodnoty může odkazovat na jiné entity. Například v aplikaci, která generuje trasu, která popisuje, jak se dostat z jednoho bodu do druhého, by tato trasa byla hodnotovým objektem. Jednalo by se o snímek bodů na konkrétní trase, ale tato navrhovaná trasa by neměla identitu, i když interně by se mohla vztahovat na subjekty, jako je Město, Silnice atd.

Obrázek 7-13 znázorňuje objekt hodnoty Adresa v rámci agregace Pořadí.

![Diagram znázorňující hodnotu adresy-objekt uvnitř agregace pořadí.](./media/implement-value-objects/value-object-within-aggregate.png)

**Obrázek 7-13**. Objekt hodnoty adresy v rámci agregace Objednávka

Jak je znázorněno na obrázku 7-13, entita se obvykle skládá z více atributů. Entita `Order` může být například modelována jako entita s identitou a tvořena interně sadou atributů, jako je OrderId, OrderDate, OrderItems atd. Ale adresa, která je jednoduše komplexní hodnota složená z země nebo oblasti, ulice, města atd.

## <a name="important-characteristics-of-value-objects"></a>Důležité vlastnosti hodnotových objektů

Existují dvě hlavní charakteristiky pro hodnotové objekty:

- Nemají žádnou identitu.

- Jsou neměnné.

První charakteristika byla již diskutována. Neměnnost je důležitým požadavkem. Hodnoty objektu hodnoty musí být neměnné, jakmile je objekt vytvořen. Proto při vytvoření objektu je nutné zadat požadované hodnoty, ale nesmíte povolit jejich změny během životnosti objektu.

Hodnotové objekty vám umožní provádět určité triky pro výkon, díky své neměnné povaze. To platí zejména v systémech, kde mohou existovat tisíce instancí objektu hodnoty, z nichž mnohé mají stejné hodnoty. Jejich neměnná povaha umožňuje jejich opětovné použití; mohou být zaměnitelné objekty, protože jejich hodnoty jsou stejné a nemají žádnou identitu. Tento typ optimalizace může někdy dělat rozdíl mezi softwarem, který běží pomalu a software s dobrým výkonem. Samozřejmě všechny tyto případy závisí na prostředí aplikace a kontextu nasazení.

## <a name="value-object-implementation-in-c"></a>Implementace objektu hodnoty v C\#

Pokud jde o implementaci, můžete mít základní třídu objektu hodnoty, která má základní metody nástroje, jako je rovnost, na základě porovnání mezi všemi atributy (protože objekt hodnoty nesmí být založen na identitě) a dalšízákladní charakteristiky. Následující příklad ukazuje základní třídu objektu hodnoty použitou v objednávání mikroslužby z eShopOnContainers.

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

Tuto třídu můžete použít při implementaci objektu skutečné hodnoty, stejně jako u objektu hodnoty Adresa zobrazeném v následujícím příkladu:

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

Můžete vidět, jak tato implementace objektu hodnoty Address nemá žádnou identitu a proto žádné pole ID, ani na Address třídy ani na ValueObject třídy.

Bez ID pole ve třídě, které mají být použity entity Framework (EF) nebylo možné až EF Core 2.0, což výrazně pomáhá implementovat lepší hodnotu objekty bez ID. To je přesně vysvětlení další části.

To by mohlo být argumentoval, že hodnota objekty, je neměnný, by měl být jen pro čtení (to znamená, že mají vlastnosti pouze pro získání), a to je opravdu pravda. Však hodnoty objekty jsou obvykle serializovány a rekonstruovat projít fronty zpráv a právě jen pro čtení zastaví deserializer z přiřazení hodnot, takže jsme jen ponechat jako soukromou sadu, která je jen pro čtení dost být praktické.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a>Jak zachovat hodnotové objekty v databázi s EF Core 2.0 a novější

Právě jste viděli, jak definovat objekt hodnoty v modelu domény. Ale jak můžete skutečně zachovat do databáze pomocí entity framework core, protože obvykle cílí na entity s identitou?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Souvislosti a starší přístupy využívající EF Core 1.1

Jako pozadí omezení při použití EF Core 1.0 a 1.1 bylo, že nelze použít [složité typy,](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) jak je definováno v EF 6.x v tradiční rozhraní .NET Framework. Proto pokud používáte EF Core 1.0 nebo 1.1, je třeba uložit objekt hodnoty jako entitu EF s polem ID. Pak, takže to vypadalo spíše jako objekt hodnoty bez identity, můžete skrýt jeho ID, takže si můžete jasně, že identita objektu hodnoty není důležité v modelu domény. Toto ID můžete skrýt pomocí ID jako [vlastnosti stín](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Vzhledem k tomu, že konfigurace pro skrytí ID v modelu je nastavena na úrovni infrastruktury EF, by bylo trochu transparentní pro model domény.

V počáteční verzi eShopOnContainers (.NET Core 1.1) skryté ID potřebné infrastruktury EF Core bylo implementováno následujícím způsobem na úrovni DbContext pomocí fluent api v projektu infrastruktury. Proto ID byla skryta z hlediska modelu domény, ale stále k dispozici v infrastruktuře.

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

Trvalost tohoto objektu hodnoty do databáze však byla provedena jako normální entita v jiné tabulce.

S EF Core 2.0 a novější, existují nové a lepší způsoby, jak zachovat hodnoty objektů.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a>Zachovat objekty hodnoty jako typy vlastněných entit v EF Core 2.0 a novějším

I s některými mezerami mezi vzorem objektu kanonické hodnoty v DDD a typem vlastněné entity v EF Core je aktuálně nejlepším způsobem, jak zachovat hodnotové objekty s EF Core 2.0 a novějším. Omezení naleznete na konci této části.

Funkce typu vlastněné entity byla přidána do EF Core od verze 2.0.

Typ vlastní entity umožňuje mapovat typy, které nemají vlastní identitu explicitně definovanou v modelu domény a používají se jako vlastnosti, jako je například objekt hodnoty, v rámci libovolné entity. Vlastněný typ entity sdílí stejný typ CLR s jiným typem entity (to znamená, že je to pouze běžná třída). Entita obsahující definující navigaci je entita vlastníka. Při dotazování vlastníka jsou ve výchozím nastavení zahrnuty vlastněné typy.

Jen při pohledu na model domény, vlastněný typ vypadá, že nemá žádnou identitu. Však pod kryty, vlastněné typy mají identitu, ale vlastnost navigace vlastníka je součástí této identity.

Identita instancí vlastněných typů není zcela vlastní. Skládá se ze tří složek:

- Totožnost vlastníka

- Vlastnost navigace směřující k nim

- V případě kolekcí vlastněných typů, nezávislá komponenta (podporována v EF Core 2.2 a novější).

Například v modelu objednávací domény v eShopOnContainers jako součást entity Order je objekt hodnoty Adresa implementován jako typ vlastněné entity v rámci entity vlastníka, což je entita Objednávka. Adresa je typ bez vlastnosti identity definované v modelu domény. Používá se jako vlastnost typu Objednávka k určení dodací adresy pro konkrétní objednávku.

Podle konvence je vytvořen stínový primární klíč pro vlastněný typ a bude mapován na stejnou tabulku jako vlastník pomocí rozdělení tabulky. To umožňuje použít vlastněné typy podobně jako složité typy se používají v EF6 v tradiční rozhraní .NET Framework.

Je důležité si uvědomit, že vlastněné typy nejsou nikdy zjištěny podle konvence v EF Core, takže je nutné deklarovat explicitně.

V eShopOnContainers, na OrderingContext.cs v rámci OnModelCreating() metoda, jsou více konfigurace infrastruktury se používá. Jeden z nich souvisí s entitou Objednávka.

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

V následujícím kódu je pro entitu Objednávka definována infrastruktura trvalosti:

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

V předchozím kódu `orderConfiguration.OwnsOne(o => o.Address)` metoda určuje, `Address` že vlastnost je vlastněnou entitou `Order` typu.

Ve výchozím nastavení ef základní konvence název sloupce databáze pro `EntityProperty_OwnedEntityProperty`vlastnosti typu vlastní entity jako . `Address` Proto se v `Orders` tabulce s názvy `Address_Street` `Address_City` (a tak dále `State`pro `Country` `ZipCode`, a ).

Můžete připojit plynulou metodu `Property().HasColumnName()` přejmenovat tyto sloupce. V případě, `Address` kdy je veřejná vlastnost, mapování by bylo následující:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Je možné zřetězit `OwnsOne` metodu plynulým mapováním. V následujícím `OrderDetails` hypotetickém `BillingAddress` příkladu vlastní `ShippingAddress` `Address` a , které jsou oba typy. Potom `OrderDetails` je vlastněn typem. `Order`

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

### <a name="additional-details-on-owned-entity-types"></a>Další podrobnosti o typech vlastněných entit

- Vlastní typy jsou definovány při konfiguraci navigační vlastnost i pro určitý typ pomocí OwnsOne fluent API.

- Definice vlastněného typu v našem modelu metadat je složena z: typ vlastníka, navigační vlastnost a typ CLR vlastněného typu.

- Identita (klíč) instance vlastněného typu v našem zásobníku je složený z identity typu vlastníka a definice vlastněného typu.

#### <a name="owned-entities-capabilities"></a>Možnosti vlastněných entit

- Vlastněné typy mohou odkazovat na jiné entity, buď vlastněné (vnořené vlastněné typy) nebo nevlastněné (vlastnosti navigace s pravidelným odkazem na jiné entity).

- Můžete mapovat stejný typ CLR jako různé vlastněné typy ve stejné entitě vlastníka prostřednictvím samostatných navigačních vlastností.

- Rozdělení tabulky je nastaveno podle konvence, ale můžete se odhlásit mapováním vlastněného typu na jinou tabulku pomocí ToTable.

- Eager načítání se provádí automaticky na vlastněné typy, to `.Include()` znamená, že není nutné volat na dotaz.

- Lze konfigurovat s `[Owned]`atributem , pomocí EF Core 2.1 a novější.

- Zvládne kolekce vlastněných typů (pomocí verze 2.2 a novější).

#### <a name="owned-entities-limitations"></a>Omezení vlastněných subjektů

- Nelze vytvořit `DbSet<T>` typ vlastněného (záměrně).

- Nelze volat `ModelBuilder.Entity<T>()` na vlastněné typy (aktuálně záměrné).

- Žádná podpora pro volitelné (to znamená, nullable) vlastněné typy, které jsou mapovány s vlastníkem ve stejné tabulce (to znamená pomocí rozdělení tabulky). Důvodem je, že mapování se provádí pro každou vlastnost, nemáme samostatný sentinel pro komplexní hodnotu null jako celek.

- Žádná podpora mapování dědičnosti pro vlastněné typy, ale měli byste být schopni mapovat dva typy listů stejné hierarchie dědičnosti jako různé vlastněné typy. EF Core nebude důvod o tom, že jsou součástí stejné hierarchie.

#### <a name="main-differences-with-ef6s-complex-types"></a>Hlavní rozdíly s komplexními typy EF6

- Rozdělení tabulky je volitelné, to znamená, že mohou být volitelně mapovány na samostatnou tabulku a stále vlastněné typy.

- Mohou odkazovat na jiné entity (to znamená, že mohou působit jako závislá strana na vztazích s jinými nevlastněnými typy).

## <a name="additional-resources"></a>Další zdroje

- **Martin Fowler. Vzor ValueObject** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Návrh řízený doménou: Řešení složitosti v srdci softwaru.** (Kniha; obsahuje diskusi o hodnotových objektech) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon, to je můj zástupce. Implementace návrhu řízeného doménou.** (Kniha; obsahuje diskusi o hodnotových objektech) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Typy vlastněných entit** \
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- **Vlastnosti stínu** \
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- **Komplexní typy a/nebo hodnotové objekty**. Diskuse v úložišti EF Core GitHub (karta Problémy) \
  <https://github.com/dotnet/efcore/issues/246>

- **ValueObject.cs.** Třída objektu základní hodnoty v eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Třída adres.** Ukázková třída objektu hodnoty v eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Předchozí](seedwork-domain-model-base-classes-interfaces.md)
> [další](enumeration-classes-over-enum-types.md)
