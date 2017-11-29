---
title: "Implementace založené na události komunikace mezi mikroslužeb (integrace událostí)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace založené na události komunikace mezi mikroslužeb (integrace událostí)"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e438607ab3549d63b89bef6af64c6723a4cac950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementace založené na události komunikace mezi mikroslužeb (integrace událostí)

Jak je popsáno výše, pokud použijete komunikaci na základě událostí, mikroslužbu publikuje událost v případě významné se stane něco, například při aktualizaci obchodní entity. Další mikroslužeb přihlásit k odběru těchto událostí. Událost přijetí mikroslužbu ho aktualizovat vlastní obchodní entity, které může vést k další události je publikován. Tento systém publikování a přihlášení k odběru se obvykle provádí pomocí implementace sběrnici událostí. Sběrnici událostí můžete navrhnout jako rozhraní s rozhraním API potřebné k přihlášení k odběru a odhlášení odběru událostí a publikování událostí. Může také obsahovat jeden nebo více implementace založené na všechny meziprocesovou nebo zasílání zpráv komunikaci, jako je zasílání zpráv fronty nebo služby service bus, která podporuje asynchronní komunikaci a model publikování a přihlášení k odběru.

Můžete použít události implementovat obchodní transakce, které jsou rozmístěny v několika služeb, která umožňuje konzistence typu případné mezi tyto služby. Nakonec byl konzistentní transakce se skládá z řady distribuované akce. Na každou akci mikroslužbu aktualizace obchodní entity a publikuje události, která spouští další akce.

![](./media/image19.PNG)

**Obrázek 8 až 18**. Událostmi řízené komunikace na základě na sběrnici událostí

Tato část popisuje, jak tento typ komunikace s .NET můžete implementovat pomocí rozhraní bus je obecný událostí, jak ukazuje obrázek 8 až 18. Existuje více potenciální implementace, každý pomocí různých technologií nebo infrastruktury, například RabbitMQ, Azure Service Bus, nebo jakékoli jiné třetích stran s otevřeným zdrojem nebo komerční služby service bus.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Pomocí sběrnice zpráv zprostředkovatelé a služby pro produkční systémy.

Jak je uvedeno v části architektura, můžete z více technologie zasílání zpráv pro implementace sběrnice vaší abstraktní událostí. Ale tyto technologie jsou na různých úrovních. Například RabbitMQ, zasílání zpráv zprostředkovatele přenos, je na nižší úrovni než jako Azure Service Bus, NServiceBus, MassTransit nebo Brighter komerční produkty. Většina těchto produktů můžete pracovat nad RabbitMQ nebo Azure Service Bus. Výběr produktu závisí na tom, kolik funkce a kolik out-of-the-box škálovatelnost potřebujete pro vaši aplikaci.

