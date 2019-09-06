---
title: Asynchronní komunikace založená na zprávách
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Asynchronní komunikace založená na zprávách je zásadní pojem architektury mikroslužeb, protože je to nejlepší způsob, jak uchovávat mikroslužby nezávisle na sobě a zároveň je synchronizovat.
ms.date: 09/20/2018
ms.openlocfilehash: 65bd0cd2b316fe7011ad8e878852547ee5949f09
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295572"
---
# <a name="asynchronous-message-based-communication"></a>Asynchronní komunikace založená na zprávách

Asynchronní zasílání zpráv a komunikace řízených událostmi jsou klíčové při rozšiřování změn napříč více mikroslužbami a jejich souvisejícími doménovými modely. Jak bylo zmíněno dříve v diskusích mikroslužeb a ohraničených kontextech (BCs), modely (uživatel, zákazník, produkt, účet atd.) můžou znamenat různé věci pro různé mikroslužby nebo službu BCs. To znamená, že když dojde ke změnám, budete potřebovat nějaký způsob, jak sjednotit změny v různých modelech. Řešení představuje konečnou konzistenci a komunikaci založenou na událostech na základě asynchronního zasílání zpráv.

Při použití zasílání zpráv komunikuje procesy asynchronně výměnou zpráv. Klient vytvoří příkaz nebo požadavek na službu odesláním zprávy. Pokud služba potřebuje odpovědět, pošle jinou zprávu zpátky klientovi. Vzhledem k tomu, že se jedná o komunikaci založenou na zprávách, klient předpokládá, že odpověď nebude přijata okamžitě a že nemusí vůbec reagovat.

Zpráva se skládá z hlavičky (metadata, jako je například identifikace nebo informace o zabezpečení) a těla. Zprávy jsou obvykle odesílány prostřednictvím asynchronních protokolů, jako je AMQP.

Upřednostňovaná infrastruktura pro tento typ komunikace v komunitě mikroslužeb je zjednodušený zprostředkovatel zpráv, který se liší od velkých zprostředkovatelů a orchestrace používaných v SOA. V odlehčeném zprostředkovateli zpráv je infrastruktura obvykle "Dumb", která funguje jenom jako zprostředkovatel zpráv, a s jednoduchými implementacemi, jako je RabbitMQ nebo škálovatelná sběrnice služby v cloudu, jako je Azure Service Bus. V tomto scénáři je většina "inteligentních" přemýšlejí stále v koncových bodech, které vytvářejí a spotřebovávají zprávy – to znamená v mikroslužbách.

Další pravidlo, které byste měli vyzkoušet co nejvíc, je používat jenom asynchronní zasílání zpráv mezi interními službami a používat synchronní komunikaci (například HTTP) z klientských aplikací do front-endové služby (brány rozhraní API plus první úroveň mikroslužeb).

Existují dva druhy komunikace asynchronního zasílání zpráv: komunikace s jedním přijímačem a komunikace na základě zpráv s více přijímači. V následujících oddílech jsou uvedeny podrobnosti o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikace založená na zprávách s jedním přijímačem

Asynchronní komunikace založená na zprávách s jedním přijímačem znamená, že existuje zpráva typu Point-to-Point, která doručuje zprávu k přesně jednomu z uživatelů čtených z kanálu a že se zpráva zpracovává jenom jednou. Existují však zvláštní situace. Například v případě cloudového systému, který se pokusí o automatické obnovení při selhání, může být stejná zpráva odeslána několikrát. V důsledku sítě nebo jiných selhání musí klient být schopný se znovu odeslat zprávy a server musí implementovat operaci, která se má idempotentní, aby mohla zpracovat konkrétní zprávu jenom jednou.

Komunikace založená na zprávách s jedním přijímačem je zvláště vhodná pro posílání asynchronních příkazů z jedné mikroslužby na jinou, jak je znázorněno na obrázku 4-18, který tento postup znázorňuje.

Jakmile začnete odesílat komunikaci na základě zpráv (s příkazy nebo událostmi), měli byste se vyhnout kombinování komunikace založené na zprávách s synchronní komunikací HTTP.

![Jedna mikroslužba přijímající asynchronní zprávu](./media/image18.png)

**Obrázek 4-18**. Jedna mikroslužba přijímající asynchronní zprávu

