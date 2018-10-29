---
title: Přihlášení k odběru událostí
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Přihlášení k odběru událostí
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 5e53e0a3578c19b09f5327f444d1a5c013ad4cd9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194069"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="2c6ab-103">Přihlášení k odběru událostí</span><span class="sxs-lookup"><span data-stu-id="2c6ab-103">Subscribing to events</span></span>

<span data-ttu-id="2c6ab-104">Prvním krokem pro používání událostí Service bus je odběru mikroslužeb k událostem, které chtějí dostávat.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="2c6ab-105">Který se má počítat v mikroslužbách příjemce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="2c6ab-106">Následující jednoduchý kód ukazuje, co každá mikroslužba příjemce musí implementovat při spuštění služby (to znamená v `Startup` třídy), přihlásí se k události se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="2c6ab-107">V takovém případě `basket.api` mikroslužeb je potřeba se přihlásit k odběru `ProductPriceChangedIntegrationEvent` a `OrderStartedIntegrationEvent` zprávy.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span> 

<span data-ttu-id="2c6ab-108">Například při přihlášení k odběru `ProductPriceChangedIntegrationEvent` události, která provádí mikroslužeb nákupní košík znát některé změny cena produktu a umožňuje ji upozornit uživatele o změnu, je-li tento produkt je v koši uživatele.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="2c6ab-109">Po spuštění tohoto kódu mikroslužeb odběratele se naslouchání prostřednictvím RabbitMQ kanálů.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="2c6ab-110">Všechny zprávy typu ProductPriceChangedIntegrationEvent dorazí kód vyvolá obslužnou rutinu události, která je předána a zpracovává události.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="2c6ab-111">Publikování událostí prostřednictvím událostí Service bus</span><span class="sxs-lookup"><span data-stu-id="2c6ab-111">Publishing events through the event bus</span></span>

<span data-ttu-id="2c6ab-112">Nakonec odesílatele zprávy (mikroslužeb původu) publikuje události integrace s kódem, podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="2c6ab-113">(Toto je zjednodušený příklad, který nemá atomicitu v úvahu). Podobný kód by implementovat pokaždé, když událost musí být šířena napříč několika mikroslužeb, obvykle hned po potvrzení dat nebo transakcí z mikroslužeb původu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="2c6ab-114">Objekt implementace sběrnice událostí (podle RabbitMQ nebo podle služby Service bus) by nejprve vloženy v konstruktoru řadič, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="2c6ab-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="2c6ab-115">Pak použijete jej z metody vašeho kontroleru, stejně jako v metodě UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="2c6ab-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("update")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="2c6ab-116">V takovém případě původu mikroslužeb je jednoduché mikroslužby CRUD, tento kód nachází vpravo do kontroleru webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> 
 
