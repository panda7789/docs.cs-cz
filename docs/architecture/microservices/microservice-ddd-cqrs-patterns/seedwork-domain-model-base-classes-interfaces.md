---
title: Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Použijte koncept seedwork jako výchozí bod pro zahájení implementace pro doménový model orientovaný na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: ab0aadc28dbd1175c75b04dadca29b7b0947f29b
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116567"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="213f9-103">Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)</span><span class="sxs-lookup"><span data-stu-id="213f9-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="213f9-104">Složka řešení obsahuje složku *SeedWork* .</span><span class="sxs-lookup"><span data-stu-id="213f9-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="213f9-105">Tato složka obsahuje vlastní základní třídy, které lze použít jako základ pro vaše doménové entity a objekty hodnot.</span><span class="sxs-lookup"><span data-stu-id="213f9-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="213f9-106">Použijte tyto základní třídy, takže nemáte redundantní kód ve třídě objektu v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="213f9-106">Use these base classes so you don't have redundant code in each domain’s object class.</span></span> <span data-ttu-id="213f9-107">Složka pro tyto typy tříd se nazývá *SeedWork* a ne jako *rozhraní*.</span><span class="sxs-lookup"><span data-stu-id="213f9-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="213f9-108">Má název *SeedWork* , protože složka obsahuje pouze malou podmnožinu opakovaně použitelných tříd, které nemohou být skutečně považovány za rozhraní.</span><span class="sxs-lookup"><span data-stu-id="213f9-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes that cannot really be considered a framework.</span></span> <span data-ttu-id="213f9-109">*Seedwork* je pojem, který zavádí [Michael peří](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a je oblíbený pomocí [Novák Fowlera](https://martinfowler.com/bliki/Seedwork.html) , ale můžete také pojmenovat složku Common, SharedKernel nebo podobnou.</span><span class="sxs-lookup"><span data-stu-id="213f9-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="213f9-110">Obrázek 7-12 ukazuje třídy, které tvoří seedwork doménového modelu při řazení mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="213f9-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="213f9-111">Má několik vlastních základních tříd, jako je entita, ValueObject a výčet, a navíc několik rozhraní.</span><span class="sxs-lookup"><span data-stu-id="213f9-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="213f9-112">Tato rozhraní (IRepository a IUnitOfWork) informují vrstvu infrastruktury o tom, co je potřeba implementovat.</span><span class="sxs-lookup"><span data-stu-id="213f9-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="213f9-113">Tato rozhraní se používají také prostřednictvím injektáže závislosti z aplikační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="213f9-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Snímek obrazovky tříd obsažených ve složce SeedWork":::
<span data-ttu-id="213f9-115">Podrobný obsah složky SeedWork obsahující základní třídy a rozhraní: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs a ValueObject.cs.</span><span class="sxs-lookup"><span data-stu-id="213f9-115">The detailed contents of the SeedWork folder, containing base classes and interfaces: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs, and ValueObject.cs.</span></span>
:::image-end:::

<span data-ttu-id="213f9-116">**Obrázek 7-12**.</span><span class="sxs-lookup"><span data-stu-id="213f9-116">**Figure 7-12**.</span></span> <span data-ttu-id="213f9-117">Ukázková sada základních tříd a rozhraní doménové modelu seedwork</span><span class="sxs-lookup"><span data-stu-id="213f9-117">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="213f9-118">Toto je typ opakovaného použití kopírování a vložení, který mnoho vývojářů sdílí mezi projekty, nikoli formálním rozhraním.</span><span class="sxs-lookup"><span data-stu-id="213f9-118">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="213f9-119">Můžete mít seedworks v libovolné vrstvě nebo knihovně.</span><span class="sxs-lookup"><span data-stu-id="213f9-119">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="213f9-120">Nicméně pokud sada tříd a rozhraní bude dostatečně velká, může být vhodné vytvořit jedinou knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="213f9-120">However, if the set of classes and interfaces gets large enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="213f9-121">Třída Custom entity Base</span><span class="sxs-lookup"><span data-stu-id="213f9-121">The custom Entity base class</span></span>

<span data-ttu-id="213f9-122">Následující kód je příkladem základní třídy entity, kde můžete umístit kód, který lze použít stejným způsobem jako jakákoli entita domény, například ID entity, [operátory rovnosti](../../../csharp/language-reference/operators/equality-operators.md), seznam událostí domény na entitu atd.</span><span class="sxs-lookup"><span data-stu-id="213f9-122">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](../../../csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

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

<span data-ttu-id="213f9-123">Předchozí kód, který používá seznam událostí domény pro každou entitu, bude vysvětlený v dalších částech při zaměření na události domény.</span><span class="sxs-lookup"><span data-stu-id="213f9-123">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="213f9-124">Kontrakty úložiště (rozhraní) ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="213f9-124">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="213f9-125">Kontrakty úložiště jsou jednoduše rozhraní .NET, která vyjadřují požadavky na kontrakt úložišť, která se mají použít pro každou agregaci.</span><span class="sxs-lookup"><span data-stu-id="213f9-125">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="213f9-126">Samotná úložiště nesmí být v doménovém modelu implementovaná pomocí EF Coreho kódu nebo jakýchkoli jiných závislostí infrastruktury a kódu (LINQ, SQL atd.). úložiště by měla implementovat pouze rozhraní, které definujete v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="213f9-126">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="213f9-127">Vzor vztahující se k tomuto postupu (umístění rozhraní úložiště do vrstvy doménové struktury) je model odděleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="213f9-127">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="213f9-128">Jak [je vysvětleno](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) v Martinu Fowlera, "použijte oddělené rozhraní k definování rozhraní v jednom balíčku, ale jeho implementaci v jiném.</span><span class="sxs-lookup"><span data-stu-id="213f9-128">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="213f9-129">Tímto způsobem klient, který potřebuje závislost na rozhraní, může zcela nevědět o implementaci. "</span><span class="sxs-lookup"><span data-stu-id="213f9-129">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="213f9-130">Po použití vzoru odděleného rozhraní umožňuje aplikační vrstvě (v tomto případě projekt webového rozhraní API pro mikroslužeb) závislosti na požadavcích definovaných v doménovém modelu, ale ne na přímé závislosti na vrstvě infrastruktury/trvalosti.</span><span class="sxs-lookup"><span data-stu-id="213f9-130">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="213f9-131">Navíc můžete pomocí injektáže závislosti izolovat implementaci, která je implementována v infrastruktuře/trvalosti vrstvy pomocí úložišť.</span><span class="sxs-lookup"><span data-stu-id="213f9-131">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="213f9-132">Například následující příklad s rozhraním IOrderRepository definuje, které operace bude třída OrderRepository potřebovat implementovat na vrstvu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="213f9-132">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="213f9-133">V aktuální implementaci aplikace kód pouze potřebuje přidat nebo aktualizovat Objednávky do databáze, protože dotazy jsou rozděleny podle zjednodušeného přístupu CQRS.</span><span class="sxs-lookup"><span data-stu-id="213f9-133">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="213f9-134">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="213f9-134">Additional resources</span></span>

- <span data-ttu-id="213f9-135">**Martin Fowlera. Rozhraní oddělené.**</span><span class="sxs-lookup"><span data-stu-id="213f9-135">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="213f9-136">[Předchozí](net-core-microservice-domain-model.md)
>[Další](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="213f9-136">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
