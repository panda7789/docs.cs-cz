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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí

Jsme měli nejprve informacemi o tom, že pokud vaše vlastní události Service bus podle RabbitMQ spuštění v kontejneru, stejně jako aplikaci eShopOnContainers aplikaci vytvoříte, ji by měla sloužit pouze pro vývojová a testovací prostředí. Nepoužívejte ho pro vaše produkční prostředí, pokud nevytváříte ho jako součást připravené pro produkční prostředí služby Service bus. Service bus jednoduchý vlastní události mohou chybět mnoho funkcí důležité produkční prostředí, které má komerční služby Service bus.

Jednou z vlastní implementace sběrnice událostí v aplikaci eShopOnContainers je v podstatě knihovny pomocí rozhraní API RabbitMQ (existuje jiné implementace založené na Azure Service Bus).

Implementace sběrnice událostí pomocí RabbitMQ umožňuje mikroslužeb přihlášení k odběru událostí, publikování událostí a příjem událostí, jak je znázorněno v obrázek 6 – 21.

![RabbitMQ funguje jako prostředník mezi zprávy vydavatele a odběratele, zpracování distribuce.](./media/image22.png)

**Obrázek 6 – 21.** RabbitMQ implementace sběrnice událostí

V kódu EventBusRabbitMQ třída implementuje obecné rozhraní IEventBus. Takže můžete zaměnit z této verze pro vývoj/testování pro produkční verze je založená na vkládání závislostí.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

RabbitMQ implementace sběrnice událostí ukázky pro vývoj/testování je často používaný kód. Má ke zpracování připojení k serveru RabbitMQ a zadejte kód pro publikování událostí zpráv do front. Je také k implementaci slovníku kolekcí integrace obslužné rutiny událostí pro každý typ události; Tyto typy událostí mohou mít různé vytváření instancí a různých předplatných u jednotlivých mikroslužeb příjemce, jak je znázorněno v obrázek 6 – 21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Metoda s RabbitMQ Implementing jednoduchý publikování.

Následující kód je ***zjednodušené*** verzi implementace sběrnice událostí pro RabbitMQ, aby ukazovala celý scénář. Můžete nezpracovávají skutečně připojení tímto způsobem. Úplnou implementaci, najdete v sekci skutečný kód [dotnet architektura/aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) úložiště. 

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

[Skutečný kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikování metodu v aplikaci eShopOnContainers aplikace je vylepšen pomocí [Polly](https://github.com/App-vNext/Polly) zásady, bude úloha s určitým počtem opakování se v případě, že je kontejner RabbitMQ opakování není připraven. Tato situace může nastat při docker-compose se spouští kontejnery; kontejner RabbitMQ například může začít pomaleji než jiné kontejnery.

Jak už bylo zmíněno dříve, existuje celá řada možných konfigurací v RabbitMQ, tak tento kód by měla sloužit pouze pro prostředí pro vývoj/testování.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementace kódu předplatného pomocí rozhraní API RabbitMQ

Stejně jako u kódu, publikovat, následující kód je zjednodušení součástí implementace sběrnice událostí pro RabbitMQ. Znovu můžete obvykle nemusíte ho měnit, pokud ho vylepšujeme.

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

Každý typ událost má související kanálu chcete získávat události z RabbitMQ. Potom může mít libovolný počet obslužných rutin událostí na typ kanálu a události podle potřeby.

Metoda přihlásit k odběru přijímá objekt IIntegrationEventHandler, což je jako metody zpětného volání v aktuálním mikroslužeb, a její související objekt IntegrationEvent. Tato obslužná rutina události kód pak přidá do seznamu obslužných rutin událostí, které může mít každý typ události integrace jednotlivých mikroslužbách klienta. Pokud klientský kód nebyl již přihlášení k odběru události, vytvoří kód kanálu pro typ události, takže může přijímat události ve stylu nabízených oznámení z RabbitMQ při publikování této události z jakékoli služby.

>[!div class="step-by-step"]
>[Předchozí](integration-event-based-microservice-communications.md)
>[další](subscribe-events.md)
