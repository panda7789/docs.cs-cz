---
title: "Implementace modelu mikroslužbu domény s .NET Core"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace modelu mikroslužbu domény s .NET Core"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="d37f3-104">Implementace modelu mikroslužbu domény s .NET Core</span><span class="sxs-lookup"><span data-stu-id="d37f3-104">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="d37f3-105">V předchozí části byly vysvětlené základní principy a vzory návrhu modelu domény.</span><span class="sxs-lookup"><span data-stu-id="d37f3-105">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="d37f3-106">Nyní je čas na vyzkoušení možné způsoby, jak implementovat modelu domény pomocí .NET Core (prostý C\# kódu) a základní EF.</span><span class="sxs-lookup"><span data-stu-id="d37f3-106">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="d37f3-107">Všimněte si, že váš model domény bude skládat jednoduše vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-107">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="d37f3-108">Na EF bude mít jenom základní EF modelu požadavky, ale ne skutečné závislosti.</span><span class="sxs-lookup"><span data-stu-id="d37f3-108">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="d37f3-109">Pevné závislosti nebo odkazy na základní EF nebo jiných ORM by neměl mít v modelu domény.</span><span class="sxs-lookup"><span data-stu-id="d37f3-109">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="d37f3-110">Doménovou strukturu modelu v knihovně vlastní .NET Standard</span><span class="sxs-lookup"><span data-stu-id="d37f3-110">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="d37f3-111">Složka organizace používá pro odkaz na aplikaci eShopOnContainers ukazuje DDD modelu pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d37f3-111">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="d37f3-112">Můžete se setkat jinou složku organizace více jasně komunikuje možnosti návrhu, které jsou vytvářeny pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d37f3-112">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="d37f3-113">Jak vidíte v obrázek 9 – 10, v řazení modelu domény existují dvě agregace, agregace pořadí a kupujících agregace.</span><span class="sxs-lookup"><span data-stu-id="d37f3-113">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="d37f3-114">Každý agregace je skupina domény entity a hodnota objekty, i když můžete mít agregace také skládá z jedné domény entity (agregační kořenové nebo kořenové entity).</span><span class="sxs-lookup"><span data-stu-id="d37f3-114">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="d37f3-115">**Obrázek 9 – 10**.</span><span class="sxs-lookup"><span data-stu-id="d37f3-115">**Figure 9-10**.</span></span> <span data-ttu-id="d37f3-116">Doménovou strukturu modelu pro řazení mikroslužbu v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="d37f3-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="d37f3-117">Kromě toho vrstva modelu domény zahrnuje smlouvy úložiště (rozhraní), které jsou požadavky na infrastrukturu modelu domény.</span><span class="sxs-lookup"><span data-stu-id="d37f3-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="d37f3-118">Jinými slovy, tyto rozhraní express jaké úložiště vrstvě infrastruktury musí implementovat a jak.</span><span class="sxs-lookup"><span data-stu-id="d37f3-118">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="d37f3-119">Je důležité, aby implementace úložišť umístit mimo vrstva modelu domény, v knihovně infrastruktury vrstvy tak vrstva modelu domény není "napadeny" rozhraní API nebo třídy z infrastruktury technologie, jako je rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d37f3-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="d37f3-120">Můžete také zjistit [SeedWork](https://martinfowler.com/bliki/Seedwork.html) složku, která obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty, takže není nutné redundantní kódu v každé doméně třída objektu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="d37f3-121">Strukturování agregací ve vlastní knihovna .NET Standard</span><span class="sxs-lookup"><span data-stu-id="d37f3-121">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="d37f3-122">Agregace odkazuje na clusteru s podporou objektů domény tak, aby odpovídaly transakční konzistence seskupeny dohromady.</span><span class="sxs-lookup"><span data-stu-id="d37f3-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="d37f3-123">Tyto objekty může být instancí entit (z nichž jeden je agregační kořenový server WSUS nebo kořenové entity) plus všechny objekty další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="d37f3-124">Transakční konzistence znamená, že agregace záruku, že se konzistentní a aktuální na konci obchodní akce.</span><span class="sxs-lookup"><span data-stu-id="d37f3-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="d37f3-125">Například agregace pořadí z eShopOnContainers řazení mikroslužbu modelu domény se skládá, jak ukazuje obrázek 9 – 11.</span><span class="sxs-lookup"><span data-stu-id="d37f3-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="d37f3-126">**Obrázek 9-11**.</span><span class="sxs-lookup"><span data-stu-id="d37f3-126">**Figure 9-11**.</span></span> <span data-ttu-id="d37f3-127">Pořadí agregační v řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d37f3-127">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="d37f3-128">Otevřete-li některý ze souborů ve složce aplikace agregační, uvidíte jak je označen jako vlastní základní třídu nebo rozhraní, jako je entity nebo hodnota objektu, jak jsou implementované ve [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) složky.</span><span class="sxs-lookup"><span data-stu-id="d37f3-128">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="d37f3-129">Implementace entity domény jako třídy objektů POCO</span><span class="sxs-lookup"><span data-stu-id="d37f3-129">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="d37f3-130">Implementaci modelu domény v rozhraní .NET a vytváření tříd objektů POCO, které implementují entity vaší domény.</span><span class="sxs-lookup"><span data-stu-id="d37f3-130">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="d37f3-131">V následujícím příkladu je třída pořadí definovaná jako entity a také jako agregovaná kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="d37f3-131">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="d37f3-132">Protože pořadí třída odvozena z třídy base entita, můžete znovu použít společný kód související s entitami.</span><span class="sxs-lookup"><span data-stu-id="d37f3-132">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="d37f3-133">Berte v úvahu, že tyto základní třídy a rozhraní jsou definované uživatelem v projektu modelu domény, tak, aby byl kód, není infrastruktury kód z ORM jako EF.</span><span class="sxs-lookup"><span data-stu-id="d37f3-133">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="d37f3-134">Je důležité si uvědomit, že toto je entita domény, implementovaný jako třídu objektů POCO.</span><span class="sxs-lookup"><span data-stu-id="d37f3-134">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="d37f3-135">Nástroj nemá žádné přímé závislost na Entity Framework Core nebo jiné infrastruktury framework.</span><span class="sxs-lookup"><span data-stu-id="d37f3-135">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="d37f3-136">Tato implementace je tak, jak má, právě C\# kód implementace modelu domény.</span><span class="sxs-lookup"><span data-stu-id="d37f3-136">This implementation is as it should be, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="d37f3-137">Kromě toho je třída označených pomocí rozhraní s názvem IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="d37f3-137">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="d37f3-138">Toto rozhraní je prázdný rozhraní, někdy nazývané *rozhraní značek*, která je použít jenom k označení, že tato třída entity je také agregační kořenové.</span><span class="sxs-lookup"><span data-stu-id="d37f3-138">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="d37f3-139">Rozhraní značek se někdy považuje za proti vzor; je však také čistou způsob, jak označit třídu, zejména v případě, že rozhraní může být vyvíjející se.</span><span class="sxs-lookup"><span data-stu-id="d37f3-139">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="d37f3-140">Atribut může být volba pro značky, ale je rychlejší najdete v části základní třídy (entita) vedle rozhraní IAggregate místo vložení agregační atribut značky nad třídu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-140">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="d37f3-141">Je metter preference, v každém případě.</span><span class="sxs-lookup"><span data-stu-id="d37f3-141">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="d37f3-142">S agregační kořenové znamená, že většinu kódu související s konzistence a obchodní pravidla na agregaci entit by měla být implementována jako metody ve třídě agregační kořenové pořadí (například AddOrderItem při přidávání objektu OrderItem do agregace) .</span><span class="sxs-lookup"><span data-stu-id="d37f3-142">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="d37f3-143">Nesmí vytvořit nebo aktualizovat objekty OrderItems, samostatně nebo přímo. Třída AggregateRoot musí je udržovat v řízení a konzistence všechny operace aktualizace proti podřízených entit.</span><span class="sxs-lookup"><span data-stu-id="d37f3-143">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

<span data-ttu-id="d37f3-144">Je třeba, měli byste *není* udělejte z libovolné příkaz obslužná rutina metoda nebo aplikaci vrstvy třídy:</span><span class="sxs-lookup"><span data-stu-id="d37f3-144">For example, you should *not* do the following from any command handler method or application layer class:</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="d37f3-145">Metodu Add. v takovém případě je čistě operace přidání dat s přímým přístupem ke kolekci OrderItems.</span><span class="sxs-lookup"><span data-stu-id="d37f3-145">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="d37f3-146">Proto většinu logiku domény, pravidel nebo ověření související se, že operace podřízenými položkami, bude možné rozdělit do aplikační vrstvu (obslužné rutiny příkazů a řadičů webového rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="d37f3-146">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="d37f3-147">Pokud přejdete kolem agregační kořenové, nemůže zaručit kořenu agregační jeho výstupních podmínek, jeho platnost nebo jeho konzistence.</span><span class="sxs-lookup"><span data-stu-id="d37f3-147">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="d37f3-148">Nakonec bude mít špagety kód nebo kód transakční skriptu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-148">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="d37f3-149">Podle vzorů DDD, nesmí mít entity v libovolné vlastnosti entity, veřejné setter.</span><span class="sxs-lookup"><span data-stu-id="d37f3-149">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="d37f3-150">Změny v entitě by měl být doprovází explicitní metody s explicitní všudypřítomný jazyk o změny, které se provádí v entitě.</span><span class="sxs-lookup"><span data-stu-id="d37f3-150">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="d37f3-151">Kromě toho kolekce v rámci entity (např. pořadí položek) by měla být vlastnosti jen pro čtení (metoda AsReadOnly vysvětleno dále).</span><span class="sxs-lookup"><span data-stu-id="d37f3-151">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="d37f3-152">Nyní byste měli mít pouze z aktualizovat v rámci metody třídy agregační kořenové nebo podřízené metody entity.</span><span class="sxs-lookup"><span data-stu-id="d37f3-152">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="d37f3-153">Jak můžete vidět v kódu pro kořenovou agregační pořadí, všechny setter musí být privátní nebo alespoň oprávnění jen pro čtení externě, tak, aby všechny operace proti entity data nebo jeho podřízených entit musí být provedena prostřednictvím metody ve třídě entity.</span><span class="sxs-lookup"><span data-stu-id="d37f3-153">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="d37f3-154">Tím se zachová konzistence řízené a objektově orientované způsobem místo implementace kód transakční skriptu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-154">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="d37f3-155">Následující fragment kódu ukazuje správný způsob, jak můžete kód úkolu přidávání objekt OrderItem k agregaci pořadí.</span><span class="sxs-lookup"><span data-stu-id="d37f3-155">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="d37f3-156">V tento fragment kódu, bude většina ověření nebo logiku související vytvoření objektu OrderItem pod kontrolou agregační kořenu pořadí – v metodě AddOrderItem – zejména ověření a logiku související s další prvky v souhrnném.</span><span class="sxs-lookup"><span data-stu-id="d37f3-156">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="d37f3-157">Například může získat položce produktu v důsledku několik volání AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="d37f3-157">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="d37f3-158">V dané metody můžete prozkoumat položky produktu a konsolidovat stejné položek produktu do jednoho objektu OrderItem u několik jednotek.</span><span class="sxs-lookup"><span data-stu-id="d37f3-158">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="d37f3-159">Kromě toho pokud existují různé slevu objemy, ale ID produktu je stejný, by pravděpodobně použijete vyšší slevy.</span><span class="sxs-lookup"><span data-stu-id="d37f3-159">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="d37f3-160">Tato zásada se vztahuje na další logiku domény OrderItem objektu.</span><span class="sxs-lookup"><span data-stu-id="d37f3-160">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="d37f3-161">Kromě toho nové OrderItem(params) operaci rovněž se řídí a provádí metodu AddOrderItem z kořene agregační pořadí.</span><span class="sxs-lookup"><span data-stu-id="d37f3-161">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="d37f3-162">Proto většinu logiky nebo ověření související se, že operace, (zejména všechno, co má dopad na konzistenci mezi dalšími subjekty, podřízené) bude na jednom místě v kořenu agregační.</span><span class="sxs-lookup"><span data-stu-id="d37f3-162">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="d37f3-163">Toto je ultimate účel agregační kořenové vzoru.</span><span class="sxs-lookup"><span data-stu-id="d37f3-163">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="d37f3-164">Pokud používáte Entity Framework 1.1, DDD entita může být lépe vyjádřený, protože jedna z nových funkcí Entity Framework Core 1.1, že umožňuje [mapování polí](https://docs.microsoft.com/ef/core/modeling/backing-field) kromě vlastností.</span><span class="sxs-lookup"><span data-stu-id="d37f3-164">When you use Entity Framework 1.1, a DDD entity can be better expressed because one of the new features of Entity Framework Core 1.1 is that it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="d37f3-165">To je užitečné, když chráníte kolekcí podřízených entit nebo hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="d37f3-165">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="d37f3-166">Toto vylepšení můžete použít jednoduchý privátním polím místo vlastnosti a můžete implementovat žádné aktualizace ke kolekci pole v veřejné metody a poskytovat přístup jen pro čtení prostřednictvím metody AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="d37f3-166">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="d37f3-167">V DDD chcete entitu aktualizovat pouze prostřednictvím metody v entitě (nebo konstruktoru), aby bylo možné řídit všechny neutrální a konzistence dat takže vlastnosti jsou definované pouze s přistupující objekt get.</span><span class="sxs-lookup"><span data-stu-id="d37f3-167">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="d37f3-168">Vlastnosti jsou zajišťované privátním polím.</span><span class="sxs-lookup"><span data-stu-id="d37f3-168">The properties are backed by private fields.</span></span> <span data-ttu-id="d37f3-169">Soukromé členy pouze přístupná v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="d37f3-169">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="d37f3-170">Ale zde jedna výjimka: základní EF je třeba nastavit také těchto polí.</span><span class="sxs-lookup"><span data-stu-id="d37f3-170">However, there one exception: EF Core needs to set these fields as well.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="d37f3-171">Mapování vlastností s pouze získat přístupové objekty na pole v tabulce databáze</span><span class="sxs-lookup"><span data-stu-id="d37f3-171">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="d37f3-172">Mapování vlastností na sloupce tabulky databáze není odpovědnost domény, ale součást vrstvě infrastruktury a trvalost.</span><span class="sxs-lookup"><span data-stu-id="d37f3-172">Mapping properties to the database table columns is not a domain responsibility, but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="d37f3-173">Jsme zmínili toto tady jednoduše, takže víte o nové funkce v EF 1.1 související s jak můžete modelu entity.</span><span class="sxs-lookup"><span data-stu-id="d37f3-173">We mention this here just so you are aware of the new capabilities in EF 1.1 related to how you can model entities.</span></span> <span data-ttu-id="d37f3-174">Další informace o tomto tématu jsou vysvětleny v sekci infrastruktury a trvalost.</span><span class="sxs-lookup"><span data-stu-id="d37f3-174">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="d37f3-175">Při použití EF 1.0, v rámci DbContext, budete muset mapy – vlastnosti, které jsou definovány pouze s mechanismy získání skutečné pole v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="d37f3-175">When you use EF 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="d37f3-176">To se provádí pomocí metody HasField PropertyBuilder třídy.</span><span class="sxs-lookup"><span data-stu-id="d37f3-176">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="d37f3-177">Mapování polí bez vlastností</span><span class="sxs-lookup"><span data-stu-id="d37f3-177">Mapping fields without properties</span></span>

<span data-ttu-id="d37f3-178">Pomocí nové funkce v 1.1 základní EF pro mapování sloupců na pole je také možné nepoužívat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d37f3-178">With the new feature in EF Core 1.1 to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="d37f3-179">Místo toho můžete namapovat jenom sloupce z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="d37f3-179">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="d37f3-180">Běžně používá pro tento je privátním polím pro vnitřní stav, který nemusí být subjekty mimo entity.</span><span class="sxs-lookup"><span data-stu-id="d37f3-180">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="d37f3-181">Například v předchozím příkladu kódu \_someOrderInternalState pole nemá související vlastnost pro nastavení nebo getter.</span><span class="sxs-lookup"><span data-stu-id="d37f3-181">For example, in the preceding code example, the \_someOrderInternalState field has no related property for either a setter or getter.</span></span> <span data-ttu-id="d37f3-182">Toto pole také se počítá v rámci obchodní logiku pořadí a použije z metod pořadí, ale je potřeba nastavit jako trvalý, v databázi také.</span><span class="sxs-lookup"><span data-stu-id="d37f3-182">That field will also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="d37f3-183">Ano v EF 1.1 je způsob, jak mapování pole bez související vlastnosti na sloupec v databázi.</span><span class="sxs-lookup"><span data-stu-id="d37f3-183">So, in EF 1.1 there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="d37f3-184">To je také podrobně [vrstvě infrastruktury](#the-infrastructure-layer) části této příručky.</span><span class="sxs-lookup"><span data-stu-id="d37f3-184">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d37f3-185">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d37f3-185">Additional resources</span></span>

-   <span data-ttu-id="d37f3-186">**Vaughn Vernon. Modelování agregace s DDD a Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="d37f3-186">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="d37f3-187">Všimněte si, že toto je *není* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="d37f3-187">Note that this is *not* Entity Framework Core.</span></span>
    [<span data-ttu-id="d37f3-188">*https://vaughnvernon.co/?p=879*</span><span class="sxs-lookup"><span data-stu-id="d37f3-188">*https://vaughnvernon.co/?p=879*</span></span>](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="d37f3-189">**Julie Lerman. Kódování řízené domény návrh: tipy pro zaměřené na Data Devs**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="d37f3-189">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="d37f3-190">**UDI Dahan. Postup vytvoření plně zapouzdřené domény modely**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="d37f3-190">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d37f3-191">[Předchozí] (mikroslužbu domain-model.md) [Další] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="d37f3-191">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>
