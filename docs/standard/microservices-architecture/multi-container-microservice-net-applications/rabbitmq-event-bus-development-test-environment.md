---
title: Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace zasílání zpráv, integrace událostí za vývojová nebo testovací prostředí sběrnice událostí pomocí RabbitMQ.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 2bcd3491c58884653cd6c119753696019151bfed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864261"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="49adb-103">Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="49adb-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="49adb-104">Jsme měli nejprve informacemi o tom, že pokud vaše vlastní události Service bus podle RabbitMQ spuštění v kontejneru, stejně jako aplikaci eShopOnContainers aplikaci vytvoříte, ji by měla sloužit pouze pro vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="49adb-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="49adb-105">Nepoužívejte ho pro vaše produkční prostředí, pokud nevytváříte ho jako součást připravené pro produkční prostředí služby Service bus.</span><span class="sxs-lookup"><span data-stu-id="49adb-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="49adb-106">Service bus jednoduchý vlastní události mohou chybět mnoho funkcí důležité produkční prostředí, které má komerční služby Service bus.</span><span class="sxs-lookup"><span data-stu-id="49adb-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="49adb-107">Jednou z vlastní implementace sběrnice událostí v aplikaci eShopOnContainers je v podstatě knihovny pomocí rozhraní API RabbitMQ (existuje jiné implementace založené na Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="49adb-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span>

<span data-ttu-id="49adb-108">Implementace sběrnice událostí pomocí RabbitMQ umožňuje mikroslužeb přihlášení k odběru událostí, publikování událostí a příjem událostí, jak je znázorněno v obrázek 6 – 21.</span><span class="sxs-lookup"><span data-stu-id="49adb-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![RabbitMQ funguje jako prostředník mezi zprávy vydavatele a odběratele, zpracování distribuce.](./media/image22.png)

<span data-ttu-id="49adb-110">**Obrázek 6 – 21.**</span><span class="sxs-lookup"><span data-stu-id="49adb-110">**Figure 6-21.**</span></span> <span data-ttu-id="49adb-111">RabbitMQ implementace sběrnice událostí</span><span class="sxs-lookup"><span data-stu-id="49adb-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="49adb-112">V kódu EventBusRabbitMQ třída implementuje obecné rozhraní IEventBus.</span><span class="sxs-lookup"><span data-stu-id="49adb-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="49adb-113">Takže můžete zaměnit z této verze pro vývoj/testování pro produkční verze je založená na vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="49adb-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="49adb-114">RabbitMQ implementace sběrnice událostí ukázky pro vývoj/testování je často používaný kód.</span><span class="sxs-lookup"><span data-stu-id="49adb-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="49adb-115">Má ke zpracování připojení k serveru RabbitMQ a zadejte kód pro publikování událostí zpráv do front.</span><span class="sxs-lookup"><span data-stu-id="49adb-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="49adb-116">Je také k implementaci slovníku kolekcí integrace obslužné rutiny událostí pro každý typ události; Tyto typy událostí mohou mít různé vytváření instancí a různých předplatných u jednotlivých mikroslužeb příjemce, jak je znázorněno v obrázek 6 – 21.</span><span class="sxs-lookup"><span data-stu-id="49adb-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="49adb-117">Metoda s RabbitMQ Implementing jednoduchý publikování.</span><span class="sxs-lookup"><span data-stu-id="49adb-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="49adb-118">Následující kód je ***zjednodušené*** verzi implementace sběrnice událostí pro RabbitMQ, aby ukazovala celý scénář.</span><span class="sxs-lookup"><span data-stu-id="49adb-118">The following code is a ***simplified*** version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="49adb-119">Můžete nezpracovávají skutečně připojení tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="49adb-119">You don't really handle the connection this way.</span></span> <span data-ttu-id="49adb-120">Úplnou implementaci, najdete v sekci skutečný kód [dotnet architektura/aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) úložiště.</span><span class="sxs-lookup"><span data-stu-id="49adb-120">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span> 

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

<span data-ttu-id="49adb-121">[Skutečný kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikování metodu v aplikaci eShopOnContainers aplikace je vylepšen pomocí [Polly](https://github.com/App-vNext/Polly) zásady, bude úloha s určitým počtem opakování se v případě, že je kontejner RabbitMQ opakování není připraven.</span><span class="sxs-lookup"><span data-stu-id="49adb-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="49adb-122">Tato situace může nastat při docker-compose se spouští kontejnery; kontejner RabbitMQ například může začít pomaleji než jiné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="49adb-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="49adb-123">Jak už bylo zmíněno dříve, existuje celá řada možných konfigurací v RabbitMQ, tak tento kód by měla sloužit pouze pro prostředí pro vývoj/testování.</span><span class="sxs-lookup"><span data-stu-id="49adb-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="49adb-124">Implementace kódu předplatného pomocí rozhraní API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="49adb-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="49adb-125">Stejně jako u kódu, publikovat, následující kód je zjednodušení součástí implementace sběrnice událostí pro RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="49adb-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="49adb-126">Znovu můžete obvykle nemusíte ho měnit, pokud ho vylepšujeme.</span><span class="sxs-lookup"><span data-stu-id="49adb-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="49adb-127">Každý typ událost má související kanálu chcete získávat události z RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="49adb-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="49adb-128">Potom může mít libovolný počet obslužných rutin událostí na typ kanálu a události podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="49adb-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="49adb-129">Metoda přihlásit k odběru přijímá objekt IIntegrationEventHandler, což je jako metody zpětného volání v aktuálním mikroslužeb, a její související objekt IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="49adb-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="49adb-130">Tato obslužná rutina události kód pak přidá do seznamu obslužných rutin událostí, které může mít každý typ události integrace jednotlivých mikroslužbách klienta.</span><span class="sxs-lookup"><span data-stu-id="49adb-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="49adb-131">Pokud klientský kód nebyl již přihlášení k odběru události, vytvoří kód kanálu pro typ události, takže může přijímat události ve stylu nabízených oznámení z RabbitMQ při publikování této události z jakékoli služby.</span><span class="sxs-lookup"><span data-stu-id="49adb-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49adb-132">[Předchozí](integration-event-based-microservice-communications.md)
>[další](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="49adb-132">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
