---
title: Přihlášení k odběru událostí
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s podrobnostmi publikování a předplatného integračních událostí.
ms.date: 01/30/2020
ms.openlocfilehash: 3bfcdb1766a15b1a8e8deab46055f14e1791c2cc
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523594"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="5e5db-103">Přihlášení k odběru událostí</span><span class="sxs-lookup"><span data-stu-id="5e5db-103">Subscribing to events</span></span>

<span data-ttu-id="5e5db-104">Prvním krokem pro použití sběrnice událostí je přihlásit mikroslužeb k události, které chcete přijímat.</span><span class="sxs-lookup"><span data-stu-id="5e5db-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="5e5db-105">To by mělo být provedeno v mikroslužbách přijímače.</span><span class="sxs-lookup"><span data-stu-id="5e5db-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="5e5db-106">Následující jednoduchý kód ukazuje, co každý přijímač mikroslužby potřebuje implementovat `Startup` při spuštění služby (to znamená, že ve třídě), takže se přihlásí k odběru událostí, které potřebuje.</span><span class="sxs-lookup"><span data-stu-id="5e5db-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="5e5db-107">V takovém případě `basket-api` mikroslužby musí `ProductPriceChangedIntegrationEvent` přihlásit k odběru a `OrderStartedIntegrationEvent` zprávy.</span><span class="sxs-lookup"><span data-stu-id="5e5db-107">In this case, the `basket-api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="5e5db-108">Například při přihlášení k odběru `ProductPriceChangedIntegrationEvent` události, který dělá mikroslužbu košíku vědomi jakékoli změny ceny produktu a umožňuje upozornit uživatele o změně, pokud je tento produkt v košíku uživatele.</span><span class="sxs-lookup"><span data-stu-id="5e5db-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="5e5db-109">Po spuštění tohoto kódu bude mikroslužba odběratele naslouchat prostřednictvím kanálů RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="5e5db-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="5e5db-110">Při doručení jakékoli zprávy typu ProductPriceChangedIntegrationEvent kód vyvolá obslužnou rutinu události, která je mu předána, a zpracuje událost.</span><span class="sxs-lookup"><span data-stu-id="5e5db-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="5e5db-111">Publikování událostí prostřednictvím sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="5e5db-111">Publishing events through the event bus</span></span>

<span data-ttu-id="5e5db-112">Nakonec odesílatel zprávy (původ mikroslužby) publikuje události integrace s kódem podobný následujícímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="5e5db-113">(Toto je zjednodušený příklad, který nebere v úvahu nedělitost.) Podobný kód byste implementovali vždy, když událost musí být šířena ve více mikroslužbách, obvykle hned po potvrzení dat nebo transakcí z mikroslužby původu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="5e5db-114">Nejprve objekt implementace sběrnice událostí (na základě RabbitMQ nebo na základě sběrnice) by být vložen a konstruktoru řadiče, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5e5db-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="5e5db-115">Potom jej použijete z metod ovladače, například v metodě UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="5e5db-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("items")]
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

