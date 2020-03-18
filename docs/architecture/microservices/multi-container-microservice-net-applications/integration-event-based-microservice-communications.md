---
title: Implementace komunikace mezi mikroslužbami založené na událostech (události integrace)
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Porozumět událostem integrace k implementaci komunikace založené na událostech mezi mikroslužbami.
ms.date: 10/02/2018
ms.openlocfilehash: 6d4e324a05def91935a82df41c971a75cb75c3f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712400"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implementace komunikace mezi mikroslužbami založené na událostech (události integrace)

Jak je popsáno dříve, při použití komunikace založené na událostech, mikroslužba publikuje událost, když se stane něco pozoruhodného, například když aktualizuje obchodní entitu. Ostatní mikroslužby přihlásit k odběru těchto událostí. Když mikroslužba obdrží událost, může aktualizovat své vlastní obchodní entity, což může vést k publikování dalších událostí. To je podstata konečného konceptu konzistence. Tento systém publikování/odběru se obvykle provádí pomocí implementace sběrnice událostí. Sběrnice událostí může být navržena jako rozhraní s rozhraním API potřebným k přihlášení k odběru a odhlášení z odběru událostí a publikování událostí. Může mít také jednu nebo více implementací založených na jakékoli komunikaci mezi procesy nebo zasílání zpráv, jako je například fronta zpráv nebo sběrnice služby, která podporuje asynchronní komunikaci a model publikování/odběru.

Události můžete použít k implementaci obchodních transakcí, které pokrývají více služeb, což vám dává konečnou konzistenci mezi těmito službami. Nakonec konzistentní transakce se skládá z řady distribuovaných akcí. Při každé akci mikroslužby aktualizuje obchodní entity a publikuje událost, která aktivuje další akci. Obrázek 6-18 níže, ukazuje PriceUpdated událost publikovaná prostřednictvím a sběrnice událostí, takže aktualizace ceny je rozšířena do košíku a dalších mikroslužeb.

