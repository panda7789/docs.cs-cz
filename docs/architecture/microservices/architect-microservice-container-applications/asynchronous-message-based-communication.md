---
title: Asynchronní komunikace založená na zprávách
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Asynchronní komunikace založená na zprávuje základní koncept v architektuře mikroslužeb, protože je to nejlepší způsob, jak zachovat mikroslužeb nezávislé na sobě a zároveň je synchronizován nakonec.
ms.date: 09/20/2018
ms.openlocfilehash: 84eaf70178cce91a86dae8a55badb0b4ddd6a7c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73454230"
---
# <a name="asynchronous-message-based-communication"></a>Asynchronní komunikace založená na zprávách

Asynchronní zasílání zpráv a komunikace řízená událostmi jsou důležité při šíření změn mezi více mikroslužeb a jejich souvisejících modelů domén. Jak již bylo zmíněno dříve v diskusi mikroslužeb a ohraničené kontexty (BCs), modely (uživatel, zákazník, produkt, účet atd.) může znamenat různé věci pro různé mikroslužeb nebo BC. To znamená, že když dojde ke změnám, potřebujete nějaký způsob, jak sladit změny mezi různými modely. Řešením je případná konzistence a komunikace založená na událostech na základě asynchronního zasílání zpráv.

Při použití zasílání zpráv procesy komunikovat prostřednictvím výměny zpráv asynchronně. Klient provede příkaz nebo požadavek na službu odesláním zprávy. Pokud služba potřebuje odpovědět, odešle klientovi jinou zprávu. Vzhledem k tomu, že se jedná o komunikaci založenou na zprávě, klient předpokládá, že odpověď nebude přijata okamžitě a že nemusí existovat žádná odpověď vůbec.

Zpráva se skládá z hlavičky (metadata, jako jsou identifikační nebo bezpečnostní informace) a tělo. Zprávy jsou obvykle odesílány prostřednictvím asynchronních protokolů, jako je AMQP.

Upřednostňovaná infrastruktura pro tento typ komunikace v komunitě mikroslužeb je zjednodušené zprostředkovatele zpráv, který se liší od velkých zprostředkovatelů a orchestrátorů používaných v SOA. V zprostředkovateli lehkých zpráv infrastruktury je obvykle "němý", funguje pouze jako zprostředkovatel zpráv, s jednoduché implementace, jako je RabbitMQ nebo škálovatelné sběrnice v cloudu, jako je Azure Service Bus. V tomto scénáři většina "inteligentní" myšlení stále žije v koncových bodech, které jsou vytváření a spotřebovává zprávy, které je v mikroslužeb.

Dalším pravidlem, které byste se měli snažit co nejvíce dodržovat, je používat pouze asynchronní zasílání zpráv mezi interními službami a používat synchronní komunikaci (například HTTP) pouze z klientských aplikací do front-endových služeb (brány rozhraní API plus první úroveň mikroslužeb).

Existují dva druhy asynchronní komunikace zasílání zpráv: komunikace založená na zprávách jednoho příjemce a komunikace založená na zprávách více příjemců. V následujících částech jsou uvedeny podrobnosti o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikace založená na zprávě s jedním přijímačem

Asynchronní komunikace založená na zprávě s jedním příjemcem znamená, že je komunikace point-to-point, která doručuje zprávu přesně jednomu z příjemců, který čte z kanálu, a že zpráva je zpracována pouze jednou. Existují však zvláštní situace. Například v cloudovém systému, který se snaží automaticky zotavit z chyb, může být stejná zpráva odeslána vícekrát. Z důvodu sítě nebo jiných selhání musí být klient schopen opakovat odesílání zpráv a server musí implementovat operaci, která má být idempotentní, aby bylo možné zpracovat konkrétní zprávu pouze jednou.

Komunikace založená na zprávě s jedním přijímačem je obzvláště vhodná pro odesílání asynchronních příkazů z jedné mikroslužby do druhé, jak je znázorněno na obrázku 4-18, který ilustruje tento přístup.

Jakmile začnete odesílat komunikaci založenou na zprávě (buď s příkazy nebo událostmi), měli byste se vyhnout míchání komunikace založené na zprávě se synchronní komunikací HTTP.

![Jedna mikroslužba přijímající asynchronní zprávu](./media/asynchronous-message-based-communication/single-receiver-message-based-communication.png)

