---
title: Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 21f502d74aab10b306e350ee831583f06b394dc7
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105100"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="618c4-103">Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)</span><span class="sxs-lookup"><span data-stu-id="618c4-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="618c4-104">Obsahuje složky řešení *SeedWork* složky.</span><span class="sxs-lookup"><span data-stu-id="618c4-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="618c4-105">*SeedWork* složka obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="618c4-105">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="618c4-106">V každé doméně třída objektu nemáte redundantní kódu použijte tyto základní třídy.</span><span class="sxs-lookup"><span data-stu-id="618c4-106">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="618c4-107">Složka pro tyto typy třídy se nazývá *SeedWork* a není něco jako *Framework*.</span><span class="sxs-lookup"><span data-stu-id="618c4-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="618c4-108">Je volána *SeedWork* vzhledem k tomu, že složka obsahuje pouze malou podmnožinu opakovaně použitelné třídy, které nelze skutečně považovat za rozhraní.</span><span class="sxs-lookup"><span data-stu-id="618c4-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="618c4-109">*Seedwork* je termín zavedené službou [peří Michael](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a popularized podle [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , ale také mohla mít název této složky běžné, SharedKernel, nebo podobné.</span><span class="sxs-lookup"><span data-stu-id="618c4-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="618c4-110">Obrázek 9 – 12 obsahuje třídy, které tvoří seedwork modelu domény v řazení mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="618c4-110">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="618c4-111">Má několik vlastní základní třídy jako entita, ValueObject a výčet a navíc několik rozhraní.</span><span class="sxs-lookup"><span data-stu-id="618c4-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="618c4-112">Tato rozhraní (IRepository a IUnitOfWork) informovat o toho, co je třeba implementovat vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="618c4-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="618c4-113">Tyto rozhraní používají taky pomocí vkládání závislostí z aplikační vrstvu.</span><span class="sxs-lookup"><span data-stu-id="618c4-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="618c4-114">**Obrázek 9 – 12**.</span><span class="sxs-lookup"><span data-stu-id="618c4-114">**Figure 9-12**.</span></span> <span data-ttu-id="618c4-115">Ukázka sada domény modelu "seedwork" základní třídy a rozhraní</span><span class="sxs-lookup"><span data-stu-id="618c4-115">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="618c4-116">Jedná se o typ, kopírování a vkládání opakované použití, celá řada vývojářů sdílet mezi projekty, není formální framework.</span><span class="sxs-lookup"><span data-stu-id="618c4-116">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="618c4-117">Můžete mít seedworks v libovolném vrstvy nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="618c4-117">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="618c4-118">Však sadu třídy a rozhraní získá dostatečně velký, můžete chtít vytvořit knihovnu jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="618c4-118">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="618c4-119">Vlastní základní třídu Entity</span><span class="sxs-lookup"><span data-stu-id="618c4-119">The custom Entity base class</span></span>

<span data-ttu-id="618c4-120">Následující kód je příkladem základní třídu Entity, kde můžete umístit kód, který lze použít stejným způsobem jako ve všech entita domény, jako je například entity ID [operátory rovnosti](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), seznam domén událost na entitu, atd.</span><span class="sxs-lookup"><span data-stu-id="618c4-120">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), a domain event list per entity, etc.</span></span>

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

<span data-ttu-id="618c4-121">Když zaměřené na události domény bude vysvětlení předchozí kód pomocí seznamu domény událost na entitu najdete v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="618c4-121">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span> 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="618c4-122">Kontrakty úložiště (rozhraní) ve vrstvě modelu domény.</span><span class="sxs-lookup"><span data-stu-id="618c4-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="618c4-123">Kontrakty úložiště jsou jednoduše rozhraní .NET, která express požadavky kontrakt úložišť má být použit pro každý agregace.</span><span class="sxs-lookup"><span data-stu-id="618c4-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> 

<span data-ttu-id="618c4-124">Sami úložiště s EF základní kód nebo další závislosti infrastrukturu a kód (Linq, SQL, atd.), nesmí být prováděna v rámci modelu domény; úložiště by měla implementovat jenom rozhraní, které definujete.</span><span class="sxs-lookup"><span data-stu-id="618c4-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span> 

<span data-ttu-id="618c4-125">Vzor související se tento postup (uvedení rozhraní úložiště vrstva modelu domény) je vzor oddělené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="618c4-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="618c4-126">Jako [vysvětlené](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) ve Martin Fowler "rozhraní oddělené použijte k definování rozhraní v jednom balíčku ale implementovat v jiném.</span><span class="sxs-lookup"><span data-stu-id="618c4-126">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="618c4-127">Tímto způsobem klienta, který potřebuje závislost na rozhraní může být zcela nebere v úvahu implementace."</span><span class="sxs-lookup"><span data-stu-id="618c4-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="618c4-128">Následující vzoru oddělené rozhraní umožňuje mít závislost na požadavky definované v modelu domény, ale není přímé závislost na infrastrukturu nebo trvalost aplikační vrstvu (v tomto případě projekt webového rozhraní API pro mikroslužbu) vrstva.</span><span class="sxs-lookup"><span data-stu-id="618c4-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="618c4-129">Kromě toho izolace implementace, které je implementované v infrastruktuře pomocí vkládání závislostí / vrstvu trvalosti pomocí úložiště.</span><span class="sxs-lookup"><span data-stu-id="618c4-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="618c4-130">Například v následujícím příkladu s rozhraním IOrderRepository definuje jakým operacím OrderRepository třída bude nutné implementovat ve vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="618c4-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="618c4-131">V aktuální implementace aplikace kód právě musí přidat nebo aktualizovat objednávky k databázi, vzhledem k tomu, že dotazy jsou rozděleny následující zjednodušené CQRS přístup.</span><span class="sxs-lookup"><span data-stu-id="618c4-131">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="618c4-132">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="618c4-132">Additional resources</span></span>

-   <span data-ttu-id="618c4-133">**Martin Fowler. Oddělených rozhraní.**
    [*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span><span class="sxs-lookup"><span data-stu-id="618c4-133">**Martin Fowler. Separated Interface.**
[*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="618c4-134">[Předchozí](net-core-microservice-domain-model.md)
[další](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="618c4-134">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