<span data-ttu-id="2c6ab-117">V pokročilejších mikroslužeb, stejně jako při použití modelu CQRS přístupy, se dá implementovat v `CommandHandler` třídy v rámci `Handle()` metody.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span> 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="2c6ab-118">Navrhování atomicitu a odolnost proti chybám při publikování událostí Service bus</span><span class="sxs-lookup"><span data-stu-id="2c6ab-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="2c6ab-119">Při publikování události integrace prostřednictvím distribuované zasílání zpráv systému, jako je vaše událostí Service bus, budete mít problém atomicky aktualizuje původní databáze a publikování události.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="2c6ab-120">Například v zjednodušený příklad je uvedeno výše, kód potvrdí data do databáze při cena produktu se změnilo a pak publikuje zprávu ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="2c6ab-121">Na začátku může vypadat základní atomicky provést tyto dvě operace.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="2c6ab-122">Ale pokud používáte distribuovaných transakcí týkajících se databáze a zprávy zprostředkovatele, stejně jako v starší systémy, jako je [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), toto nastavení nedoporučujeme důvodů popsaného [Věty](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="2c6ab-123">V podstatě mikroslužeb použijete k sestavení škálovatelné a vysoce dostupné systémy.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="2c6ab-124">Zjednodušení trochu, věty říká, že nemůže vytvořit databázi (nebo mikroslužeb, který vlastní svůj model), který je neustále k dispozici, silně konzistentních *a* vůči žádný oddíl.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-124">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="2c6ab-125">Musíte zvolit dvě z těchto tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="2c6ab-126">V architekturách založených na mikroslužbách byste měli zvolit dostupnost a odolnost a měli omezit silnou konzistenci.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="2c6ab-127">Proto se ve většině moderních aplikací založených na mikroslužbách, obvykle nechcete používat distribuovaných transakcí v zasílání zpráv, stejně jako při implementaci [distribuované transakce](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) založené na Windows distribuované transakce Koordinátor (DTC) s [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="2c6ab-128">Vraťme se k počáteční problému a jeho příklad.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="2c6ab-129">Pokud po aktualizaci databáze dojde k chybě služby (v tomto případě klikněte pravým tlačítkem za řádkem kódu pomocí \_kontextu. SaveChangesAsync()), ale před publikováním integrace událostí může nekonzistenci celého systému.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="2c6ab-130">To může být pro důležité obchodní informace, v závislosti na konkrétní obchodní operace, které se zabývají.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="2c6ab-131">Jak je uvedeno výše v části architektura, může mít několik přístupů pro řešení tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="2c6ab-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="2c6ab-132">Použití úplného [model Event Sourcing](https://msdn.microsoft.com/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-132">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="2c6ab-133">Pomocí [protokol transakcí dolování](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="2c6ab-134">Použití [pošta k odeslání vzoru](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="2c6ab-135">Toto je transakční tabulku pro ukládání událostí integrace (rozšíření místní transakce).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="2c6ab-136">V tomto scénáři použití úplné modelu Event Sourcing (ES) je jedním z osvědčených postupů, *není-li* nejlepší.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="2c6ab-137">V mnoha scénářích aplikací, ale nemusí být schopni implementovat úplnou ES operace.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="2c6ab-138">ES znamená, že ukládání pouze události domény v transakční databáze, místo uložení aktuální data o stavu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="2c6ab-139">Uložení pouze událostí domény může mít skvělé výhody, jako je například s historii vašeho systému, které jsou k dispozici a nebudou moct určení stavu systému v každém okamžiku v minulosti.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="2c6ab-140">Ale implementace úplnou ES vyžaduje, abyste úprava architektury většina vašeho systému a přináší mnoho dalších složitosti a požadavky.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="2c6ab-141">Například můžete chcete použít databázi vytvořené speciálně pro model event sourcing, například [události Store](https://geteventstore.com/), nebo databáze dokumentově orientované, jako je Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="2c6ab-142">ES je skvělé přístup k tomuto problému, ale ne Nejjednodušším řešením, pokud jste již obeznámeni s modelem event sourcing.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="2c6ab-143">Možnost použití transakční protokol dolování zpočátku vypadá velmi transparentní.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="2c6ab-144">Ale pro tuto metodu použijte mikroslužbách musí být vázány na protokol transakce relační databázový systém, jako je například protokolu transakcí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="2c6ab-145">To je pravděpodobně není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-145">This is probably not desirable.</span></span> <span data-ttu-id="2c6ab-146">Jiné nevýhodou je, že nízké úrovně aktualizací zaznamenaných v transakčním protokolu nemusí být na stejné úrovni jako základní integrace událostí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="2c6ab-147">Pokud ano, proces zpětnou tyto operace protokolu transakcí může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="2c6ab-148">Vyvážený přístup je kombinace zjednodušený model ES a tabulku transakcí databáze.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="2c6ab-149">Můžete použít stav, jako je například "připraveno k publikování událostí,", které jste nastavili v původní událost, když ji zapište do tabulky událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="2c6ab-150">Pak se pokusí publikovat událost událostí Service bus.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="2c6ab-151">Pokud události publikování akce proběhne úspěšně, můžete spustit jinou transakcí ve službě původu a přesouvat stavu "připraveno k publikování události" na "událost již publikována."</span><span class="sxs-lookup"><span data-stu-id="2c6ab-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="2c6ab-152">Pokud akce události publikování událostí Service bus se nezdaří, data stále budou konzistentní v rámci původu mikroslužeb, stále je označen jako "připraveno k publikování události", a s ohledem na ostatní služby, nakonec bude konzistentní vzhledem k aplikacím.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="2c6ab-153">Vždy máte úlohy na pozadí kontroluje se stav transakce nebo integrace událostí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="2c6ab-154">Pokud úloha nalezne událost ve stavu "připraveno k publikování události", můžete zkusit znovu publikovat tuto událost do událostí Service bus.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="2c6ab-155">Všimněte si, že s tímto přístupem uchováváte pouze události integrace u jednotlivých mikroslužeb původu a pouze události, které chcete komunikovat s jinými mikroslužby nebo externí systémy.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="2c6ab-156">Naproti tomu v rámci systému ES ukládat všechny události domény i.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="2c6ab-157">Proto tento vyvážené přístup je zjednodušené ES.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="2c6ab-158">Potřebujete seznam integrace událostí s jejich aktuální stav ("připraveno k publikování" a "publikováno").</span><span class="sxs-lookup"><span data-stu-id="2c6ab-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="2c6ab-159">Ale potřebujete implementovat tyto stavy pro události integrace.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="2c6ab-160">A v takovém případě nepotřebujete k uložení všech vašich dat domény jako události v transakční databází, jako byste to udělali v plném ES systému.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="2c6ab-161">Pokud už používáte relační databáze, můžete transakční tabulku pro ukládání událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="2c6ab-162">K dosažení atomicitu ve vaší aplikaci, použít dvoustupňový proces založené na místní transakce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="2c6ab-163">V podstatě máte tabulku IntegrationEvent ve stejné databázi, ve které máte doménu entity.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="2c6ab-164">Tuto tabulku funguje jako pojištění pro dosažení atomicitu tak, že zahrnete trvalé události integrace do stejné transakce, které se potvrzují data vaší domény.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="2c6ab-165">Krok za krokem probíhá takto: aplikace začne místní databázové transakce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-165">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="2c6ab-166">Pak aktualizuje stav entity domény a vloží do tabulky události integrace událost.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-166">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="2c6ab-167">Nakonec potvrzení transakce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-167">Finally, it commits the transaction.</span></span> <span data-ttu-id="2c6ab-168">Získáte požadovanou atomicitu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-168">You get the desired atomicity.</span></span>

<span data-ttu-id="2c6ab-169">Při implementaci kroky k publikování událostí, máte tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="2c6ab-169">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="2c6ab-170">Publikování události integrace hned po potvrzení transakce a k označení události v tabulce jako publikování použijte jinou místní transakcí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-170">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="2c6ab-171">Potom použijte tabulce stejně jako artefakt pro sledování události integrace v případě problémů v vzdálené mikroslužeb a provádět vyrovnávací akce na základě událostí uložených integrace.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-171">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="2c6ab-172">Tabulku použijte jako typ fronty.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-172">Use the table as a kind of queue.</span></span> <span data-ttu-id="2c6ab-173">Vlákna samostatné aplikace nebo proces dotazuje tabulku události integrace, publikuje události pro události Service bus a pak používá k označení události publikování místní transakce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-173">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="2c6ab-174">22. obrázek 8 ukazuje architekturu první z těchto přístupů.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-174">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="2c6ab-175">**Obrázek 8 do 22**.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-175">**Figure 8-22**.</span></span> <span data-ttu-id="2c6ab-176">Atomicitu při publikování událostí do událostí Service bus</span><span class="sxs-lookup"><span data-stu-id="2c6ab-176">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="2c6ab-177">Přístup znázorněný v obrázku 8 do 22 chybí pracovní mikroslužeb, který má na starosti kontrole a potvrzení úspěšné publikované integrace událostí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-177">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="2c6ab-178">V případě selhání můžete tuto další kontrolu pracovního procesu mikroslužeb číst události z tabulky a znovu publikovat.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-178">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="2c6ab-179">O druhým přístupem: protokol událostí tabulku použijte jako fronty a vždy použijte mikroslužbě pracovního procesu k publikování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-179">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="2c6ab-180">V takovém případě proces se tímto způsobem zobrazí obrázek 8-23.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-180">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="2c6ab-181">Zobrazí se další mikroslužeb a v tabulce je jediným zdrojem při publikování události.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-181">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="2c6ab-182">**Obrázek 8-23**.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-182">**Figure 8-23**.</span></span> <span data-ttu-id="2c6ab-183">Atomicitu při publikování událostí do sběrnice událostí pomocí mikroslužeb pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="2c6ab-183">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="2c6ab-184">Pro zjednodušení používá ukázková aplikaci eShopOnContainers první přístup (s žádné další procesy nebo prerequisite checker mikroslužeb) plus událostí Service bus.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-184">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="2c6ab-185">Aplikaci eShopOnContainers však neošetřuje všechny případy možného selhání.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-185">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="2c6ab-186">V reálné aplikaci nasadit do cloudu musí si osvojí skutečnost, že bude vzniku nakonec a je nutné implementovat, zkontrolujte a znovu odeslat logiku.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-186">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="2c6ab-187">Pokud máte danou tabulku jako jediný zdroj událostí při publikování přes Service bus události může být efektivnější než první přístup pomocí tabulky jako do fronty.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-187">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="2c6ab-188">Implementace atomicitu při publikování události integrace přes Service bus události</span><span class="sxs-lookup"><span data-stu-id="2c6ab-188">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="2c6ab-189">Následující kód ukazuje, jak můžete vytvořit jeden transakce zahrnující více objektů DbContext – jeden kontext související s původní data aktualizují a kontextu druhé související tabulce IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-189">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="2c6ab-190">Všimněte si, že transakce ve níže uvedeného ukázkového kódu nesmí být odolné pro případ, připojení k databázi mít jakýkoli problém v době, kdy kód běží.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-190">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="2c6ab-191">To může nastat v cloudové systémy, jako je Azure SQL DB, která může přesun databází mezi servery.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-191">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="2c6ab-192">Implementace odolných transakce napříč několika kontextech, najdete v článku [implementace odolnost připojení Entity Framework Core SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) dále v tomto průvodci.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-192">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="2c6ab-193">Pro přehlednost následující příklad ukazuje celý proces v každé z kódu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-193">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="2c6ab-194">Implementace aplikaci eShopOnContainers ale je ve skutečnosti teď vyčleněný a rozdělit tuto logiku na víc tříd tak, aby byl snazší Údržba.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-194">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate) 
{
  var catalogItem = 
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id == 
                                                               productToUpdate.Id); 
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false; 
  IntegrationEvent priceChangedEvent = null; 

  if (catalogItem.Price != productToUpdate.Price) 
          raiseProductPriceChangedEvent = true; 

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price; 
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price, 
                                                                  oldPrice); 
  }
  // Update current product
  catalogItem = productToUpdate; 

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent) 
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog 
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem); 
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent) 
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent); 

           transaction.Commit();
        }   

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