<span data-ttu-id="5e5db-116">V tomto případě vzhledem k tomu, že původ mikroslužby je jednoduchý crud mikroslužby, tento kód je umístěn přímo do řadiče webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5e5db-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="5e5db-117">V pokročilejší mikroslužeb, jako při použití přístupů CQRS, `CommandHandler` může být `Handle()` implementována ve třídě v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="5e5db-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="5e5db-118">Navrhování nedělitosti a odolnosti při publikování na sběrnici událostí</span><span class="sxs-lookup"><span data-stu-id="5e5db-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="5e5db-119">Při publikování událostí integrace prostřednictvím systému distribuovaného zasílání zpráv, jako je sběrnice událostí, máte problém atomicky aktualizovat původní databázi a publikování události (to znamená, že obě operace dokončena nebo žádná z nich).</span><span class="sxs-lookup"><span data-stu-id="5e5db-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="5e5db-120">Například ve zjednodušeném příkladu zobrazeném dříve kód potvrdí data do databáze při změně ceny produktu a poté publikuje zprávu ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="5e5db-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="5e5db-121">Zpočátku může vypadat nezbytné, aby tyto dvě operace byly provedeny atomicky.</span><span class="sxs-lookup"><span data-stu-id="5e5db-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="5e5db-122">Pokud však používáte distribuovanou transakci zahrnující databázi a zprostředkovatele zpráv, stejně jako ve starších systémech, jako je [služba Microsoft Message Queuing (MSMQ),](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)nedoporučujeme to z důvodů popsaných [teorém emistorem CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="5e5db-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="5e5db-123">V podstatě můžete použít mikroslužeb k vytváření škálovatelných a vysoce dostupných systémů.</span><span class="sxs-lookup"><span data-stu-id="5e5db-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="5e5db-124">Zjednodušení poněkud, cap teorém říká, že nelze vytvořit (distribuované) databáze (nebo mikroslužbu, která vlastní svůj model), který je neustále k dispozici, silně konzistentní *a* tolerantní k libovolnému oddílu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="5e5db-125">Je nutné zvolit dvě z těchto tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="5e5db-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="5e5db-126">V architekturách založených na mikroslužbách byste měli zvolit dostupnost a toleranci a měli byste deemphasize silné konzistence.</span><span class="sxs-lookup"><span data-stu-id="5e5db-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="5e5db-127">Proto ve většině moderních aplikací založených na mikroslužbách obvykle nechcete používat distribuované transakce ve zasílání zpráv, stejně jako při implementaci [distribuovaných transakcí](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) založených na koordinátoru DTC (Windows Distributed Transaction Coordinator) se [službou MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="5e5db-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="5e5db-128">Vraťme se k původnímu problému a jeho příkladu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="5e5db-129">Pokud dojde k chybě služby po aktualizaci databáze (v tomto \_případě hned za řádek kódu s kontextem. SaveChangesAsync()), ale před publikováním události integrace může být celkový systém nekonzistentní.</span><span class="sxs-lookup"><span data-stu-id="5e5db-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="5e5db-130">To může být důležité pro podnikání, v závislosti na konkrétní obchodní operace, kterou máte co do činění s.</span><span class="sxs-lookup"><span data-stu-id="5e5db-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="5e5db-131">Jak již bylo zmíněno dříve v části architektura, můžete mít několik přístupů pro řešení tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="5e5db-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="5e5db-132">Použití úplného [vzoru získávání událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span><span class="sxs-lookup"><span data-stu-id="5e5db-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="5e5db-133">Použití [dolování transakční protokol](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="5e5db-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="5e5db-134">Použití [vzoru Pošta k poště k poště k poště .](https://www.kamilgrzybek.com/design/the-outbox-pattern/)</span><span class="sxs-lookup"><span data-stu-id="5e5db-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="5e5db-135">Toto je transakční tabulka pro uložení událostí integrace (rozšíření místní transakce).</span><span class="sxs-lookup"><span data-stu-id="5e5db-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="5e5db-136">V tomto scénáři pomocí úplné události Sourcing (ES) vzor je *the* jedním z nejlepších přístupů, ne-li nejlepší.</span><span class="sxs-lookup"><span data-stu-id="5e5db-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="5e5db-137">V mnoha scénářích aplikace však nemusí být možné implementovat úplný systém ES.</span><span class="sxs-lookup"><span data-stu-id="5e5db-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="5e5db-138">ES znamená ukládání pouze události domény v transakční databázi, namísto ukládání aktuálních dat stavu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="5e5db-139">Ukládání pouze události domény může mít velké výhody, jako je například mít historii vašeho systému k dispozici a je schopen určit stav systému v každém okamžiku v minulosti.</span><span class="sxs-lookup"><span data-stu-id="5e5db-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="5e5db-140">Implementace úplného systému ES však vyžaduje, abyste přezákladňovali většinu systému a zavedli mnoho dalších složitostí a požadavků.</span><span class="sxs-lookup"><span data-stu-id="5e5db-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="5e5db-141">Například byste chtěli použít databázi speciálně vyrobenou pro získávání událostí, jako je [například úložiště událostí](https://eventstore.org/), nebo databázi orientovanou na dokumenty, jako je Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB.</span><span class="sxs-lookup"><span data-stu-id="5e5db-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="5e5db-142">ES je skvělý přístup k tomuto problému, ale není nejjednodušší řešení, pokud jste již obeznámeni s event sourcing.</span><span class="sxs-lookup"><span data-stu-id="5e5db-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="5e5db-143">Možnost použít dolování transakční protokol zpočátku vypadá velmi transparentní.</span><span class="sxs-lookup"><span data-stu-id="5e5db-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="5e5db-144">Chcete-li však použít tento přístup, mikroslužby musí být spojeny s protokolem transakcí RDBMS, jako je například protokol transakcí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5e5db-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="5e5db-145">To pravděpodobně není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-145">This is probably not desirable.</span></span> <span data-ttu-id="5e5db-146">Další nevýhodou je, že aktualizace nižší úrovně zaznamenané v transakčním protokolu nemusí být na stejné úrovni jako události integrace na vysoké úrovni.</span><span class="sxs-lookup"><span data-stu-id="5e5db-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="5e5db-147">Pokud ano, proces zpětného inženýrství těchto operací transakční protokol může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="5e5db-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="5e5db-148">Vyvážený přístup je kombinací transakční databázové tabulky a zjednodušeného vzoru ES.</span><span class="sxs-lookup"><span data-stu-id="5e5db-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="5e5db-149">Můžete použít stav, jako je například "připraven o publikování události", který nastavíte v původní události, když ji potvrdíte do tabulky událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="5e5db-150">Potom se pokusíte publikovat událost do sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="5e5db-151">Pokud akce publikování události úspěšné, spustíte jinou transakci ve službě původu a přesunout stav z "připraven o publikování události" na "událost již byla publikována."</span><span class="sxs-lookup"><span data-stu-id="5e5db-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="5e5db-152">Pokud akce publikování události v sběrnici události selže, data stále nebude nekonzistentní v rámci mikroslužby původu – je stále označenjako "připraven k publikování události" a s ohledem na ostatní služby nakonec bude konzistentní.</span><span class="sxs-lookup"><span data-stu-id="5e5db-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="5e5db-153">Vždy můžete mít úlohy na pozadí, které kontrolují stav transakcí nebo událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="5e5db-154">Pokud úloha najde událost ve stavu "připraveno k publikování události", může se pokusit znovu publikovat tuto událost do sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="5e5db-155">Všimněte si, že s tímto přístupem přetrvává pouze události integrace pro každou mikroslužbu původu a pouze události, které chcete komunikovat s jinými mikroslužbami nebo externími systémy.</span><span class="sxs-lookup"><span data-stu-id="5e5db-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="5e5db-156">Naproti tomu v úplném systému ES ukládáte také všechny události domény.</span><span class="sxs-lookup"><span data-stu-id="5e5db-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="5e5db-157">Tento vyvážený přístup je proto zjednodušeným systémem ES.</span><span class="sxs-lookup"><span data-stu-id="5e5db-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="5e5db-158">Potřebujete seznam integračních událostí s jejich aktuálním stavem ("připraveno k publikování" versus "publikováno").</span><span class="sxs-lookup"><span data-stu-id="5e5db-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="5e5db-159">Ale stačí implementovat tyto stavy pro události integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="5e5db-160">A v tomto přístupu není nutné ukládat všechna data domény jako události v transakční databázi, jako byste v úplném systému ES.</span><span class="sxs-lookup"><span data-stu-id="5e5db-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="5e5db-161">Pokud již používáte relační databázi, můžete použít transakční tabulku k ukládání událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="5e5db-162">K dosažení nedělitelnosti v aplikaci, použijte dvoustupňový proces založený na místní transakce.</span><span class="sxs-lookup"><span data-stu-id="5e5db-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="5e5db-163">V podstatě máte Tabulku IntegrationEvent ve stejné databázi, kde máte entity domény.</span><span class="sxs-lookup"><span data-stu-id="5e5db-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="5e5db-164">Tato tabulka funguje jako pojištění pro dosažení nedělitosti, takže zahrnete trvalé události integrace do stejných transakcí, které posuzují data domény.</span><span class="sxs-lookup"><span data-stu-id="5e5db-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="5e5db-165">Krok za krokem, proces jde takto:</span><span class="sxs-lookup"><span data-stu-id="5e5db-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="5e5db-166">Aplikace spustí transakci místní databáze.</span><span class="sxs-lookup"><span data-stu-id="5e5db-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="5e5db-167">Potom aktualizuje stav entit domény a vloží událost do tabulky událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="5e5db-168">Nakonec potvrdí transakci, takže získáte požadovanou nedělitost a pak</span><span class="sxs-lookup"><span data-stu-id="5e5db-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="5e5db-169">Událost publikujete nějak (další).</span><span class="sxs-lookup"><span data-stu-id="5e5db-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="5e5db-170">Při implementaci kroků publikování událostí máte tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="5e5db-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="5e5db-171">Publikovat událost integrace hned po potvrzení transakce a použít jinou místní transakci označit události v tabulce jako publikována.</span><span class="sxs-lookup"><span data-stu-id="5e5db-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="5e5db-172">Potom použijte tabulku stejně jako artefakt ke sledování událostí integrace v případě problémů ve vzdálených mikroslužeb a provádět kompenzační akce na základě událostí uložené integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="5e5db-173">Použijte tabulku jako druh fronty.</span><span class="sxs-lookup"><span data-stu-id="5e5db-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="5e5db-174">Samostatné vlákno aplikace nebo proces dotazuje tabulku událostí integrace, publikuje události do sběrnice událostí a pak použije místní transakci k označení událostí jako publikovaných.</span><span class="sxs-lookup"><span data-stu-id="5e5db-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="5e5db-175">Obrázek 6-22 ukazuje architekturu pro první z těchto přístupů.</span><span class="sxs-lookup"><span data-stu-id="5e5db-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Diagram nedělitosti při publikování bez mikroslužby pracovníka.](./media/subscribe-events/atomicity-publish-event-bus.png)

<span data-ttu-id="5e5db-177">**Obrázek 6-22**.</span><span class="sxs-lookup"><span data-stu-id="5e5db-177">**Figure 6-22**.</span></span> <span data-ttu-id="5e5db-178">Nedělitost při publikování událostí do sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="5e5db-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="5e5db-179">Přístup znázorněný na obrázku 6-22 chybí další mikroslužeb pracovníka, který má na starosti kontrolu a potvrzení úspěchu publikovaných událostí integrace.</span><span class="sxs-lookup"><span data-stu-id="5e5db-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="5e5db-180">V případě selhání, že další kontrolovky pracovní mikroslužby můžete číst události z tabulky a znovu publikovat, to znamená, opakujte krok číslo 2.</span><span class="sxs-lookup"><span data-stu-id="5e5db-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="5e5db-181">O druhý přístup: použijete Tabulka EventLog jako fronty a vždy použít pracovní mikroslužbu k publikování zpráv.</span><span class="sxs-lookup"><span data-stu-id="5e5db-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="5e5db-182">V takovém případě je proces podobný tomu, který je znázorněn na obrázku 6-23.</span><span class="sxs-lookup"><span data-stu-id="5e5db-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="5e5db-183">To ukazuje další mikroslužbu a tabulka je jeden zdroj při publikování událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Diagram nedělitosti při publikování s mikroslužbou pracovního procesu.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

<span data-ttu-id="5e5db-185">**Obrázek 6-23**.</span><span class="sxs-lookup"><span data-stu-id="5e5db-185">**Figure 6-23**.</span></span> <span data-ttu-id="5e5db-186">Nedělitnost při publikování událostí do sběrnice událostí s mikroslužbou pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="5e5db-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="5e5db-187">Pro jednoduchost eShopOnContainers ukázka používá první přístup (bez dalších procesů nebo kontrolní mikroslužeb) plus sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="5e5db-188">EShopOnContainers však nezpracovává všechny možné případy selhání.</span><span class="sxs-lookup"><span data-stu-id="5e5db-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="5e5db-189">V reálné aplikaci nasazené do cloudu, musíte přijmout skutečnost, že problémy nakonec vzniknou a musíte implementovat tuto logiku kontroly a opětovného odeslání.</span><span class="sxs-lookup"><span data-stu-id="5e5db-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="5e5db-190">Použití tabulky jako fronty může být efektivnější než první přístup, pokud máte tuto tabulku jako jediný zdroj událostí při jejich publikování (s pracovníkem) prostřednictvím sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="5e5db-191">Implementace nedělitosti při publikování událostí integrace prostřednictvím sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="5e5db-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="5e5db-192">Následující kód ukazuje, jak můžete vytvořit jednu transakci zahrnující více objektů DbContext – jeden kontext související s původní data jsou aktualizovány a druhý kontext související s integrationeventlog tabulky.</span><span class="sxs-lookup"><span data-stu-id="5e5db-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="5e5db-193">Všimněte si, že transakce v ukázkovém kódu níže nebude odolná, pokud připojení k databázi mají nějaký problém v době, kdy je spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="5e5db-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="5e5db-194">K tomu může dojít v cloudových systémech, jako je Azure SQL DB, které můžou přesouvat databáze mezi servery.</span><span class="sxs-lookup"><span data-stu-id="5e5db-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="5e5db-195">Implementace odolných transakcí ve více kontextech najdete v [části Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) dále v této příručce.</span><span class="sxs-lookup"><span data-stu-id="5e5db-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="5e5db-196">Pro přehlednost následující příklad ukazuje celý proces v jedné části kódu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="5e5db-197">Implementace eShopOnContainers je však ve skutečnosti refaktorována a rozdělí tuto logiku do více tříd, takže je snadnější udržovat.</span><span class="sxs-lookup"><span data-stu-id="5e5db-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="5e5db-198">Po ProductPriceChangedIntegrationEvent integrační událost zahrnuje transakce, která ukládá původní operace domény (aktualizace položky katalogu) také trvalost události v tabulce EventLog.</span><span class="sxs-lookup"><span data-stu-id="5e5db-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="5e5db-199">Díky tomu je jedna transakce a vždy budete moci zkontrolovat, zda byly odeslány zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="5e5db-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="5e5db-200">Tabulka protokolu událostí je atomicky aktualizována původní databázovou operací pomocí místní transakce proti stejné databázi.</span><span class="sxs-lookup"><span data-stu-id="5e5db-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="5e5db-201">Pokud některá z operací selže, je vyvolána výjimka a transakce vrátí zpět všechny dokončené operace, čímž se zachová konzistence mezi operacemi domény a zprávami událostí uloženými do tabulky.</span><span class="sxs-lookup"><span data-stu-id="5e5db-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="5e5db-202">Příjem zpráv z předplatných: obslužné rutiny událostí v mikroslužbách příjemce</span><span class="sxs-lookup"><span data-stu-id="5e5db-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="5e5db-203">Kromě logiky odběru událostí je třeba implementovat interní kód pro obslužné rutiny událostí integrace (jako je metoda zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="5e5db-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="5e5db-204">Obslužná rutina události je místo, kde určíte, kde budou přijímány a zpracovány zprávy o událostech určitého typu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="5e5db-205">Obslužná rutina události nejprve obdrží instanci události z sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="5e5db-206">Pak vyhledá součást, která má být zpracována související s událostí integrace, šíření a trvalé události jako změna stavu v mikroslužbě příjemce.</span><span class="sxs-lookup"><span data-stu-id="5e5db-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="5e5db-207">Například pokud ProductPriceChanged událost pochází z mikroslužby katalogu, je zpracována v mikroslužbě košíku a změní stav v tomto košíku příjemce mikroslužeb také, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="5e5db-208">Obslužná rutina události musí ověřit, zda produkt existuje v některé z instancí košíku.</span><span class="sxs-lookup"><span data-stu-id="5e5db-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="5e5db-209">Aktualizuje také cenu zboží pro každou související řádkovou položku košíku.</span><span class="sxs-lookup"><span data-stu-id="5e5db-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="5e5db-210">Nakonec vytvoří výstrahu, která se zobrazí uživateli o změně ceny, jak je znázorněno na obrázku 6-24.</span><span class="sxs-lookup"><span data-stu-id="5e5db-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Snímek obrazovky s prohlížečem zobrazujícím oznámení o změně ceny v uživatelském košíku](./media/subscribe-events/display-item-price-change.png)

<span data-ttu-id="5e5db-212">**Obrázek 6-24**.</span><span class="sxs-lookup"><span data-stu-id="5e5db-212">**Figure 6-24**.</span></span> <span data-ttu-id="5e5db-213">Zobrazení změny ceny položky v košíku, jak je sděleno událostmi integrace</span><span class="sxs-lookup"><span data-stu-id="5e5db-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="5e5db-214">Idempotence v událostech zpráv aktualizace</span><span class="sxs-lookup"><span data-stu-id="5e5db-214">Idempotency in update message events</span></span>

<span data-ttu-id="5e5db-215">Důležitým aspektem události zprávy aktualizace je, že selhání v libovolném okamžiku v komunikaci by měla způsobit zprávu opakovat.</span><span class="sxs-lookup"><span data-stu-id="5e5db-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="5e5db-216">V opačném případě se úloha na pozadí může pokusit publikovat událost, která již byla publikována, a vytvořit tak spor.</span><span class="sxs-lookup"><span data-stu-id="5e5db-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="5e5db-217">Musíte se ujistit, že aktualizace jsou idempotentní nebo že poskytují dostatek informací, abyste zajistili, že můžete zjistit duplikát, zahodit je a odeslat zpět pouze jednu odpověď.</span><span class="sxs-lookup"><span data-stu-id="5e5db-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="5e5db-218">Jak již bylo uvedeno dříve, idempotence znamená, že operace může být provedena vícekrát bez změny výsledku.</span><span class="sxs-lookup"><span data-stu-id="5e5db-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="5e5db-219">V prostředí zasílání zpráv, jako při komunikaci událostí, událost je idempotentní, pokud může být doručena vícekrát beze změny výsledku pro mikroslužbu příjemce.</span><span class="sxs-lookup"><span data-stu-id="5e5db-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="5e5db-220">To může být nezbytné z důvodu povahy samotné události nebo z důvodu způsobu, jakým systém zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="5e5db-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="5e5db-221">Idempotence zprávy je důležité v každé aplikaci, která používá zasílání zpráv, nikoli pouze v aplikacích, které implementují vzor sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="5e5db-222">Příkladem idempotentní operace je příkaz SQL, který vkládá data do tabulky pouze v případě, že tato data ještě nejsou v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5e5db-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="5e5db-223">Nezáleží na tom, kolikrát spustíte, že vložit příkaz SQL; výsledek bude stejný – tabulka bude tato data obsahovat.</span><span class="sxs-lookup"><span data-stu-id="5e5db-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="5e5db-224">Idempotence, jako je tato může být také nezbytné při práci se zprávami, pokud zprávy mohou být potenciálně odeslány a proto zpracovány více než jednou.</span><span class="sxs-lookup"><span data-stu-id="5e5db-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="5e5db-225">Například pokud logika opakování způsobí, že odesílatel odeslat přesně stejnou zprávu více než jednou, je třeba se ujistit, že je idempotentní.</span><span class="sxs-lookup"><span data-stu-id="5e5db-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="5e5db-226">Je možné navrhnout idempotentní zprávy.</span><span class="sxs-lookup"><span data-stu-id="5e5db-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="5e5db-227">Můžete například vytvořit událost s nápisem "nastavit cenu produktu na 25 USD" namísto "přidat 5 USD k ceně produktu".</span><span class="sxs-lookup"><span data-stu-id="5e5db-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="5e5db-228">Můžete bezpečně zpracovat první zprávu libovolný počet opakování a výsledek bude stejný.</span><span class="sxs-lookup"><span data-stu-id="5e5db-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="5e5db-229">To neplatí pro druhou zprávu.</span><span class="sxs-lookup"><span data-stu-id="5e5db-229">That is not true for the second message.</span></span> <span data-ttu-id="5e5db-230">Ale i v prvním případě možná nebudete chtít zpracovat první událost, protože systém mohl také odeslat novější událost změny ceny a novou cenu byste přepsali.</span><span class="sxs-lookup"><span data-stu-id="5e5db-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="5e5db-231">Dalším příkladem může být událost dokončená pořadí, která se šíří více odběratelům.</span><span class="sxs-lookup"><span data-stu-id="5e5db-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="5e5db-232">Je důležité, aby informace o objednávce byly aktualizovány v jiných systémech pouze jednou, i když existují duplicitní události zprávy pro stejnou událost dokončení objednávky.</span><span class="sxs-lookup"><span data-stu-id="5e5db-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="5e5db-233">Je vhodné mít nějaký druh identity na událost, takže můžete vytvořit logiku, která vynucuje, že každá událost je zpracována pouze jednou na příjemce.</span><span class="sxs-lookup"><span data-stu-id="5e5db-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="5e5db-234">Některé zpracování zpráv je ze své podstaty idempotentní.</span><span class="sxs-lookup"><span data-stu-id="5e5db-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="5e5db-235">Pokud například systém generuje miniatury obrázků, nemusí záležet na tom, kolikrát bude zpráva o generované miniaturě zpracována; Výsledkem je, že miniatury jsou generovány a jsou pokaždé stejné.</span><span class="sxs-lookup"><span data-stu-id="5e5db-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="5e5db-236">Na druhou stranu operace, jako je volání platební brány k platbě z kreditní karty, nemusí být vůbec idempotentní.</span><span class="sxs-lookup"><span data-stu-id="5e5db-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="5e5db-237">V těchto případech je třeba zajistit, že zpracování zprávy vícekrát má účinek, který očekáváte.</span><span class="sxs-lookup"><span data-stu-id="5e5db-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5e5db-238">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5e5db-238">Additional resources</span></span>

- <span data-ttu-id="5e5db-239">**Ctít idempotenci zprávy** </span><span class="sxs-lookup"><span data-stu-id="5e5db-239">**Honoring message idempotency** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="5e5db-240">Odstranění duplicitních zpráv událostí integrace</span><span class="sxs-lookup"><span data-stu-id="5e5db-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="5e5db-241">Můžete se ujistit, že události zprávy jsou odesílány a zpracovávány pouze jednou na odběratele na různých úrovních.</span><span class="sxs-lookup"><span data-stu-id="5e5db-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="5e5db-242">Jedním ze způsobů je použití funkce odstranění duplicit, kterou nabízí infrastruktura zasílání zpráv, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="5e5db-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="5e5db-243">Dalším je implementovat vlastní logiku v cílové mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="5e5db-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="5e5db-244">S ověřením na úrovni přenosu i na úrovni aplikace je vaše nejlepší sázka.</span><span class="sxs-lookup"><span data-stu-id="5e5db-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="5e5db-245">Odstranění duplicitních událostí zpráv na úrovni EventHandler</span><span class="sxs-lookup"><span data-stu-id="5e5db-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="5e5db-246">Jedním ze způsobů, jak zajistit, že událost je zpracována pouze jednou libovolným příjemcem je implementací určité logiky při zpracování událostí zprávy v obslužných rutinách událostí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="5e5db-247">Například to je přístup používaný v aplikaci eShopOnContainers, jak můžete vidět ve [zdrojovém kódu třídy UserCheckoutAcceptedIntegrationEventHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) když obdrží událost integrace UserCheckoutAcceptedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="5e5db-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="5e5db-248">(V tomto případě jsme zabalit CreateOrderCommand s IdentifiedCommand, pomocí eventMsg.RequestId jako identifikátor, před odesláním do obslužné rutiny příkazu).</span><span class="sxs-lookup"><span data-stu-id="5e5db-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="5e5db-249">Odstranění duplicitzpráv při používání funkce RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="5e5db-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="5e5db-250">Dojde-li k občasnému selhání sítě, mohou být zprávy duplikovány a příjemce zprávy musí být připraven ke zpracování těchto duplicitních zpráv.</span><span class="sxs-lookup"><span data-stu-id="5e5db-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="5e5db-251">Pokud je to možné, příjemci by měli zpracovávat zprávy idempotentním způsobem, což je lepší než explicitní zpracování s deduplikací.</span><span class="sxs-lookup"><span data-stu-id="5e5db-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="5e5db-252">Podle [dokumentace RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Pokud je zpráva doručena spotřebiteli a pak requeued (protože nebyla potvrzena před připojení spotřebitele maže, například), pak RabbitMQ nastaví znovu doručena příznak na něj, když je doručena znovu (zda ke stejnému spotřebiteli nebo jiný).</span><span class="sxs-lookup"><span data-stu-id="5e5db-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="5e5db-253">Pokud je nastaven příznak "redelivered", příjemce musí vzít v úvahu, protože zpráva již mohla být zpracována.</span><span class="sxs-lookup"><span data-stu-id="5e5db-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="5e5db-254">To však není zaručeno; zpráva pravděpodobně nikdy nedosáhlpříjemce poté, co opustil zprostředkovatele zpráv, pravděpodobně z důvodu problémů se sítí.</span><span class="sxs-lookup"><span data-stu-id="5e5db-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="5e5db-255">Na druhou stranu, pokud "redelivered" příznak není nastaven, je zaručeno, že zpráva nebyla odeslána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="5e5db-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="5e5db-256">Příjemce proto potřebuje deduplikovat zprávy nebo zpracovat zprávy idempotentním způsobem pouze v případě, že je ve zprávě nastaven příznak "redelivered".</span><span class="sxs-lookup"><span data-stu-id="5e5db-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5e5db-257">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5e5db-257">Additional resources</span></span>

- <span data-ttu-id="5e5db-258">**Vidlicí eShopOnKontejnery používající NServiceBus (konkrétní software)** </span><span class="sxs-lookup"><span data-stu-id="5e5db-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="5e5db-259">**Zasílání zpráv řízených událostmi** </span><span class="sxs-lookup"><span data-stu-id="5e5db-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="5e5db-260">**Jimmyho Bogarda. Refaktoring směrem k odolnosti: Hodnocení spojky** </span><span class="sxs-lookup"><span data-stu-id="5e5db-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="5e5db-261">**Kanál publikování a odběru** </span><span class="sxs-lookup"><span data-stu-id="5e5db-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="5e5db-262">**Komunikace mezi ohraničené kontexty** </span><span class="sxs-lookup"><span data-stu-id="5e5db-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="5e5db-263">**Konečná konzistence** </span><span class="sxs-lookup"><span data-stu-id="5e5db-263">**Eventual Consistency** </span></span>\
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- <span data-ttu-id="5e5db-264">**Philipbrown, to je můj otec. Strategie pro integraci ohraničených kontextů** </span><span class="sxs-lookup"><span data-stu-id="5e5db-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="5e5db-265">**Chrise Richardsona. Vývoj transakčních mikroslužeb pomocí agregátů, zdrojů událostí a CQRS - část 2** </span><span class="sxs-lookup"><span data-stu-id="5e5db-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="5e5db-266">**Chrise Richardsona. Vzor získávání událostí** </span><span class="sxs-lookup"><span data-stu-id="5e5db-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="5e5db-267">**Představujeme získávání událostí** </span><span class="sxs-lookup"><span data-stu-id="5e5db-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="5e5db-268">**Databáze úložiště událostí**.</span><span class="sxs-lookup"><span data-stu-id="5e5db-268">**Event Store database**.</span></span> <span data-ttu-id="5e5db-269">Oficiální stránky.</span><span class="sxs-lookup"><span data-stu-id="5e5db-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="5e5db-270">**Patrik Nommensen. Správa dat řízená událostmi pro mikroslužby** </span><span class="sxs-lookup"><span data-stu-id="5e5db-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="5e5db-271">**Teorém SZP** </span><span class="sxs-lookup"><span data-stu-id="5e5db-271">**The CAP Theorem** </span></span>\
    <https://en.wikipedia.org/wiki/CAP_theorem>

- <span data-ttu-id="5e5db-272">**Co je cap teorém?**</span><span class="sxs-lookup"><span data-stu-id="5e5db-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="5e5db-273">**Základní nátěr konzistence dat** </span><span class="sxs-lookup"><span data-stu-id="5e5db-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="5e5db-274">**Rick Saling. Teorém SZP: Proč je "Všechno je jiné" s cloudem a internetem** </span><span class="sxs-lookup"><span data-stu-id="5e5db-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="5e5db-275">**Eric Brewer, to je ono. SZP o dvanáct let později: Jak se změnila "pravidla"** </span><span class="sxs-lookup"><span data-stu-id="5e5db-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="5e5db-276">**Azure Service Bus. Zprostředkované zasílání zpráv: vyhledávání duplicit**  </span><span class="sxs-lookup"><span data-stu-id="5e5db-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="5e5db-277">**Průvodce spolehlivostí** (dokumentace RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="5e5db-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> <span data-ttu-id="5e5db-278">[Předchozí](rabbitmq-event-bus-development-test-environment.md)
> [další](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="5e5db-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