**Obrázek 4-18**. Jedna mikroslužba přijímající asynchronní zprávu

Všimněte si, že když příkazy pocházejí z klientských aplikací, mohou být implementovány jako synchronní příkazy HTTP. Příkazy založené na zprávach byste měli používat, když potřebujete vyšší škálovatelnost nebo když už jste v obchodním procesu založeném na zprávě.

## <a name="multiple-receivers-message-based-communication"></a>Více přijímačů komunikace založená na textech

Jako flexibilnější přístup můžete také použít mechanismus publikování/odběru tak, aby vaše komunikace od odesílatele bude k dispozici další mikroslužeb odběratele nebo externí aplikace. Proto vám pomáhá dodržovat [princip otevření/uzavření](https://en.wikipedia.org/wiki/Open/closed_principle) v odesílající službě. Tímto způsobem další předplatitelé mohou být přidány v budoucnu bez nutnosti měnit službu odesílatele.

Při použití publikování nebo odběru komunikace, můžete používat rozhraní sběrnice událostí publikovat události pro všechny odběratele.

## <a name="asynchronous-event-driven-communication"></a>Asynchronní komunikace řízená událostmi

Při použití asynchronní komunikace řízené událostmi mikroslužba publikuje událost integrace, když se něco stane v rámci své domény a jiné mikroslužby musí být vědomi, jako je změna ceny v katalogu produktů mikroslužeb. Další mikroslužby přihlásit k odběru událostí, aby je můžete přijímat asynchronně. V takovém případě mohou příjemci aktualizovat své vlastní entity domény, což může způsobit publikování dalších událostí integrace. Tento systém publikování/odběru se obvykle provádí pomocí implementace sběrnice událostí. Sběrnice událostí může být navržena jako abstrakce nebo rozhraní s rozhraním API, které je potřeba k přihlášení k odběru nebo odhlášení z odběru událostí a publikování událostí. Sběrnice událostí může mít také jednu nebo více implementací založených na jakémkoli zprostředkovateli mezi procesy a zasílání zpráv, jako je fronta zpráv nebo sběrnice služby, která podporuje asynchronní komunikaci a model publikování/odběru.

Pokud systém používá konečnou konzistenci řízenou událostmi integrace, doporučuje se, aby byl tento přístup koncovému uživateli zcela jasný. Systém by neměl používat přístup, který napodobuje události integrace, jako je SignalR nebo dotazování systémy z klienta. Koncový uživatel a vlastník firmy musí explicitně přijmout konečnou konzistenci v systému a uvědomit si, že v mnoha případech podnikání nemá žádný problém s tímto přístupem, pokud je to explicitní. To je důležité, protože uživatelé mohou očekávat, že některé výsledky okamžitě a to nemusí dojít s konečnou konzistenci.

Jak je uvedeno dříve v [části Výzvy a řešení pro správu distribuovaných dat,](distributed-data-management.md) můžete použít události integrace k implementaci obchodních úkolů, které pokrývají více mikroslužeb. Proto budete mít konečný soulad mezi těmito službami. Nakonec konzistentní transakce se skládá z kolekce distribuovaných akcí. Při každé akci související mikroslužby aktualizuje entitu domény a publikuje další událost integrace, která vyvolá další akci v rámci stejného obchodního úkolu od konce do konce.

Důležitým bodem je, že můžete chtít komunikovat s více mikroslužeb, které jsou přihlášeni ke stejné události. Chcete-li tak učinit, můžete použít publikování nebo odběru zpráv na základě komunikace řízené událostmi, jak je znázorněno na obrázku 4-19. Tento mechanismus publikování/odběru není výhradní architekturou mikroslužeb. Je to podobné jako [ohraničené kontexty](https://martinfowler.com/bliki/BoundedContext.html) v DDD by měl komunikovat, nebo způsob, jakým šíření aktualizací z databáze zápisu do databáze pro čtení v [příkazu a dotazu odpovědnost i gregace (CQRS)](https://martinfowler.com/bliki/CQRS.html) architektura vzor. Cílem je mít konečnou konzistenci mezi více zdroji dat v celém distribuovaném systému.

![Diagram znázorňující asynchronní komunikaci řízenou událostmi.](./media/asynchronous-message-based-communication/asynchronous-event-driven-communication.png)

**Obrázek 4-19**. Asynchronní komunikace zpráv řízená událostmi

V komunikaci řízené asynchronní události jeden mikroslužba publikuje události do sběrnice událostí a mnoho mikroslužeb můžete přihlásit k odběru, získat oznámení a jednat na to. Vaše implementace určí, jaký protokol se má použít pro komunikaci založenou na událostech a zprávách. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) může pomoci dosáhnout spolehlivé komunikace ve frontě.

Při použití sběrnice událostí můžete chtít použít úroveň abstrakce (například rozhraní sběrnice událostí) na základě související implementace ve třídách s kódem pomocí rozhraní API z brokeru zpráv, jako je [RabbitMQ](https://www.rabbitmq.com/) nebo service bus, jako je [Azure Service Bus s tématy](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Případně můžete chtít použít vyšší úroveň sběrnice, jako je NServiceBus, MassTransit nebo Brighter, k formulování sběrnice událostí a publikování/odběru systému.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Poznámka o technologiích zasílání zpráv pro produkční systémy

Technologie zasílání zpráv, které jsou k dispozici pro implementaci sběrnice abstraktních událostí, jsou na různých úrovních. Například produkty jako RabbitMQ (přenos zprostředkovatele zasílání zpráv) a Azure Service Bus jsou na nižší úrovni než jiné produkty, jako je NServiceBus, MassTransit nebo Brighter, které můžou fungovat na rabbitmq a Azure Service Bus. Vaše volba závisí na tom, kolik bohatých funkcí na úrovni aplikace a out-of-the-box škálovatelnost, kterou potřebujete pro vaši aplikaci. Pro implementaci pouze proof-of-concept sběrnice událostí pro vaše vývojové prostředí, jak to bylo provedeno v eShopOnContainers vzorku, jednoduchá implementace na vrcholu RabbitMQ běží na kontejneru Dockeru může stačit.

Pro kritické a produkční systémy, které potřebují hyperškálovatelnost, však můžete chtít vyhodnotit Azure Service Bus. Pro vysoké úrovně abstrakce a funkce, které usnadňují vývoj distribuovaných aplikací, doporučujeme vyhodnotit další komerční a open source servisní sběrnice, jako je Například NServiceBus, MassTransit a Brighter. Samozřejmě můžete vytvořit vlastní funkce service-bus na nižší úrovni technologií, jako je RabbitMQ a Docker. Ale že instalatérské práce může stát příliš mnoho pro vlastní podnikové aplikace.

## <a name="resiliently-publishing-to-the-event-bus"></a>Odolné publikování na sběrnici událostí

Výzvou při implementaci architektury řízené událostmi napříč více mikroslužbami je, jak atomicky aktualizovat stav v původní mikroslužbě a zároveň odolně publikovat související integrační událost do sběrnice událostí, jaksi na základě Transakce. Následuje několik způsobů, jak toho dosáhnout, i když by mohly být další přístupy také.

- Použití transakční fronty (založené na DTC), jako je služba MSMQ. (Jedná se však o starší přístup.)

- Použití [dolování transakční protokol](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Použití [úplného](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) vzoru získávání událostí.

- Použití [vzoru Pošta k odeslání](https://www.kamilgrzybek.com/design/the-outbox-pattern/): transakční databázová tabulka jako fronta zpráv, která bude základem pro komponentu tvůrce událostí, která by vytvořila událost a publikovala ji.

Další témata, která je třeba vzít v úvahu při použití asynchronní komunikace, jsou idempotence zprávy a odstranění duplicit zpráv. Tato témata jsou popsány v části [Implementace komunikace založené na událostech mezi mikroslužeb (události integrace)](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) dále v této příručce.

## <a name="additional-resources"></a>Další zdroje

- **Zasílání zpráv řízených událostmi** \
  <https://soapatterns.org/design_patterns/event_driven_messaging>

- **Publikovat/odebírat kanál** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Udi Dahan. Vyjasněné CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **Oddělení odpovědnosti příkazů a dotazů (CQRS)** \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Komunikace mezi ohraničené kontexty** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Konečná konzistence** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmyho Bogarda. Refaktoring směrem k odolnosti: Hodnocení spojky** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Předchozí](communication-in-microservice-architecture.md)
> [další](maintain-microservice-apis.md)
