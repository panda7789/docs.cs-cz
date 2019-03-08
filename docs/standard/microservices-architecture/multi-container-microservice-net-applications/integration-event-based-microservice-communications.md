---
title: Implementace komunikace mezi mikroslužbami (události integrace) na základě událostí
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Principy integrace událostí k implementaci založený na událostech komunikace mezi mikroslužbami.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: b451d896186ffb650e495c10786106c37ab16131
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676015"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementace komunikace mezi mikroslužbami (události integrace) na základě událostí

Jak je popsáno výše, při použití komunikace na základě událostí, mikroslužby publikuje událost v případě určité významné události, jako je například při aktualizaci obchodní entitě. Další mikroslužeb přihlášení k odběru těchto událostí. Událost přijetí mikroslužba je aktualizovat své vlastní obchodní entity, které by mohly vést k další události publikování. Je podstata konceptu konečné konzistence. Tento systém publikování/odběr se obvykle provádí pomocí implementace sběrnice událostí. Service bus události lze navrhnout jako rozhraní s rozhraním API, třeba pro předplatné a odhlášení odběru událostí a k publikování událostí. Také může mít jeden nebo více implementací podle jakékoli mezi procesy nebo zasílání zpráv komunikace, jako jsou fronty zasílání zpráv nebo Azure service bus, která podporuje asynchronní komunikace a modelu publikování a přihlášení k odběru.

Můžete použít události k implementaci obchodních transakcí, které zahrnují více služeb, poskytující konečnou konzistenci mezi těmito službami. Konečnou konzistenci transakcí se skládá z řady distribuovaných akcí. Na každou akci mikroslužeb aktualizuje obchodní entity a publikuje událost, která aktivuje další akci.

![Katalog mikroslužeb, pomocí řízené událostmi komunikace prostřednictvím Service bus událostí k dosažení konečnou konzistenci s nákupní košík a další mikroslužeb.](./media/image19.png)

**Obrázek 6 – 18**. Komunikace založená na událostech podle sběrnice událostí

Tato část popisuje, jak můžete implementovat tento typ komunikace s .NET pomocí rozhraní Service bus Obecná událost, jak je znázorněno v obrázek 6 – 18. Existuje několik potenciálních implementací, každý pomocí různých technologií nebo infrastruktury, jako je například RabbitMQ, Azure Service Bus nebo jakékoli jiné třetích stran open source nebo komerční služby Service bus.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Pomocí sběrnice zpráv zprostředkovatele a služby pro produkční systémy.

Jak je uvedeno v části architektury, můžete vybrat z různými technologiemi zasílání zpráv pro implementace sběrnice vaše abstraktní událost. Ale tyto technologie jsou na různých úrovních. Například RabbitMQ, zasílání zpráv Service broker přenos, je na nižší úrovni než komerční produkty, jako je Azure Service Bus, NServiceBus, MassTransit nebo Brighter. Většina těchto produktů může pracovat nad RabbitMQ nebo Azure Service Bus. Podle vašeho výběru produktů závisí na tom, kolik funkce a kolik out-of-the-box škálovatelnost potřebujete pro vaši aplikaci.

Pro implementaci pouze události Service bus testování konceptu jako vývojové prostředí, stejně jako v ukázkové aplikaci eShopOnContainers mohou být jednoduché implementace nad RabbitMQ běžícího jako kontejner dostatečné. Ale pro nepostradatelné a produkční systémy, které potřebují vysokou škálovatelnost, můžete k vyhodnocení a používat Azure Service Bus.

