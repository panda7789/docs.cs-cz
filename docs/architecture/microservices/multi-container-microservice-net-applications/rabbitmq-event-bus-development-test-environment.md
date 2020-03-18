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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí

Měli bychom začít tím, že pokud vytvoříte vlastní sběrnici událostí založenou na RabbitMQ spuštěné v kontejneru, jako aplikace eShopOnContainers, by měla být použita pouze pro vývoj a testovací prostředí. Neměli byste jej používat pro produkční prostředí, pokud jej nevytváříte jako součást servisní sběrnice připravené k výrobě. Jednoduché vlastní sběrnice událostí může chybět mnoho důležitých funkcí připravených pro produkční prostředí, které má komerční servisní sběrnice.

Jedna z vlastní implementace sběrnice událostí v eShopOnContainers je v podstatě knihovna pomocí rozhraní API RabbitMQ (Existuje další implementace založená na Azure Service Bus).

Implementace sběrnice událostí s RabbitMQ umožňuje mikroslužeb přihlásit k odběru událostí, publikovat události a přijímat události, jak je znázorněno na obrázku 6-21.

![Diagram znázorňující RabbitMQ mezi odesílatelem zprávy a příjemcem zprávy.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Obrázek 6-21.** RabbitMQ implementace sběrnice událostí

RabbitMQ funguje jako prostředník mezi vydavatelem zpráv a odběrateli, pro zpracování distribuce. V kódu třída EventBusRabbitMQ implementuje obecné rozhraní IEventBus. To je založeno na vkládání závislostí, takže můžete převést z této verze pro vývoj a testování na produkční verzi.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Implementace Sběrnice událostí RabbitMQ je standardní kód. Musí zpracovat připojení k serveru RabbitMQ a poskytnout kód pro publikování události zprávy do front. Musí také implementovat slovník kolekcí integračních obslužných rutin událostí pro každý typ události; tyto typy událostí může mít různé instance a různé odběry pro každý přijímač mikroslužby, jak je znázorněno na obrázku 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementace jednoduché metody publikování pomocí Funkce RabbitMQ

Následující kód je ***zjednodušená*** verze implementace sběrnice událostí pro RabbitMQ, chcete-li předvést celý scénář. Takhle se spojení moc nezvládá. Chcete-li zobrazit úplnou implementaci, podívejte se na skutečný kód v [úložišti dotnet-architecture/eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)

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

[Skutečný kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) Metody Publish v aplikaci eShopOnContainers je vylepšen pomocí [polly zásady](https://github.com/App-vNext/Polly) opakování, která opakuje úkol určitý počet opakování v případě, že kontejner RabbitMQ není připraven. Tato situace může nastat, když docker-compose spouští kontejnery; Například kontejner RabbitMQ může spustit pomaleji než ostatní kontejnery.

Jak již bylo zmíněno dříve, existuje mnoho možných konfigurací v RabbitMQ, takže tento kód by měl být používán pouze pro vývoj a testování prostředí.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementace kódu předplatného pomocí rozhraní RabbitMQ API

Stejně jako u kódu publikování následující kód je zjednodušení části implementace sběrnice událostí pro RabbitMQ. Opět platí, že obvykle nemusíte měnit, pokud jste ji zlepšit.

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

Každý typ události má související kanál získat události z RabbitMQ. Potom můžete mít tolik obslužné rutiny událostí na kanál a typ události podle potřeby.

Subscribe Metoda přijímá iIntegrationEventHandler objekt, který je jako metoda zpětného volání v aktuální mikroslužby, plus jeho související IntegrationEvent objektu. Kód pak přidá tuto obslužnou rutinu události do seznamu obslužných rutin událostí, které může mít každý typ události integrace pro mikroslužbu klienta. Pokud kód klienta ještě nebyl přihlášen k odběru události, kód vytvoří kanál pro typ události, takže může přijímat události ve stylu push z RabbitMQ při publikování této události z jiné služby.

Jak bylo uvedeno výše, sběrnice událostí implementovaná v eShopOnContainers má pouze a vzdělávací účel, protože zpracovává pouze hlavní scénáře, takže není připravena k produkčnímu.

Pro produkční scénáře zkontrolujte další prostředky níže, specifické pro RabbitMQ a [implementace komunikace založené na událostech mezi mikroslužeb](./integration-event-based-microservice-communications.md#additional-resources) části.

## <a name="additional-resources"></a>Další zdroje

Řešení připravená k výrobě s podporou rabbitmq.

- **EasyNetQ** - Open Source .NET API klient pro RabbitMQ \
  <http://easynetq.com/>

- **Hromadná doprava** \
  <https://masstransit-project.com/>
  
>[!div class="step-by-step"]
>[Předchozí](integration-event-based-microservice-communications.md)
>[další](subscribe-events.md)
