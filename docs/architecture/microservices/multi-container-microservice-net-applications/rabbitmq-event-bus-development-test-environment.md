---
title: Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Použijte RabbitMQ k implementaci zasílání zpráv služby Event Bus pro integrační události pro vývojová nebo testovací prostředí.
ms.date: 10/02/2018
ms.openlocfilehash: af02208bb9e680403a04377ccb740a8b15be29bc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296562"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implementace sběrnice událostí pomocí RabbitMQ pro vývojové nebo testovací prostředí

Měli bychom začít tím, že pokud vytvoříte vlastní sběrnici událostí založenou na RabbitMQ spuštěném v kontejneru, jako aplikace eShopOnContainers, měla by se používat jenom pro vývojová a testovací prostředí. Nepoužívejte ho pro produkční prostředí, pokud ho nevytváříte jako součást služby Service Bus připravené pro produkční prostředí. Jednoduchá vlastní sběrnice událostí může chybět mnoho důležitých funkcí připravených pro produkční prostředí, které má komerční služba Service Bus.

Jedna z vlastních implementací do sběrnice Event v eShopOnContainers je v podstatě knihovna využívající rozhraní RabbitMQ API (na základě Azure Service Bus existuje jiná implementace).

Implementace sběrnice událostí s RabbitMQ umožňuje mikroslužbám přihlašovat se k odběru událostí, publikovat události a přijímat události, jak je znázorněno na obrázku 6-21.

![RabbitMQ funguje jako prostředník mezi vydavatelem zprávy a předplatiteli za účelem zpracování distribuce.](./media/image22.png)

**Obrázek 6-21.** RabbitMQ implementace sběrnice událostí

V kódu třída EventBusRabbitMQ implementuje obecné rozhraní IEventBus. Tato možnost je založena na injektáže závislosti, takže se můžete z této verze pro vývoj a testování vyměnit na produkční verzi.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

RabbitMQ implementace ukázkové sběrnice událostí pro vývoj/testování je často používaný kód. Musí zpracovávat připojení k serveru RabbitMQ a poskytovat kód pro publikování události zprávy do front. Také musí implementovat slovník kolekcí obslužných rutin událostí integrace pro každý typ události; Tyto typy událostí mohou mít různé instance a různé odběry pro každou mikroslužbu přijímače, jak je znázorněno na obrázku 6-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implementace jednoduché metody publikování s RabbitMQ

Následující kód je ***zjednodušenou*** verzí implementace sběrnice událostí pro RabbitMQ, která prezentuje celý scénář. Toto připojení opravdu nezpracováváte tímto způsobem. Chcete-li zobrazit úplnou implementaci, přečtěte si skutečný kód v úložišti [dotnet-Architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) . 

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

[Skutečný kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) metody publikování v aplikaci eShopOnContainers je vylepšený pomocí zásady opakování [Polly](https://github.com/App-vNext/Polly) , která tento úkol opakuje po určitém počtu případů, kdy kontejner RabbitMQ není připravený. K tomu může dojít, když Docker – sestavování spouští kontejnery; například kontejner RabbitMQ může začínat pomaleji než ostatní kontejnery.

Jak bylo zmíněno dříve, existuje mnoho možných konfigurací v RabbitMQ, takže tento kód by se měl používat jenom pro vývojová a testovací prostředí.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implementace kódu předplatného s rozhraním API RabbitMQ

Stejně jako u kódu publikování je následující kód zjednodušením části implementace sběrnice událostí pro RabbitMQ. Znovu ji nemusíte měnit, pokud ji nevylepšujete.

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

Každý typ události má související kanál pro získání událostí z RabbitMQ. Pak můžete v případě potřeby mít tolik obslužných rutin událostí na kanál a typ události.

Metoda přihlášení k odběru akceptuje objekt IIntegrationEventHandler, který je jako metoda zpětného volání v aktuální mikroslužbě, a příslušný objekt IntegrationEvent. Kód pak přidá tuto obslužnou rutinu události do seznamu obslužných rutin událostí, které mohou mít každý typ události Integration pro každou klientskou mikroslužbu. Pokud kód klienta ještě není přihlášený k odběru události, kód vytvoří kanál pro typ události, aby mohl přijímat události ve stylu nabízených oznámení z RabbitMQ, pokud je tato událost publikována z jakékoli jiné služby.

>[!div class="step-by-step"]
>[Předchozí](integration-event-based-microservice-communications.md)Další
>[](subscribe-events.md)