Všimněte si, že když se příkazy dostanou z klientských aplikací, dají se implementovat jako synchronní příkazy HTTP. Příkazy založené na zprávách byste měli použít, když potřebujete vyšší škálovatelnost nebo když už jste v podnikovém procesu založeném na zprávách.

## <a name="multiple-receivers-message-based-communication"></a>Komunikace na základě zpráv s více přijímači

Pružně flexibilní přístup můžete použít také k tomu, abyste mohli používat mechanismus pro publikování a odběr, aby vaše komunikace od odesilatele byla dostupná pro další mikroslužby pro předplatitele nebo externí aplikace. Proto vám pomůže postupovat podle pokynů pro [otevření/uzavření](https://en.wikipedia.org/wiki/Open/closed_principle) v odesílající službě. Tímto způsobem můžete v budoucnu přidat další předplatitele bez nutnosti měnit službu odesílatele.

Pokud používáte komunikaci s publikováním a odběrem, můžete k publikování událostí do libovolného předplatitele použít rozhraní sběrnice událostí.

## <a name="asynchronous-event-driven-communication"></a>Asynchronní komunikace řízená událostmi

Při použití komunikace založené na asynchronních událostech publikuje mikroslužba událost integrace, když se něco stane v rámci své domény, a další mikroslužba je musí znát, jako je například změna ceny v mikroslužbě katalogu produktů. Další mikroslužby přihlásily k odběru událostí, aby je mohli přijímat asynchronně. Pokud k tomu dojde, můžou příjemci aktualizovat vlastní entity domény, což může způsobit publikování dalších událostí integrace. Tento systém pro publikování a odběr se obvykle provádí pomocí implementace sběrnice událostí. Sběrnice událostí může být navržena jako abstrakce nebo rozhraní s rozhraním API, které je potřeba k přihlášení k odběru nebo odhlášení odběru událostí a k publikování událostí. Tato sběrnice může mít taky jednu nebo více implementací na základě jakéhokoli procesu a zprostředkovatele zasílání zpráv, jako je fronta pro zasílání zpráv nebo sběrnice, která podporuje asynchronní komunikaci a model publikování/odběr.

Pokud systém používá konečnou konzistenci založenou na integračních událostech, doporučuje se, aby byl tento přístup zcela jasný pro koncového uživatele. Systém by neměl používat přístup, který napodobuje integrační události, jako jsou například systémy signalizace nebo cyklického dotazování z klienta. Koncový uživatel a majitel firmy musí výslovně využít konečnou konzistenci v systému a zjistit, že v mnoha případech obchod nemá žádné potíže s tímto přístupem, pokud je to tak tak dlouho. To je důležité, protože uživatelé můžou očekávat, že se výsledky zobrazí okamžitě a že k tomu nemusí docházet s konečnou konzistencí.

Jak bylo popsáno dříve v části [výzvy a řešení pro správu distribuovaných dat](distributed-data-management.md) , můžete použít integrační události k implementaci obchodních úloh, které jsou rozloženy na více mikroslužeb. Proto budete mít konečnou konzistenci mezi těmito službami. Nakonec konzistentní transakce se skládá z kolekce distribuovaných akcí. V každé akci související mikroslužba aktualizuje doménovou entitu a publikuje jinou událost integrace, která vyvolá další akci v rámci stejného koncového podnikového úkolu.

Důležité je, že budete chtít komunikovat s více mikroslužbami, které se přihlásily ke stejné události. K tomu můžete použít publikování a odběr zpráv na základě komunikace řízené událostmi, jak je znázorněno na obrázku 4-19. Tento mechanismus publikování/odběru není výhradně součástí architektury mikroslužeb. Podobá se tomu, že by měl komunikovat s [ohraničenými kontexty](https://martinfowler.com/bliki/BoundedContext.html) v ddd nebo jak rozšířit aktualizace z databáze pro zápis do databáze pro čtení ve vzoru architektury [CQRS (Command and Query Responsibility segregation) (CQRS)](https://martinfowler.com/bliki/CQRS.html) . Cílem je mít v rámci distribuovaného systému konečnou konzistenci mezi několika zdroji dat.

![V asynchronní komunikaci založené na událostech jedna mikroslužba publikuje události do sběrnice událostí a spousta mikroslužeb se může přihlásit k odběru, aby se k ní mohl dostat oznámení a reagovat na ně.](./media/image19.png)

**Obrázek 4-19**. Komunikace zpráv řízených asynchronními událostmi

Vaše implementace určí, který protokol bude použit pro komunikaci založenou na událostech. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) může pomáhat dosáhnout spolehlivé komunikace ve frontě.

Pokud používáte sběrnici událostí, možná budete chtít použít úroveň abstrakce (například rozhraní sběrnice událostí) založenou na související implementaci ve třídách s kódem pomocí rozhraní API od zprostředkovatele zpráv, jako je [RabbitMQ](https://www.rabbitmq.com/) nebo Service Bus, jako je [Azure Service Bus s tématy. ](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternativně můžete chtít použít vyšší úroveň služby Service Bus, jako je NServiceBus, MassTransit nebo jasnější, aby vyjadřují Vaši sběrnici událostí a systém pro publikování a odběr.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Poznámka o technologiích zasílání zpráv pro produkční systémy

Technologie zasílání zpráv, které jsou k dispozici pro implementaci vaší abstraktní sběrnice událostí, jsou na různých úrovních. Například produkty, jako je například RabbitMQ (přenos prostřednictvím zprostředkovatele zasílání zpráv) a Azure Service Bus, jsou na nižší úrovni než jiné produkty, jako je NServiceBus, MassTransit nebo jasnější, což může pracovat na RabbitMQ a Azure Service Bus. Vaše volba závisí na tom, kolik funkcí je na úrovni aplikace a předem připravená škálovatelnost, kterou potřebujete pro vaši aplikaci. Pro implementaci jediné sběrnice událostí ve vývojovém prostředí, jak byla provedena v ukázce eShopOnContainers, může být k dispozici Jednoduchá implementace na RabbitMQ spuštěném v kontejneru Docker.

U kritických a produkčních systémů, které vyžadují škálovatelnost technologie Hyper-v, ale můžete chtít vyhodnotit Azure Service Bus. Pro abstrakce a funkce vysoké úrovně, které usnadňují vývoj distribuovaných aplikací, doporučujeme, abyste vyhodnotili jiné komerční a open source sběrnice, jako je NServiceBus, MassTransit a jasnější. Samozřejmě můžete sestavovat vlastní funkce sběrnice služby na základě technologií nižší úrovně, jako je RabbitMQ a Docker. Tato pracovní verze ale může být pro vlastní podnikovou aplikaci příliš velká.

## <a name="resiliently-publishing-to-the-event-bus"></a>Odolné publikování do sběrnice událostí

Při implementaci architektury založené na událostech napříč více mikroslužbami se jedná o způsob, jak atomicky aktualizovat stav původní mikroslužeb a zároveň bez problémů publikovat související integrační událost do sběrnice událostí, a to ani v závislosti na převody. Toto je několik způsobů, jak to provést, i když můžou existovat i další přístupy.

- Použití transakční fronty (založené na koordinátoru DTC), jako je například MSMQ. (Toto je však starší přístup.)

- Pomocí [dolování protokolu transakcí](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Použití úplného vzoru pro [zdroje událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) .

- Použití [vzoru pošty k odeslání](http://gistlabs.com/2014/05/the-outbox/): transakční tabulka databáze jako fronta zpráv, která bude základem pro komponentu Event-Creator, která by vytvořila událost a publikuje ji.

Další témata, která je potřeba vzít v úvahu při použití asynchronní komunikace, jsou idempotence zprávy a odstranění duplicitních zpráv. Tato témata jsou popsaná v části [implementace komunikace založené na událostech mezi mikroslužby (události integrace)](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) dále v této příručce.

## <a name="additional-resources"></a>Další zdroje

- **Zasílání zpráv řízených událostmi** \
  <http://soapatterns.org/design_patterns/event_driven_messaging>

- **Kanál pro publikování a odběr** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Udi Dahan. Vyjasněné CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **CQRS (Command and Query Responsibility Segregation) (CQRS)**  \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Komunikace mezi ohraničenými kontexty** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Konečná konzistence** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy Bogard. Refaktoring směrem k odolnosti: Vyhodnocování spojovacího zařízení** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Předchozí](communication-in-microservice-architecture.md)Další
> [](maintain-microservice-apis.md)
