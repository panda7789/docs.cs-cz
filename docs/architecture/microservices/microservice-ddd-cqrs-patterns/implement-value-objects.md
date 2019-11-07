---
title: Implementace objektů hodnot
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Získejte informace a možnosti pro implementaci objektů hodnot pomocí nových funkcí Entity Framework.
ms.date: 10/08/2018
ms.openlocfilehash: 2608517c4006f5e8da1d31b2c337d8ddd3ddd542
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739865"
---
# <a name="implement-value-objects"></a>Implementace objektů hodnot

Jak je popsáno výše v části informace o entitách a agregacích, je identita pro entity zásadní. V systému je však mnoho objektů a datových položek, které nevyžadují sledování identity a identity, jako jsou například objekty hodnot.

Objekt hodnoty může odkazovat na jiné entity. Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do druhého, by tento postup představoval objekt hodnoty. Může to být snímek bodů na konkrétní trase, ale tato navrhovaná trasa by nemusela mít identitu, i když interně by se mohla vztahovat na entity jako City, Road atd.

Obrázek 7-13 ukazuje objekt hodnoty adresy v rámci agregace pořadí.

![Diagram znázorňující hodnotu adresa – objekt uvnitř agregace objednávky](./media/implement-value-objects/value-object-within-aggregate.png)

**Obrázek 7-13**. Hodnota objektu adresy v rámci agregace objednávky

Jak je znázorněno na obrázku 7-13, entita se obvykle skládá z více atributů. Například entita `Order` může být modelována jako entita s identitou a složená interně ze sady atributů, jako je například ČísloObjednávky, DatumObjednávky, OrderItems atd. Ale adresa, která je prostě složitou hodnotu složenou ze země/oblasti, ulice, města atd. a nemá v této doméně žádnou identitu, musí být modelována a zpracována jako objekt hodnoty.

## <a name="important-characteristics-of-value-objects"></a>Důležité vlastnosti objektů hodnot

Existují dvě hlavní vlastnosti pro objekty hodnot:

- Nemají žádnou identitu.

- Jsou neměnné.

První charakterizace již byla diskutována. Neměnnosti je důležitým požadavkem. Hodnoty objektu hodnoty musí být po vytvoření objektu neměnné. Proto je-li objekt vytvořen, je nutné zadat požadované hodnoty, ale je nutné, aby se během životnosti objektu nepovolily měnit.

Objekty hodnot umožňují provádět určité štychy pro výkon, a to díky jejich neměnnému charakteru. To je obzvláště pravdivé v systémech, kde může existovat tisíce instancí objektů hodnot, mnoho z nich má stejné hodnoty. Jejich neproměnlivá povaha umožňuje jejich použití znovu; můžou se jednat o objekty, které mají být zaměnitelné, protože jejich hodnoty jsou stejné a nemají žádnou identitu. Tento typ optimalizace může někdy způsobit rozdíl mezi softwarem, který běží pomalu, a softwarem s dobrým výkonem. Všechny tyto případy jsou samozřejmě závislé na prostředí aplikace a kontextu nasazení.

## <a name="value-object-implementation-in-c"></a>Implementace objektu hodnoty v jazyce C\#

V souvislosti s implementací můžete mít základní třídu objektu hodnoty, která má základní obslužné metody, jako je rovnost na základě porovnání všech atributů (vzhledem k tomu, že objekt hodnoty nesmí být založen na identitě) a další základní charakteristiky. Následující příklad ukazuje základní třídu hodnotového objektu použitou při řazení mikroslužby z eShopOnContainers.

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

Tuto třídu můžete použít při implementaci vlastního objektu Value, stejně jako objekt hodnoty adresy zobrazený v následujícím příkladu:

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

Můžete zjistit, jak tato implementace objektu hodnoty nemá žádnou identitu, a proto žádné pole ID není ani na třídě Address ani na třídě ValueObject.

Neexistence pole ID ve třídě, která má být použita Entity Framework nebyla možná, dokud EF Core 2,0, což významně pomáhá implementovat lépe vícehodnotové objekty bez ID. To je přesně vysvětlení další části.

Může být namítáno, že objekty hodnot, které jsou neměnné, by měly být jen pro čtení (tj. vlastnosti jen pro získání), a to vlastně pravdivé. Objekty hodnot se ale obvykle serializovat a deserializovat, aby procházely přes fronty zpráv a jen pro čtení zastaví deserializaci, aby bylo možné přiřadit hodnoty, takže je pouze máme soukromá sada, která je dostatečně čitelná, aby mohla být praktická.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Jak zachovat objekty hodnot v databázi pomocí EF Core 2,0

