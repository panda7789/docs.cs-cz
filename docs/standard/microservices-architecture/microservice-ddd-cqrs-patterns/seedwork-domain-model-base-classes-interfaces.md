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
ms.openlocfilehash: 17602d94ea167997389a77f0d2358326258a8219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="5de88-104">Seedwork (opakovaně použitelné základní třídy a rozhraní pro váš model domény)</span><span class="sxs-lookup"><span data-stu-id="5de88-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="5de88-105">Obsahuje složky řešení *SeedWork* složky.</span><span class="sxs-lookup"><span data-stu-id="5de88-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="5de88-106">*SeedWork* složka obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="5de88-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="5de88-107">V každé doméně třída objektu nemáte redundantní kódu použijte tyto základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5de88-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="5de88-108">Složka pro tyto typy třídy se nazývá *SeedWork* a není něco jako *Framework*.</span><span class="sxs-lookup"><span data-stu-id="5de88-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="5de88-109">Je volána *SeedWork* vzhledem k tomu, že složka obsahuje pouze malou podmnožinu opakovaně použitelné třídy, které nelze skutečně považovat za rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5de88-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="5de88-110">*Seedwork* je termín zavedené službou [peří Michael](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) a popularized podle [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , ale také mohla mít název této složky běžné, SharedKernel, nebo podobné.</span><span class="sxs-lookup"><span data-stu-id="5de88-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="5de88-111">Obrázek 9 – 12 obsahuje třídy, které tvoří seedwork modelu domény v řazení mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="5de88-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="5de88-112">Má několik vlastní základní třídy jako entita, ValueObject a výčet a navíc několik rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5de88-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="5de88-113">Tato rozhraní (IRepository a IUnitOfWork) informovat o toho, co je třeba implementovat vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="5de88-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="5de88-114">Tyto rozhraní používají taky pomocí vkládání závislostí z aplikační vrstvu.</span><span class="sxs-lookup"><span data-stu-id="5de88-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="5de88-115">**Obrázek 9 – 12**.</span><span class="sxs-lookup"><span data-stu-id="5de88-115">**Figure 9-12**.</span></span> <span data-ttu-id="5de88-116">Ukázka sada domény modelu "seedwork" základní třídy a rozhraní</span><span class="sxs-lookup"><span data-stu-id="5de88-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="5de88-117">Jedná se o typ, kopírování a vkládání opakované použití, celá řada vývojářů sdílet mezi projekty, není formální framework.</span><span class="sxs-lookup"><span data-stu-id="5de88-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="5de88-118">Můžete mít seedworks v libovolném vrstvy nebo knihovny.</span><span class="sxs-lookup"><span data-stu-id="5de88-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="5de88-119">Však sadu třídy a rozhraní získá dostatečně velký, můžete chtít vytvořit knihovnu jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="5de88-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="5de88-120">Vlastní základní třídu Entity</span><span class="sxs-lookup"><span data-stu-id="5de88-120">The custom Entity base class</span></span>

<span data-ttu-id="5de88-121">Následující kód je příkladem základní třídu Entity, kde můžete umístit kód, který lze použít stejným způsobem jako ve všech entita domény, jako je například entity ID [operátory rovnosti](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx)atd.</span><span class="sxs-lookup"><span data-stu-id="5de88-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.</span></span>

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

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="5de88-122">Kontrakty úložiště (rozhraní) ve vrstvě modelu domény.</span><span class="sxs-lookup"><span data-stu-id="5de88-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="5de88-123">Kontrakty úložiště jsou jednoduše rozhraní .NET, která express požadavky kontrakt úložišť má být použit pro každý agregace.</span><span class="sxs-lookup"><span data-stu-id="5de88-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> <span data-ttu-id="5de88-124">Sami úložiště s EF základní kód nebo další závislosti infrastrukturu a kód, nesmí být prováděna v rámci modelu domény; úložiště by měla implementovat jenom rozhraní, které definujete.</span><span class="sxs-lookup"><span data-stu-id="5de88-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code, must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span>

<span data-ttu-id="5de88-125">Vzor související se tento postup (uvedení rozhraní úložiště vrstva modelu domény) je vzor oddělené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5de88-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="5de88-126">Jako [vysvětlené](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) ve Martin Fowler "rozhraní oddělené použijte k definování rozhraní v jednom balíčku ale implementovat v jiném.</span><span class="sxs-lookup"><span data-stu-id="5de88-126">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="5de88-127">Tímto způsobem klienta, který potřebuje závislost na rozhraní může být zcela nebere v úvahu implementace."</span><span class="sxs-lookup"><span data-stu-id="5de88-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="5de88-128">Následující vzoru oddělené rozhraní umožňuje mít závislost na požadavky definované v modelu domény, ale není přímé závislost na infrastrukturu nebo trvalost aplikační vrstvu (v tomto případě projekt webového rozhraní API pro mikroslužbu) vrstva.</span><span class="sxs-lookup"><span data-stu-id="5de88-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="5de88-129">Kromě toho izolace implementace, které je implementované v infrastruktuře pomocí vkládání závislostí / vrstvu trvalosti pomocí úložiště.</span><span class="sxs-lookup"><span data-stu-id="5de88-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="5de88-130">Například v následujícím příkladu s rozhraním IOrderRepository definuje jakým operacím OrderRepository třída bude nutné implementovat ve vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="5de88-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="5de88-131">V aktuální implementace aplikace kód právě musí přidat pořadí k databázi, vzhledem k tomu, že dotazy jsou následující rozdělení, CQS přístupu a aktualizace objednávky není implementováno.</span><span class="sxs-lookup"><span data-stu-id="5de88-131">In the current implementation of the application, the code just needs to add the order to the database, since queries are split following the CQS approach, and updates to orders are not implemented.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="5de88-132">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5de88-132">Additional resources</span></span>

-   <span data-ttu-id="5de88-133">**Martin Fowler. Oddělených rozhraní. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span><span class="sxs-lookup"><span data-stu-id="5de88-133">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5de88-134">[Předchozí] (net-core mikroslužbu domény model.md) [Další] (implementace objects.md hodnota)</span><span class="sxs-lookup"><span data-stu-id="5de88-134">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
