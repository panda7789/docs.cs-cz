---
title: Komunikace v architektuře mikroslužeb
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Komunikace v architekturách architektura mikroslužeb
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 827d28adda90403d866e7bc13d9eae99fe47c137
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43804104"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikace v architektuře mikroslužeb

V monolitické aplikace běžící v jednom procesu vyvolání komponenty mezi sebou pomocí metody na úrovni jazyka nebo volání funkce. Ty je možné důrazně kombinovat se při vytváření objektů s kódem (například `new ClassName()`), nebo může být vyvolána oddělující způsobem, pokud používáte injektáž závislostí odkazem abstrakcí, nikoli konkrétní objekt instance. V obou případech objekty jsou spuštěné v rámci stejného procesu. Největším problémem při změně z monolitické aplikace do aplikací založených na mikroslužbách spočívá v změna mechanizmus pro komunikaci. Způsobí, že výřečných přímý převod z volání metody v procesu do vzdáleného volání Procedur volání služeb a není efektivní komunikace, která nebude provádět i v distribuovaných prostředích. Navrhování distribuovaných systémů správně obtíže spojené s dostatečně dobře znají, že ještě neexistuje canon označované jako [falešné představy o distribuovaném výpočetním prostředí](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) , který obsahuje seznam předpokladů, které vývojáři často musíte dělat při přesunu z monolitického pro distribuované vzory.

Není jedním z řešení, ale několik. Jedním z řešení zahrnuje izolace co nejvíc obchodní mikroslužeb. Použít asynchronní komunikaci mezi interní mikroslužeb a nahraďte podrobných komunikace, která je typická uvnitř procesu komunikace mezi objekty s hrubší grained komunikace. Můžete to provést seskupením volání a tak, že vrací data, která agreguje výsledky více vnitřní volání do klienta.

Aplikace založená na mikroslužbách je distribuovaný systém běží na několika procesy nebo služby, obvykle i napříč více servery nebo hostitele. Každá instance služby je obvykle proces. Proto služby musí komunikovat pomocí meziprocesové komunikace protokolu HTTP, AMQP nebo binární protokol například TCP, v závislosti na povaze jednotlivých služeb.

Společenství mikroslužeb podporuje filozofie z "[inteligentních koncové body a vlečný kanály](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)." Tato pyramidu může vést ke vzniku návrh, který je oddělený co nejlépe mezi mikroslužbami a tak získá na ucelenosti jako možné v rámci jednoho mikroslužeb. Jak jsme vysvětlili výše, vlastní jednotlivých mikroslužeb svoje vlastní data a vlastní logiky domény. Ale mikroslužeb sestavování začátku do konce aplikace jsou obvykle stačí choreographed pomocí REST komunikace místo složitých protokoly, jako je WS -\* a flexibilní komunikace založená na událostech namísto centralizované obchodní proces orchestrátorů.

Dva běžně používané protokoly jsou žádost/odpověď HTTP s prostředku rozhraní API (při dotazování na většinu všechny) a zjednodušené asynchronní zasílání zpráv při komunikaci aktualizace napříč několika mikroslužeb. Tyto jsou vysvětlené podrobněji v následujících částech.

## <a name="communication-types"></a>Typy komunikace

Klienta a služby můžou komunikovat přes mnoho různých typů komunikace, každý z nich cílí na jiný scénář a cíle. Tyto typy komunikace na začátku může být zařazeno do dvě osy.

První osy je určení, zda je protokol synchronní nebo asynchronní:

-   Synchronní protokol. HTTP je synchronní protokol. Klient odešle požadavek a čeká na odpověď ze služby. Který je nezávislý na provádění kódu klienta, který by mohl být synchronní (vlákno je blokováno), nebo asynchronní (neblokuje vlákna a odpovědi nakonec dosáhne zpětné volání). Důležitý bod je, že je synchronní protokol (HTTP/HTTPS) a klientský kód může pouze pokračovat svých úkolů při přijetí odpovědi HTTP serveru.

