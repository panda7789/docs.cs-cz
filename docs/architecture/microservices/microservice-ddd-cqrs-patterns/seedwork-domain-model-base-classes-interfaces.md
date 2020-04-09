---
title: Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pomocí konceptu seedwork jako výchozí bod pro spuštění implementace pro model domény orientované na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 545be2723ba468a5fd65f81978799328234ca113
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988307"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)

Složka řešení obsahuje složku *SeedWork.* Tato složka obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a objekty hodnot. Použijte tyto základní třídy, takže nemáte redundantní kód v každé třídě objektů domény. Složka pro tyto typy tříd se nazývá *SeedWork* a ne něco jako *Framework*. Nazývá se *SeedWork,* protože složka obsahuje pouze malou podmnožinu opakovaně použitelných tříd, které nelze skutečně považovat za rámec. *Seedwork* je termín zavedený [Michael feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a popularizoval [Martin Fowler,](https://martinfowler.com/bliki/Seedwork.html) ale můžete také název, že složka Společné, SharedKernel, nebo podobné.

Obrázek 7-12 ukazuje třídy, které tvoří seedwork modelu domény v objednávání mikroslužby. Má několik vlastních základních tříd, jako je Entita, ValueObject a Výčet, plus několik rozhraní. Tato rozhraní (IRepository a IUnitOfWork) informují vrstvu infrastruktury o tom, co je třeba implementovat. Tato rozhraní se také používají prostřednictvím vkládání závislostí z aplikační vrstvy.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Snímek obrazovky s třídami obsaženými ve složce SeedWork":::
Podrobný obsah složky SeedWork obsahující základní třídy a rozhraní: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs a ValueObject.cs.
:::image-end:::

**Obrázek 7-12**. Ukázková sada základních tříd a rozhraní modelu domény "seedwork"

Toto je typ kopírování a vkládání opakované použití, které mnoho vývojářů sdílet mezi projekty, nikoli formální rámec. Seedworks můžete mít v libovolné vrstvě nebo knihovně. Pokud je však sada tříd a rozhraní dostatečně velká, můžete vytvořit jednu knihovnu tříd.

## <a name="the-custom-entity-base-class"></a>Základní třída vlastní entity

Následující kód je příkladem základní třídy entity, kde můžete umístit kód, který může použít stejným způsobem libovolná entita domény, například ID entity, [operátory rovnosti](../../../csharp/language-reference/operators/equality-operators.md), seznam událostí domény pro každou entitu atd.

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
            // https://docs.microsoft.com/archive/blogs/ericlippert/guidelines-and-rules-for-gethashcode
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

Předchozí kód pomocí seznamu událostí domény pro jednotlivé entity bude vysvětlen v dalších částech při zaměření na události domény.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty úložiště (rozhraní) ve vrstvě modelu domény

Kontrakty úložiště jsou jednoduše rozhraní .NET, která vyjadřují požadavky na smlouvy úložišť, které mají být použity pro každou agregaci.

Samotná úložiště s EF core kódem nebo jinými závislostmi infrastruktury a kódem (Linq, SQL atd.) nesmí být implementována v rámci modelu domény; úložiště by měla implementovat pouze rozhraní, která definujete v modelu domény.

Vzor související s touto praxí (umístění rozhraní úložiště ve vrstvě modelu domény) je vzor odděleného rozhraní. Jak [vysvětlil](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, "Použijte oddělené rozhraní definovat rozhraní v jednom balíčku, ale implementovat v jiném. Tímto způsobem klient, který potřebuje závislost na rozhraní může být zcela nevědomý implementace."

Následující vzor oddělené rozhraní umožňuje aplikační vrstvy (v tomto případě projekt webového rozhraní API pro mikroslužbu) mít závislost na požadavky definované v modelu domény, ale ne přímou závislost na vrstvě infrastruktury/trvalosti. Kromě toho můžete použít vkládání závislostí izolovat implementaci, která je implementována ve vrstvě infrastruktury/ trvalosti pomocí úložišť.

Například následující příklad s rozhraním IOrderRepository definuje, jaké operace orderrepository třídy bude muset implementovat ve vrstvě infrastruktury. V aktuální implementaci aplikace kód stačí přidat nebo aktualizovat objednávky do databáze, protože dotazy jsou rozděleny podle zjednodušeného přístupu CQRS.

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

- **Martin Fowler. Oddělené rozhraní.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Předchozí](net-core-microservice-domain-model.md)
>[další](implement-value-objects.md)
