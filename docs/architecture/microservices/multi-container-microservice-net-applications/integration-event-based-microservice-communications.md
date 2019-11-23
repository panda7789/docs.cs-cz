---
title: Implementace komunikace mezi mikroslužbami založené na událostech (události integrace)
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení integračních událostí pro implementaci komunikace založené na událostech mezi mikroslužbami.
ms.date: 10/02/2018
ms.openlocfilehash: 70566745dc084ba9016a850ad749fefb958e89ec
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737157"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementace komunikace mezi mikroslužbami založené na událostech (události integrace)

Jak bylo popsáno výše, při použití komunikace založené na událostech publikuje mikroslužba událost, když dojde k nějaké významné situaci, například při aktualizaci obchodní entity. Další mikroslužby se přihlásí k odběru těchto událostí. Když mikroslužba obdrží událost, může aktualizovat své vlastní obchodní entity, což může vést k publikování dalších událostí. Toto je podstata konečné koncepce s ohledem na konzistenci. Tento systém pro publikování a odběr se obvykle provádí pomocí implementace sběrnice událostí. Tato sběrnice se dá navrhovat jako rozhraní s rozhraním API, které se potřebuje k přihlášení k odběru událostí a k jejich zrušení a publikování událostí. Může také mít jednu nebo více implementací na základě jakékoli komunikace mezi procesy nebo zasílání zpráv, jako je například fronta zpráv nebo sběrnice podporující asynchronní komunikaci a model publikování/odběr.

Události můžete použít k implementaci obchodních transakcí, které obsahují více služeb, což vám umožní zajistit jejich konzistenci mezi těmito službami. Nakonec konzistentní transakce se skládá z řady distribuovaných akcí. V každé akci mikroslužba aktualizuje obchodní entitu a publikuje událost, která spustí další akci. Obrázek 6-18 níže ukazuje událost PriceUpdated publikovanou prostřednictvím služby a sběrnice událostí, takže se aktualizace ceny rozšíří na košík a další mikroslužby.

