---
title: Asynchronní komunikace založená na zprávách
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Asynchronní komunikace založená na zprávách je základní koncept v architektuře mikroslužeb, protože je nejlepší způsob, jak zobrazovat nezávislé mikroslužeb od sebe při také zabránit v synchronizaci nakonec.
ms.date: 09/20/2018
ms.openlocfilehash: 65bd0cd2b316fe7011ad8e878852547ee5949f09
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641377"
---
# <a name="asynchronous-message-based-communication"></a>Asynchronní komunikace založená na zprávách

Asynchronní zasílání zpráv a komunikace založená na událostech jsou důležité při šíření změn napříč několika mikroslužbami a jejich související doménových modelů. Jak je uvedeno výše v diskusi mikroslužeb a ohraničených kontextech (BCs), může znamenat modely (uživatel, Zákazník, produkt, účet atd.) různé věci pro různé mikroslužby nebo BCs. To znamená, že pokud dojde ke změnám, budete potřebovat způsob, jak sloučit změny v různých modelech. Řešení je konečné konzistence a komunikace založená na událostech podle asynchronní zasílání zpráv.

Při použití zasílání zpráv, procesy komunikují asynchronně výměnou zpráv. Klient odešle příkaz nebo žádostí o službu odesláním zprávy. Pokud služba musí odpovědět, odešle zprávu různých zpět do klienta. Protože je komunikace založená na zprávách, klient předpokládá, že odpověď nepřicházejí okamžitě a že může existovat žádná odpověď ve všech.

Zpráva se skládá ze záhlaví (metadat – například informace o identifikaci nebo zabezpečení) a text. Zprávy se obvykle odesílají přes asynchronní protokolů, jako jsou AMQP.

Upřednostňované infrastruktury pro tento typ komunikace v komunitě mikroslužeb je zprostředkovatel zjednodušené zpráv, které se liší od velkých zprostředkovatelů a orchestrátorů používané SOA. Zprostředkovatel zjednodušené zpráv je obvykle "vlečný," funguje pouze jako zprostředkovatel zpráv, pomocí jednoduché implementace, jako je například RabbitMQ nebo škálovatelné služby Service bus v cloudu jako Azure Service Bus infrastruktury. V tomto scénáři většinu "inteligentní" přemýšlení stále nachází koncové body, které jsou vytváření a přijímat zprávy – to znamená, že v mikroslužby.

Je další pravidlo, které byste měli sledovat, co je to možné, používejte pouze asynchronní zasílání zpráv mezi službami interní a použít synchronní sdělení (např. HTTP) jenom klientské aplikace front-endové služby (brány rozhraní API a první úroveň mikroslužeb).

Existují dva druhy asynchronní zasílání zpráv komunikace: komunikace založená na zprávách jednoho příjemce a komunikace založená na zprávách více příjemců. Následující části obsahují podrobnosti o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikace založená na zprávách jednoho příjemce

Asynchronní komunikace založená na zprávách s jednoho příjemce znamená, že existuje komunikace typu point-to-point, který doručuje zprávy přesně jednomu příjemci, který je čtení z kanálu, a zpráva se zpracuje jenom jednou. Existují však speciálních situacích. Například v systému cloud, který se pokusí automaticky zotavit po selhání, stejnou zprávu dala odeslat více než jednou. Z důvodu sítě nebo jiné chyby klient musí být schopen opakování odesílání zpráv a má server provádět operace jako idempotentní, aby bylo možné zpracovat konkrétní zprávu pouze jednou.

Komunikace založená na zprávách jednoho příjemce je zvlášť vhodná pro odesílání asynchronní příkazy z jednoho mikroslužeb na jiný, jak je znázorněno v obrázek 4 – 18, který znázorňuje tento přístup.

Po spuštění odesílání komunikace na základě zpráv (buď pomocí příkazů nebo události), měli byste se vyhnout, kombinování komunikace založená na zprávách s synchronní komunikaci pomocí protokolu HTTP.

![Jeden mikroslužeb příjem asynchronních zpráv](./media/image18.png)

**Obrázek 4 – 18**. Jeden mikroslužeb příjem asynchronních zpráv

