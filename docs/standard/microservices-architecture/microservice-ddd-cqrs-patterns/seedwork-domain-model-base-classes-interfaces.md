---
title: "Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d65448bbbed350eb3f75ff2a26ee9097d31eb481
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)

Obsahuje složky řešení *SeedWork* složky. *SeedWork* složka obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty. V každé doméně třída objektu nemáte redundantní kódu použijte tyto základní třídy. Složka pro tyto typy třídy se nazývá *SeedWork* a není něco jako *Framework*. Je volána *SeedWork* vzhledem k tomu, že složka obsahuje pouze malou podmnožinu opakovaně použitelné třídy, které nelze skutečně považovat za rozhraní. *Seedwork* je termín zavedené službou [peří Michael](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a popularized podle [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , ale také mohla mít název této složky běžné, SharedKernel, nebo podobné.

Obrázek 9 – 12 obsahuje třídy, které tvoří seedwork modelu domény v řazení mikroslužby. Má několik vlastní základní třídy jako entita, ValueObject a výčet a navíc několik rozhraní. Tato rozhraní (IRepository a IUnitOfWork) informovat o toho, co je třeba implementovat vrstvě infrastruktury. Tyto rozhraní používají taky pomocí vkládání závislostí z aplikační vrstvu.

![](./media/image13.PNG)

**Obrázek 9 – 12**. Ukázka sada domény modelu "seedwork" základní třídy a rozhraní

Jedná se o typ, kopírování a vkládání opakované použití, celá řada vývojářů sdílet mezi projekty, není formální framework. Můžete mít seedworks v libovolném vrstvy nebo knihovny. Však sadu třídy a rozhraní získá dostatečně velký, můžete chtít vytvořit knihovnu jednu třídu.

## <a name="the-custom-entity-base-class"></a>Vlastní základní třídu Entity

Následující kód je příkladem základní třídu Entity, kde můžete umístit kód, který lze použít stejným způsobem jako ve všech entita domény, jako je například entity ID [operátory rovnosti](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal)atd.

```csharp
// ENTITY FRAMEWORK CORE 1.1
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;

    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }
  
    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() \^ 31;
            // XOR for random distribution. See:
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }

    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }

    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty úložiště (rozhraní) ve vrstvě modelu domény.

Kontrakty úložiště jsou jednoduše rozhraní .NET, která express požadavky kontrakt úložišť má být použit pro každý agregace. Sami úložiště s EF základní kód nebo další závislosti infrastrukturu a kód, nesmí být prováděna v rámci modelu domény; úložiště by měla implementovat jenom rozhraní, které definujete.

Vzor související se tento postup (uvedení rozhraní úložiště vrstva modelu domény) je vzor oddělené rozhraní. Jako [vysvětlené](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) ve Martin Fowler "rozhraní oddělené použijte k definování rozhraní v jednom balíčku ale implementovat v jiném. Tímto způsobem klienta, který potřebuje závislost na rozhraní může být zcela nebere v úvahu implementace."

Následující vzoru oddělené rozhraní umožňuje mít závislost na požadavky definované v modelu domény, ale není přímé závislost na infrastrukturu nebo trvalost aplikační vrstvu (v tomto případě projekt webového rozhraní API pro mikroslužbu) vrstva. Kromě toho izolace implementace, které je implementované v infrastruktuře pomocí vkládání závislostí / vrstvu trvalosti pomocí úložiště.

Například v následujícím příkladu s rozhraním IOrderRepository definuje jakým operacím OrderRepository třída bude nutné implementovat ve vrstvě infrastruktury. V aktuální implementace aplikace kód právě musí přidat pořadí k databázi, vzhledem k tomu, že dotazy jsou následující rozdělení, CQS přístupu a aktualizace objednávky není implementováno.

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
}

public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a>Další zdroje

-   **Martin Fowler. Oddělených rozhraní. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)


>[!div class="step-by-step"]
[Předchozí] (net-core mikroslužbu domény model.md) [Další] (implementace objects.md hodnota)