![Diagram asynchronní komunikace řízené událostmi se sběrnicí událostí.](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Obrázek 6-18**. Komunikace řízená událostmi na základě sběrnice událostí

Tato část popisuje, jak můžete implementovat tento typ komunikace s rozhraním .NET pomocí obecného rozhraní sběrnice událostí, jak je znázorněno na obrázku 6-18. Existuje několik potenciálních implementací, z nichž každá používá jinou technologii nebo infrastrukturu, jako je RabbitMQ, Azure Service Bus nebo jakákoli jiná open source nebo komerční sběrnice.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Použití zprostředkovatelů zpráv a sběrnic služeb pro výrobní systémy

Jak je uvedeno v části architektura, můžete si vybrat z více technologií zasílání zpráv pro implementaci sběrnice abstraktní události. Ale tyto technologie jsou na různých úrovních. Například RabbitMQ, přenos zprostředkovatele zasílání zpráv, je na nižší úrovni než komerční produkty, jako je Azure Service Bus, NServiceBus, MassTransit nebo Brighter. Většina těchto produktů může fungovat na webu RabbitMQ nebo Azure Service Bus. Výběr produktu závisí na tom, kolik funkcí a kolik out-of-the-box škálovatelnost, kterou potřebujete pro vaši aplikaci.

Pro implementaci pouze sběrnice událostí proof-of-concept pro vývojové prostředí, jako v eShopOnContainers vzorku, jednoduchá implementace nad RabbitMQ běží jako kontejner může stačit. Ale pro kritické a produkční systémy, které vyžadují vysokou škálovatelnost, můžete chtít vyhodnotit a používat Azure Service Bus.

Pokud požadujete abstrakce na vysoké úrovni a bohatší funkce, jako [je Sagas](https://docs.particular.net/nservicebus/sagas/) pro dlouhotrvající procesy, které usnadňují distribuovaný vývoj, stojí za to vyhodnotit další komerční a open source servisní autobusy, jako je NServiceBus, MassTransit a Brighter. V tomto případě abstrakce a API k použití by obvykle přímo ty, které poskytují tyto vysoké úrovni servisní chrupnaté místo své vlastní abstrakce (jako [jednoduché abstrakce události sběrnice poskytované na eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). Když na to přijde, můžete zkoumat [rozlokka eShopOnContainers pomocí NServiceBus](https://go.particular.net/eShopOnContainers) (další odvozené ukázky implementované konkrétní software).

Samozřejmě můžete vždy vytvořit vlastní funkce sběrnice na nižší úrovni technologií, jako je RabbitMQ a Docker, ale práce potřebná k "znovuobjevení kola" může být příliš nákladná pro vlastní podnikovou aplikaci.

Chcete-li zopakovat: ukázkové abstrakce sběrnice událostí a implementace uvedené v eShopOnContainers vzorku jsou určeny k použití pouze jako důkaz koncepce. Jakmile se rozhodnete, že chcete mít asynchronní a událostmi řízenou komunikaci, jak je vysvětleno v aktuální části, měli byste zvolit produkt sběrnice, který nejlépe vyhovuje vašim potřebám pro výrobu.

## <a name="integration-events"></a>Události integrace

Události integrace se používají pro synchronizaci stavu domény ve více mikroslužbách nebo externích systémech. To se provádí publikováním událostí integrace mimo mikroslužbu. Při publikování události do více mikroslužeb příjemce (tolik mikroslužeb, jak jsou přihlášeni k odběru události integrace), příslušné obslužné rutiny události v každém mikroslužbě příjemce zpracovává událost.

Událost integrace je v podstatě třída pro držení dat, jako v následujícím příkladu:

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

Události integrace lze definovat na úrovni aplikace každé mikroslužby, takže jsou odděleny od jiných mikroslužeb, způsobem srovnatelným s tím, jak Jsou definovány ViewModels v serveru a klienta. Co se nedoporučuje, je sdílení společné knihovny událostí integrace mezi více mikroslužeb; přitom by bylo propojení těchto mikroslužeb s knihovnou dat definice jedné události. Nechcete to provést ze stejných důvodů, proč nechcete sdílet společný model domény napříč více mikroslužeb: mikroslužeb musí být zcela autonomní.

Existuje pouze několik druhů knihoven, které byste měli sdílet mezi mikroslužbami. Jedním z nich jsou knihovny, které jsou konečné bloky aplikace, jako [je rozhraní API klienta event bus](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), jako v eShopOnContainers. Dalším je knihovny, které představují nástroje, které by mohly být také sdíleny jako součásti NuGet, jako jsou serializátory JSON.

## <a name="the-event-bus"></a>Sběrnice událostí

Sběrnice událostí umožňuje publikovat/odebírat styl komunikace mezi mikroslužeb bez nutnosti komponenty explicitně znát navzájem, jak je znázorněno na obrázku 6-19.

![Diagram znázorňující základní vzor publikování/odběru.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Obrázek 6-19**. Publikování/přihlášení k odběru základů pomocí sběrnice událostí

Výše uvedený diagram ukazuje, že mikroslužeb A publikuje na Event Bus, který distribuuje k odběru mikroslužeb B a C, aniž by vydavatel potřebuje znát předplatitele. Sběrnice událostí souvisí s Observer vzor a publikování odběru vzor.

### <a name="observer-pattern"></a>Vzor pozorovatele

Ve [vzoru Observer](https://en.wikipedia.org/wiki/Observer_pattern), primární objekt (označovaný jako pozorovatelné) upozorní další objekty zájem (označované jako Pozorovatelé) s relevantní informace (události).

### <a name="publishsubscribe-pubsub-pattern"></a>Vzor Publikovat/Přihlásit se k odběru (Pub/Sub)

Účel [publikování/odběru vzor](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) je stejný jako Observer vzor: chcete upozornit ostatní služby, když dojde k určité události. Ale tam je důležitý rozdíl mezi Pozorovatel a Pub / Sub vzory. Ve vzoru pozorovatele se vysílání provádí přímo z pozorovatelných pozorovatelů, takže se navzájem "znají". Ale při použití Pub / Sub vzor, je třetí součást, volal broker nebo zprávy broker nebo událost sběrnice, která je známa vydavatel i odběratel. Proto při použití Pub / Sub vzor vydavatel a odběratelé jsou přesně odděleny díky uvedené události sběrnice nebo zprávy broker.

### <a name="the-middleman-or-event-bus"></a>Prostředník nebo autobus událostí

Jak dosáhnout anonymity mezi vydavatelem a předplatitelem? Snadný způsob je nechat prostředníka, aby se postaral o veškerou komunikaci. Autobus událostí je jeden takový prostředník.

Sběrnice událostí se obvykle skládá ze dvou částí:

- Abstrakce nebo rozhraní.

- Jedna nebo více implementací.

Na obrázku 6-19 můžete vidět, jak z hlediska aplikace není sběrnice událostí ničím jiným než kanálem Pub/Sub. Způsob implementace této asynchronní komunikace se může lišit. Může mít více implementací, takže mezi nimi můžete přepínat v závislosti na požadavcích na prostředí (například produkční versus vývojová prostředí).

Na obrázku 6-20 můžete vidět abstrakci sběrnice událostí s více implementacemi na základě technologií zasílání zpráv infrastruktury, jako je RabbitMQ, Azure Service Bus nebo jiného zprostředkovatele událostí nebo zpráv.

![Diagram znázorňující přidání vrstvy abstrakce sběrnice událostí.](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Obrázek 6- 20.** Více implementací sběrnice událostí

Je dobré mít sběrnici událostí definovanou prostřednictvím rozhraní, aby ji bylo možné implementovat pomocí několika technologií, jako je sběrnice RabbitMQ Azure Service nebo jiné. Nicméně, a jak již bylo zmíněno dříve, pomocí vlastní abstrakce (rozhraní sběrnice událostí) je dobré pouze v případě, že potřebujete základní funkce sběrnice událostí podporované abstrakce. Pokud potřebujete bohatší funkce služby Service Bus, měli byste pravděpodobně použít rozhraní API a abstrakce poskytované upřednostňovanou komerční sběrnicí služby namísto vlastních abstrakcí.

### <a name="defining-an-event-bus-interface"></a>Definování rozhraní sběrnice událostí

Začněme s některými kódimplementace pro rozhraní sběrnice událostí a možné implementace pro účely průzkumu. Rozhraní by mělo být obecné a jednoduché, jako v následujícím rozhraní.

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

Metoda `Publish` je přímočará. Sběrnice událostí bude vysílat integrační událost, která jí byla předána jakékoli mikroslužbě nebo dokonce externí aplikaci, která se k této události přihlásila. Tato metoda se používá mikroslužby, která publikuje událost.

Metody `Subscribe` (můžete mít několik implementací v závislosti na argumenty) jsou používány mikroslužeb, které chcete přijímat události. Tato metoda má dva argumenty. První je integrační událost, k které se můžete přihlásit (`IntegrationEvent`). Druhý argument je obslužná rutina `IIntegrationEventHandler<T>`události integrace (nebo metoda zpětného volání), s názvem , která má být provedena, když mikroslužba příjemce získá zprávu události integrace.

## <a name="additional-resources"></a>Další zdroje

Některá řešení zasílání zpráv připravená pro produkční prostředí:

- **Azure Service Bus** \
  <https://docs.microsoft.com/azure/service-bus-messaging/>
  
- **Sběrnice NServiceBus** \
  <https://particular.net/nservicebus>
  
- **Hromadná doprava** \
  <https://masstransit-project.com/>

> [!div class="step-by-step"]
> [Předchozí](database-server-container.md)
> [další](rabbitmq-event-bus-development-test-environment.md)
