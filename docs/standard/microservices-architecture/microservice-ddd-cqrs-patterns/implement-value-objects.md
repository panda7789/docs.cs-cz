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
# <a name="implementing-value-objects"></a>Implementace hodnota objekty

Jak je popsáno v předchozích částech o entity a agregace, identita je zásadní pro entity. Existují však mnoho objektů a dat položky v rámci systému, které nevyžadují, aby identita a identity, jako je například hodnota objektů pro sledování.

Objekt hodnoty můžete odkazovat ostatní entity. Například v aplikaci, která generuje trasu, která popisuje, jak získat z jednoho bodu do jiného že směrování by objekt hodnoty. Je snímek body na konkrétní trase, ale tato trasa navrhované neměli svou identitu, i když interně může odkazovat na entity města, silniční, atd.

Obrázek 9 – 13 ukazuje objekt hodnoty adres v rámci agregace pořadí.

![](./media/image14.png)

**Obrázek 9 – 13**. Adresa hodnota objekt v rámci agregace pořadí

Jak znázorňuje obrázek 9 – 13, entity se obvykle skládá z více atributů. Například pořadí můžete modelován jako entity s identitou a interně tvořený sadu atributů například OrderId, OrderDate, OrderItems atd. Ale na adresu, což je jednoduše komplexní hodnota skládá z země, ulici, města, musí být modelovány a považován za objekt hodnoty atd.

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
    // Other utilility methods
}
```

Tuto třídu můžete použít při implementaci skutečnou hodnotu objektu, stejně jako u adres objekt hodnoty vidět v následujícím příkladu:

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

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>Skrytí vlastnosti identity při použití EF základní udržení hodnota objekty

Omezení při použití EF základní je, že v jeho aktuální verze (EF základní 1.1) nelze použít [komplexní typy](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) definovaným v EF 6.x. Proto musíte uložit hodnotu objektu jako EF entity. Však můžete skrýt jeho ID, takže byste měli vytvořit jasné, že identita není důležité v modelu, který je součástí objekt hodnoty. Skrýt ID je pomocí ID jako vlastnost stínové. Vzhledem k tomu, že tato konfigurace pro skrytí ID v modelu je nastaven na úrovni infrastruktury, je transparentní pro váš model domény a jeho implementace infrastruktury může v budoucnu změnit.

Skrytá ID vyžaduje EF základní infrastruktury je v eShopOnContainers, implementovaná tímto způsobem na úrovni DbContext pomocí rozhraní Fluent API v projektu OMI.

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

Proto ID je skrytý z hlediska domény modelu a v budoucnu infrastruktury objekt hodnotu lze také implementovat jako komplexní typ nebo jiným způsobem.

## <a name="additional-resources"></a>Další zdroje

-   **Martin Fowler. Vzor ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru.** (Sešit; zahrnuje diskuzi o hodnotu objekty) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Implementace návrhu řízené domény.** (Sešit; zahrnuje diskuzi o hodnotu objekty) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Komplexní typy nebo hodnoty objekty**. Diskusi do úložiště GitHub základní EF (karta problémy) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Základní hodnota třída objektu v eShopOnContainers.
    [*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Třídy adres.** Ukázka třídy objektu hodnotu v eShopOnContainers.
    [*https://github.com/DotNet/eShopOnContainers/BLOB/Master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
[Předchozí] (seedwork-domain-model-base-classes-interfaces.md) [Další] (výčet třídy over výčtu types.md)
