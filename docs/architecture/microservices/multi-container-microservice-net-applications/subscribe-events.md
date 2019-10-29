---
title: Přihlášení k odběru událostí
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s podrobnostmi o publikování a předplatném integračních událostí.
ms.date: 10/02/2018
ms.openlocfilehash: 208b0f27aa1e6ceb6686e9e846b6e31d9f1c74df
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035642"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="ce35c-103">Přihlášení k odběru událostí</span><span class="sxs-lookup"><span data-stu-id="ce35c-103">Subscribing to events</span></span>

<span data-ttu-id="ce35c-104">Prvním krokem pro použití sběrnice Event je přihlášení k odběru mikroslužeb k událostem, které chtějí přijímat.</span><span class="sxs-lookup"><span data-stu-id="ce35c-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="ce35c-105">To by mělo být provedeno v mikroslužbách přijímače.</span><span class="sxs-lookup"><span data-stu-id="ce35c-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="ce35c-106">Následující jednoduchý kód ukazuje, co každá mikroslužba přijímače potřebuje implementovat při spuštění služby (to znamená ve třídě `Startup`), aby se přihlásila k odběru událostí, které potřebuje.</span><span class="sxs-lookup"><span data-stu-id="ce35c-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="ce35c-107">V takovém případě se `basket.api` mikroslužeb musí přihlásit k odběru `ProductPriceChangedIntegrationEvent` a `OrderStartedIntegrationEvent` zpráv.</span><span class="sxs-lookup"><span data-stu-id="ce35c-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="ce35c-108">Například při přihlášení k odběru události `ProductPriceChangedIntegrationEvent`, která umožňuje, aby mikroslužba koše mohla vědět o jakýchkoli změnách ceny za produkt, a umožňuje uživateli upozornit na změnu v případě, že je tento produkt v koši uživatele.</span><span class="sxs-lookup"><span data-stu-id="ce35c-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="ce35c-109">Po spuštění tohoto kódu bude služba pro předplatitele naslouchat prostřednictvím RabbitMQ kanálů.</span><span class="sxs-lookup"><span data-stu-id="ce35c-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="ce35c-110">Při doručení libovolné zprávy typu ProductPriceChangedIntegrationEvent kód vyvolá obslužnou rutinu události, která je předána a zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="ce35c-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="ce35c-111">Publikování událostí prostřednictvím sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="ce35c-111">Publishing events through the event bus</span></span>

