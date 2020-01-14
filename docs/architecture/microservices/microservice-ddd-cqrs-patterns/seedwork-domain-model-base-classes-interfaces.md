---
title: Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Použijte koncept seedwork jako výchozí bod pro zahájení implementace pro doménový model orientovaný na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 491ff39f493a8f5ab192dc4a8376f560a8a7624b
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937177"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)

Složka řešení obsahuje složku *SeedWork* . Tato složka obsahuje vlastní základní třídy, které lze použít jako základ pro vaše doménové entity a objekty hodnot. Použijte tyto základní třídy, takže nemáte redundantní kód ve třídě objektu v každé doméně. Složka pro tyto typy tříd se nazývá *SeedWork* a ne jako *rozhraní*. Má název *SeedWork* , protože složka obsahuje pouze malou podmnožinu opakovaně použitelných tříd, které nemohou být skutečně považovány za rozhraní. *Seedwork* je pojem, který zavádí [Michael peří](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a je oblíbený pomocí [Novák Fowlera](https://martinfowler.com/bliki/Seedwork.html) , ale můžete také pojmenovat složku Common, SharedKernel nebo podobnou.

Obrázek 7-12 ukazuje třídy, které tvoří seedwork doménového modelu při řazení mikroslužby. Má několik vlastních základních tříd, jako je entita, ValueObject a výčet, a navíc několik rozhraní. Tato rozhraní (IRepository a IUnitOfWork) informují vrstvu infrastruktury o tom, co je potřeba implementovat. Tato rozhraní se používají také prostřednictvím injektáže závislosti z aplikační vrstvy.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Snímek obrazovky tříd obsažených ve složce SeedWork":::
Podrobný obsah složky SeedWork obsahující základní třídy a rozhraní: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs a ValueObject.cs.
:::image-end:::

**Obrázek 7-12**. Ukázková sada základních tříd a rozhraní doménové modelu seedwork

Toto je typ opakovaného použití kopírování a vložení, který mnoho vývojářů sdílí mezi projekty, nikoli formálním rozhraním. Můžete mít seedworks v libovolné vrstvě nebo knihovně. Nicméně pokud sada tříd a rozhraní bude dostatečně velká, může být vhodné vytvořit jedinou knihovnu tříd.

## <a name="the-custom-entity-base-class"></a>Třída Custom entity Base

Následující kód je příkladem základní třídy entity, kde můžete umístit kód, který lze použít stejným způsobem jako jakákoli entita domény, například ID entity, [operátory rovnosti](../../../csharp/language-reference/operators/equality-operators.md), seznam událostí domény na entitu atd.

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

Předchozí kód, který používá seznam událostí domény pro každou entitu, bude vysvětlený v dalších částech při zaměření na události domény.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty úložiště (rozhraní) ve vrstvě doménového modelu

Kontrakty úložiště jsou jednoduše rozhraní .NET, která vyjadřují požadavky na kontrakt úložišť, která se mají použít pro každou agregaci.

Samotná úložiště nesmí být v doménovém modelu implementovaná pomocí EF Coreho kódu nebo jakýchkoli jiných závislostí infrastruktury a kódu (LINQ, SQL atd.). úložiště by měla implementovat pouze rozhraní, které definujete v doménovém modelu.

Vzor vztahující se k tomuto postupu (umístění rozhraní úložiště do vrstvy doménové struktury) je model odděleného rozhraní. Jak [je vysvětleno](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) v Martinu Fowlera, "použijte oddělené rozhraní k definování rozhraní v jednom balíčku, ale jeho implementaci v jiném. Tímto způsobem klient, který potřebuje závislost na rozhraní, může zcela nevědět o implementaci. "

Po použití vzoru odděleného rozhraní umožňuje aplikační vrstvě (v tomto případě projekt webového rozhraní API pro mikroslužeb) závislosti na požadavcích definovaných v doménovém modelu, ale ne na přímé závislosti na vrstvě infrastruktury/trvalosti. Navíc můžete pomocí injektáže závislosti izolovat implementaci, která je implementována v infrastruktuře/trvalosti vrstvy pomocí úložišť.

Například následující příklad s rozhraním IOrderRepository definuje, které operace bude třída OrderRepository potřebovat implementovat na vrstvu infrastruktury. V aktuální implementaci aplikace kód pouze potřebuje přidat nebo aktualizovat Objednávky do databáze, protože dotazy jsou rozděleny podle zjednodušeného přístupu CQRS.

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

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Martin Fowlera. Rozhraní oddělené.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Předchozí](net-core-microservice-domain-model.md)
>[Další](implement-value-objects.md)
