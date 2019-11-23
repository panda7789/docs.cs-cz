---
title: Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Použijte RabbitMQ k implementaci zasílání zpráv služby Event Bus pro integrační události pro vývojová nebo testovací prostředí.
ms.date: 10/02/2018
ms.openlocfilehash: 211348caec3c101435fcdd99bd96fd8e17a6456b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739506"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="a2ecc-103">Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="a2ecc-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="a2ecc-104">Měli bychom začít tím, že pokud vytvoříte vlastní sběrnici událostí založenou na RabbitMQ spuštěném v kontejneru, jako aplikace eShopOnContainers, měla by se používat jenom pro vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="a2ecc-105">Nepoužívejte ho pro produkční prostředí, pokud ho nevytváříte jako součást služby Service Bus připravené pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="a2ecc-106">Jednoduchá vlastní sběrnice událostí může chybět mnoho důležitých funkcí připravených pro produkční prostředí, které má komerční služba Service Bus.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="a2ecc-107">Jedna z vlastních implementací do sběrnice Event v eShopOnContainers je v podstatě knihovna využívající rozhraní RabbitMQ API (na základě Azure Service Bus existuje jiná implementace).</span><span class="sxs-lookup"><span data-stu-id="a2ecc-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="a2ecc-108">Implementace sběrnice událostí s RabbitMQ umožňuje mikroslužbám přihlašovat se k odběru událostí, publikovat události a přijímat události, jak je znázorněno na obrázku 6-21.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Diagram znázorňující RabbitMQ mezi odesílatelem zprávy a příjemcem zprávy](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="a2ecc-110">**Obrázek 6-21.**</span><span class="sxs-lookup"><span data-stu-id="a2ecc-110">**Figure 6-21.**</span></span> <span data-ttu-id="a2ecc-111">RabbitMQ implementace sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="a2ecc-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="a2ecc-112">RabbitMQ funguje jako prostředník mezi vydavatelem zprávy a předplatiteli za účelem zpracování distribuce.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-112">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="a2ecc-113">V kódu třída EventBusRabbitMQ implementuje obecné rozhraní IEventBus.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-113">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="a2ecc-114">Tato možnost je založena na injektáže závislosti, takže se můžete z této verze pro vývoj a testování vyměnit na produkční verzi.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-114">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="a2ecc-115">RabbitMQ implementace ukázkové sběrnice událostí pro vývoj/testování je často používaný kód.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-115">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="a2ecc-116">Musí zpracovávat připojení k serveru RabbitMQ a poskytovat kód pro publikování události zprávy do front.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-116">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="a2ecc-117">Také musí implementovat slovník kolekcí obslužných rutin událostí integrace pro každý typ události; Tyto typy událostí mohou mít různé instance a různé odběry pro každou mikroslužbu přijímače, jak je znázorněno na obrázku 6-21.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-117">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="a2ecc-118">Implementace jednoduché metody publikování s RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="a2ecc-118">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="a2ecc-119">Následující kód je ***zjednodušenou*** verzí implementace sběrnice událostí pro RabbitMQ, která prezentuje celý scénář.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-119">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="a2ecc-120">Toto připojení opravdu nezpracováváte tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-120">You don't really handle the connection this way.</span></span> <span data-ttu-id="a2ecc-121">Chcete-li zobrazit úplnou implementaci, přečtěte si skutečný kód v úložišti [dotnet-Architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) .</span><span class="sxs-lookup"><span data-stu-id="a2ecc-121">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

<span data-ttu-id="a2ecc-122">[Skutečný kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) metody publikování v aplikaci eShopOnContainers je vylepšený pomocí zásady opakování [Polly](https://github.com/App-vNext/Polly) , která tento úkol opakuje po určitém počtu případů, kdy kontejner RabbitMQ není připravený.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-122">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="a2ecc-123">K tomu může dojít, když Docker – sestavování spouští kontejnery; například kontejner RabbitMQ může začínat pomaleji než ostatní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-123">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="a2ecc-124">Jak bylo zmíněno dříve, existuje mnoho možných konfigurací v RabbitMQ, takže tento kód by se měl používat jenom pro vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-124">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="a2ecc-125">Implementace kódu předplatného s rozhraním API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="a2ecc-125">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="a2ecc-126">Stejně jako u kódu publikování je následující kód zjednodušením části implementace sběrnice událostí pro RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-126">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="a2ecc-127">Znovu ji nemusíte měnit, pokud ji nevylepšujete.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-127">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

<span data-ttu-id="a2ecc-128">Každý typ události má související kanál pro získání událostí z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-128">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="a2ecc-129">Pak můžete v případě potřeby mít tolik obslužných rutin událostí na kanál a typ události.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-129">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="a2ecc-130">Metoda přihlášení k odběru akceptuje objekt IIntegrationEventHandler, který je jako metoda zpětného volání v aktuální mikroslužbě, a příslušný objekt IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-130">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="a2ecc-131">Kód pak přidá tuto obslužnou rutinu události do seznamu obslužných rutin událostí, které mohou mít každý typ události Integration pro každou klientskou mikroslužbu.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-131">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="a2ecc-132">Pokud kód klienta ještě není přihlášený k odběru události, kód vytvoří kanál pro typ události, aby mohl přijímat události ve stylu nabízených oznámení z RabbitMQ, pokud je tato událost publikována z jakékoli jiné služby.</span><span class="sxs-lookup"><span data-stu-id="a2ecc-132">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a2ecc-133">[Předchozí](integration-event-based-microservice-communications.md)
>[Další](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="a2ecc-133">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