<span data-ttu-id="2c6ab-195">Po vytvoření události integrace ProductPriceChangedIntegrationEvent transakce, která ukládá původní operace domény (aktualizace položky katalogu) také zahrnuje trvalou dostupnost události v tabulce protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-195">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="2c6ab-196">Díky tomu jedné transakce a bude vždy možné zkontrolovat, zda byly odesílány zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-196">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="2c6ab-197">Tabulka protokolu událostí se aktualizuje atomicky původní databáze, pomocí operace místní transakce na stejnou databázi.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-197">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="2c6ab-198">Pokud všechny operace selžou, je vyvolána výjimka a transakce vrátí zpět všechny dokončené operace, proto zachování konzistence mezi operacemi domény a odeslání zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-198">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="2c6ab-199">Příjem zpráv z předplatného: obslužných rutin událostí v mikroslužbách příjemce</span><span class="sxs-lookup"><span data-stu-id="2c6ab-199">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="2c6ab-200">Kromě logiky odběr událostí budete muset implementovat vnitřní kód pro integraci obslužné rutiny událostí (např. metoda zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-200">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="2c6ab-201">Obslužná rutina události je, kde zadáte kde přijme a zpracuje zprávy o událostech určitého typu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-201">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="2c6ab-202">Obslužná rutina události nejprve obdrží instanci události z události Service bus.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-202">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="2c6ab-203">Potom je možné vyhledat součásti, které mají být zpracovány týkající se této události integrace, šíření a při zachování události jako změnu stavu v mikroslužbě příjemce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-203">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="2c6ab-204">Například pokud ProductPriceChanged události mohou být v katalogu mikroslužeb, to probíhá v košíku mikroslužeb a změní stav v košíku mikroslužeb tento příjemce i, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-204">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="2c6ab-205">Obslužná rutina události je potřeba ověřit, zda existuje produktu v některé z instancí nákupní košík.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-205">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="2c6ab-206">Aktualizuje také ceny položky pro každou položku řádku související nákupního košíku.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-206">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="2c6ab-207">Nakonec vytvoří výstrahu, který se má zobrazit uživateli o změny cen, jak ukazuje obrázek 8-24.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-207">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="2c6ab-208">**Obrázek 8-24**.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-208">**Figure 8-24**.</span></span> <span data-ttu-id="2c6ab-209">Zobrazení o změnu cena zboží v košíku, oznámené události integrace</span><span class="sxs-lookup"><span data-stu-id="2c6ab-209">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="2c6ab-210">Idempotence v události zpráva aktualizace</span><span class="sxs-lookup"><span data-stu-id="2c6ab-210">Idempotency in update message events</span></span>

<span data-ttu-id="2c6ab-211">Důležitou součástí událostí zpráva aktualizace je, že selhání v libovolném bodě komunikace by nemělo způsobit zprávu, která se zopakuje.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-211">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="2c6ab-212">V opačném případě úlohy na pozadí může pokusit o publikovat událost, která se už publikoval, vytváření časování.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-212">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="2c6ab-213">Potřebujete zajistit, že aktualizace jsou idempotentní nebo, že poskytuje dostatek informací k zajištění, že můžete detekovat duplicitní, ho zrušit a odeslání odpovědi back pouze jeden.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-213">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="2c6ab-214">Jak bylo uvedeno dříve, idempotence znamená, že operaci lze provést více než jednou beze změny výsledek.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-214">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="2c6ab-215">V prostředí zasílání zpráv protože při komunikaci události, události je idempotentní, pokud se více než jednou mohl být doručován beze změny výsledek pro mikroslužby příjemce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-215">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="2c6ab-216">To může být vzhledem k povaze samotné události nutné nebo kvůli způsobu, jakým systém zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-216">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="2c6ab-217">Zpráva idempotence je důležité v jakékoli aplikaci, která se používá pro přenos zpráv, ne jenom v aplikacích, které implementují vzor událostí Service bus.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-217">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="2c6ab-218">Příklad idempotentní operace je příkaz jazyka SQL, který vkládá data do tabulky pouze v případě, že data, která už není v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-218">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="2c6ab-219">Není důležité, kolikrát spuštění, které vkládají příkaz SQL Výsledkem bude stejná – tabulce bude obsahovat data.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-219">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="2c6ab-220">Idempotence tímto způsobem může být také nezbytné při práci s zprávy, pokud se zprávy můžou potenciálně a tudíž zpracovanými více než jednou.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-220">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="2c6ab-221">Například pokud logika opakovaných pokusů způsobí, že odesílatel odesílat přesně stejné zprávy více než jednou, budete muset Ujistěte se, že je idempotentní.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-221">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="2c6ab-222">Je možné návrhu idempotentní zprávy.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-222">It is possible to design idempotent messages.</span></span> <span data-ttu-id="2c6ab-223">Můžete například vytvořit událost, která říká "určovali ceny produktu \$25" místo "Přidat \$5 s cenou při produktu."</span><span class="sxs-lookup"><span data-stu-id="2c6ab-223">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="2c6ab-224">Vám může bezpečně první zprávu zpracovat libovolný počet pokusů a výsledky budou stejné.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-224">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="2c6ab-225">To není PRAVDA pro druhé zprávy.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-225">That is not true for the second message.</span></span> <span data-ttu-id="2c6ab-226">Ale i v prvním případě nebudete chtít zpracovat první událost, protože systém může také odeslali novější události Změna ceny a by přepsání nová cena.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-226">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="2c6ab-227">Dalším příkladem můžou být objednávka dokončena událost se rozšíří na několik předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-227">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="2c6ab-228">Je důležité, že informace o objednávkách aktualizují v jiných systémech pouze jednou, i v případě, že existují duplicitní zpráva události pro stejnou událost objednávka dokončena.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-228">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="2c6ab-229">Je vhodné mít nějaký druh identity na událost, aby mohl vytvořit logiku, která vynutí, že každé události budou zpracovány pouze jednou za příjemce.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-229">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="2c6ab-230">Některé zpracování zprávy je ze své podstaty idempotentní.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-230">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="2c6ab-231">Například pokud systém vygeneruje obrázek miniatury, je pravděpodobně důležité, kolikrát se zpracovává zpráva o vygenerované miniatury; Výsledkem je, že jsou generovány miniatury a jsou stejné pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-231">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="2c6ab-232">Operace, jako je volání platební brány platby prostřednictvím platební karty na druhé straně, nemusí být idempotentní vůbec.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-232">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="2c6ab-233">V těchto případech je potřeba zajistit, že zpracování zprávy více než jednou má účinek, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-233">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2c6ab-234">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2c6ab-234">Additional resources</span></span>

-   <span data-ttu-id="2c6ab-235">**Aby byla dodržena zpráv, idempotence** (podnadpisu na této stránce) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-235">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="2c6ab-236">Odstranění duplicit dat zprávy o událostech integrace</span><span class="sxs-lookup"><span data-stu-id="2c6ab-236">Deduplicating integration event messages</span></span>

<span data-ttu-id="2c6ab-237">Zajistíte, že události zprávy odeslané a zpracuje jenom jednou na předplatitele na různých úrovních.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-237">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="2c6ab-238">Jedním ze způsobů je použití funkce odstranění duplicitních dat, které nabízí infrastruktura zasílání zpráv, které používáte.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-238">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="2c6ab-239">Další je implementovat vlastní logiku ve vaší cílové mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-239">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="2c6ab-240">Ověření na úrovni přenosu i na úrovni aplikace, je nejlepším řešením.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-240">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="2c6ab-241">Odstranění duplicit dat v události zpráv na úrovni obslužná rutina události</span><span class="sxs-lookup"><span data-stu-id="2c6ab-241">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="2c6ab-242">Jedním ze způsobů, abyste měli jistotu, že události budou zpracovány pouze jednou všechny příjemce je implementace určité logiky při zpracování zprávy událostí v obslužných rutinách událostí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-242">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="2c6ab-243">Například, který je použitý v aplikaci eShopOnContainers aplikaci přístup jak je vidět v [zdrojový kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) OrdersController třídy, když přijme příkaz CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-243">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="2c6ab-244">(V tomto případě používáme příkaz požadavku HTTP není založená na zprávách příkaz, ale je podobná logika, je třeba provést příkaz založenou na zprávách idempotentní.)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-244">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="2c6ab-245">Při používání RabbitMQ odstranění duplicit dat zprávy</span><span class="sxs-lookup"><span data-stu-id="2c6ab-245">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="2c6ab-246">Pokud dochází k chybám sítě, mohou být duplicitní zprávy a příjemce zprávy musí být připravena ke zpracování těchto duplicitní zprávy.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-246">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="2c6ab-247">Pokud je to možné příjemce by měl zpracovávat zprávy jako idempotentní, což je lepší než explicitně je zpracování odstranění duplicit.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-247">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="2c6ab-248">Podle [RabbitMQ dokumentaci](https://www.rabbitmq.com/reliability.html#consumer), "Pokud zpráva je Doručená příjemce a pak znovu zařadit do fronty (protože nebyla potvrzena, před připojení consumer vyřazeno, například), pak RabbitMQ nastaví příznak redelivered na to při doručení znovu (, zda se má stejný příjemce nebo jiný).</span><span class="sxs-lookup"><span data-stu-id="2c6ab-248">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="2c6ab-249">Pokud je nastavený příznak "redelivered", příjemce, který přijme v úvahu, protože zpráva může již byly zpracovány.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-249">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="2c6ab-250">Není zaručeno,, ale zpráva může mít nedospělo příjemce poté, co je třeba ponechat zprostředkovatele zpráv z důvodu problémů se sítí.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-250">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="2c6ab-251">Na druhé straně Pokud není nastaven příznak "redelivered", není zaručeno, že zpráva nebyla odeslána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-251">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="2c6ab-252">Příjemce proto potřebuje k odstranění duplicit zprávy nebo zprávy procesu způsobem idempotentní, pouze pokud příznak "redelivered" je nastavena ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-252">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2c6ab-253">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2c6ab-253">Additional resources</span></span>

-   <span data-ttu-id="2c6ab-254">**Rozvětveného aplikaci eShopOnContainers pomocí NServiceBus (určitého softwaru)**
    [*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-254">**Forked eShopOnContainers using NServiceBus (Particular Software)**
[*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)</span></span>

-   <span data-ttu-id="2c6ab-255">**Řízené zasílání zpráv**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="2c6ab-256">**Jimmy Bogard. Refaktoring směrem k odolnosti: Vyhodnocení párování**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="2c6ab-257">**Publikování a odběru kanálu**
    [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-257">**Publish-Subscribe channel**
[*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="2c6ab-258">**Komunikace mezi ohraničené kontexty**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="2c6ab-259">**Konzistence typu případné**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="2c6ab-260">**Philip Brown. Strategie pro integraci ohraničených kontextech**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="2c6ab-261">**Chris Richardson. Vývoj transakční Mikroslužeb pomocí agregace, modelu Event Sourcing a CQRS – část 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="2c6ab-262">**Chris Richardson. Model Event Sourcing**
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-262">**Chris Richardson. Event Sourcing pattern**
[*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="2c6ab-263">**Úvod do modelu Event Sourcing**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="2c6ab-264">**Událost Store databáze**.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-264">**Event Store database**.</span></span> <span data-ttu-id="2c6ab-265">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="2c6ab-265">Official site.</span></span>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   <span data-ttu-id="2c6ab-266">**Patrick Nommensen. Správa dat založené na událostech pro Mikroslužby**
    \*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> \*</span><span class="sxs-lookup"><span data-stu-id="2c6ab-266">**Patrick Nommensen. Event-Driven Data Management for Microservices**
\*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> \*</span></span>

-   <span data-ttu-id="2c6ab-267">**Věty**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-267">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="2c6ab-268">**Co je věty?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-268">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="2c6ab-269">**Úvod do konzistence dat**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-269">**Data Consistency Primer**
[*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="2c6ab-270">**Rick Saling. Věty: Proč "Všechno, co jsou různé" bez cloudu a Internetu**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-270">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="2c6ab-271">**Eric Bureš. Zakončení později 12 letech: jak se mění "Pravidla"**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-271">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="2c6ab-272">**Účastní transakce (DTC) externí** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-272">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="2c6ab-273">**Azure Service Bus. Zprostředkované zasílání zpráv: Vyhledávání duplicit**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-273">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="2c6ab-274">**Průvodce spolehlivost** (RabbitMQ dokumentace) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-274">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="2c6ab-275">[Předchozí](rabbitmq-event-bus-development-test-environment.md)
[další](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="2c6ab-275">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