Všimněte si, že při příkazy pocházejí z klientské aplikace, že je možné implementovat jako synchronní příkazy HTTP. Pokud potřebujete vyšší škálovatelnost, nebo pokud jste již v procesu podnikání založenou na zprávách, měli byste použít příkazy založenou na zprávách.

## <a name="multiple-receivers-message-based-communication"></a>Komunikace založená na zprávách více příjemců

Zvýšení flexibility přístup se považuje za může být také vhodné použít mechanismus publikování/odebírání tak, aby vaši komunikaci od odesílatele bude k dispozici další odběratele mikroslužby nebo na externí aplikace. Proto, abyste postupovali podle pomáhá [Princip otevřený/uzavřený](https://en.wikipedia.org/wiki/Open/closed_principle) odeslání služby. Tímto způsobem lze přidat další předplatitele v budoucnosti bez nutnosti upravovat odesílatel služby.

Použijete-li publikovat/odebírat sdělení, může pomocí rozhraní Service bus událostí k publikování událostí do žádného předplatitele.

## <a name="asynchronous-event-driven-communication"></a>Asynchronní komunikace založená na událostech

Při použití asynchronní komunikace založená na událostech, publikuje mikroslužbě integrace událost v případě určité události v jeho doméně a jiné mikroslužeb je potřeba mít na paměti, jako je změna ceny v mikroslužbě katalog produktů. Další mikroslužeb se přihlásit k odběru událostí, je můžou přijímat asynchronně. Pokud k tomu dojde, příjemci může aktualizovat své vlastní domény entity, které může způsobit další události integrace pro publikování. Tento systém publikování/odběr se obvykle provádí pomocí implementace sběrnice událostí. Service bus události lze navrhnout jako abstraktní nebo rozhraní s rozhraním API, který je nezbytný pro přihlášení k odběru nebo odběr událostí a publikovat události. Události Service bus může mít také jednu nebo více implementací podle jakékoli mezi procesy a zasílání zpráv zprostředkovatele, jako je například fronty zasílání zpráv nebo služby Service bus, která podporuje asynchronní komunikace a modelu publikování a přihlášení k odběru.

Pokud systém využívá konečné konzistence řízené událostmi, integrace, doporučuje se, že tento přístup je proveden úplně jasné koncového uživatele. Systém by neměly používat přístup, který napodobuje události integrace, jako je SignalR nebo dotazování systémy od klienta. Koncový uživatel a majitel firmy musí explicitně zapojte konečnou konzistenci v systému a Uvědomte si, že v mnoha případech firmy nemusí kvůli problému s tímto přístupem tak dlouho, dokud je explicitní. To je důležité, protože uživatelé můžou očekávat některé výsledky okamžitě a nemusí k tomu dojít s konečnou konzistencí.

Jak je uvedeno výše v [výzvy a řešení pro správu dat distribuovaných](distributed-data-management.md) části Integrace událostí můžete použít k implementaci obchodní úlohy, které jsou rozmístěny v několika mikroslužeb. Proto budete mít konečnou konzistenci mezi těmito službami. Konečnou konzistenci transakcí se skládá z kolekce distribuovaných akcí. Na každou akci související mikroslužeb aktualizuje entita domény a publikuje jiné integrace událostí, která vyvolá další akce v rámci stejné úlohy obchodní začátku do konce.

Důležitý bod je, že můžete chtít sdělit několika mikroslužeb, která přihlášeni ke stejné události. V takovém případě můžete použít publikování/odběr zasílání zpráv na základě komunikace založená na událostech, jak ukazuje obrázek 4 – 19. Tento mechanismus publikování/odběr není výhradně pro architekturu mikroslužeb. Je podobným způsobem, jakým [ohraničených kontextech](https://martinfowler.com/bliki/BoundedContext.html) v DDD musí komunikovat, nebo způsobem, jakým šíření aktualizací z databáze pro zápis do databáze pro čtení v [zodpovědnosti příkazů a dotazů oddělení (CQRS)](https://martinfowler.com/bliki/CQRS.html)vzor architektury. Cílem je, aby konečnou konzistenci mezi více zdroji dat napříč distribuovaného systému.

![V asynchronní komunikace založená na událostech jednu mikroslužbu publikuje události do sběrnice událostí a mnoha mikroslužeb se mohou přihlásit k jeho, upozorňování a na ně na něj.](./media/image19.png)

**Obrázek 4-19**. Komunikace asynchronních zpráv založený na událostech

Implementace určí, co Pokud chcete použít pro komunikaci založený na událostech, založená na zprávách protokolu. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) může zajistit spolehlivou komunikaci ve frontě.

Při použití sběrnice událostí, můžete chtít použít úroveň abstrakce (jako je rozhraní událostí Service bus), podle související implementace tříd s kódem pomocí rozhraní API od zprostředkovatele zprávu jako [RabbitMQ](https://www.rabbitmq.com/) nebo Azure service bus, podobně jako [Azure Service Bus s tématy](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternativně můžete chtít použít vyšší úrovně služby Service bus jako NServiceBus, MassTransit nebo Brighter srozumitelně vysvětlit vaší sběrnice událostí a publikování/odběr systému.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Poznámka k zasílání zpráv technologie pro produkční systémy.

K dispozici pro implementace sběrnice vaše abstraktní událost zasílání zpráv technologie jsou na různých úrovních. Například produkty, jako je RabbitMQ (zasílání zpráv Service broker doprava) a Azure Service Bus vám sedět u nižší než jiné produkty, jako je, NServiceBus, MassTransit nebo Brighter, což může pracovat nad RabbitMQ a Azure Service Bus. Výběr závisí na tom, kolik bohaté funkce na úrovni aplikace a out-of-the-box škálovatelnosti, které potřebujete pro vaši aplikaci. Pro implementaci právě sběrnice událostí testování konceptu pro vaše vývojové prostředí, jako jste to udělali v ukázkové aplikaci eShopOnContainers Jednoduchá implementace nad RabbitMQ spuštění v kontejneru Dockeru mohou být dostatečné.

Ale pro nepostradatelné a produkční systémy, které je třeba hyper škálovatelnost, můžete k vyhodnocení Azure Service Bus. Abstrakce vyšší úrovně a funkce, které usnadňují vývoj distribuovaných aplikací doporučujeme vyhodnotit další obchodní a open source služby sběrnice, jako je například NServiceBus MassTransit a Brighter. Samozřejmě můžete vytvářet vlastní funkce služby Service bus na nižší úrovni technologie jako RabbitMQ a Docker. Ale tato práce zajistí funkčnost systému mohly stát příliš mnoho pro vlastní podnikové aplikace.

## <a name="resiliently-publishing-to-the-event-bus"></a>Odolné publikování ve službě Service bus události

Atomicky aktualizace stavu v původní mikroslužeb při odolné publikování do sběrnice událostí, nějakým způsobem na základě jeho související integrace událostí je výzvy při implementaci architekturu řízených událostmi napříč různými mikroslužbami transakce. Následují několik způsobů jak toho dosáhnout, i když může existovat i další přístupy.

- Použití transakční fronty (založený na DTC), jako je služba MSMQ. (To je však přístup založený na starší verzi.)

- Pomocí [protokol transakcí dolování](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Použití úplného [modelu Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) vzor.

- Použití [pošta k odeslání vzoru](http://gistlabs.com/2014/05/the-outbox/): tabulku transakční databáze jako používá fronta zpráv, které se bude základ pro komponentu Tvůrce událostí, která by vytvořit událost a publikujete ji.

Další témata, které je třeba zvážit při použití asynchronní komunikaci jsou zpráv, idempotence a odstranění duplicitních dat zprávy. Tato témata jsou popsané v části [implementace komunikace mezi mikroslužbami (události integrace) na základě událostí](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) dále v tomto průvodci.

## <a name="additional-resources"></a>Další zdroje

- **Řízené zasílání zpráv** \
  <http://soapatterns.org/design_patterns/event_driven_messaging>

- **Publikování/odběr kanálu** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Udi Dahan. Vyčištěné modelu CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **Příkaz and Query Responsibility Segregation (CQRS)** \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Komunikace mezi ohraničené kontexty** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Konzistence typu případné** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy Bogard. Refaktoring směrem k odolnosti: Vyhodnocení párování** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Předchozí](communication-in-microservice-architecture.md)
> [další](maintain-microservice-apis.md)