<span data-ttu-id="ce35c-112">Nakonec odesílatel zprávy (původ mikroslužeb) publikuje události integrace s kódem podobným následujícímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="ce35c-113">(Jedná se o zjednodušený příklad, který nebere v úvahu nedělitelnost.) Podobný kód byste implementovali vždy, když je nutné rozšířit událost napříč několika mikroslužbami, obvykle po potvrzení dat nebo transakcí od původu mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ce35c-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="ce35c-114">Nejprve bude objekt implementace sběrnice událostí (založený na RabbitMQ nebo na základě služby Service Bus) vložen do konstruktoru kontroleru, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ce35c-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="ce35c-115">Pak ho použijete z metod řadiče, jako v metodě UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="ce35c-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="ce35c-116">V tomto případě, vzhledem k tomu, že je zdrojem mikroslužeb jednoduchá CRUD, je kód umístěný přímo do kontroleru webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ce35c-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="ce35c-117">V pokročilejších mikroslužbách, například při použití CQRS přístupů, je možné ji implementovat do třídy `CommandHandler` v rámci metody `Handle()`.</span><span class="sxs-lookup"><span data-stu-id="ce35c-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="ce35c-118">Návrh atomické a odolnosti při publikování do sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="ce35c-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="ce35c-119">Když publikujete integrační události prostřednictvím distribuovaného systému zasílání zpráv, jako je vaše sběrnice událostí, máte problém s atomovou aktualizací původní databáze a publikováním události (to znamená, že se buď dokončí obě operace, nebo žádné z nich).</span><span class="sxs-lookup"><span data-stu-id="ce35c-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="ce35c-120">Například u zjednodušeného příkladu, který byl výše uveden, kód potvrdí data do databáze při změně ceny produktu a následném publikování zprávy ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="ce35c-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="ce35c-121">Zpočátku může být důležité, aby tyto dvě operace byly prováděny atomicky.</span><span class="sxs-lookup"><span data-stu-id="ce35c-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="ce35c-122">Pokud ale používáte distribuovanou transakci zahrnující databázi a zprostředkovatele zpráv, stejně jako ve starších systémech, jako je služba [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), to se nedoporučuje z důvodů popsaných v [věta Cap](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="ce35c-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="ce35c-123">V podstatě používáte mikroslužby k vytváření škálovatelných systémů s vysokou dostupností.</span><span class="sxs-lookup"><span data-stu-id="ce35c-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="ce35c-124">Poněkud větší věta znamená, že nemůžete sestavit (distribuovanou) databázi (nebo mikroslužbu, která vlastní svůj model), která je trvale dostupná, silně konzistentní *a* odolná vůči jakémukoli oddílu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="ce35c-125">Musíte zvolit dvě z těchto tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="ce35c-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="ce35c-126">V architekturách založených na mikroslužbách byste měli zvolit dostupnost a toleranci a měli byste zdůraznit silnou konzistenci.</span><span class="sxs-lookup"><span data-stu-id="ce35c-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="ce35c-127">Proto ve většině moderních aplikací založených na mikroslužbách nechcete při implementaci [distribuovaných transakcí](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) na základě Windows DTC (DISTRIBUTED Transaction Coordinator) (DTC) obvykle používat distribuované transakce v rámci zasílání zpráv. pomocí [služby MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="ce35c-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="ce35c-128">Pojďme se vrátit k původnímu problému a jeho příkladu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="ce35c-129">Pokud služba po aktualizaci databáze dojde k chybě (v tomto případě je to hned za řádkem kódu s \_m kontextem. SaveChangesAsync ()), ale před publikováním události integrace, by celkový systém mohl být nekonzistentní.</span><span class="sxs-lookup"><span data-stu-id="ce35c-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="ce35c-130">To může být důležité pro podnikání v závislosti na konkrétní obchodní operaci, se kterou se chystáte pracovat.</span><span class="sxs-lookup"><span data-stu-id="ce35c-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="ce35c-131">Jak bylo zmíněno dříve v části architektura, můžete mít několik přístupů k řešení tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="ce35c-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="ce35c-132">Pomocí vzoru úplných [zdrojů událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span><span class="sxs-lookup"><span data-stu-id="ce35c-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="ce35c-133">Pomocí [dolování protokolu transakcí](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="ce35c-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="ce35c-134">Pomocí [vzoru pošty k odeslání](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span><span class="sxs-lookup"><span data-stu-id="ce35c-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="ce35c-135">Toto je transakční tabulka pro uložení integračních událostí (rozšíření místní transakce).</span><span class="sxs-lookup"><span data-stu-id="ce35c-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="ce35c-136">V tomto scénáři je jedním z nejlepších přístupů použití vzoru úplných událostí (ES), pokud *to není nejlepší* .</span><span class="sxs-lookup"><span data-stu-id="ce35c-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="ce35c-137">V mnoha scénářích aplikací ale nemusí být možné implementovat úplný systém ES.</span><span class="sxs-lookup"><span data-stu-id="ce35c-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="ce35c-138">ES znamená ukládání pouze doménových událostí do transakční databáze místo ukládání aktuálních dat o stavu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="ce35c-139">Ukládání pouze událostí v doméně může mít skvělé výhody, jako je třeba historie vašeho systému a možnost zjistit stav systému v minulosti.</span><span class="sxs-lookup"><span data-stu-id="ce35c-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="ce35c-140">Implementace celého systému ES ale vyžaduje, abyste převedli své architekty na většinu systému a předvedli spoustu dalších složitých a požadavků.</span><span class="sxs-lookup"><span data-stu-id="ce35c-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="ce35c-141">Například byste chtěli použít databázi specifickou pro daný původ události, jako je například [úložiště událostí](https://eventstore.org/), nebo databáze orientovaný na dokument, například Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB.</span><span class="sxs-lookup"><span data-stu-id="ce35c-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="ce35c-142">ES je skvělý přístup k tomuto problému, ale ne nejjednodušší řešení, pokud už neznáte jeho původ.</span><span class="sxs-lookup"><span data-stu-id="ce35c-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="ce35c-143">Možnost použít dolování protokolu transakcí zpočátku vypadá velmi transparentně.</span><span class="sxs-lookup"><span data-stu-id="ce35c-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="ce35c-144">Chcete-li však použít tento přístup, musí být mikroslužba spojena s protokolem transakcí RDBMS, jako je například protokol transakcí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ce35c-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="ce35c-145">To pravděpodobně není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-145">This is probably not desirable.</span></span> <span data-ttu-id="ce35c-146">Další nevýhodou je, že aktualizace nízké úrovně zaznamenané v protokolu transakcí nemusí být na stejné úrovni jako vaše integrační události vysoké úrovně.</span><span class="sxs-lookup"><span data-stu-id="ce35c-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="ce35c-147">V takovém případě může být proces zpětného strojírenství těchto operací s protokolem transakcí obtížné.</span><span class="sxs-lookup"><span data-stu-id="ce35c-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="ce35c-148">Vyvážený přístup je kombinací transakční tabulky databáze a zjednodušeného vzoru ES.</span><span class="sxs-lookup"><span data-stu-id="ce35c-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="ce35c-149">Můžete použít stav, například "připraveno k publikování události", který jste nastavili v původní události při jejich potvrzení do tabulky integračních událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="ce35c-150">Pak se pokusíte publikovat událost do sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="ce35c-151">Pokud je akce publikovat-událost úspěšná, spustíte jinou transakci ve zdrojové službě a přesunete stav z "připraveno k publikování události" do "již publikované události".</span><span class="sxs-lookup"><span data-stu-id="ce35c-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="ce35c-152">Pokud akce publikovat-událost ve sběrnici událostí selže, data stále nebudou v původním mikroslužbě konzistentní – bude stále označena jako "připraveno k publikování události" a s ohledem na zbytek služeb bude nakonec konzistentní.</span><span class="sxs-lookup"><span data-stu-id="ce35c-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="ce35c-153">Kdykoli můžete mít úlohy na pozadí, které kontrolují stav transakcí nebo integračních událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="ce35c-154">Pokud úloha najde událost ve stavu "připraveno k publikování události", může se pokusit tuto událost znovu publikovat do sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="ce35c-155">Všimněte si, že s tímto přístupem jste zachovali jenom události integrace pro každou zdrojovou mikroslužbu a jenom události, které chcete komunikovat s dalšími mikroslužbami nebo externími systémy.</span><span class="sxs-lookup"><span data-stu-id="ce35c-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="ce35c-156">Na rozdíl od úplného systému ES ukládáte i všechny události domény.</span><span class="sxs-lookup"><span data-stu-id="ce35c-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="ce35c-157">Proto je tento vyvážený přístup zjednodušený systém ES.</span><span class="sxs-lookup"><span data-stu-id="ce35c-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="ce35c-158">Budete potřebovat seznam událostí integrace s jejich aktuálním stavem ("připraveno k publikování" versus "Publikováno").</span><span class="sxs-lookup"><span data-stu-id="ce35c-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="ce35c-159">Ale stačí, abyste tyto stavy implementovali pro integrační události.</span><span class="sxs-lookup"><span data-stu-id="ce35c-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="ce35c-160">A v tomto přístupu nemusíte ukládat veškerá doménová data jako události do transakční databáze, stejně jako v plném systému ES.</span><span class="sxs-lookup"><span data-stu-id="ce35c-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="ce35c-161">Pokud již používáte relační databázi, můžete k ukládání integračních událostí použít transakční tabulku.</span><span class="sxs-lookup"><span data-stu-id="ce35c-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="ce35c-162">Chcete-li dosáhnout nedělitelnost v aplikaci, použijte proces se dvěma kroky, který je založen na místních transakcích.</span><span class="sxs-lookup"><span data-stu-id="ce35c-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="ce35c-163">V podstatě máte tabulku IntegrationEvent ve stejné databázi, ve které máte vaše doménové entity.</span><span class="sxs-lookup"><span data-stu-id="ce35c-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="ce35c-164">Tato tabulka spolupracuje jako pojištění pro dosažení nedělitelnost, takže zahrnete trvalé integrační události do stejných transakcí, které potvrzují data domény.</span><span class="sxs-lookup"><span data-stu-id="ce35c-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="ce35c-165">Krok za krokem proces bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="ce35c-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="ce35c-166">Aplikace zahájí místní databázovou transakci.</span><span class="sxs-lookup"><span data-stu-id="ce35c-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="ce35c-167">Pak aktualizuje stav entit vaší domény a vloží událost do tabulky integračních událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="ce35c-168">Nakonec potvrdí transakci, takže získáte požadovanou nedělitelnost a pak</span><span class="sxs-lookup"><span data-stu-id="ce35c-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="ce35c-169">Událost se publikuje nějakým způsobem (další).</span><span class="sxs-lookup"><span data-stu-id="ce35c-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="ce35c-170">Při implementaci kroků publikování událostí máte tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="ce35c-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="ce35c-171">Publikovat událost Integration hned po potvrzení transakce a použít jinou místní transakci k označení událostí v tabulce jako publikovaná.</span><span class="sxs-lookup"><span data-stu-id="ce35c-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="ce35c-172">Pak použijte tabulku stejně jako artefakt ke sledování událostí integrace v případě problémů se vzdálenými mikroslužbami a provádění kompenzačních akcí na základě uložených integračních událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="ce35c-173">Použijte tabulku jako typ fronty.</span><span class="sxs-lookup"><span data-stu-id="ce35c-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="ce35c-174">Samostatné vlákno aplikace nebo zpracovává dotaz na tabulku událostí integrace, zveřejňuje události do sběrnice událostí a poté používá místní transakci k označení událostí jako publikovaných.</span><span class="sxs-lookup"><span data-stu-id="ce35c-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="ce35c-175">Obrázek 6-22 ukazuje architekturu pro první z těchto přístupů.</span><span class="sxs-lookup"><span data-stu-id="ce35c-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Jeden z přístupů ke zpracování nedělitelnost při publikování událostí: použijte jednu transakci k potvrzení události do tabulky protokolu událostí a pak další transakci, která se má publikovat (používá se v eShopOnContainers).](./media/image23.png)

<span data-ttu-id="ce35c-177">**Obrázek 6-22**.</span><span class="sxs-lookup"><span data-stu-id="ce35c-177">**Figure 6-22**.</span></span> <span data-ttu-id="ce35c-178">Nedělitelnost při publikování událostí do sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="ce35c-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="ce35c-179">Při přístupu na obrázku 6-22 chybí další mikroslužba pracovního procesu, která má za následek kontrolu a ověření úspěchu publikovaných integračních událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="ce35c-180">V případě selhání může tato služba Worker Worker z tabulky číst události a znovu je publikovat, to znamená opakovat krok číslo 2.</span><span class="sxs-lookup"><span data-stu-id="ce35c-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="ce35c-181">O druhém přístupu: použijte tabulku EventLog jako frontu a vždy použijte k publikování těchto zpráv pracovní mikroslužbu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="ce35c-182">V takovém případě se jedná o proces, který je znázorněn na obrázku 6-23.</span><span class="sxs-lookup"><span data-stu-id="ce35c-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="ce35c-183">Zobrazí se další mikroslužba a tabulka je jediným zdrojem při publikování událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Další způsob, jak ošetřit nedělitelnost: publikovat do tabulky protokolu událostí a pak mít další mikroslužbu (pracovníka na pozadí), která tuto událost publikuje.](./media/image24.png)

<span data-ttu-id="ce35c-185">**Obrázek 6-23**.</span><span class="sxs-lookup"><span data-stu-id="ce35c-185">**Figure 6-23**.</span></span> <span data-ttu-id="ce35c-186">Nedělitelnost při publikování událostí do sběrnice událostí pomocí mikroslužby pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="ce35c-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="ce35c-187">Pro zjednodušení ukázka eShopOnContainers používá první přístup (bez dalších procesů nebo mikroslužeb pro kontrolu) a sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="ce35c-188">EShopOnContainers ale nezpracovává všechny možné případy selhání.</span><span class="sxs-lookup"><span data-stu-id="ce35c-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="ce35c-189">V reálné aplikaci nasazené do cloudu je nutné zaplnit skutečnost, že k problémům dojde nakonec, a musíte tuto kontrolu implementovat a znovu odeslat.</span><span class="sxs-lookup"><span data-stu-id="ce35c-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="ce35c-190">Použití tabulky jako fronty může být efektivnější než první přístup, pokud tuto tabulku máte jako jediný zdroj událostí při jejich publikování (s pracovním procesem) prostřednictvím sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="ce35c-191">Implementace atomické události při publikování integračních událostí prostřednictvím sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="ce35c-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="ce35c-192">Následující kód ukazuje, jak lze vytvořit jednu transakci zahrnující více objektů DbContext – jeden kontext související s původními daty, která jsou aktualizována, a druhý kontext vztahující se k tabulce IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="ce35c-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="ce35c-193">Všimněte si, že transakce v následujícím ukázkovém kódu nebude odolná, pokud mají připojení k databázi nějaký problém v době, kdy je kód spuštěný.</span><span class="sxs-lookup"><span data-stu-id="ce35c-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="ce35c-194">K tomu může dojít v cloudových systémech, jako je Azure SQL DB, které mohou přesouvat databáze na serverech.</span><span class="sxs-lookup"><span data-stu-id="ce35c-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="ce35c-195">Informace o implementaci odolných transakcí napříč více kontexty najdete v části [implementace odolného Entity Framework Core připojení SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) dále v této příručce.</span><span class="sxs-lookup"><span data-stu-id="ce35c-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="ce35c-196">Pro přehlednost následující příklad ukazuje celý proces v jednom kusu kódu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="ce35c-197">Implementace eShopOnContainers je ale ve skutečnosti refaktorovaná a rozdělí tuto logiku do více tříd, takže ji můžete snáze udržovat.</span><span class="sxs-lookup"><span data-stu-id="ce35c-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="ce35c-198">Po vytvoření události integrace ProductPriceChangedIntegrationEvent bude transakce, která obsahuje operaci původní domény (aktualizovat položku katalogu), zahrnovat také trvalost události v tabulce EventLog.</span><span class="sxs-lookup"><span data-stu-id="ce35c-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="ce35c-199">Díky tomu bude jediná transakce a vždy budete moci ověřit, zda byly zasílány zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="ce35c-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="ce35c-200">Tabulka protokolu událostí je aktualizována atomicky s původní databázovou operací pomocí místní transakce se stejnou databází.</span><span class="sxs-lookup"><span data-stu-id="ce35c-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="ce35c-201">Pokud dojde k selhání některé z operací, je vyvolána výjimka a transakce vrátí zpět všechny dokončené operace, čímž se zachovává konzistence mezi doménovými operacemi a zprávami událostí uloženými do tabulky.</span><span class="sxs-lookup"><span data-stu-id="ce35c-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="ce35c-202">Příjem zpráv z předplatných: obslužné rutiny událostí v mikroslužbách přijímače</span><span class="sxs-lookup"><span data-stu-id="ce35c-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="ce35c-203">Kromě logiky odběru událostí je nutné implementovat interní kód pro obslužné rutiny událostí integrace (jako metoda zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="ce35c-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="ce35c-204">Obslužná rutina události je tam, kde určíte, kde budou přijaty a zpracovány zprávy událostí určitého typu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="ce35c-205">Obslužná rutina události nejprve přijme instanci události ze sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="ce35c-206">Pak vyhledá komponentu, která se má zpracovat v souvislosti s touto integrační událostí, šíří a uchovává událost jako změnu stavu ve službě přijímače.</span><span class="sxs-lookup"><span data-stu-id="ce35c-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="ce35c-207">Pokud například událost ProductPriceChanged vznikla v katalogu služby Catalog, je zpracována v mikroslužbě koše a mění stav v této mikroslužbě koše přijímače, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ce35c-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="ce35c-208">Obslužná rutina události musí ověřit, zda produkt existuje v žádné z instancí koše.</span><span class="sxs-lookup"><span data-stu-id="ce35c-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="ce35c-209">Také aktualizuje cenu položky pro každou související položku řádku košíku.</span><span class="sxs-lookup"><span data-stu-id="ce35c-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="ce35c-210">Nakonec se vytvoří výstraha, která uživateli zobrazí informace o změně ceny, jak je znázorněno na obrázku 6-24.</span><span class="sxs-lookup"><span data-stu-id="ce35c-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Zobrazení prohlížeče oznámení o změně procesu na uživatelském košíku.](./media/image25.png)

<span data-ttu-id="ce35c-212">**Obrázek 6-24**.</span><span class="sxs-lookup"><span data-stu-id="ce35c-212">**Figure 6-24**.</span></span> <span data-ttu-id="ce35c-213">Zobrazení změny ceny položky v košíku, jak se sdělují událostmi integrace</span><span class="sxs-lookup"><span data-stu-id="ce35c-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="ce35c-214">Idempotence v událostech zprávy Update</span><span class="sxs-lookup"><span data-stu-id="ce35c-214">Idempotency in update message events</span></span>

<span data-ttu-id="ce35c-215">Důležitým aspektem událostí aktualizace zpráv je to, že selhání v jakémkoli bodě komunikace by mělo způsobit opakování zprávy.</span><span class="sxs-lookup"><span data-stu-id="ce35c-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="ce35c-216">Jinak se úloha na pozadí může pokusit publikovat událost, která už je publikovaná, a vytvořit tak konflikt časování.</span><span class="sxs-lookup"><span data-stu-id="ce35c-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="ce35c-217">Je nutné zajistit, aby byly aktualizace buď idempotentní, nebo aby poskytovaly dostatek informací, aby bylo možné zjistit, zda je duplicitní, zahozena a odeslána zpět pouze jedna odpověď.</span><span class="sxs-lookup"><span data-stu-id="ce35c-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="ce35c-218">Jak bylo uvedeno dříve, idempotence znamená, že operaci lze provést několikrát, aniž by došlo ke změně výsledku.</span><span class="sxs-lookup"><span data-stu-id="ce35c-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="ce35c-219">V prostředí pro zasílání zpráv, jako při komunikaci událostí, je událost idempotentní, pokud se dá doručit víckrát, aniž by se změnil výsledek pro mikroslužbu přijímače.</span><span class="sxs-lookup"><span data-stu-id="ce35c-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="ce35c-220">To může být nutné z důvodu povahy samotné události nebo z důvodu způsobu, jakým systém událost zpracovává.</span><span class="sxs-lookup"><span data-stu-id="ce35c-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="ce35c-221">Zpráva idempotence je důležitá v jakékoli aplikaci, která používá zasílání zpráv, nejen v aplikacích, které implementují model sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="ce35c-222">Příkladem operace idempotentní je příkaz SQL, který vkládá data do tabulky pouze v případě, že tato data v tabulce ještě nejsou.</span><span class="sxs-lookup"><span data-stu-id="ce35c-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="ce35c-223">Nezáleží na tom, kolikrát spustíte příkaz Insert jazyka SQL. výsledek bude stejný, tabulka bude obsahovat tato data.</span><span class="sxs-lookup"><span data-stu-id="ce35c-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="ce35c-224">Idempotence podobným způsobem může být také nutné při práci se zprávami, pokud je možné zprávy potenciálně odeslat, a proto je zpracovat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="ce35c-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="ce35c-225">Pokud například logika opakování způsobí, že odesílatel pošle přesně stejnou zprávu více než jednou, musíte se ujistit, že je idempotentní.</span><span class="sxs-lookup"><span data-stu-id="ce35c-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="ce35c-226">Je možné navrhnout zprávy idempotentní.</span><span class="sxs-lookup"><span data-stu-id="ce35c-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="ce35c-227">Můžete například vytvořit událost s informacemi "nastavit cenu produktu na $25" místo "Přidat $5 k ceně produktu".</span><span class="sxs-lookup"><span data-stu-id="ce35c-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="ce35c-228">První zprávu můžete bezpečně zpracovat několikrát a výsledek bude stejný.</span><span class="sxs-lookup"><span data-stu-id="ce35c-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="ce35c-229">Ta není pro druhou zprávu pravdivá.</span><span class="sxs-lookup"><span data-stu-id="ce35c-229">That is not true for the second message.</span></span> <span data-ttu-id="ce35c-230">Ale i v prvním případě nebudete chtít zpracovat první událost, protože systém mohl také odeslat novou událost změny ceny a za novou cenu byste přepsali.</span><span class="sxs-lookup"><span data-stu-id="ce35c-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="ce35c-231">Dalším příkladem může být událost dokončená v pořadí, která se šíří více odběratelům.</span><span class="sxs-lookup"><span data-stu-id="ce35c-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="ce35c-232">Je důležité, aby se informace o objednávkách aktualizovaly v jiných systémech, a to i v případě, že existují duplicitní události zpráv pro stejnou událost – dokončeno.</span><span class="sxs-lookup"><span data-stu-id="ce35c-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="ce35c-233">Je vhodné mít nějaký druh identity na událost, abyste mohli vytvořit logiku, která vynutila, že každá událost je zpracována pouze jednou pro každého příjemce.</span><span class="sxs-lookup"><span data-stu-id="ce35c-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="ce35c-234">Některé zpracování zpráv je ze své podstaty idempotentní.</span><span class="sxs-lookup"><span data-stu-id="ce35c-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="ce35c-235">Například pokud systém vygeneruje miniatury obrázků, může to být bez ohledu na to, kolikrát je zpracována zpráva o vygenerované miniatuře; Výsledkem je, že jsou vygenerovány miniatury a jsou vždy stejné.</span><span class="sxs-lookup"><span data-stu-id="ce35c-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="ce35c-236">Na druhé straně operace, jako je například volání brány pro platby za účelem účtování platební karty, nemusí být idempotentní vůbec.</span><span class="sxs-lookup"><span data-stu-id="ce35c-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="ce35c-237">V těchto případech je potřeba zajistit, aby zpracování zprávy bylo ve více časech.</span><span class="sxs-lookup"><span data-stu-id="ce35c-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ce35c-238">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ce35c-238">Additional resources</span></span>

- <span data-ttu-id="ce35c-239">**Respektování zprávy idempotence**</span><span class="sxs-lookup"><span data-stu-id="ce35c-239">**Honoring message idempotency**</span></span>  
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="ce35c-240">Odstraňování duplicitních zpráv událostí integrace</span><span class="sxs-lookup"><span data-stu-id="ce35c-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="ce35c-241">Můžete zajistit, aby byly události zpráv odesílány a zpracovávány pouze jednou pro předplatitele na různých úrovních.</span><span class="sxs-lookup"><span data-stu-id="ce35c-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="ce35c-242">Jedním ze způsobů je použít funkci odstranění duplicit nabízenou infrastrukturou zasílání zpráv, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="ce35c-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="ce35c-243">Další je implementace vlastní logiky v cílové mikroslužbě.</span><span class="sxs-lookup"><span data-stu-id="ce35c-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="ce35c-244">Nejlepším řešením je použití ověření na úrovni přenosu i na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce35c-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="ce35c-245">Odstranění duplicit událostí zpráv na úrovni EventHandler</span><span class="sxs-lookup"><span data-stu-id="ce35c-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="ce35c-246">Jedním ze způsobů, jak zajistit, že událost je zpracovávána pouze jednou příjemcem, je implementace určité logiky při zpracování událostí zpráv v obslužných rutinách událostí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="ce35c-247">Například to je přístup, který se používá v aplikaci eShopOnContainers, jak můžete vidět ve [zdrojovém kódu třídy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) , když přijme událost integrace UserCheckoutAcceptedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="ce35c-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="ce35c-248">(V tomto případě jsme CreateOrderCommand pomocí IdentifiedCommand, pomocí eventMsg. RequestId jako identifikátoru, před odesláním obslužné rutině příkazu).</span><span class="sxs-lookup"><span data-stu-id="ce35c-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="ce35c-249">Odstranění duplicit zpráv při použití RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="ce35c-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="ce35c-250">Dojde-li k přerušovanému výpadku sítě, mohou být zprávy duplikovány a přijímač zpráv musí být připraven na zpracování duplicitních zpráv.</span><span class="sxs-lookup"><span data-stu-id="ce35c-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="ce35c-251">Pokud je to možné, přijímače by měly zpracovávat zprávy idempotentní způsobem, který je lepší, než je výslovně zpracovává odstranění duplicit.</span><span class="sxs-lookup"><span data-stu-id="ce35c-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="ce35c-252">Podle [dokumentace RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer)se zobrazí zpráva o tom, že pokud se pošle zpráva příjemci a pak se znovu zařadila do fronty (protože nebyla potvrzena před zahozením připojení k uživateli), pak RabbitMQ při doručení nastaví příznak opětovného doručení. znovu (zda ke stejnému uživateli nebo jinému).</span><span class="sxs-lookup"><span data-stu-id="ce35c-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="ce35c-253">Pokud je nastaven příznak "", příjemce musí brát v úvahu, protože zpráva již mohla být zpracována.</span><span class="sxs-lookup"><span data-stu-id="ce35c-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="ce35c-254">Ale to není zaručené; Zpráva by nikdy nebyla přes příjemce po ukončení služby Zprostředkovatel zpráv, možná kvůli problémům se sítí.</span><span class="sxs-lookup"><span data-stu-id="ce35c-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="ce35c-255">Na druhé straně, pokud není nastaven příznak "", je zaručeno, že zpráva nebyla odeslána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="ce35c-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="ce35c-256">Proto přijímač potřebuje k odstranění duplicitních zpráv nebo zpracování zpráv v idempotentní způsobem pouze v případě, že je ve zprávě nastaven příznak "předáno".</span><span class="sxs-lookup"><span data-stu-id="ce35c-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ce35c-257">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ce35c-257">Additional resources</span></span>

- <span data-ttu-id="ce35c-258">**Rozvětvené eShopOnContainers s použitím NServiceBus (konkrétní software)**  </span><span class="sxs-lookup"><span data-stu-id="ce35c-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="ce35c-259">**Zasílání zpráv řízených událostmi** </span><span class="sxs-lookup"><span data-stu-id="ce35c-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="ce35c-260">**Jimmy Bogard. Refaktoring směrem k odolnosti: vyhodnocení spojovacího** </span><span class="sxs-lookup"><span data-stu-id="ce35c-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="ce35c-261"> \ **kanálu pro publikování a odběr**</span><span class="sxs-lookup"><span data-stu-id="ce35c-261">**Publish-Subscribe channel** \</span></span>
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="ce35c-262">**Komunikace mezi ohraničenými kontexty** </span><span class="sxs-lookup"><span data-stu-id="ce35c-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="ce35c-263">Konečné \ **konzistence**</span><span class="sxs-lookup"><span data-stu-id="ce35c-263">**Eventual Consistency** \</span></span>
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- <span data-ttu-id="ce35c-264">**Philip Brown. Strategie pro integraci ohraničených kontextů** </span><span class="sxs-lookup"><span data-stu-id="ce35c-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="ce35c-265">**Chris Richardson. Vývoj transakčních mikroslužeb pomocí agregací, zdroje událostí a CQRS – část 2** </span><span class="sxs-lookup"><span data-stu-id="ce35c-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="ce35c-266">**Chris Richardson. \ vzorového zdroje událostí**</span><span class="sxs-lookup"><span data-stu-id="ce35c-266">**Chris Richardson. Event Sourcing pattern** \</span></span>
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="ce35c-267">**Představujeme \ zdrojů událostí**</span><span class="sxs-lookup"><span data-stu-id="ce35c-267">**Introducing Event Sourcing** \</span></span>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="ce35c-268">**Databáze úložiště událostí**</span><span class="sxs-lookup"><span data-stu-id="ce35c-268">**Event Store database**.</span></span> <span data-ttu-id="ce35c-269">Oficiální lokalita.</span><span class="sxs-lookup"><span data-stu-id="ce35c-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="ce35c-270">**NeNommensený. Správa dat řízená událostmi pro mikroslužby** </span><span class="sxs-lookup"><span data-stu-id="ce35c-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="ce35c-271">**Limit věta** </span><span class="sxs-lookup"><span data-stu-id="ce35c-271">**The CAP Theorem** </span></span>\
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- <span data-ttu-id="ce35c-272">**Co je CAP věta?**</span><span class="sxs-lookup"><span data-stu-id="ce35c-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="ce35c-273">**Úvod do konzistence dat** </span><span class="sxs-lookup"><span data-stu-id="ce35c-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="ce35c-274">**Rick Saling. CAP věta: Proč "vše je jiné" s cloudem a Internet** </span><span class="sxs-lookup"><span data-stu-id="ce35c-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="ce35c-275">**Eric pivovar. LIMIT 12 let později: způsob, jakým se změnila pravidla** </span><span class="sxs-lookup"><span data-stu-id="ce35c-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="ce35c-276">**Azure Service Bus. Zprostředkované zasílání zpráv:  \ zjišťování duplicit**</span><span class="sxs-lookup"><span data-stu-id="ce35c-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  \</span></span>
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="ce35c-277">**Průvodce spolehlivostí** (dokumentace RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="ce35c-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> <span data-ttu-id="ce35c-278">[Předchozí](rabbitmq-event-bus-development-test-environment.md)
> [Další](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="ce35c-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