![Diagram komunikace založené na asynchronní události se sběrnicí událostí](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Obrázek 6-18**. Komunikace řízená událostmi na základě sběrnice událostí

Tato část popisuje, jak můžete implementovat tento typ komunikace s .NET pomocí obecného rozhraní pro sběrnici událostí, jak je znázorněno na obrázku 6-18. Existuje několik možných implementací, z nichž každá využívá jinou technologii nebo infrastrukturu, jako je RabbitMQ, Azure Service Bus nebo jakákoli jiná Open Source nebo komerční služba Service Bus třetí strany.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Používání služby zprostředkovatelé zpráv a služeb pro produkční systémy

Jak je uvedeno v části architektura, můžete si vybrat z více technologií zasílání zpráv pro implementaci abstraktní sběrnice událostí. Tyto technologie jsou ale na různých úrovních. Například RabbitMQ, přenos zprostředkovatele zasílání zpráv, je nižší než komerční produkty, jako je Azure Service Bus, NServiceBus, MassTransit nebo jasnější. Většina těchto produktů může pracovat na RabbitMQ nebo Azure Service Bus. Vaše volba produktu závisí na tom, kolik funkcí a kolik je potřeba pro vaši aplikaci.

V případě, že je pro vaše vývojové prostředí implementováno pouze vytváření konceptů služby Event Bus, jako v ukázce eShopOnContainers, může být k dispozici Jednoduchá implementace nad RabbitMQ spuštěným jako kontejner. Ale u důležitých a produkčních systémů, které vyžadují vysokou škálovatelnost, možná budete chtít vyhodnotit a použít Azure Service Bus.

Pokud vyžadujete, aby se vyhodnotily špičkové abstrakce a bohatší funkce jako [Sagas](https://docs.particular.net/nservicebus/sagas/) pro dlouhotrvající procesy, které usnadňují distribuovaný vývoj, budou se vyhodnocovat i další komerční a open-source sběrnice, jako je NServiceBus, MassTransit a jasnější. V tomto případě by se abstrakce a rozhraní API používaly obvykle přímo z těch, které poskytují tyto sběrnice služby na vysoké úrovni, a ne vlastní abstrakce (jako jsou [jednoduché abstrakce sběrnice událostí poskytované na eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). V takovém případě můžete prohledat [rozvětvené eShopOnContainers pomocí NServiceBus](https://go.particular.net/eShopOnContainers) (další odvozená ukázka implementovaná konkrétním softwarem).

Samozřejmě byste mohli kdykoli vytvořit vlastní funkce služby Service Bus, jako je RabbitMQ a Docker, ale práci potřebnou k rezásobě kol může být pro vlastní podnikovou aplikaci moc nákladné.

Pro opakování iterace: ukázkové abstrakce a implementace sběrnice událostí v ukázce eShopOnContainers jsou určené k použití jenom jako důkaz konceptu. Jakmile se rozhodnete, že chcete mít asynchronní a událostní komunikaci, jak je vysvětleno v aktuální části, měli byste zvolit produkt Service Bus, který nejlépe vyhovuje vašim potřebám v produkčním prostředí.

## <a name="integration-events"></a>Události integrace

Integrační události se používají k zavedení stavu domény v synchronizaci napříč několika mikroslužbami nebo externími systémy. To se provádí publikováním událostí integrace mimo mikroslužby. Když je událost publikovaná u více mikroslužeb přijímače (do tolika mikroslužeb, které se přihlásily k odběru události Integration), příslušná obslužná rutina události v každé mikroslužbě přijímače tuto událost zpracuje.

Událost integrace je v podstatě Třída datového hospodářství, jak je znázorněno v následujícím příkladu:

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

Integrační události lze definovat na úrovni aplikace každé mikroslužby, takže jsou odděleny od ostatních mikroslužeb způsobem, který je srovnatelný s tím, jak jsou definovány ViewModels na serveru a klientovi. Nedoporučuje se sdílet společnou knihovnu integračních událostí napříč více mikroslužbami. To by bylo propojení těchto mikroslužeb s jednou knihovnou dat definice události. Nechcete to dělat ze stejných důvodů, proč nechcete sdílet společný doménový model napříč více mikroslužbami: mikroslužby musí být zcela autonomní.

Existuje jen několik druhů knihoven, které byste měli sdílet mezi mikroslužbami. Jednou z nich jsou knihovny finálních aplikačních bloků, jako je například [klientské rozhraní API sběrnice událostí](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jako v eShopOnContainers. Další jsou knihovny, které představují nástroje, které by mohly být také sdíleny jako komponenty NuGet, například serializátory JSON.

## <a name="the-event-bus"></a>Sběrnice událostí

Sběrnice událostí umožňuje komunikaci ve stylu pro publikování a odběr mezi mikroslužbami, aniž by bylo nutné, aby byly komponenty explicitně vzájemně jiné, jak je znázorněno na obrázku 6-19.

![Diagram znázorňující základní vzor pro publikování a odběr.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Obrázek 6-19**. Základy publikování a odběru pomocí sběrnice událostí

Výše uvedený diagram znázorňuje, že mikroslužba A publikuje do sběrnice událostí, která distribuuje odběr mikroslužeb B a C, aniž by museli znát předplatitele. Sběrnice událostí souvisí se vzorem pozorovatele a vzorem publikování a odběru.

### <a name="observer-pattern"></a>Vzor pozorovatele

Ve [vzorku pozorovatele](https://en.wikipedia.org/wiki/Observer_pattern)váš primární objekt (označovaný jako pozorovatelný) oznamuje jiné zúčastněné objekty (označované jako pozorovatelé) s relevantními informacemi (událostmi).

### <a name="publishsubscribe-pubsub-pattern"></a>Vzor pro publikování/odběr (pub/sub)

Účel [vzoru pro publikování a odběr](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) je stejný jako vzor pozorovatele: Chcete-li, aby byly určité události vykonaty, je třeba informovat další služby. Existují však důležité rozdíly mezi dvěma pozorovateli a podvzorci Pub/sub. V rámci modelu pozorovatele se všesměrové vysílání provádí přímo z pozorovatele pozorovatelům, takže "ví". Ale při použití vzoru Pub/sub je k dispozici třetí součást, která se nazývá zprostředkovatel nebo zprostředkovatel zpráv nebo sběrnice událostí, která je známá vydavatelem i předplatitelem. Proto při použití modelu Pub/sub se Vydavatel a předplatitelé přesně oddělí na zmíněnou sběrnici událostí nebo zprostředkovatele zpráv.

### <a name="the-middleman-or-event-bus"></a>Prostředníka nebo sběrnice událostí

Jak můžete dosáhnout anonymity mezi vydavatelem a předplatitelem? Snadným způsobem je, že se postará o veškerou komunikaci. Sběrnice událostí je taková střední.

Sběrnice událostí se typicky skládá ze dvou částí:

- Abstrakce nebo rozhraní.

- Jedna nebo více implementací.

Na obrázku 6-19 se můžete podívat, jak, od aplikačního bodu, není sběrnice událostí prázdná, než kanál pro publikování a následné kanály. Způsob implementace této asynchronní komunikace se může lišit. Může mít více implementací, aby bylo možné mezi nimi přepínat v závislosti na požadavcích prostředí (například na produkčních a vývojových prostředích).

Na obrázku 6-20 se můžete podívat na abstrakci sběrnice událostí s více implementacemi na základě technologie zasílání zpráv infrastruktury, jako je RabbitMQ, Azure Service Bus nebo jiný Zprostředkovatel událostí a zpráv.

![Diagram znázorňující přidání vrstvy abstrakce pro sběrnici událostí](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Obrázek 6-20.** Více implementací sběrnice událostí

Je vhodné, aby byla sběrnice událostí definovaná prostřednictvím rozhraní, aby se mohla implementovat s několika technologiemi, jako je RabbitMQ Azure Service Bus nebo jiné. A jak již bylo uvedeno dříve, použití vlastních abstrakcí (rozhraní sběrnice událostí) je dobré pouze v případě, že vaše abstrakce vyžadují základní funkce sběrnice událostí. Pokud potřebujete funkce služby Service Bus, měli byste použít rozhraní API a abstrakce poskytované upřednostňovanou komerční službou Service Bus místo vašich vlastních abstrakcí.

### <a name="defining-an-event-bus-interface"></a>Definování rozhraní sběrnice událostí

Pojďme začít s některým implementačním kódem pro rozhraní sběrnice událostí a možnými implementacemi pro účely průzkumu. Rozhraní by mělo být obecné a jednoduché, jako v následujícím rozhraní.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

Metoda `Publish` je jednoduchá. Sběrnice událostí bude všesměrově zasílat událost integrace do jakékoli mikroslužby nebo i do externí aplikace, která se přihlásí k odběru této události. Tuto metodu používá mikroslužba, která publikuje událost.

Metody `Subscribe` (můžete mít několik implementací závislých na argumentech), které jsou používány mikroslužbami, které chtějí přijímat události. Tato metoda má dva argumenty. První je událost integrace k přihlášení k odběru (`IntegrationEvent`). Druhý argument je obslužná rutina události Integration (nebo metoda zpětného volání) s názvem `IIntegrationEventHandler<T>`, která se má provést, když mikroslužba příjemce obdrží tuto zprávu události integrace.

> [!div class="step-by-step"]
> [Předchozí](database-server-container.md)
> [Další](rabbitmq-event-bus-development-test-environment.md)
