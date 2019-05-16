---
title: Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Ke spuštění implementace modelu orientované na DDD domény použijte seedwork koncept jako výchozí bod.
ms.date: 10/08/2018
ms.openlocfilehash: 298f79383e477df0cfeeaada5c4657a9274b3df3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639495"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)

Obsahuje složky řešení *SeedWork* složky. Tato složka obsahuje vlastní základní třídy, které můžete použít jako základ pro domény entity a objekty hodnotu. Použijte tyto základní třídy, takže není nutné redundantní kód ve třídě objektu každé domény. Složka pro tyto typy třídy se nazývá *SeedWork* a nemít něco podobného *Framework*. Je volána *SeedWork* vzhledem k tomu, že složka obsahuje jenom malou podmnožinu opakovaně použitelné třídy, které nelze ve skutečnosti považovat za rozhraní. *Seedwork* termín, který se používá ve [Michael peří](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a který zpopularizoval [Martina Fowlera](https://martinfowler.com/bliki/Seedwork.html) ale může také název této složky obecné SharedKernel, nebo podobného.

Obrázek 7-12 ukazuje třídy, které tvoří seedwork doménový model v pořadí mikroslužeb. Má několik vlastních základních tříd jako Entity a ValueObject, výčet a navíc několik rozhraní. Tato rozhraní (IRepository a IUnitOfWork) vrstvy infrastruktury informuje o tom, co potřebuje k implementaci. Tato rozhraní se také používají pomocí vkládání závislostí z aplikační vrstvy.

![Podrobný obsah složky SeedWork, který obsahuje základní třídy a rozhraní: Entity.cs Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs a ValueObject.cs](./media/image13.PNG)

**Obrázek 7-12**. Ukázka sada domény modelu "seedwork" základní třídy a rozhraní

Toto je typ kopírování a vkládání opakované použití, který mnoho vývojářů sdílet mezi projekty, není formální rozhraní framework. Můžete mít seedworks v libovolné vrstvě nebo knihovny. Ale sadu tříd a rozhraní, získá dostatečně velký, můžete chtít vytvořit knihovnu jednu třídu.

## <a name="the-custom-entity-base-class"></a>Vlastní Entity základní třídy

Následující kód je příklad základní třídu Entity můžete umístit kód, který můžete používat stejným způsobem jako Každá entita domény, jako je například entity ID [operátory rovnosti](~/docs/csharp/language-reference/operators/equality-operators.md), seznam domén událost na entitu, atd.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;    
    private List<INotification> _domainEvents;
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

    public List<INotification> DomainEvents => _domainEvents;        
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
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
                _requestedHashCode = this.Id.GetHashCode() ^ 31;
            // XOR for random distribution. See:
            // https://blogs.msdn.microsoft.com/ericlippert/2011/02/28/guidelines-and-rules-for-gethashcode/
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null));
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

Předchozí kód pomocí seznam domén událost na entitu se vysvětlené v následujících částech při zaměření na události domény.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty úložiště (rozhraní) ve vrstvě doménového modelu

Kontrakty úložiště jsou jednoduše rozhraní .NET, které express požadavky smlouvy z úložišť pro každou agregaci.

Úložiště sami, s EF Core kódu nebo další závislosti infrastrukturu a kód (Linq, SQL atd.), nesmí být prováděna v rámci modelu domény úložiště by měly implementovat pouze rozhraní, které definujete v doménovém modelu.

Vzor související se tento postup (umístěním úložiště rozhraní ve vrstvě doménového modelu) je model oddělených rozhraní. Jako [vysvětlení](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) od Martina Fowlera "oddělené rozhraní k definování rozhraní v jednom balíčku, ale implementovat v jiném. Tímto způsobem klient, který potřebuje závislost na rozhraní můžete zcela je nezajímat se o implementace."

Následující vzorek oddělených rozhraní umožňuje mít závislost na požadavky definované v modelu domény, ale ne přímou závislost na infrastrukturu nebo trvalost aplikační vrstvu (v tomto případě projekt webového rozhraní API pro mikroslužbách) vrstva. Kromě toho můžete použít injektáž závislostí izolovat implementace, které je implementované v infrastruktuře / vrstvy trvalosti pomocí úložišť.

Například následující příklad rozhraní IOrderRepository definuje jaké operace třída OrderRepository potřebovat provádět na vrstvě infrastruktury. Aktuální provádění aplikace kód jenom je potřeba přidat nebo aktualizovat objednávky do databáze, protože dotazy jsou rozděleny podle zjednodušený přístup modelu CQRS.

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);

    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a>Další zdroje

- **Martina Fowlera. Oddělených rozhraní.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Předchozí](net-core-microservice-domain-model.md)
>[další](implement-value-objects.md)
