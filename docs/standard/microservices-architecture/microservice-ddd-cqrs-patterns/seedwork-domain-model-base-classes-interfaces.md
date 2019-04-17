---
title: Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Ke spuštění implementace modelu orientované na DDD domény použijte seedwork koncept jako výchozí bod.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: bea2dbbc926f351179d11eaacd0dbb89fe036b12
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611065"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="53a9e-103">Seedwork (opakovaně použitelné základní třídy a rozhraní pro doménový model)</span><span class="sxs-lookup"><span data-stu-id="53a9e-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="53a9e-104">Obsahuje složky řešení *SeedWork* složky.</span><span class="sxs-lookup"><span data-stu-id="53a9e-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="53a9e-105">Tato složka obsahuje vlastní základní třídy, které můžete použít jako základ pro domény entity a objekty hodnotu.</span><span class="sxs-lookup"><span data-stu-id="53a9e-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="53a9e-106">Použijte tyto základní třídy, takže není nutné redundantní kód ve třídě objektu každé domény.</span><span class="sxs-lookup"><span data-stu-id="53a9e-106">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="53a9e-107">Složka pro tyto typy třídy se nazývá *SeedWork* a nemít něco podobného *Framework*.</span><span class="sxs-lookup"><span data-stu-id="53a9e-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="53a9e-108">Je volána *SeedWork* vzhledem k tomu, že složka obsahuje jenom malou podmnožinu opakovaně použitelné třídy, které nelze ve skutečnosti považovat za rozhraní.</span><span class="sxs-lookup"><span data-stu-id="53a9e-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="53a9e-109">*Seedwork* termín, který se používá ve [Michael peří](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a který zpopularizoval [Martina Fowlera](https://martinfowler.com/bliki/Seedwork.html) ale může také název této složky obecné SharedKernel, nebo podobného.</span><span class="sxs-lookup"><span data-stu-id="53a9e-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="53a9e-110">Obrázek 7-12 ukazuje třídy, které tvoří seedwork doménový model v pořadí mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="53a9e-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="53a9e-111">Má několik vlastních základních tříd jako Entity a ValueObject, výčet a navíc několik rozhraní.</span><span class="sxs-lookup"><span data-stu-id="53a9e-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="53a9e-112">Tato rozhraní (IRepository a IUnitOfWork) vrstvy infrastruktury informuje o tom, co potřebuje k implementaci.</span><span class="sxs-lookup"><span data-stu-id="53a9e-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="53a9e-113">Tato rozhraní se také používají pomocí vkládání závislostí z aplikační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="53a9e-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![Podrobný obsah složky SeedWork, který obsahuje základní třídy a rozhraní: Entity.cs Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs a ValueObject.cs](./media/image13.PNG)

<span data-ttu-id="53a9e-115">**Obrázek 7-12**.</span><span class="sxs-lookup"><span data-stu-id="53a9e-115">**Figure 7-12**.</span></span> <span data-ttu-id="53a9e-116">Ukázka sada domény modelu "seedwork" základní třídy a rozhraní</span><span class="sxs-lookup"><span data-stu-id="53a9e-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="53a9e-117">Toto je typ kopírování a vkládání opakované použití, který mnoho vývojářů sdílet mezi projekty, není formální rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="53a9e-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="53a9e-118">Můžete mít seedworks v libovolné vrstvě nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="53a9e-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="53a9e-119">Ale sadu tříd a rozhraní, získá dostatečně velký, můžete chtít vytvořit knihovnu jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="53a9e-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="53a9e-120">Vlastní Entity základní třídy</span><span class="sxs-lookup"><span data-stu-id="53a9e-120">The custom Entity base class</span></span>

<span data-ttu-id="53a9e-121">Následující kód je příklad základní třídu Entity můžete umístit kód, který můžete používat stejným způsobem jako Každá entita domény, jako je například entity ID [operátory rovnosti](~/docs/csharp/language-reference/operators/equality-operators.md), seznam domén událost na entitu, atd.</span><span class="sxs-lookup"><span data-stu-id="53a9e-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](~/docs/csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

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

<span data-ttu-id="53a9e-122">Předchozí kód pomocí seznam domén událost na entitu se vysvětlené v následujících částech při zaměření na události domény.</span><span class="sxs-lookup"><span data-stu-id="53a9e-122">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="53a9e-123">Kontrakty úložiště (rozhraní) ve vrstvě doménového modelu</span><span class="sxs-lookup"><span data-stu-id="53a9e-123">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="53a9e-124">Kontrakty úložiště jsou jednoduše rozhraní .NET, které express požadavky smlouvy z úložišť pro každou agregaci.</span><span class="sxs-lookup"><span data-stu-id="53a9e-124">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="53a9e-125">Úložiště sami, s EF Core kódu nebo další závislosti infrastrukturu a kód (Linq, SQL atd.), nesmí být prováděna v rámci modelu domény úložiště by měly implementovat pouze rozhraní, které definujete v doménovém modelu.</span><span class="sxs-lookup"><span data-stu-id="53a9e-125">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="53a9e-126">Vzor související se tento postup (umístěním úložiště rozhraní ve vrstvě doménového modelu) je model oddělených rozhraní.</span><span class="sxs-lookup"><span data-stu-id="53a9e-126">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="53a9e-127">Jako [vysvětlení](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) od Martina Fowlera "oddělené rozhraní k definování rozhraní v jednom balíčku, ale implementovat v jiném.</span><span class="sxs-lookup"><span data-stu-id="53a9e-127">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="53a9e-128">Tímto způsobem klient, který potřebuje závislost na rozhraní můžete zcela je nezajímat se o implementace."</span><span class="sxs-lookup"><span data-stu-id="53a9e-128">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="53a9e-129">Následující vzorek oddělených rozhraní umožňuje mít závislost na požadavky definované v modelu domény, ale ne přímou závislost na infrastrukturu nebo trvalost aplikační vrstvu (v tomto případě projekt webového rozhraní API pro mikroslužbách) vrstva.</span><span class="sxs-lookup"><span data-stu-id="53a9e-129">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="53a9e-130">Kromě toho můžete použít injektáž závislostí izolovat implementace, které je implementované v infrastruktuře / vrstvy trvalosti pomocí úložišť.</span><span class="sxs-lookup"><span data-stu-id="53a9e-130">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="53a9e-131">Například následující příklad rozhraní IOrderRepository definuje jaké operace třída OrderRepository potřebovat provádět na vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="53a9e-131">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="53a9e-132">Aktuální provádění aplikace kód jenom je potřeba přidat nebo aktualizovat objednávky do databáze, protože dotazy jsou rozděleny podle zjednodušený přístup modelu CQRS.</span><span class="sxs-lookup"><span data-stu-id="53a9e-132">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="53a9e-133">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="53a9e-133">Additional resources</span></span>

- <span data-ttu-id="53a9e-134">**Martina Fowlera. Oddělených rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="53a9e-134">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="53a9e-135">[Předchozí](net-core-microservice-domain-model.md)
>[další](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="53a9e-135">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