Pro implementaci právě události sběrnice ověření – koncepce pro vývojové prostředí, jako v ukázce eShopOnContainers jednoduché implementace nad RabbitMQ spuštěna jako kontejner může být dost. Ale pro kritické a produkční systémy, které potřebují vysokou škálovatelnost, můžete vyhodnotit a použít Azure Service Fabric. Pokud požadujete vysoké úrovni abstrakce a bohatší funkce, jako jsou [sagas](https://docs.particular.net/nservicebus/sagas/) pro dlouho běžící procesy, které distribuované vývoj sběrnicích jednodušší, jiné komerční a open source služby jako NServiceBus, MassTransit, a Jasnější jsou vhodné vyhodnocení. Samozřejmě je vždy sestavení vlastní funkce služby sběrnice na nižší úrovni technologie, jako je RabbitMQ a Docker, ale práce potřebné k reinvent kolečka může být příliš nákladná pro vlastní podnikovou aplikaci.

Chcete-li znovu opakují: Ukázka události sběrnice abstrakce a implementace showcased v ukázce eShopOnContainers mají za cíl má být použit pouze jako testování konceptu. Jakmile jste se rozhodli, že budete chtít mít asynchronní a událostmi řízené komunikaci, jak je popsáno v části aktuální, měli byste vybrat produkt service bus, který nejlépe vyhovuje vašim potřebám.

## <a name="integration-events"></a>Události integrace

Integrace události se používají pro převedení stav domény synchronizované mezi více mikroslužeb nebo externími systémy. K tomu je potřeba publikování události integrace mimo mikroslužby. Pokud je událost publikovaná více mikroslužeb příjemce (pro tolik mikroslužeb jako předplacené události integrace), obslužné rutiny odpovídající události v každý příjemce mikroslužbu zpracovává událost.

Integrace událost je v podstatě třída uložení dat, jako v následujícím příkladu:

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

Event – třída integrace může být jednoduchý; například může obsahovat identifikátor GUID pro jeho ID.

Události integrace lze definovat na úrovni aplikace z každé mikroslužbu, jsou odpojené od jiných mikroslužeb způsobem, který je porovnatelný z hlediska na tom, jak jsou definovány ViewModels v serverem a klientem. Co se nedoporučuje sdílí společné knihovny události integrace mezi více mikroslužeb; učinit by být spojovacích těchto mikroslužeb s knihovnou jedna událost definice data. Nechcete kvůli tomu, ze stejného důvodu, že nechcete sdílet mezi více mikroslužeb běžné modelu domény: musí být zcela autonomní mikroslužeb.

Existují jenom pár druhy knihoven, které by měly sdílet mezi mikroslužeb. Jedna je knihovny, které jsou bloky konečné aplikace, jako je třeba [událostí sběrnice klientského rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jako v eShopOnContainers. Další je knihovny, které tvoří nástroje, které může také sdílen jako součásti NuGet, jako je serializátorů JSON.

## <a name="the-event-bus"></a>Sběrnici událostí

Sběrnici událostí umožňuje publikování/přihlášení k odběru style komunikace mezi mikroslužeb bez nutnosti součásti, které explicitně mějte na paměti, jak ukazuje obrázek 8-19.

![](./media/image20.png)

**Obrázek 8-19**. Publikování a přihlášení k odběru základy s sběrnici událostí

Sběrnici událost souvisí s vzor pozorovatel a publikování-přihlášení k odběru vzor.

### <a name="observer-pattern"></a>Vzor pozorovatel

V [vzor pozorovatel](https://en.wikipedia.org/wiki/Observer_pattern), primární objektu (označované jako lze zobrazit) upozorní jiné zúčastněným objekty (označované jako pozorovatelů) s příslušnými informacemi (událostí).

### <a name="publish-subscribe-pubsub-pattern"></a>Vzor publikování a odběru (Pub nebo Sub) 

Účelem [Pub nebo Sub vzor](https://msdn.microsoft.com/en-us/library/ff649664.aspx) je stejný jako vzor pozorovatel: chcete zasílat oznámení jiných služeb, při provádění určité události. Ale je důležité sémantického rozdíl mezi vzorce pozorovatele a Pub nebo Sub. Ve vzoru Pub nebo Sub zaměřuje se na zprávy všesměrového vysílání. Naopak v vzoru pozorovatel lze zobrazit nebude vědět, kdo události se chystáte, stačí, kteří neprošli out. Jinými slovy lze zobrazit (vydavatel) nebude vědět, kdo jsou pozorovatelů (odběratele).

### <a name="the-middleman-or-event-bus"></a>Sběrnici prostředník nebo událostí 

Jak můžete dosáhnout anonymity mezi vydavatele a odběratele? Snadný způsob je umožnit prostředník, postará o veškerá komunikace. Sběrnici událostí je jeden takový prostředník.

Sběrnici událostí se obvykle skládá ze dvou částí:

-   Abstrakce nebo rozhraní.

-   Jeden nebo více implementace.

Obrázek 8-19 uvidíte, jak z aplikace hlediska, sběrnici událostí není nic jiného než kanál Pub nebo Sub. Způsob, jak implementovat asynchronní komunikaci se může lišit. Může mít několik implementace tak, aby můžete zaměnit mezi nimi, v závislosti na požadavcích prostředí (například produkční a vývojových prostředích).

Obrázek 8-20 uvidíte abstrakci sběrnici událostí s více implementací na základě infrastruktury zasílání zpráv technologie, jako je RabbitMQ, Azure Service Bus nebo jiné služby sběrnicích NServiceBus, MassTransit, atd.

![](./media/image21.png)

**Obrázek 8 - 20.** Více implementace sběrnici událostí

Jako zvýrazněná dříve, použití abstrakce (rozhraní sběrnice událostí) je možné pouze v případě, že potřebujete základní událostí sběrnice funkcí podporovaných vaší abstrakce. Pokud potřebujete bohatší funkce service bus, měli byste použít pravděpodobně rozhraní API poskytované upřednostňované sběrnice místo vlastní abstrakce.

### <a name="defining-an-event-bus-interface"></a>Definování rozhraní sběrnice událostí

Začněme s možné implementace pro účely zkoumání a určitý kód implementace událostí rozhraní sběrnice. Rozhraní by měl být obecné a jasné, stejně jako následující rozhraní.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);
    void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T: IntegrationEvent;

    void Unsubscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent;
}
```

Metoda publikování je jednoduchá. Sběrnici událostí bude vysílání události integrace do ní předán do jakékoli mikroslužbu odběru na tuto událost. Tato metoda se používá ve mikroslužbu, který je publikování události.

Metoda přihlásit k odběru používá mikroslužeb, který chcete přijímat události. Tato metoda má dvě části. První je integrace události k odběru (IntegrationEvent). Druhá část je obslužné rutiny události integrace (nebo metoda zpětného volání), která se má volat (IIntegrationEventHandler&lt;T&gt;) při mikroslužbu přijme této integrace událostí zprávu.


>[!div class="step-by-step"]
[Předchozí] (database-server-container.md) [Další] (rabbitmq-event-bus-development-test-environment.md)