Pokud potřebujete vyšší úrovni abstrakce a bohatší funkce, jako jsou [Ság](https://docs.particular.net/nservicebus/sagas/) pro dlouho běžící procesy, které usnadňují distribuovaných vývojových jednodušší a další obchodní a open source služby sběrnice jako NServiceBus MassTransit, a Jasnější stojí za vaše rozhodnutí vyzkoušet. V takovém případě abstrakce a rozhraní API pro použití by obvykle neměl přímo ta poskytuje tyto základní služby sběrnice místo vlastní abstrakce (podobně jako [abstrakce jednoduché události Service bus k dispozici v aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). K tomuto účelu můžete prozkoumat [Rozvětvená aplikaci eShopOnContainers pomocí NServiceBus](https://go.particular.net/eShopOnContainers) (další vzorek odvozené implementované určitého softwaru)

Samozřejmě může vždy sestavovat vlastní funkce služby Service bus na nižší úrovni technologie jako RabbitMQ a Docker, ale práce potřebné k "nesnažil" může být moc nákladný pro vlastní podnikové aplikace.

Zdůrazňujeme: Ukázka událostí Service bus abstrakce a implementace, které vystavíte v ukázkové aplikaci eShopOnContainers jsou určena pro použití pouze jako testování konceptu. Až si ověříte, že chcete mít komunikace asynchronní a založený na událostech, jak je popsáno v části aktuální, měli byste zvolit produkt služby Service bus, která nejlépe vyhovuje vašim potřebám pro produkční prostředí.

## <a name="integration-events"></a>Integrace událostí

Integrace události se používají pro přenesení stavu domény synchronizované napříč několika mikroslužbami nebo externí systémy. To se provádí publikování události integrace mimo mikroslužbách. Při publikování události do několika mikroslužeb příjemce (na tolik mikroslužby jako přihlášeni k této události integrace), zpracuje obslužná rutina odpovídající události v jednotlivých mikroslužeb příjemce událost.

Integrace událost je v podstatě třída dat podniku, jako v následujícím příkladu:

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

Události integrace lze definovat na úrovni aplikace jednotlivých mikroslužeb, takže jsou oddělené od dalších mikroslužeb, způsobem, který je srovnatelná s hodnotou jak modely ViewModels jsou definované na serveru a klienta. Co se nedoporučuje sdílí společné knihovny integrace událostí mezi různými mikroslužbami; To provedete by být párování těchto mikroslužeb s knihovnou jednu událost definice data. Nechcete provést ze stejného důvodu, že nechcete sdílet společný model domény napříč různými mikroslužbami: musí být zcela autonomní mikroslužeb.

Existují jenom pár typy knihoven, které by měly sdílet napříč mikroslužeb. Jeden je knihovny, které jsou bloky konečné aplikace, jako je třeba [sběrnice událostí klientského rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jako v aplikaci eShopOnContainers. Další knihovny, které tvoří nástroje, které by se dají sdílet taky jako NuGet komponenty, jako je JSON serializátory je.

## <a name="the-event-bus"></a>Události Service bus

Sběrnice událostí umožňuje publikování/přihlášení odběru – vizuální styl komunikace mezi mikroslužbami, aniž by komponent je potřeba explicitně vědět, jak je znázorněno v obrázek 6 – 19.

![Základní pub/sub vzoru, Mikroslužby A publikuje do sběrnice událostí, který distribuuje předplacení mikroslužeb B a C, aniž by museli znát odběratelů vydavatele.](./media/image20.png)

**Obrázek 6-19**. Publikování/odběr základy s sběrnice událostí

Service bus události týkající se vzor pozorovatel a publikovat – vzorec odběru.

### <a name="observer-pattern"></a>Vzor pozorovatel

V [vzor pozorovatel](https://en.wikipedia.org/wiki/Observer_pattern), váš primární objekt (označuje se jako pozorovat) upozorní další zúčastněné objekty (označuje se jako pozorovatelů) s příslušnými informacemi (události).

### <a name="publishsubscribe-pubsub-pattern"></a>Vzor publikování/přihlášení k odběru (publikování a odběr)

Účelem [vzor publikování/přihlášení k odběru](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) je stejný jako vzor pozorovatel: Chcete upozornit jiné služby, probíhají určité události. Existuje ale podstatným rozdílem mezi pozorovatel a Pub/Sub vzory. Ve vzoru pozorovatel vysílání je provádět přímo pozorovat k pozorovatelé, tak jejich "know" mezi sebou. Ale při použití modelu Pub/Sub, je třetí součást, která volá zprostředkovatele nebo zprávy Service broker nebo událostí Service bus, která se označuje vydavatele a odběratele. Proto při použití modelu Pub/Sub vydavatele a odběratele se přesně odděleném díky uvedené události Service bus nebo zprávy zprostředkovatele.

### <a name="the-middleman-or-event-bus"></a>Prostředník nebo událostí Service bus

Jak dosáhnete anonymity mezi vydavatele a odběratele Snadný způsob, je nechat prostředník postará o veškerá komunikace. Sběrnice událostí je jeden takový prostředník.

Sběrnice událostí se obvykle skládá ze dvou částí:

- Abstraktní nebo rozhraní.

- Jeden nebo více implementací.

Obrázek 6-19 uvidíte, jak z aplikace hlediska, sběrnice událostí není nic jiného než Pub/Sub kanálu. Způsob implementace této asynchronní komunikace se může lišit. Může mít několik implementací tak, aby můžete přepínat mezi nimi, v závislosti na požadavcích prostředí (například produkčního prostředí a vývojová prostředí).

Obrázek 6 – 20 uvidíte abstrakce sběrnice událostí s více implementací na základě infrastruktury zasílání zpráv technologie, jako je RabbitMQ, Azure Service Bus nebo jiného zprostředkovatele událostí/zpráv.

![Je dobré si co sběrnice událostí definován pomocí rozhraní, takže je možné implementovat pomocí několika technologie, jako jsou RabbitMQ Azure Service bus nebo jiných.](./media/image21.png)

**Obrázek 6 – 20.** Více implementací sběrnice událostí

Ale a jak bylo zmíněno dříve pomocí vlastní abstrakce (rozhraní události Service bus) je vhodné, pouze pokud je potřeba základní událost funkce Service bus podporuje vaše abstrakce. Pokud potřebujete širší funkce služby Service bus, je vhodné použít rozhraní API a abstrakce poskytované vaší preferované komerční služby Service bus místo vlastních odběrů.

### <a name="defining-an-event-bus-interface"></a>Definování rozhraní událostí Service bus

Začněme možná implementace pro účely zkoumání a implementace kódu pro rozhraní události Service bus. Rozhraní musí být obecný a jasné, stejně jako v následujícím rozhraní.

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

`Publish` Metoda je jednoduchá. Sběrnice událostí bude vysílat události integrace do něho předaný všechny mikroslužby nebo dokonce i externí aplikaci, na tuto událost odběru. Tato metoda používá mikroslužeb, která publikuje události.

`Subscribe` Metod (může mít několik implementací v závislosti na argumenty) jsou používány mikroslužeb, která chcete přijímat události. Tato metoda má dva argumenty. První možností je integrace událostí přihlášení k odběru (`IntegrationEvent`). Druhý argument je integrace událostí obslužnou rutinu (nebo metoda zpětného volání), s názvem `IIntegrationEventHandler<T>`, který se spustí při získá mikroslužeb příjemce této zprávy integrace událostí.

> [!div class="step-by-step"]
> [Předchozí](database-server-container.md)
> [další](rabbitmq-event-bus-development-test-environment.md)
