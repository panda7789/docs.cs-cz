---
title: Přihlášení k odběru událostí
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Přihlášení k odběru událostí
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 6cc5563f93915d1516e5a5f22a104012c1bb85d6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106574"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="7ef7f-103">Přihlášení k odběru událostí</span><span class="sxs-lookup"><span data-stu-id="7ef7f-103">Subscribing to events</span></span>

<span data-ttu-id="7ef7f-104">Prvním krokem pro používání sběrnici událostí je přihlášení k odběru mikroslužeb k událostem, které chtějí přijímat.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="7ef7f-105">Která se má provést v mikroslužeb příjemce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="7ef7f-106">Následující jednoduchý kód ukazuje, co každý příjemce mikroslužbu musí implementovat při spouštění služby (který je v `Startup` třída), přihlásí se k událostem, které se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="7ef7f-107">V takovém případě `basket.api` mikroslužbu musí přihlásit k odběru `ProductPriceChangedIntegrationEvent` a `OrderStartedIntegrationEvent` zprávy.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span> 

<span data-ttu-id="7ef7f-108">Například když se přihlásíte k odběru `ProductPriceChangedIntegrationEvent` událost, která umožňuje mikroslužbu košík vědět, všechny změny cena produktu a umožňuje ji upozornit uživatele o změnu, pokud tento produkt je v koši uživatele.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="7ef7f-109">Po spuštění tohoto kódu mikroslužbu odběratele se naslouchání prostřednictvím RabbitMQ kanálů.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="7ef7f-110">Pokud dorazí jakékoli zprávy typu ProductPriceChangedIntegrationEvent, vyvolá kód obslužné rutiny události, který je předán a zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="7ef7f-111">Publikování události prostřednictvím sběrnici událostí</span><span class="sxs-lookup"><span data-stu-id="7ef7f-111">Publishing events through the event bus</span></span>

<span data-ttu-id="7ef7f-112">Nakonec odesílatele zprávy (počátek mikroslužbu) publikuje události integrace s kódem podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="7ef7f-113">(Toto je zjednodušená příklad, který nevyžaduje nedělitelnost v úvahu). Podobný kód by implementovat vždy, když událost musí být rozšířena napříč více mikroslužeb, obvykle hned po potvrzení dat nebo transakcí z počátku mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="7ef7f-114">V konstruktoru řadiče, jako v následujícím kódu by nejprve vložit objekt implementace sběrnice událostí (podle RabbitMQ nebo v závislosti na služby service bus):</span><span class="sxs-lookup"><span data-stu-id="7ef7f-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="7ef7f-115">Můžete ho pak použít z vašeho řadiče metod, jako metodu UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="7ef7f-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="7ef7f-116">V takovém případě je tento kód jednoduché mikroslužbu CRUD totiž mikroslužbu počátek umístěna vpravo do kontroleru webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> 
 
