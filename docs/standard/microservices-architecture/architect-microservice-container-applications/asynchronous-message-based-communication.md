---
title: Asynchronní komunikaci na základě zpráv
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Asynchronní komunikaci na základě zpráv
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5fb5d2f9f4f63ee885752a5dcc45cc45f71dc32f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106405"
---
# <a name="asynchronous-message-based-communication"></a>Asynchronní komunikaci na základě zpráv

Asynchronní zasílání zpráv a komunikaci s událostmi řízené jsou důležité, pokud šíření změny napříč více mikroslužeb a modelu související domény. Jak je uvedeno výše v diskusi mikroslužeb a ohraničenou kontexty (BCs), může zahrnovat modely (uživatel, Zákazník, produktu, účtu atd.) na různých mikroslužeb nebo BCs různých věcí. To znamená, že při změnách, je nutné nějakým způsobem sloučit změny v různých modelech. Řešení je konzistence typu případné a komunikaci s událostmi řízené podle asynchronní zasílání zpráv.

Pokud používáte zasílání zpráv, procesy komunikují nahrazením zprávy asynchronně. Klient odešle příkaz nebo žádostí o služby odesláním zprávy. Pokud služba musí odpovědět, odešle zprávu různých zpět do klienta. Vzhledem k tomu, že je komunikace na základě zprávy, klient předpokládá odpověď nebude možné přijímání okamžitě a že může být žádná odpověď na všech.

Zprávu se skládá hlavičku (metadata jsou to například informace o identifikaci nebo zabezpečení) a text. Zprávy jsou obvykle odesílány prostřednictvím asynchronní protokolů jako AMQP.

Upřednostňované infrastrukturu pro tento typ komunikace v komunitě mikroslužeb je zprostředkovatele lightweight zpráv, které se liší od velké zprostředkovatelé a orchestrators použít v SOA. V broker lightweight zpráva je obvykle "vlečný," funguje pouze jako zprostředkovatele zpráv, s jednoduché implementace, jako je například RabbitMQ nebo škálovatelné služby service bus v cloudu jako Azure Service Bus infrastruktury. V tomto scénáři většinu "smart" přemýšlení stále žije v koncových bodů, které jsou vytvoření a přijímat zprávy – to znamená, že v mikroslužeb.

Jiné pravidlo, které byste měli postupovat podle, co nejvíce, je použít jenom asynchronní zasílání zpráv mezi interních služeb a použít synchronní komunikaci (jako je například HTTP) pouze z klientské aplikace front-endové služby (brány rozhraní API a první úroveň z mikroslužeb).

Existují dva druhy asynchronní komunikaci zasílání zpráv: komunikace na základě zpráv jednoho příjemce a komunikace na základě zpráv více příjemců. V následujících částech budeme obsahují podrobné informace o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikace na základě zpráv jednoho příjemce 

Na základě zpráv asynchronní komunikaci s jednoho příjemce znamená, že point-to-point komunikaci, která přináší zprávu právě jeden příjemce, který je čtení z tohoto kanálu, a zpráva se zpracuje jenom jednou. Existují však zvláštní situace. Například v cloudu systému, by se automaticky zotavit po selhání, stejná zpráva může odeslat vícekrát. Z důvodu sítě nebo jiné chyby klient má být schopni opakujte odesílání zpráv a server má implementovat určité operace idempotent aby bylo možné zpracovat zprávu konkrétní pouze jednou.

Komunikace na základě zpráv jednoho příjemce je velmi dobře vhodné pro odesílání asynchronní příkazy z jednoho mikroslužbu do jiného jak je znázorněno v obrázek 4 až 18 ilustrující tento přístup.

Jakmile začnete odesílání na základě zpráv komunikace (buď pomocí příkazů nebo událostí), neměli byste kombinování komunikace na základě zpráv s synchronní komunikaci pomocí protokolu HTTP.

![](./media/image18.PNG)

**Obrázek 4 až 18**. Jeden mikroslužbu přijetí asynchronní zprávy

