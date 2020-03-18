---
title: Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pomocí funkce RabbitMQ implementujte zasílání zpráv sběrnice událostí pro události integrace pro vývojová nebo testovací prostředí.
ms.date: 10/02/2018
ms.openlocfilehash: ba1cea9384893955ae0743ac8d6a34c350224cd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711202"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="8650a-103">Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="8650a-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="8650a-104">Měli bychom začít tím, že pokud vytvoříte vlastní sběrnici událostí založenou na RabbitMQ spuštěné v kontejneru, jako aplikace eShopOnContainers, by měla být použita pouze pro vývoj a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="8650a-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="8650a-105">Neměli byste jej používat pro produkční prostředí, pokud jej nevytváříte jako součást servisní sběrnice připravené k výrobě.</span><span class="sxs-lookup"><span data-stu-id="8650a-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="8650a-106">Jednoduché vlastní sběrnice událostí může chybět mnoho důležitých funkcí připravených pro produkční prostředí, které má komerční servisní sběrnice.</span><span class="sxs-lookup"><span data-stu-id="8650a-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="8650a-107">Jedna z vlastní implementace sběrnice událostí v eShopOnContainers je v podstatě knihovna pomocí rozhraní API RabbitMQ (Existuje další implementace založená na Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="8650a-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="8650a-108">Implementace sběrnice událostí s RabbitMQ umožňuje mikroslužeb přihlásit k odběru událostí, publikovat události a přijímat události, jak je znázorněno na obrázku 6-21.</span><span class="sxs-lookup"><span data-stu-id="8650a-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Diagram znázorňující RabbitMQ mezi odesílatelem zprávy a příjemcem zprávy.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="8650a-110">**Obrázek 6-21.**</span><span class="sxs-lookup"><span data-stu-id="8650a-110">**Figure 6-21.**</span></span> <span data-ttu-id="8650a-111">RabbitMQ implementace sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="8650a-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="8650a-112">RabbitMQ funguje jako prostředník mezi vydavatelem zpráv a odběrateli, pro zpracování distribuce.</span><span class="sxs-lookup"><span data-stu-id="8650a-112">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="8650a-113">V kódu třída EventBusRabbitMQ implementuje obecné rozhraní IEventBus.</span><span class="sxs-lookup"><span data-stu-id="8650a-113">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="8650a-114">To je založeno na vkládání závislostí, takže můžete převést z této verze pro vývoj a testování na produkční verzi.</span><span class="sxs-lookup"><span data-stu-id="8650a-114">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="8650a-115">Implementace Sběrnice událostí RabbitMQ je standardní kód.</span><span class="sxs-lookup"><span data-stu-id="8650a-115">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="8650a-116">Musí zpracovat připojení k serveru RabbitMQ a poskytnout kód pro publikování události zprávy do front.</span><span class="sxs-lookup"><span data-stu-id="8650a-116">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="8650a-117">Musí také implementovat slovník kolekcí integračních obslužných rutin událostí pro každý typ události; tyto typy událostí může mít různé instance a různé odběry pro každý přijímač mikroslužby, jak je znázorněno na obrázku 6-21.</span><span class="sxs-lookup"><span data-stu-id="8650a-117">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="8650a-118">Implementace jednoduché metody publikování pomocí Funkce RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="8650a-118">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="8650a-119">Následující kód je ***zjednodušená*** verze implementace sběrnice událostí pro RabbitMQ, chcete-li předvést celý scénář.</span><span class="sxs-lookup"><span data-stu-id="8650a-119">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="8650a-120">Takhle se spojení moc nezvládá.</span><span class="sxs-lookup"><span data-stu-id="8650a-120">You don't really handle the connection this way.</span></span> <span data-ttu-id="8650a-121">Chcete-li zobrazit úplnou implementaci, podívejte se na skutečný kód v [úložišti dotnet-architecture/eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)</span><span class="sxs-lookup"><span data-stu-id="8650a-121">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

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

<span data-ttu-id="8650a-122">[Skutečný kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Metody Publish v aplikaci eShopOnContainers je vylepšen pomocí [polly zásady](https://github.com/App-vNext/Polly) opakování, která opakuje úkol určitý počet opakování v případě, že kontejner RabbitMQ není připraven.</span><span class="sxs-lookup"><span data-stu-id="8650a-122">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="8650a-123">Tato situace může nastat, když docker-compose spouští kontejnery; Například kontejner RabbitMQ může spustit pomaleji než ostatní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="8650a-123">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="8650a-124">Jak již bylo zmíněno dříve, existuje mnoho možných konfigurací v RabbitMQ, takže tento kód by měl být používán pouze pro vývoj a testování prostředí.</span><span class="sxs-lookup"><span data-stu-id="8650a-124">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="8650a-125">Implementace kódu předplatného pomocí rozhraní RabbitMQ API</span><span class="sxs-lookup"><span data-stu-id="8650a-125">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="8650a-126">Stejně jako u kódu publikování následující kód je zjednodušení části implementace sběrnice událostí pro RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="8650a-126">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="8650a-127">Opět platí, že obvykle nemusíte měnit, pokud jste ji zlepšit.</span><span class="sxs-lookup"><span data-stu-id="8650a-127">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="8650a-128">Každý typ události má související kanál získat události z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="8650a-128">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="8650a-129">Potom můžete mít tolik obslužné rutiny událostí na kanál a typ události podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="8650a-129">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="8650a-130">Subscribe Metoda přijímá iIntegrationEventHandler objekt, který je jako metoda zpětného volání v aktuální mikroslužby, plus jeho související IntegrationEvent objektu.</span><span class="sxs-lookup"><span data-stu-id="8650a-130">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="8650a-131">Kód pak přidá tuto obslužnou rutinu události do seznamu obslužných rutin událostí, které může mít každý typ události integrace pro mikroslužbu klienta.</span><span class="sxs-lookup"><span data-stu-id="8650a-131">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="8650a-132">Pokud kód klienta ještě nebyl přihlášen k odběru události, kód vytvoří kanál pro typ události, takže může přijímat události ve stylu push z RabbitMQ při publikování této události z jiné služby.</span><span class="sxs-lookup"><span data-stu-id="8650a-132">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="8650a-133">Jak bylo uvedeno výše, sběrnice událostí implementovaná v eShopOnContainers má pouze a vzdělávací účel, protože zpracovává pouze hlavní scénáře, takže není připravena k produkčnímu.</span><span class="sxs-lookup"><span data-stu-id="8650a-133">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="8650a-134">Pro produkční scénáře zkontrolujte další prostředky níže, specifické pro RabbitMQ a [implementace komunikace založené na událostech mezi mikroslužeb](./integration-event-based-microservice-communications.md#additional-resources) části.</span><span class="sxs-lookup"><span data-stu-id="8650a-134">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8650a-135">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8650a-135">Additional resources</span></span>

<span data-ttu-id="8650a-136">Řešení připravená k výrobě s podporou rabbitmq.</span><span class="sxs-lookup"><span data-stu-id="8650a-136">A production-ready solutions with support for RabbitMQ.</span></span>

- <span data-ttu-id="8650a-137">**EasyNetQ** - Open Source .NET API klient pro RabbitMQ </span><span class="sxs-lookup"><span data-stu-id="8650a-137">**EasyNetQ** - Open Source .NET API client for RabbitMQ </span></span>\
  <http://easynetq.com/>

- <span data-ttu-id="8650a-138">**Hromadná doprava** </span><span class="sxs-lookup"><span data-stu-id="8650a-138">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
><span data-ttu-id="8650a-139">[Předchozí](integration-event-based-microservice-communications.md)
>[další](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="8650a-139">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