<span data-ttu-id="7ef7f-117">V pokročilejší mikroslužeb, jako při použití CQRS přístupy, můžou se implementovat v `CommandHandler` třídy uvnitř `Handle()` metoda.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span> 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="7ef7f-118">Navrhování nedělitelnost a odolnost proti chybám při publikování ke sběrnici událostí</span><span class="sxs-lookup"><span data-stu-id="7ef7f-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="7ef7f-119">Při publikování události integrace pomocí distribuované zasílání zpráv systému jako vaše sběrnice událostí, budete mít problém atomicky aktualizace původní databáze a publikování události.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="7ef7f-120">Například z zjednodušené příkladu výše, kód potvrdí data do databáze při cena produktu se změní a pak publikuje zprávu ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="7ef7f-121">Na začátku může vypadat základní těchto dvou operací atomicky provést.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="7ef7f-122">Ale pokud používáte distribuované transakce zahrnující databáze a zprávy zprostředkovatel, stejně jako ve starších systémů jako [Microsoft služby Řízení front zpráv (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), to není doporučeno důvodů popsaného [Věta CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="7ef7f-123">V podstatě použijete mikroslužeb k sestavení systémy škálovatelné a vysoce dostupné.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="7ef7f-124">Ke zjednodušení poněkud, věta CAP uvádí nemůže vytvořit databázi (nebo mikroslužbu, který vlastní svůj model), se průběžně k dispozici, důrazně konzistentní *a* odolný vůči chybám pro libovolný oddíl.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-124">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="7ef7f-125">Musíte zvolit dva z těchto tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="7ef7f-126">V případě architektur se na základě mikroslužeb měli byste vybrat dostupnost a odolnost proti a měli omezit silnou konzistenci.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="7ef7f-127">Proto v většina moderních aplikací na základě mikroslužbu, obvykle nechcete používat distribuovaných transakcí v zasílání zpráv, stejně jako při implementaci [distribuované transakce](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) založené na distribuovanou transakci Windows Koordinátor (DTC) s [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="7ef7f-128">Přejděte zpět do počáteční problému a jeho příklad.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="7ef7f-129">Pokud po aktualizaci databáze dojde k chybě služby (v tomto případě pravým po řádku kódu pomocí \_kontextu. SaveChangesAsync()), ale před publikováním události integrace celého systému může být nekonzistentní.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="7ef7f-130">To může být kritické, v závislosti na konkrétní firemní operaci, kterou chcete pracovat s firmy.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="7ef7f-131">Jak je uvedeno výše v části architektura, může mít několik přístupů pro s řešením tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="7ef7f-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="7ef7f-132">Pomocí kompletní [Sourcing událostí vzor](https://msdn.microsoft.com/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-132">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="7ef7f-133">Pomocí [transakce protokolu dolování](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="7ef7f-134">Pomocí [pošta k odeslání vzoru](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="7ef7f-135">Toto je transakcí tabulku pro ukládání událostí integrace (rozšíření místní transakce).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="7ef7f-136">Pro tento scénář pomocí úplné vzoru událostí Sourcing (ES) je jedním z osvědčených postupů, není-li *nejlepší*.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="7ef7f-137">V mnoha scénářích aplikace, ale nemusí být schopen implementovat úplnou ES operace.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="7ef7f-138">ES znamená ukládání jenom události domény v transakční databáze, místo ukládání dat v aktuálním stavu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="7ef7f-139">Ukládání jenom události domény může mít velký výhod, jako je například s historii vašeho systému, které jsou k dispozici a schopnost určit stav systému v každém okamžiku v minulosti.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="7ef7f-140">Ale implementace úplnou ES vyžaduje, abyste rearchitect většinu systému a představuje mnoho složité kroky a požadavky.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="7ef7f-141">Například by chcete použít databázi vytvořené speciálně pro událost sourcing, například [událostí úložiště](https://geteventstore.com/), nebo databázi orientované dokumentu například Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="7ef7f-142">ES je skvělým přístup pro tento problém, ale není Nejsnazším řešením, pokud jste již obeznámeni s sourcing událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="7ef7f-143">Možnost použít transakčního protokolu dolování původně vypadá velmi transparentní.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="7ef7f-144">Pro tento postup, ale mikroslužbu má pro spojení protokolu RDBMS transakce, jako je například protokolu transakcí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="7ef7f-145">To je pravděpodobně není žádoucí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-145">This is probably not desirable.</span></span> <span data-ttu-id="7ef7f-146">Další nevýhodou je, že nízké úrovně aktualizací zaznamenávají v protokolu transakcí nemusí být na stejné úrovni jako vysoké úrovně integrace události.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="7ef7f-147">Pokud ano, proces zpětnou tyto operace transakce protokolu může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="7ef7f-148">Vyrovnáváním přístup je směs tabulku transakcí databáze a zjednodušená ES vzor.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="7ef7f-149">Můžete použít stav, jako je například "připravené k publikování událostí,", které se nastavují v původní událost v případě potvrzení události tabulky integrace.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="7ef7f-150">Potom se pokusíte publikovat událost ke sběrnici událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="7ef7f-151">Pokud akce publikování událostí úspěšné, spustit jinou transakcí v rámci služby původu a přesun stavu z "připravena k publikování události" do "událost již zveřejněny."</span><span class="sxs-lookup"><span data-stu-id="7ef7f-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="7ef7f-152">Pokud akce publikování událostí události sběrnici selže, data stále nebudou konzistentní v rámci mikroslužbu počátek – stále je označena jako "připravené k publikování události", a s ohledem na zbytek služby, případně bude konzistentní.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="7ef7f-153">Vždycky můžete mít kontrolu stavu transakce nebo události integrace úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="7ef7f-154">Pokud úloha nalezne událost ve stavu "připraveno k publikování události", můžete zkusit znovu publikovat tuto událost ke sběrnici událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="7ef7f-155">Všimněte si, že s tímto přístupem uchováváte jenom události integrace pro každý mikroslužbu původ a jenom události, které chcete sdělit další mikroslužeb nebo externími systémy.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="7ef7f-156">Naopak v rámci systému ES ukládat všechny události domény také.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="7ef7f-157">Proto tento vyrovnáváním přístup je zjednodušená ES systému.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="7ef7f-158">Je třeba seznam události integrace s jejich aktuální stav ("je připravena k publikování" a "publikovat").</span><span class="sxs-lookup"><span data-stu-id="7ef7f-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="7ef7f-159">Ale potřebujete implementovat tyto stavy pro události integrace.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="7ef7f-160">A v tento přístup, není nutné ukládat všechny domény data jako události v databázi transakcí, stejně jako v úplnou ES.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="7ef7f-161">Pokud už používáte relační databázi, můžete k uložení událostí integrace transakčních tabulku.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="7ef7f-162">K dosažení nedělitelnost ve vaší aplikaci, můžete použít ve dvou krocích založené na místní transakce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="7ef7f-163">V podstatě máte tabulku IntegrationEvent ve stejné databázi, kdy máte entity vaší domény.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="7ef7f-164">Tato tabulka funguje jako pojištění k dosažení nedělitelnost tak, aby zahrnete trvalé události integrace do stejné transakcí, které se potvrzují data vaší domény.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="7ef7f-165">Krok za krokem procesu přejde takto: aplikace začne transakce místní databáze.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-165">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="7ef7f-166">Pak aktualizuje stav entity vaší domény a vloží do tabulky události integrace událost.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-166">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="7ef7f-167">Nakonec potvrdí transakce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-167">Finally, it commits the transaction.</span></span> <span data-ttu-id="7ef7f-168">Zobrazí požadovanou nedělitelnost.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-168">You get the desired atomicity.</span></span>

<span data-ttu-id="7ef7f-169">Při implementaci kroky publikování události, máte tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="7ef7f-169">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="7ef7f-170">Publikování události integrace hned po potvrzení transakce a k označení události v tabulce jako publikovanému použijte jinou místní transakcí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-170">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="7ef7f-171">Pak pomocí tabulky stejně jako artefakt sledovat události integrace v případě problémů v vzdálené mikroslužeb a provádět vyrovnávací akce založené na události uložené integrace.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-171">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="7ef7f-172">Tabulku použijte jako typ fronty.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-172">Use the table as a kind of queue.</span></span> <span data-ttu-id="7ef7f-173">Vlákno samostatné aplikace nebo proces dotazuje tabulku událostí integrace, publikuje události ke sběrnici událostí a pak použije místní transakce označit události jako publikovaná.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-173">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="7ef7f-174">Obrázek 8 do 22 ukazuje architekturu pro první z těchto přístupů.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-174">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="7ef7f-175">**Obrázek 8 do 22**.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-175">**Figure 8-22**.</span></span> <span data-ttu-id="7ef7f-176">Nedělitelnost při publikování události ke sběrnici událostí</span><span class="sxs-lookup"><span data-stu-id="7ef7f-176">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="7ef7f-177">Přístup zobrazené v obrázek 8 do 22 chybí mikroslužbu další pracovního procesu, který má na starosti kontrole a potvrzení úspěch události publikované integrace.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-177">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="7ef7f-178">V případě selhání můžete tuto další kontrolu pracovní mikroslužbu číst události z tabulky a znovu publikovat.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-178">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="7ef7f-179">O druhý přístup: protokolu událostí tabulku použijte jako fronty a k publikování zpráv vždycky používat mikroslužbu pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-179">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="7ef7f-180">Proces v takovém případě se zobrazí jako je například v obrázek 8 – 23.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-180">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="7ef7f-181">Zobrazí se další mikroslužbu a tabulka je jediným zdrojem při publikování události.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-181">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="7ef7f-182">**Obrázek 8 – 23**.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-182">**Figure 8-23**.</span></span> <span data-ttu-id="7ef7f-183">Nedělitelnost při publikování události ke sběrnici událostí s mikroslužbu pracovního procesu</span><span class="sxs-lookup"><span data-stu-id="7ef7f-183">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="7ef7f-184">Pro jednoduchost používá ukázka eShopOnContainers prvním přístupem (bez dalších procesů nebo kontrolu mikroslužeb) plus sběrnici událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-184">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="7ef7f-185">Však není eShopOnContainers zpracování všech možných selhání případech.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-185">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="7ef7f-186">V reálné aplikaci nasadit do cloudu musíte použít skutečnost, že se vyskytnout potíže se nakonec a musí implementovat, zkontrolujte a opakujte odeslání logiky.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-186">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="7ef7f-187">Pokud máte tato tabulka jako jednoho zdroje událostí, pokud je publikování přes sběrnici událostí může být efektivnější než prvním přístupem pomocí tabulky jako fronty.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-187">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="7ef7f-188">Implementace nedělitelnost při publikování události integrace přes sběrnici událostí</span><span class="sxs-lookup"><span data-stu-id="7ef7f-188">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="7ef7f-189">Následující kód ukazuje, jak můžete vytvořit jeden transakce zahrnující víc objektů DbContext – jeden kontext související s původní data aktualizují a druhý kontext související s IntegrationEventLog tabulky.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-189">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="7ef7f-190">Všimněte si, že transakce v následujícím příkladu kódu nebude odolné, pokud připojení k databázi jakýkoli problém v době, kdy kód běží.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-190">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="7ef7f-191">K tomu dochází v cloudových systémech jako databázi SQL Azure, který může přesunutí databází mezi servery.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-191">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="7ef7f-192">Implementace odolné transakce napříč více kontexty, najdete v článku [implementace odolné připojení Entity Framework Core SQL](#implementing_resilient_EFCore_SQL_conns) dále v této příručce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-192">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="7ef7f-193">Pro přehlednost následující příklad ukazuje celého procesu v jeden úsek kódu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-193">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="7ef7f-194">Implementace eShopOnContainers ale ve skutečnosti je teď vyčleněný a rozdělení této logiky do více tříd, takže je snazší správa.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-194">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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
  if !(raiseProductPriceChangedEvent) 
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

<span data-ttu-id="7ef7f-195">Po vytvoření události integrace ProductPriceChangedIntegrationEvent transakce, která ukládá původní operace domény (aktualizace položka katalogu, kterou) také zahrnuje trvalost události v protokolu událostí tabulce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-195">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="7ef7f-196">Díky tomu jedné transakci a vždy bude moct zkontrolovat, zda byly odeslány zprávy o událostech.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-196">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="7ef7f-197">V tabulce v protokolu událostí se aktualizuje atomicky původní databáze, pomocí operace místní transakce proti stejné databáze.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-197">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="7ef7f-198">Pokud selžou všechny operace, je vyvolána výjimka, a transakce se vrátí zpět všechny dokončené operace, a proto zachování konzistence mezi domény operace a zprávy událostí odeslané.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-198">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="7ef7f-199">Přijímání zpráv z předplatných: obslužné rutiny událostí v mikroslužeb příjemce</span><span class="sxs-lookup"><span data-stu-id="7ef7f-199">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="7ef7f-200">Kromě logice odběru událostí potřebujete implementovat vnitřní kód pro obslužné rutiny událostí integrace (jako metody zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-200">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="7ef7f-201">Obslužné rutiny události je, kde můžete určit, kde přijme a zpracuje zprávy o událostech určitého typu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-201">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="7ef7f-202">Obslužné rutiny události nejprve obdrží instanci události z události sběrnice.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-202">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="7ef7f-203">Pak je možné vyhledat součásti, které mají být zpracovány vztahující se k této události integrace, šíření a zachování událost jako ke změně stavu v mikroslužbu příjemce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-203">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="7ef7f-204">Například pokud ProductPriceChanged událost pochází v katalogu mikroslužbu, ho je zpracována v košíku mikroslužbu a změní stav v košíku mikroslužbu tento příjemce i, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-204">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="7ef7f-205">Obslužné rutiny události musí ověřit, zda v některém z instancí košík existuje produktu.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-205">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="7ef7f-206">Aktualizuje také cena zboží pro každou položku řádku související nákupní košík.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-206">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="7ef7f-207">Nakonec vytvoří výstrahu, který se má zobrazit uživateli o změně ceny, jak ukazuje obrázek 8 – 24.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-207">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="7ef7f-208">**Obrázek 8 – 24**.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-208">**Figure 8-24**.</span></span> <span data-ttu-id="7ef7f-209">Zobrazení o změnu cena zboží v košíku, oznámené události integrace</span><span class="sxs-lookup"><span data-stu-id="7ef7f-209">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="7ef7f-210">Idempotenci v události zpráva aktualizace</span><span class="sxs-lookup"><span data-stu-id="7ef7f-210">Idempotency in update message events</span></span>

<span data-ttu-id="7ef7f-211">Důležitým aspektem události zpráva aktualizace je, že selhání v libovolném bodě komunikace by nemělo způsobit zpráva, která má být opakována.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-211">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="7ef7f-212">Úlohy na pozadí v opačném případě může pokusit publikovat událost, která už se publikovala, vytváření časování.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-212">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="7ef7f-213">Můžete potřebovat a ujistěte se, že aktualizace jsou idempotent nebo že poskytují dostatek informací k zajištění, že můžete zjistit duplicitní, ji zrušit a odeslání odpovědi zpět jenom jeden.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-213">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="7ef7f-214">Jak již bylo uvedeno dříve, idempotenci znamená, že operaci lze provést několikrát beze změny výsledek.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-214">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="7ef7f-215">V prostředí zasílání zpráv jako při komunikaci události, je událost idempotent, pokud ho může doručit víckrát beze změny výsledek pro příjemce mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-215">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="7ef7f-216">To může být způsobeno povaha samotné události nezbytné nebo z důvodu způsob, jakým systém zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-216">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="7ef7f-217">Zpráva idempotenci je důležité v jakékoli aplikaci, která používá zasílání zpráv, ne jenom v aplikacích, které implementovat vzor sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-217">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="7ef7f-218">Příkaz SQL, který vkládá data do tabulky, pouze pokud tato data již není v tabulce je například idempotent operace.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-218">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="7ef7f-219">Není důležité, kolik časy spuštění, které vložte příkaz jazyka SQL; Výsledkem bude stejná – tabulka bude obsahovat data.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-219">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="7ef7f-220">Idempotenci jako to může být také nezbytné při plánování práce s zprávy, pokud se zprávy může potenciálně odeslat a proto zpracování více než jednou.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-220">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="7ef7f-221">Například pokud logika opakovaných pokusů způsobí, že odesílatel přesně stejnou zprávu odeslat více než jednou, musíte zajistit, že se jedná o idempotent.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-221">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="7ef7f-222">Je možné návrhu idempotent zprávy.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-222">It is possible to design idempotent messages.</span></span> <span data-ttu-id="7ef7f-223">Například můžete vytvořit událost, která uvádí, že "nastavit cena produktu na \$25" místo "Přidat \$5 a cena produktu."</span><span class="sxs-lookup"><span data-stu-id="7ef7f-223">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="7ef7f-224">Vám může bezpečně první zprávu zpracovat libovolný počet časy a výsledkem bude stejná.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-224">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="7ef7f-225">Který není pro druhou zprávu na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-225">That is not true for the second message.</span></span> <span data-ttu-id="7ef7f-226">Ale i v prvním případě možná nebudete chtít zpracovat první událost, protože v systému může také odeslali novější událostí změna ceny a by přepsal nového ceníku.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-226">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="7ef7f-227">Dalším příkladem může být událost dokončit pořadí nebyl rozšířen do více odběrateli.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-227">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="7ef7f-228">Je důležité, aby informace o objednávce pouze jednou, aktualizovat v ostatních systémech i v případě, že existují duplicitní zpráva události pro jednu událost dokončit pořadí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-228">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="7ef7f-229">Je vhodné používat nějaký druh identity na událost, takže můžete vytvořit logiku, která vynucuje, že každá událost je jenom jednou zpracovaných za příjemce.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-229">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="7ef7f-230">Některé zpracování zprávy je ze své podstaty idempotent.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-230">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="7ef7f-231">Například pokud systém vygeneruje miniatur bitové kopie, je nemusí důležité, kolikrát je zpracovat zprávu o generovaného miniaturu; výsledek je, že jsou generovány miniatur a jsou stejné pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-231">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="7ef7f-232">Operace, jako například volání platební brány účtují platební karty na druhé straně, nemusí být idempotent vůbec.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-232">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="7ef7f-233">V těchto případech je potřeba zajistit, že zpracování zprávy několikrát má vliv očekáváte, že.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-233">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7ef7f-234">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="7ef7f-234">Additional resources</span></span>

-   <span data-ttu-id="7ef7f-235">**Aby byla dodržena idempotenci zpráva** (Podtitulek na této stránce) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-235">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="7ef7f-236">Odstranění duplicit dat zprávy o událostech integrace</span><span class="sxs-lookup"><span data-stu-id="7ef7f-236">Deduplicating integration event messages</span></span>

<span data-ttu-id="7ef7f-237">Zajistit odesílání a zpracuje jenom jednou za odběratele na různých úrovních zpráva události.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-237">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="7ef7f-238">Jedním ze způsobů je použít funkci odstranění duplicitních dat, které nabízí infrastrukturu zasílání zpráv, které používáte.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-238">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="7ef7f-239">Jiné je implementace vlastní logiky ve vaší cílové mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-239">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="7ef7f-240">Ověření na úrovni přenosu i na úrovni aplikace je nejlepším řešením.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-240">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="7ef7f-241">Odstranění duplicit dat události zpráv na úrovni obslužná rutina události</span><span class="sxs-lookup"><span data-stu-id="7ef7f-241">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="7ef7f-242">Jedním ze způsobů, abyste měli jistotu, že událost pouze jednou zpracovává libovolné receiver je implementace určité logiku při zpracování zprávy událostí v obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-242">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="7ef7f-243">Například, je metoda používaná v aplikaci eShopOnContainers, jak můžete vidět v [zdrojový kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) třídy OrdersController při přijetí příkazu CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-243">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="7ef7f-244">(V tomto případě používáme příkaz požadavku HTTP není na základě zpráv příkaz, ale logiku, budete muset udělat na základě zpráv příkaz idempotent je podobný.)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-244">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="7ef7f-245">Při použití RabbitMQ odstranění duplicit dat zprávy</span><span class="sxs-lookup"><span data-stu-id="7ef7f-245">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="7ef7f-246">Pokud dochází k občasným chybám sítě, zprávy mohou být duplicitní a příjemce zprávy musí být připravené pro zpracování těchto duplicitní zpráv.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-246">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="7ef7f-247">Pokud je to možné příjemci by měla řídit zprávy idempotent způsobem, který je lepší, než je explicitně zpracovávat s odstraněním duplicit.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-247">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="7ef7f-248">Podle požadavků [RabbitMQ dokumentace](https://www.rabbitmq.com/reliability.html#consumer), "Pokud zpráva je doručen k příjemce a pak zařazena (protože nebyla potvrzena, před ztrátě připojení k příjemce, například), pak RabbitMQ nastaví příznak redelivered na je po doručení znovu (jestli k příjemce stejný nebo jiný).</span><span class="sxs-lookup"><span data-stu-id="7ef7f-248">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="7ef7f-249">Pokud je nastavený příznak "redelivered", příjemce, vyžaduje v úvahu, protože zpráva může již byly zpracovány.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-249">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="7ef7f-250">Ale který není zaručena; zpráva může nikdy dosáhli příjemce po jeho levé zprostředkovatele zpráv, možná z důvodu problémů se sítí.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-250">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="7ef7f-251">Na druhé straně Pokud není nastavený příznak "redelivered", tak, aby zajistil, že zpráva nebyla odeslána více než jednou.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-251">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="7ef7f-252">Proto musí příjemce k odstranění duplicit zprávy nebo zpracování zpráv způsobem idempotent pouze v případě, že je "redelivered" nastavený příznak ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-252">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7ef7f-253">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="7ef7f-253">Additional resources</span></span>

-   <span data-ttu-id="7ef7f-254">**Forked eShopOnContainers pomocí NServiceBus (určitého softwaru)**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-254">**Forked eShopOnContainers using NServiceBus (Particular Software)**
[*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)</span></span>

-   <span data-ttu-id="7ef7f-255">**Událost řízené zasílání zpráv**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="7ef7f-256">**Jimmy Bogard. Refaktoring směrem odolnost: Vyhodnocení párování**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="7ef7f-257">**Publikování a odběru kanálu**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-257">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="7ef7f-258">**Komunikace mezi ohraničené kontexty**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="7ef7f-259">**Konzistence typu případné**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="7ef7f-260">**Hnědá Philip. Kontexty ohraničenou strategií pro integraci**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="7ef7f-261">**Jan Ryšánková. Vývoj transakční Mikroslužeb pomocí agregace, Sourcing událostí a CQRS - část 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="7ef7f-262">**Jan Ryšánková. Vzor Sourcing událostí**
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-262">**Chris Richardson. Event Sourcing pattern**
[*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="7ef7f-263">**Představení Sourcing událostí**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="7ef7f-264">**Databáze úložiště událostí**.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-264">**Event Store database**.</span></span> <span data-ttu-id="7ef7f-265">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="7ef7f-265">Official site.</span></span>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   <span data-ttu-id="7ef7f-266">**Patrik Nommensen. Správa dat založeného na událostech pro Mikroslužeb**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span><span class="sxs-lookup"><span data-stu-id="7ef7f-266">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="7ef7f-267">**Věta Zakončení**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-267">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="7ef7f-268">**Co je Zakončení věta?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-268">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="7ef7f-269">**Úvod do konzistence dat**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-269">**Data Consistency Primer**
[*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="7ef7f-270">**Rick Saling. Věta Zakončení: Proč "Vše, co je různé" s cloudu a Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-270">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="7ef7f-271">**Erica Brewer. Zakončení 12 letech později: jak změnily "Pravidla"**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-271">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="7ef7f-272">**Účastní transakcí (DTC) externí** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-272">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="7ef7f-273">**Azure Service Bus. Zprostředkované zasílání zpráv: Detekce duplicitních**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-273">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="7ef7f-274">**Průvodce spolehlivost** (RabbitMQ dokumentace) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-274">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="7ef7f-275">[Předchozí](rabbitmq-event-bus-development-test-environment.md)
[další](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="7ef7f-275">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
