---
title: Implementace sběrnici událostí s RabbitMQ pro vývojové nebo testovací prostředí
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace sběrnici událostí s RabbitMQ pro vývojové nebo testovací prostředí
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: e2b0f1a6152df5d323164fb2eca102fcb973667e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580234"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementace sběrnici událostí s RabbitMQ pro vývojové nebo testovací prostředí

Jsme měli začít informacemi o tom, že pokud vaše vlastní události sběrnice eShopOnContainers aplikace v závislosti na RabbitMQ spuštěné v kontejneru, vytvoříte, by být používána pouze pro vývoj a testovací prostředí. Nepoužívejte ho pro produkční prostředí, pokud vytváříte ho jako součást sběrnici služby produkční prostředí. Sběrnice jednoduché vlastní události mohou chybět řadu funkcí kritické produkční prostředí, které má komerční služby service bus.

Jedním z vlastní implementaci sběrnice událostí v eShopOnContainers je v podstatě knihovny pomocí rozhraní API RabbitMQ (je jiné implementace založené na Azure Service Bus). 

Implementace sběrnice událostí s RabbitMQ umožňuje mikroslužeb přihlásit k odběru událostí, publikování událostí a přijímat události, jak ukazuje obrázek 8-21.

![](./media/image22.png)

**Obrázek 8-21.** Implementace RabbitMQ sběrnici událostí

V kódu EventBusRabbitMQ třída implementuje obecné rozhraní IEventBus. To je založené na vkládání závislostí, takže můžete zaměnit z této verze pro vývoj/testování pro produkční verzi.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

Implementace RabbitMQ sběrnicí ukázka vývoje/testování událostí je často používaný kód. Má ke zpracování připojení k serveru RabbitMQ a zadejte kód pro publikování na událost zprávy do fronty. Je také nutné implementovat slovník kolekcí integrace obslužných rutin událostí pro každý typ události; Tyto typy událostí může mít různé vytváření instancí a různých předplatných pro každý příjemce mikroslužbu, jak ukazuje obrázek 8-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementace jednoduchou metodu s RabbitMQ publikování

Následující kód je součástí je implementace sběrnice zjednodušené událostí pro RabbitMQ, vylepšené v [kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) z eShopOnContainers. Obvykle není potřeba ho kódu, pokud se něco vylepšovat. Kód získá připojení a kanál, ke RabbitMQ, vytvoří zprávu a pak publikuje zprávu do fronty.

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

[Kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) publikování je metoda v aplikaci eShopOnContainers vylepšen pomocí [Polly](https://github.com/App-vNext/Polly) opakujte zásady, které úkol stanovený počet opakuje, v případě, že je RabbitMQ kontejner není připraven. Tato situace může nastat při docker compose zahajuje kontejnery; například kontejneru RabbitMQ může spustit pomaleji než jiných kontejnerů.

Jak už bylo zmíněno dříve, existuje celá řada možných konfigurací v RabbitMQ, takže tento kód by měl použít pouze pro prostředí pro vývoj/testování.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementace kód odběru s rozhraním API RabbitMQ

Jako kód publikovat, následující kód je zjednodušení součástí implementaci sběrnice událostí pro RabbitMQ. Znovu obvykle není nutné ho měnit, pokud jsou vylepšení ho.

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

Každý typ události má související kanálu pro získání událostí z RabbitMQ. Potom může mít libovolný počet obslužných rutin událostí podle typu kanál a událostí podle potřeby.

Přihlásit k odběru metoda přijímá objekt IIntegrationEventHandler, což je jako metody zpětného volání v aktuálním mikroslužbu, a její související objekt IntegrationEvent. Kód pak přidá do seznamu obslužných rutin událostí, které může mít každý typ události integrace za klienta mikroslužbu této obslužné rutiny události. Pokud kód klienta nebyl byl již naslouchá na události, kód vytvoří kanál pro typ události, aby mohl přijímat události ve stylu nabízené z RabbitMQ této události je při publikování z jiné služby.


>[!div class="step-by-step"]
[Předchozí] (integrace událostí – na základě mikroslužbu communications.md) [Další] (přihlášení k odběru events.md)
