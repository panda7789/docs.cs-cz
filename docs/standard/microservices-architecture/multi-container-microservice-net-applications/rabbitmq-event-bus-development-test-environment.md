---
title: Implementace sběrnici událostí s RabbitMQ pro vývojové nebo testovací prostředí
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace sběrnici událostí s RabbitMQ pro vývojové nebo testovací prostředí
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: fb9bf51d947774cddd7b42ade0f05abc8fb3d7e9
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104750"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="0d362-103">Implementace sběrnici událostí s RabbitMQ pro vývojové nebo testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="0d362-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="0d362-104">Jsme měli začít informacemi o tom, že pokud vaše vlastní události sběrnice eShopOnContainers aplikace v závislosti na RabbitMQ spuštěné v kontejneru, vytvoříte, by být používána pouze pro vývoj a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="0d362-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="0d362-105">Nepoužívejte ho pro produkční prostředí, pokud vytváříte ho jako součást sběrnici služby produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="0d362-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="0d362-106">Sběrnice jednoduché vlastní události mohou chybět řadu funkcí kritické produkční prostředí, které má komerční služby service bus.</span><span class="sxs-lookup"><span data-stu-id="0d362-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="0d362-107">Jedním z vlastní implementaci sběrnice událostí v eShopOnContainers je v podstatě knihovny pomocí rozhraní API RabbitMQ (je jiné implementace založené na Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="0d362-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span> 

<span data-ttu-id="0d362-108">Implementace sběrnice událostí s RabbitMQ umožňuje mikroslužeb přihlásit k odběru událostí, publikování událostí a přijímat události, jak ukazuje obrázek 8-21.</span><span class="sxs-lookup"><span data-stu-id="0d362-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="0d362-109">**Obrázek 8-21.**</span><span class="sxs-lookup"><span data-stu-id="0d362-109">**Figure 8-21.**</span></span> <span data-ttu-id="0d362-110">Implementace RabbitMQ sběrnici událostí</span><span class="sxs-lookup"><span data-stu-id="0d362-110">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="0d362-111">V kódu EventBusRabbitMQ třída implementuje obecné rozhraní IEventBus.</span><span class="sxs-lookup"><span data-stu-id="0d362-111">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="0d362-112">To je založené na vkládání závislostí, takže můžete zaměnit z této verze pro vývoj/testování pro produkční verzi.</span><span class="sxs-lookup"><span data-stu-id="0d362-112">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="0d362-113">Implementace RabbitMQ sběrnicí ukázka vývoje/testování událostí je často používaný kód.</span><span class="sxs-lookup"><span data-stu-id="0d362-113">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="0d362-114">Má ke zpracování připojení k serveru RabbitMQ a zadejte kód pro publikování na událost zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="0d362-114">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="0d362-115">Je také nutné implementovat slovník kolekcí integrace obslužných rutin událostí pro každý typ události; Tyto typy událostí může mít různé vytváření instancí a různých předplatných pro každý příjemce mikroslužbu, jak ukazuje obrázek 8-21.</span><span class="sxs-lookup"><span data-stu-id="0d362-115">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="0d362-116">Implementace jednoduchou metodu s RabbitMQ publikování</span><span class="sxs-lookup"><span data-stu-id="0d362-116">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="0d362-117">Následující kód je součástí je implementace sběrnice zjednodušené událostí pro RabbitMQ, vylepšené v [kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0d362-117">The following code is part is a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="0d362-118">Obvykle není potřeba ho kódu, pokud se něco vylepšovat.</span><span class="sxs-lookup"><span data-stu-id="0d362-118">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="0d362-119">Kód získá připojení a kanál, ke RabbitMQ, vytvoří zprávu a pak publikuje zprávu do fronty.</span><span class="sxs-lookup"><span data-stu-id="0d362-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="0d362-120">[Kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikování je metoda v aplikaci eShopOnContainers vylepšen pomocí [Polly](https://github.com/App-vNext/Polly) opakujte zásady, které úkol stanovený počet opakuje, v případě, že je RabbitMQ kontejner není připraven.</span><span class="sxs-lookup"><span data-stu-id="0d362-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="0d362-121">Tato situace může nastat při docker compose zahajuje kontejnery; například kontejneru RabbitMQ může spustit pomaleji než jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="0d362-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="0d362-122">Jak už bylo zmíněno dříve, existuje celá řada možných konfigurací v RabbitMQ, takže tento kód by měl použít pouze pro prostředí pro vývoj/testování.</span><span class="sxs-lookup"><span data-stu-id="0d362-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="0d362-123">Implementace kód odběru s rozhraním API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="0d362-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="0d362-124">Jako kód publikovat, následující kód je zjednodušení součástí implementaci sběrnice událostí pro RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="0d362-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="0d362-125">Znovu obvykle není nutné ho měnit, pokud jsou vylepšení ho.</span><span class="sxs-lookup"><span data-stu-id="0d362-125">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="0d362-126">Každý typ události má související kanálu pro získání událostí z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="0d362-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="0d362-127">Potom může mít libovolný počet obslužných rutin událostí podle typu kanál a událostí podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="0d362-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="0d362-128">Přihlásit k odběru metoda přijímá objekt IIntegrationEventHandler, což je jako metody zpětného volání v aktuálním mikroslužbu, a její související objekt IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="0d362-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="0d362-129">Kód pak přidá do seznamu obslužných rutin událostí, které může mít každý typ události integrace za klienta mikroslužbu této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0d362-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="0d362-130">Pokud kód klienta nebyl byl již naslouchá na události, kód vytvoří kanál pro typ události, aby mohl přijímat události ve stylu nabízené z RabbitMQ této události je při publikování z jiné služby.</span><span class="sxs-lookup"><span data-stu-id="0d362-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0d362-131">[Předchozí](integration-event-based-microservice-communications.md)
[další](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="0d362-131">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