Právě jste viděli, jak v doménovém modelu definovat objekt hodnoty. Ale jak můžete ve skutečnosti uchovávat v databázi prostřednictvím jádra Entity Framework (EF), která obvykle cílí na entity s identitou?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Pozadí a starší přístupy pomocí EF Core 1,1

Jako pozadí omezení při použití EF Core 1,0 a 1,1 bylo, že nemůžete použít [komplexní typy](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) definované v EF 6. x v tradičním .NET Framework. Proto pokud používáte EF Core 1,0 nebo 1,1, je třeba uložit objekt hodnoty jako entitu EF s polem ID. Proto, aby vypadala podobně jako objekt hodnoty bez identity, mohli byste skrýt jeho ID, aby bylo jasné, že identita objektu value není v doménovém modelu důležitá. Toto ID můžete skrýt pomocí ID jako [vlastnosti Shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Vzhledem k tomu, že konfigurace pro skrývání ID v modelu je nastavená na úrovni infrastruktury EF, bude to pro váš doménový model transparentní.

V počáteční verzi eShopOnContainers (.NET Core 1,1) se skryté ID, které potřebuje infrastruktura EF Core, implementovalo následujícím způsobem na úrovni DbContext, pomocí rozhraní Fluent API v projektu infrastruktury. Z tohoto důvodu bylo ID z hlediska doménového modelu skryté, ale stále přítomné v infrastruktuře.

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

Trvalost tohoto objektu Value do databáze se ale prováděla jako regulární entita v jiné tabulce.

S EF Core 2,0 existují nové a lepší způsoby, jak zachovat objekty hodnot.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Zachovat objekty hodnot jako vlastněné typy entit v EF Core 2,0

I s některými mezerami mezi vzorem objektu kanonické hodnoty v DDD a vlastněnou entitou typu v EF Core je aktuálně nejlepším způsobem, jak zachovat objekty hodnot pomocí EF Core 2,0. Na konci této části můžete vidět omezení.

Do EF Core od verze 2,0 byla přidána funkce typu vlastněné entity.

Vlastněný typ entity umožňuje mapovat typy, které nemají vlastní identitu explicitně definované v doménovém modelu a jsou používány jako vlastnosti, jako je například objekt hodnoty, v rámci kterékoli z entit. Vlastněný typ entity sdílí stejný typ CLR s jiným typem entity (to znamená pouze regulární třída). Entita obsahující definici navigace je entitou vlastníka. Při dotazování vlastníka jsou ve výchozím nastavení zahrnuty vlastní typy.

Podobně jako při prohlížení doménového modelu vypadá vlastněný typ, který nemá žádnou identitu. Nicméně v rámci pokrývání mají vlastněné typy identitu, ale vlastnost navigace vlastníka je součástí této identity.

Identita instancí vlastněných typů není zcela vlastní. Skládá se ze tří součástí:

- Identita vlastníka

- Navigační vlastnost, na kterou se odkazuje

- V případě kolekcí vlastněných typů se nezávislá komponenta (zatím nepodporovaná v EF Core 2,0, která se nachází na 2,2).

Například v modelu domény řazení na eShopOnContainers jako součást entity Order je objekt hodnoty adresy implementován jako vlastněný typ entity v rámci entity Owner, která je objednávka. Adresa je typ bez vlastnosti identity definované v doménovém modelu. Slouží jako vlastnost typu objednávky k určení dodací adresy pro konkrétní objednávku.

Podle konvence se vytvoří stínový primární klíč pro vlastní typ a bude namapován na stejnou tabulku jako vlastník pomocí rozdělení tabulky. To umožňuje použít vlastněné typy podobně jako složité typy používané v EF6 v tradičním .NET Framework.

Je důležité si uvědomit, že vlastní typy nejsou nikdy zjištěny v konvenci v EF Core, takže je musíte deklarovat explicitně.

V eShopOnContainers platí, že v OrderingContext.cs v rámci metody OnModelCreating () existuje více konfigurací infrastruktury. Jedna z nich se vztahuje k entitě Order.

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

V následujícím kódu je pro entitu pro objednávku definována infrastruktura trvalosti:

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

V předchozím kódu metoda `orderConfiguration.OwnsOne(o => o.Address)` určuje, že vlastnost `Address` je vlastněnou entitou typu `Order`.

Ve výchozím nastavení EF Core konvence pojmenují sloupce databáze pro vlastnosti typu vlastněné entity jako `EntityProperty_OwnedEntityProperty`. Proto se vnitřní vlastnosti `Address` zobrazí v tabulce `Orders` s názvy `Address_Street``Address_City` (atd. `State``Country` a `ZipCode`).

K přejmenování těchto sloupců můžete připojit metodu `Property().HasColumnName()` Fluent. V případě, kdy `Address` je veřejná vlastnost, by mapování vypadalo takto:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Je možné zřetězit metodu `OwnsOne` v mapování Fluent. V následujícím hypotetickém příkladu `OrderDetails` vlastní `BillingAddress` a `ShippingAddress`, které jsou oba `Address` typy. Pak `OrderDetails` vlastní `Order` typ.

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

### <a name="additional-details-on-owned-entity-types"></a>Další podrobnosti o vlastněných typech entit

- Vlastněné typy jsou definovány při konfiguraci navigační vlastnosti na konkrétní typ pomocí rozhraní OwnsOne Fluent API.

- Definice vlastněného typu v našem modelu metadat je složená z: typ vlastníka, navigační vlastnost a typ CLR vlastněných typů.

- Identita (klíč) instance vlastního typu v našem zásobníku je složena z identity typu vlastníka a definice vlastněného typu.

#### <a name="owned-entities-capabilities"></a>Možnosti vlastněných entit:

- Vlastněné typy mohou odkazovat na jiné entity, buď vlastněné (vnořené vlastněné typy), nebo nevlastní (standardní referenční vlastnosti navigace jiným entitám).

- Stejný typ CLR můžete mapovat jako jiné vlastněné typy ve stejné entitě Owner prostřednictvím samostatných vlastností navigace.

- Rozdělení tabulky je nastavení podle konvence, ale můžete si ji vyfiltrovat tak, že namapujete vlastněný typ na jinou tabulku pomocí ToTable.

- Načítání Eager se provádí automaticky na vlastněných typech, tj. není nutné volat include () na dotaz.

- Dá se nakonfigurovat s atributem \[vlastní\], od EF Core 2,1

#### <a name="owned-entities-limitations"></a>Omezení entit vlastněných entitami:

- Nemůžete vytvořit\> Negenerickými\<T vlastněných typu (podle návrhu).

- Nelze volat ModelBuilder. entity\<T\>() na vlastněných typech (aktuálně podle návrhu).

- Zatím nejsou žádné kolekce vlastněných typů (od EF Core 2,1, ale budou podporované v 2,2).

- Není podporována podpora volitelného typu (to znamená Nullable), který je namapován s vlastníkem ve stejné tabulce (tj. použití rozdělení tabulky). Důvodem je to, že mapování se provádí pro každou vlastnost, ale nepoužíváme samostatnou sentinelou pro komplexní hodnotu null a jako celek.

- Pro vlastněné typy není podporovaná podpora mapování dědičnosti, ale měli byste být schopni mapovat dva typy listů stejných hierarchií dědičnosti jako jiné vlastněné typy. EF Core nebude mít důvod k tomu, že jsou součástí stejné hierarchie.

#### <a name="main-differences-with-ef6s-complex-types"></a>Hlavní rozdíly s EF6's komplexními typy

- Rozdělení tabulky je volitelné, tj. je možné je volitelně namapovat na samostatnou tabulku a nadále mít vlastní typy.

- Můžou odkazovat na jiné entity (to znamená, že můžou fungovat jako závislá strana na vztazích s jinými nevlastními typy).

## <a name="additional-resources"></a>Další zdroje

- **Martin Fowlera. \ vzor ValueObject**
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Návrh založený na doméně: řešení složitosti na srdce softwaru.** (Kniha; obsahuje diskuzi o objektech hodnot) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon. Implementace návrhu založeného na doméně.** (Kniha; obsahuje diskuzi o objektech hodnot) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vlastnosti stínu** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Komplexní typy a/nebo hodnotové objekty**. Diskuze v úložišti GitHubu EF Core (karta problémy) \
  <https://github.com/aspnet/EntityFramework/issues/246>

- **ValueObject.cs.** Třída objektů základní hodnoty v eShopOnContainers \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Adresa třídy.** Ukázková hodnota třídy objektu v eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Předchozí](seedwork-domain-model-base-classes-interfaces.md)
> [Další](enumeration-classes-over-enum-types.md)
