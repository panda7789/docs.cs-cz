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
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="7349b-103">Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)</span><span class="sxs-lookup"><span data-stu-id="7349b-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="7349b-104">Složka řešení obsahuje složku *SeedWork.*</span><span class="sxs-lookup"><span data-stu-id="7349b-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="7349b-105">Tato složka obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="7349b-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="7349b-106">Použijte tyto základní třídy, takže nemáte redundantní kód v každé třídě objektů domény.</span><span class="sxs-lookup"><span data-stu-id="7349b-106">Use these base classes so you don't have redundant code in each domain's object class.</span></span> <span data-ttu-id="7349b-107">Složka pro tyto typy tříd se nazývá *SeedWork* a ne něco jako *Framework*.</span><span class="sxs-lookup"><span data-stu-id="7349b-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="7349b-108">Nazývá se *SeedWork,* protože složka obsahuje pouze malou podmnožinu opakovaně použitelných tříd, které nelze skutečně považovat za rámec.</span><span class="sxs-lookup"><span data-stu-id="7349b-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes that cannot really be considered a framework.</span></span> <span data-ttu-id="7349b-109">*Seedwork* je termín zavedený [Michael feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a popularizoval [Martin Fowler,](https://martinfowler.com/bliki/Seedwork.html) ale můžete také název, že složka Společné, SharedKernel, nebo podobné.</span><span class="sxs-lookup"><span data-stu-id="7349b-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="7349b-110">Obrázek 7-12 ukazuje třídy, které tvoří seedwork modelu domény v objednávání mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="7349b-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="7349b-111">Má několik vlastních základních tříd, jako je Entita, ValueObject a Výčet, plus několik rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7349b-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="7349b-112">Tato rozhraní (IRepository a IUnitOfWork) informují vrstvu infrastruktury o tom, co je třeba implementovat.</span><span class="sxs-lookup"><span data-stu-id="7349b-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="7349b-113">Tato rozhraní se také používají prostřednictvím vkládání závislostí z aplikační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="7349b-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Snímek obrazovky s třídami obsaženými ve složce SeedWork":::
<span data-ttu-id="7349b-115">Podrobný obsah složky SeedWork obsahující základní třídy a rozhraní: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs a ValueObject.cs.</span><span class="sxs-lookup"><span data-stu-id="7349b-115">The detailed contents of the SeedWork folder, containing base classes and interfaces: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs, and ValueObject.cs.</span></span>
:::image-end:::

<span data-ttu-id="7349b-116">**Obrázek 7-12**.</span><span class="sxs-lookup"><span data-stu-id="7349b-116">**Figure 7-12**.</span></span> <span data-ttu-id="7349b-117">Ukázková sada základních tříd a rozhraní modelu domény "seedwork"</span><span class="sxs-lookup"><span data-stu-id="7349b-117">A sample set of domain model "seedwork" base classes and interfaces</span></span>

<span data-ttu-id="7349b-118">Toto je typ kopírování a vkládání opakované použití, které mnoho vývojářů sdílet mezi projekty, nikoli formální rámec.</span><span class="sxs-lookup"><span data-stu-id="7349b-118">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="7349b-119">Seedworks můžete mít v libovolné vrstvě nebo knihovně.</span><span class="sxs-lookup"><span data-stu-id="7349b-119">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="7349b-120">Pokud je však sada tříd a rozhraní dostatečně velká, můžete vytvořit jednu knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="7349b-120">However, if the set of classes and interfaces gets large enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="7349b-121">Základní třída vlastní entity</span><span class="sxs-lookup"><span data-stu-id="7349b-121">The custom Entity base class</span></span>

<span data-ttu-id="7349b-122">Následující kód je příkladem základní třídy entity, kde můžete umístit kód, který může použít stejným způsobem libovolná entita domény, například ID entity, [operátory rovnosti](../../../csharp/language-reference/operators/equality-operators.md), seznam událostí domény pro každou entitu atd.</span><span class="sxs-lookup"><span data-stu-id="7349b-122">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](../../../csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

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

<span data-ttu-id="7349b-123">Předchozí kód pomocí seznamu událostí domény pro jednotlivé entity bude vysvětlen v dalších částech při zaměření na události domény.</span><span class="sxs-lookup"><span data-stu-id="7349b-123">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="7349b-124">Kontrakty úložiště (rozhraní) ve vrstvě modelu domény</span><span class="sxs-lookup"><span data-stu-id="7349b-124">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="7349b-125">Kontrakty úložiště jsou jednoduše rozhraní .NET, která vyjadřují požadavky na smlouvy úložišť, které mají být použity pro každou agregaci.</span><span class="sxs-lookup"><span data-stu-id="7349b-125">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="7349b-126">Samotná úložiště s EF core kódem nebo jinými závislostmi infrastruktury a kódem (Linq, SQL atd.) nesmí být implementována v rámci modelu domény; úložiště by měla implementovat pouze rozhraní, která definujete v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="7349b-126">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="7349b-127">Vzor související s touto praxí (umístění rozhraní úložiště ve vrstvě modelu domény) je vzor odděleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7349b-127">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="7349b-128">Jak [vysvětlil](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, "Použijte oddělené rozhraní definovat rozhraní v jednom balíčku, ale implementovat v jiném.</span><span class="sxs-lookup"><span data-stu-id="7349b-128">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, "Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="7349b-129">Tímto způsobem klient, který potřebuje závislost na rozhraní může být zcela nevědomý implementace."</span><span class="sxs-lookup"><span data-stu-id="7349b-129">This way a client that needs the dependency to the interface can be completely unaware of the implementation."</span></span>

<span data-ttu-id="7349b-130">Následující vzor oddělené rozhraní umožňuje aplikační vrstvy (v tomto případě projekt webového rozhraní API pro mikroslužbu) mít závislost na požadavky definované v modelu domény, ale ne přímou závislost na vrstvě infrastruktury/trvalosti.</span><span class="sxs-lookup"><span data-stu-id="7349b-130">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="7349b-131">Kromě toho můžete použít vkládání závislostí izolovat implementaci, která je implementována ve vrstvě infrastruktury/ trvalosti pomocí úložišť.</span><span class="sxs-lookup"><span data-stu-id="7349b-131">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="7349b-132">Například následující příklad s rozhraním IOrderRepository definuje, jaké operace orderrepository třídy bude muset implementovat ve vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="7349b-132">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="7349b-133">V aktuální implementaci aplikace kód stačí přidat nebo aktualizovat objednávky do databáze, protože dotazy jsou rozděleny podle zjednodušeného přístupu CQRS.</span><span class="sxs-lookup"><span data-stu-id="7349b-133">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="7349b-134">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="7349b-134">Additional resources</span></span>

- <span data-ttu-id="7349b-135">**Martin Fowler. Oddělené rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="7349b-135">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="7349b-136">[Předchozí](net-core-microservice-domain-model.md)
>[další](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="7349b-136">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