Všimněte si, že pokud příkazy vycházejí z klientské aplikace, mohou být provedeny jako synchronní příkazy HTTP. Měli byste použít příkazy na základě zpráv, když potřebujete vyšší škálovatelnost, nebo pokud jste již v na základě zpráv obchodní proces.

## <a name="multiple-receivers-message-based-communication"></a>Komunikace na základě zpráv více příjemců 

Jako více flexibilní přístup můžete také chtít použít mechanismus publikování a přihlášení k odběru, tak, aby komunikaci od odesílatele, bude k dispozici další odběratele mikroslužeb nebo na externí aplikace. Proto, abyste postupovali podle pomáhá [otevřený nebo zavřený Princip](https://en.wikipedia.org/wiki/Open/closed_principle) ve službě odesílání. Tímto způsobem lze přidat další odběratele v budoucnu, aniž by bylo nutné upravit službu odesílatele.

Pokud použijete komunikaci ve formě publikovat/odebírat, by mohla využívat rozhraní sběrnice událostí k publikování událostí pro všechny odběratele.

## <a name="asynchronous-event-driven-communication"></a>Asynchronní komunikaci založeného na událostech

Při použití asynchronní komunikaci založeného na událostech, mikroslužbu publikuje integrace událost v případě, že se něco stane v jeho doméně a jiné mikroslužbu musí mít na paměti, jako je změna ceny v katalogu mikroslužbu produktu. Další mikroslužeb se přihlásit k odběru události, se může přijímat asynchronně. Pokud k tomu dojde, může aktualizovat příjemci své vlastní domény entity, které může způsobit další události integrace k publikování. Tento systém publikování a přihlášení k odběru se obvykle provádí pomocí implementace sběrnici událostí. Sběrnici událostí můžete navrhnout jako abstrakce nebo rozhraní s rozhraním API, který je potřebný k přihlášení k odběru nebo odhlášení odběru událostí a k publikování událostí. Sběrnici událost může mít jeden nebo více implementace založené na všechny meziprocesovou a zasílání zpráv broker, jako je zasílání zpráv fronty nebo služby service bus, která podporuje asynchronní komunikaci a model publikování a přihlášení k odběru.

Pokud systém využívá konzistence typu případné doprovází události integrace, se doporučuje, aby tento postup provést úplně vymazat pro koncového uživatele. Systém neměli používat přístup, která napodobuje události integrace, jako je SignalR nebo systémy dotazování z klienta. Koncový uživatel a majitel firmy musí explicitně zapojení konzistence typu případné v systému a Uvědomte si, že v mnoha případech firmy nemá jakýkoli problém s tímto přístupem, dokud je explicitní.

Jak jsme uvedli výše [problémy a řešení pro správu dat distribuované](#challenges-and-solutions-for-distributed-data-management) části události integrace můžete použít k implementaci pracovní úkoly, které jsou rozmístěny v několika mikroslužeb. Proto bude mít konzistence typu případné mezi tyto služby. Nakonec byl konzistentní transakce se skládá z kolekce distribuované akce. Na každou akci související mikroslužbu aktualizuje entita domény a publikuje jiný integrace událost, která vyvolá další akce v rámci stejné úlohy obchodní začátku do konce.

Důležité je, že můžete chtít komunikovat s více mikroslužeb, která se připojila ke stejné události. V takovém případě můžete publikovat/odebírat zasílání zpráv na základě událostmi řízené komunikaci, jak ukazuje obrázek 4-19. Tento mechanismus publikování/přihlášení k odběru není výhradně pro architektury mikroslužby. Je podobně jako [ohraničenou kontexty](https://martinfowler.com/bliki/BoundedContext.html) v DDD musí komunikovat, nebo jako rozšířit aktualizace z databáze zápis do čtení databáze v [příkazů a dotazů odpovědnost oddělení (CQRS)](https://martinfowler.com/bliki/CQRS.html)architektura vzor. Cílem je mít konzistence typu případné mezi více zdrojů dat napříč distribuovaného systému.

![](./media/image19.png)

**Obrázek 4-19**. Komunikace asynchronní zprávu založeného na událostech

Implementace určí, co Pokud chcete použít pro komunikaci s událostmi, na základě zpráv protokolu. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) může pomoci dosáhnout spolehlivé komunikace ve frontě.

Pokud používáte sběrnici událostí, můžete chtít použít úroveň abstrakce (např. událost sběrnice rozhraní), podle související implementace v třídách s kódem pomocí rozhraní API z zprostředkovatele zpráv jako [RabbitMQ](https://www.rabbitmq.com/) nebo sběrnici služby jako [Azure Service Bus s tématy](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternativně můžete chtít použít vyšší úrovně služby service bus jako NServiceBus, MassTransit nebo Brighter a vyjádřete vaše události sběrnice publikování a přihlášení k odběru systému.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Poznámka o zasílání zpráv technologie pro produkční systémy.

Zasílání zpráv technologie, které jsou k dispozici pro implementace sběrnice vaší abstraktní událostí jsou na různých úrovních. Například produktů, třeba RabbitMQ (zasílání zpráv zprostředkovatele doprava) a Azure Service Bus nacházejí na nižší úrovni než jiné produkty, jako je NServiceBus, MassTransit nebo Brighter, které můžete pracovat nad RabbitMQ a Azure Service Bus. Výběr závisí na tom, kolik bohaté funkce na úrovni aplikace a out-of-the-box škálovatelnost, potřebnou pro vaši aplikaci. Pro implementaci právě událost testování konceptu sběrnice pro vývojové prostředí, jak je uvedeno v ukázce eShopOnContainers v jednoduché implementace nad RabbitMQ systémem kontejner Docker může být dost.

Ale pro kritické a produkční systémy, které je třeba hyper škálovatelnost, můžete vyhodnotit Azure Service Bus. Vysoké úrovni abstrakce a funkce, které usnadňují vývoj distribuovaných aplikací doporučujeme vyhodnotit jiné sběrnice služby komerční a open source, například NServiceBus, MassTransit a Brighter. Samozřejmě můžete vytvořit vlastní funkce služby service bus na nižší úrovni technologie, jako je RabbitMQ a Docker. Ale které pracují vložení může náklady příliš mnoho pro vlastní podnikovou aplikaci.

## <a name="resiliently-publishing-to-the-event-bus"></a>Pružným způsobem publikování ke sběrnici událostí

Výzvy při implementaci architekturu událostmi řízené napříč více mikroslužeb je postup atomicky aktualizace stavu v původní mikroslužbu při pružným způsobem publikování do sběrnici událostí nějakým způsobem na základě jeho událost související integrace transakce. Tady uvádíme několik způsobů, jak dosáhnout, i když může být také další přístupy.

-   Použití transakcí (DTC na základě) fronty jako služby MSMQ. (Je to ale starší verze přístup.)

-   Pomocí [transakce protokolu dolování](https://www.scoop.it/t/sql-server-transaction-log-mining).

-   Pomocí úplného [Sourcing událostí](https://msdn.microsoft.com/library/dn589792.aspx) vzor.

-   Pomocí [pošta k odeslání vzoru](http://gistlabs.com/2014/05/the-outbox/): transakční databázové tabulky jako fronta zpráv, které se bude základ pro komponentu creator událost, která by vytvoření události a jeho publikování.

Další témata vzít v úvahu při použití asynchronní komunikaci jsou zprávy idempotenci a odstranění duplicitních zpráv. Tato témata jsou popsané v části [implementace založené na události komunikace mezi mikroslužeb (události integrace)](#implementing_event_based_comms_microserv) dál v této příručce.

## <a name="additional-resources"></a>Další zdroje

-   **Událost řízené zasílání zpráv**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Publikování a přihlášení k odběru kanálu**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Udi Dahan. Vyčištěné CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Příkaz a dotaz odpovědnost oddělení (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **Komunikace mezi ohraničené kontexty**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Konzistence typu případné**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard. Refaktoring směrem odolnost: Vyhodnocení párování**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[Předchozí](communication-in-microservice-architecture.md)
[další](maintain-microservice-apis.md)