-   Asynchronní protokol. Jiné protokoly, jako AMQP (protokol, který podporuje mnoho operační systémy a cloudovými prostředími) pomocí asynchronních zpráv. Klienta kódu nebo zprávy odesílatel obvykle nečeká na odpověď. Právě pošle zprávu jako při odesílání zprávy do fronty RabbitMQ nebo jiné zprostředkovatele zpráv.

Sekundární osy je definování v případě komunikace nemá jednoho příjemce nebo více příjemcům:

-   Jednoho příjemce. Každý požadavek musí být zpracovány přesně jeden příjemce nebo službou. Je například tato komunikace [příkaz vzor](https://en.wikipedia.org/wiki/Command_pattern).

-   Několik příjemců. Každý požadavek může být zpracována nula více příjemcům. Tento typ komunikace musí být asynchronní. Příkladem je [publikování/odběr](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mechanismus použít v vzorů, jako jsou [architektury řízené událostmi](https://microservices.io/patterns/data/event-driven-architecture.html). To je založené na zprostředkovatele rozhraní nebo zprávy sběrnice událostí při šíření aktualizací dat mezi různými mikroslužbami prostřednictvím události. Obvykle je implementováno prostřednictvím služby Service bus nebo podobné artefaktů, jako je [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) pomocí [témata a odběry](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikace založené na mikroslužbách často používat kombinaci tyto styly komunikace. Nejběžnějším typem je jeden příjemce komunikaci s synchronní protokol například HTTP/HTTPS při vyvolání regulární služby webového rozhraní API HTTP. Mikroslužby také běžně používat protokoly zasílání zpráv pro asynchronní komunikace mezi mikroslužbami.

Tyto osy je dobré vědět, takže máte přehlednost na možné komunikačních mechanizmů, ale nejsou důležité aspekty při sestavování mikroslužeb. Asynchronní povaze klienta, spouštění vláken ani asynchronní povaze vybraného protokolu jsou důležité body při integraci mikroslužeb. Co *je* důležité je třeba možnost integrovat mikroslužby asynchronně při zachování nezávislost mikroslužeb, jak je vysvětleno v následující části.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Integrace asynchronní mikroslužeb vynucuje autonomie mikroslužeb.

Jak už bylo zmíněno, je důležité při sestavování aplikací založených na mikroslužbách tak, jak integrovat mikroslužby. V ideálním případě by se pokuste minimalizovat komunikaci mezi interní mikroslužeb. Méně komunikace mezi mikroslužbami, tím lépe. Můžete ale samozřejmě v mnoha případech budete muset nějakým způsobem integrovat mikroslužby. Když budete potřebovat k tomu, kritické pravidlo je, že by měl být asynchronní komunikaci mezi mikroslužby. To neznamená, že je nutné použít určitý protokol (například asynchronní zasílání zpráv a synchronní HTTP). Znamená pouze to, že komunikace mezi mikroslužbami by mělo být provedeno pouze pomocí šíření data asynchronně, ale nepokusí závisí na jiné interní mikroslužeb jako součást operace požadavku/odpovědi HTTP počáteční služby.

Pokud je to možné, nikdy závisí na synchronní komunikace (žádostí a odpovědí) mezi několika mikroslužeb, dokonce ani pro dotazy. Cílem jednotlivých mikroslužeb je možné autonomní a příjemci klienta k dispozici i v případě ostatních služeb, které jsou součástí aplikace začátku do konce se dolů nebo není v pořádku. Pokud se domníváte, že budete muset provést volání z jednoho mikroslužeb na jiné mikroslužby (například provedení požadavku HTTP pro dotaz na data) v pořadí bude schopen poskytnout odpověď do klientské aplikace, máte architekturu, která nesmí být odolné, až se některé mikroslužby nezdaří.

Kromě toho mají závislosti protokolu HTTP mezi mikroslužeb, jako je při vytváření dlouhé cykly žádost/odpověď s protokolem HTTP požadavku řetězců, jak je znázorněno v první části z 15-obrázek 4, nejen umožňuje mikroslužby není autonomní ale je také jejich výkon vliv jako jedna ze služeb v tomto řetězci není dobře funguje. 

Tím přidáte synchronní závislosti mezi mikroslužeb, jako je například požadavků na dotazy, tím horší získá celková doba odezvy pro klientské aplikace.

![](./media/image15.png)

**Obrázek 4 – 15**. Antimodely a vzory v komunikace mezi mikroslužbami

Pokud vaše mikroslužeb je potřeba vyvolat další akce v jiném mikroslužeb, pokud je to možné, neprovádějte tuto akci synchronně a jako součást původní operace dotazů a odpovědí mikroslužeb. Místo toho proveďte asynchronně (pomocí asynchronního zasílání zpráv nebo integrace událostí, front, atd.). Ale co nejvíce, Ne akci vyvolat synchronně jako součást původní synchronní operace dotazů a odpovědí.

A nakonec (a to je, ve kterém vznikají většinu problémů při vytváření mikroslužeb), pokud vaše počáteční mikroslužeb potřebuje data, která původně vlastní jiné mikroslužeb, nespoléhejte na to, jak synchronní žádosti pro tato data. Místo toho replikovat nebo rozšíří tato data (pouze atributy, které potřebujete) do databáze služby počáteční pomocí konečnou konzistenci (obvykle události integrace, jak je vysvětleno v nadcházejících částech).

Jak je uvedeno výše v části [identifikace hranic mezi modelem a doménou u jednotlivých mikroslužeb](#identifying-domain-model-boundaries-for-each-microservice), duplikování některá data napříč několika mikroslužeb není nesprávná návrhu – naopak, když to, které jsou dobře převeditelné data do konkrétního jazyka nebo podmínky další domény nebo ohraničená kontextu. Například v [aplikaci eShopOnContainers](https://aka.ms/MicroservicesArchitecture) aplikace máte mikroslužby s názvem identity.api, který má na starosti většinu dat uživatele s entitou pojmenovaného uživatele. Ale když budete potřebovat k uložení dat uživatele v rámci řazení mikroslužeb, uložíte ho jako jinou entitu s názvem odběratele. Kupující sdílí stejnou identitu s původní entita uživatele, ale může mít pouze několik atributů, které jsou potřeba pro řazení domény a ne celý uživatelský profil.

Můžete použít libovolný protokol pro komunikaci a rozšíří data asynchronně do mikroslužeb abyste měli konečné konzistence. Jak už bylo zmíněno, můžete použít události integrace pomocí sběrnice událostí nebo zprávy zprostředkovatele nebo můžete dokonce může používat protokol HTTP pomocí cyklického dotazování ostatním službám místo. Nezáleží. Je důležité pravidlo tak, aby nevytvářela synchronní závislosti mezi mikroslužby.

Následující části popisují různé styly komunikace můžete zvážit použití v aplikacích založených na mikroslužbách.

## <a name="communication-styles"></a>Styly komunikace

Existuje mnoho protokolů a volby, které můžete použít pro komunikaci, v závislosti na typu komunikaci, kterou chcete použít. Pokud používáte synchronní založené na požadavku/odpovědi komunikační mechanizmus, protokoly, například HTTP a ZBÝVAJÍCÍ přístupy jsou nejčastější, zejména v případě, že publikujete služby mimo cluster mikroslužeb nebo hostitele Dockeru. Pokud je komunikace mezi službami interně (v rámci hostitele nebo mikroslužeb cluster Dockeru) můžete také použít binární formát komunikačních mechanizmů (např. Vzdálená komunikace Service Fabric nebo WCF pomocí protokolu TCP a binární formát). Alternativně můžete použít asynchronní komunikaci založenou na zprávách mechanismy, jako je například AMQP.

Existují také více formáty zpráv, jako je JSON nebo XML, nebo dokonce binární formáty, které může být efektivnější. Pokud váš zvolený binárním formátu není standard, není pravděpodobně vhodné veřejně publikování vašich služeb pomocí tohoto formátu. Můžete použít nestandardní formát pro interní komunikaci mezi mikroslužby. Můžete tak učinit při komunikaci mezi mikroslužbami v Dockeru hostitele nebo mikroslužeb clusteru (orchestrátorů Dockeru nebo Azure Service Fabric) nebo pro vlastní klientské aplikace, které komunikují se mikroslužby.

### <a name="requestresponse-communication-with-http-and-rest"></a>Žádost/odpověď komunikaci přes protokol HTTP a REST 

Pokud klient používá komunikaci žádostí a odpovědí, odešle požadavek do služby, potom procesy služby požadavku a zašle zpět odpověď. Žádost/odpověď komunikace je zvlášť vhodná pro dotazování dat v reálném čase uživatelského rozhraní (živé uživatelského rozhraní) z klientských aplikací. Proto v architektuře mikroslužeb pravděpodobně použijete tento komunikační mechanizmus pro většinu dotazů, jak ukazuje obrázek 4-16.

![](./media/image16.png)

**Obrázek 4 – 16**. Pomocí komunikaci pomocí protokolu HTTP požadavku nebo odpovědi (synchronní nebo asynchronní)

Pokud klient používá komunikaci žádost odpověď, předpokládá, že odpovědi budou doručeny v krátkém čase, obvykle menší než druhý nebo pár sekund nejvíce. Zpožděné odpovědí, budete muset implementovat asynchronní komunikaci na základě [způsobů zasílání zpráv](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) a [zasílání zpráv technologie](https://en.wikipedia.org/wiki/Message-oriented_middleware), což je jiný přístup, který vám vysvětlíme v další části.

Oblíbeným stylem architektury pro komunikaci požadavku nebo odpovědi je [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Tento přístup je založena na a úzce spjat s, [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protokol, příkazy HTTP, jako jsou GET, POST, středu a vložit. REST je nejčastěji používaná přístupem architektury komunikace při vytváření služby. Při vývoji služby webového rozhraní API ASP.NET Core můžete implementovat služby REST.

Při použití jako jazyk definice rozhraní HTTP REST služby je další hodnota. Například pokud používáte [Swagger metadata](https://swagger.io/) popisu rozhraní API služby, můžete použít nástroje, které vygenerovat provizorní kódy klienta, které můžete přímo objevovat a používat vaše služby.

### <a name="additional-resources"></a>Další zdroje

-   **Martina Fowlera. Model vyspělosti Richardson.** Popis modelu REST.
    [*https://martinfowler.com/articles/richardsonMaturityModel.html*](https://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger.** Oficiální web.
    [*https://swagger.io/*](https://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>Nabízená oznámení a komunikaci v reálném čase, které jsou založené na protokolu HTTP

Další možností (obvykle pro jiné účely než REST), jako je v reálném čase a jeden mnoho komunikaci s vyšší úrovně rozhraní [funkce SignalR technologie ASP.NET](https://www.asp.net/signalr) a protokoly, jako například [objekty Websocket](https://en.wikipedia.org/wiki/WebSocket).

Jak ukazuje obrázek 4-17 v reálném čase komunikaci pomocí protokolu HTTP znamená, že můžete mít kód serveru doručením (push) obsah připojeným klientům jak budou data k dispozici, namísto nutnosti čekat klient k vyžádání nových dat serveru.

![](./media/image17.png)

**Obrázek 4-17**. 1: 1 zpráv v reálném čase asynchronní komunikace

Protože je komunikace v reálném čase, se změny zobrazily klientských aplikací téměř okamžitě. To je obvykle zajišťuje protokol, jako je například objekty Websocket, použijete mnoho připojení objekty Websocket (jeden do každého klienta). Typickým příkladem je, když služba komunikuje změna skóre sportovní hra pro mnoho klientských webových aplikací současně.


>[!div class="step-by-step"]
[Předchozí](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
[další](asynchronous-message-based-communication.md)
