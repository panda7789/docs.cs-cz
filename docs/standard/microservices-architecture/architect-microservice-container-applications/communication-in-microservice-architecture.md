---
title: Komunikace v architektury mikroslužby
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Komunikace v architektura architektury mikroslužby
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: f0e0e63c6ce2e4699cc4f9c0bd0d120549b88cca
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106009"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikace v architektury mikroslužby

V monolitický aplikace běžící v jednom procesu vyvolají komponenty navzájem pomocí metody úroveň jazyka nebo volání funkce. To může být silného spojen při vytváření objektů s kódem (například `new ClassName()`), nebo můžete vyvolat odpojeného způsobem, pokud používáte vkládání závislostí odkazem abstrakce, nikoli konkrétní objekt instancí. V obou případech objekty jsou spuštěny v rámci stejného procesu. Největší výzvou při změně z monolitický aplikace k aplikaci na základě mikroslužeb spočívá v změna komunikační mechanizmus. Přímé převod z volání metod v procesu do volání vzdáleného volání Procedur služby způsobí, že chatty a není efektivní komunikaci, která nebude provádět i v distribuovaných prostředích. Obtíže spojené s navrhování distribuovaného systému správně jsou dostatečně dobře známé se i canon, označuje jako [Fallacies distribuovaných počítačů](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) , uvádí předpoklady, které vývojáři často při přesouvání z monolitický pro distribuované návrhů.

Není jedno řešení, ale některé. Jedno řešení zahrnuje izolace co nejvíce obchodní mikroslužeb. Potom použít asynchronní komunikaci mezi interní mikroslužeb a nahraďte podrobných komunikaci, která je typické v komunikaci mezi objekty s hrubší podrobných komunikace uvnitř procesy. To můžete udělat, tím, že volání a vrácením data, která agreguje výsledky více interní volání do klienta.

Aplikace založené na mikroslužeb na je distribuovaný systém systémem více procesů nebo služeb, obvykle to i v rámci více serverů nebo hostitele. Každá instance služby je obvykle proces. Proto služby musí komunikovat pomocí protokol komunikaci mezi procesy, jako je například HTTP, AMQP nebo binární protokol například TCP, v závislosti na povaze jednotlivých služeb.

Mikroslužbu Společenství podporuje filosofie z "[inteligentní koncových bodů a vlečný kanály](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)." Jedná o tento reklamní umožňuje návrh, který je jako odpojené možném mezi mikroslužeb a jako získá na ucelenosti nejblíže v rámci jedné mikroslužby. Jak je popsáno výše, každý mikroslužbu vlastní svá vlastní data a vlastní logiku domény. Ale mikroslužeb skládání začátku do konce aplikace jsou obvykle jednoduše choreographed pomocí komunikaci REST místo komplexní protokoly, jako je například WS -\* a centralizované flexibilní komunikace místo založeného na událostech obchodní proces orchestrators.

Dva běžně používané protokoly jsou požadavek/odpověď HTTP s prostředkem rozhraní API (při dotazování většinu všech) a lightweight asynchronní zasílání zpráv při komunikaci aktualizace napříč více mikroslužeb. Tyto jsou vysvětlené podrobněji v následujících částech.

## <a name="communication-types"></a>Typy komunikace

Klienta a služby mohou komunikovat prostřednictvím různých typech komunikace, každé z nich cílené na jiný scénář a cíle. Tyto typy komunikace původně, můžou být klasifikované v dvěma osami.

První osa je definování, pokud je protokol synchronní nebo asynchronní:

-   Synchronní protokol. HTTP je synchronní protokol. Klient odešle požadavek a čeká na odpověď ze služby. Která je nezávislá provádění kódu klienta, které by mohly být synchronní (vlákno je blokované) nebo asynchronní (vlákno není blokované a odpovědi bude nakonec dosáhnout zpětné volání). Zde důležité je, že protokol (HTTP nebo HTTPS), je synchronní a kód klienta můžete jenom pokračovat úkolu, když obdrží odpověď HTTP serveru.

-   Asynchronní protokol. Asynchronní zprávy používají jiné protokoly, jako je AMQP (protokol, který podporuje mnoho operačních systémů a prostředí cloudu). Odesílatel kódu nebo zprávy klienta obvykle není čekat na odpověď. Právě odešle zprávu jako při odesílání zprávy do fronty RabbitMQ nebo jiné zprostředkovatele zpráv.

Druhý osy je definování komunikace má jednoho příjemce nebo několika příjemců:

-   Jednoho příjemce. Každý požadavek musí být zpracovává přesně jeden příjemce nebo službu. Je například tato komunikace [příkaz vzor](https://en.wikipedia.org/wiki/Command_pattern).

-   Několika příjemců. Každý požadavek může zpracovat nula do několika příjemců. Tento typ komunikace musí být asynchronní. Příkladem je [publikování a přihlášení k odběru](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mechanismus používaný v vypadají podobně jako [událostmi řízené architektura](https://microservices.io/patterns/data/event-driven-architecture.html). To je založené na zprostředkovatele rozhraní nebo zprávy událostí bus při šíření aktualizace dat mezi několika mikroslužeb prostřednictvím událostí; Obvykle se implementuje prostřednictvím sběrnice nebo podobné artefaktů jako [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) pomocí [témat a odběrů](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikace založené na mikroslužbu na se často používají kombinaci těchto styly komunikace. Nejběžnějším typem je jeden příjemce komunikace s synchronní protokol například HTTP nebo HTTPS, při vyvolání regulární služby webového rozhraní API HTTP. Mikroslužeb také běžně používají protokoly zasílání zpráv pro asynchronní komunikaci mezi mikroslužeb.

Tyto osy je dobré vědět, takže máte přehlednost na možné komunikační mechanizmy, ale nejsou důležité aspekty při sestavování mikroslužeb. Ani asynchronní povaha provádění vlákna klienta ani asynchronní povaha vybraného protokolu jsou důležité body při integraci mikroslužeb. Co *je* důležité je třeba možnost integrovat vaši mikroslužeb asynchronně při zachování nezávislost mikroslužeb, jak je popsáno v následující části.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Asynchronní mikroslužbu integrace vynucuje nezávislé na mikroslužbu

Jak je uvedeno, důležité při vytváření aplikace založenou na mikroslužeb je způsob, jak integrovat váš mikroslužeb. V ideálním případě by se pokuste minimalizovat komunikace mezi interní mikroslužeb. Menší komunikace mezi mikroslužeb, tím lépe. Můžete ale samozřejmě v mnoha případech je nutné k nějakým způsobem integraci mikroslužeb. Když potřebujete udělat, kritické pravidlo je, že by měla být asynchronní komunikaci mezi mikroslužeb. To neznamená, že budete muset použít konkrétní protokol (například asynchronní zasílání zpráv a synchronní HTTP). Ji právě znamená, že by mělo být provedeno pouze pomocí šíření data asynchronně komunikace mezi mikroslužeb, ale nepokusí závisí na jiné interní mikroslužeb jako součást počáteční službu operace požadavků a odpovědí HTTP.

Pokud je to možné se nikdy závisí na synchronní komunikace (požadavků a odpovědí) mezi více mikroslužeb, ani pro dotazy. Cílem každé mikroslužbu je jako autonomní a dostupné k příjemce klienta, i v případě ostatních služeb, které jsou součástí aplikace začátku do konce neběží nebo není v pořádku. Pokud se domníváte, že budete muset udělat volání z jednoho mikroslužbu jiné mikroslužeb (např. provádění požadavku HTTP pro dotaz na data) v pořadí, abyste mohli zadat odpovědi na klientskou aplikaci, je třeba architekturu, která nebude odolné, pokud některé mikroslužeb nezdaří.

Kromě toho s HTTP závislosti mezi mikroslužeb, jako při vytváření dlouhé cykly žádosti a odpovědi s protokolem HTTP žádosti o řetězcích, jak je znázorněno v první části z 15-obrázek 4, ne jenom vaše mikroslužeb není autonomního se ale je také jejich výkonu dopad na co nejrychleji a jedné ze služeb v tomto řetězci neprovádí. 

Čím víc přidat synchronní závislosti mezi mikroslužeb, například požadavky na dotaz, zhoršení získá celková doba odezvy pro klientské aplikace.

![](./media/image15.png)

**Obrázek 4 až 15**. Proti vzory a vzory komunikace mezi mikroslužeb

Pokud vaše mikroslužbu potřebuje vyvolat další akce v jiné mikroslužbu, pokud je to možné, není provedení této akce synchronně a v rámci původní operace dotazů a odpovědí mikroslužby. Místo toho provést asynchronně (pomocí asynchronní zasílání zpráv nebo události integrace, fronty, atd.). Ale v maximální míře, nevolejte akce synchronně jako součást původní synchronní operace dotazů a odpovědí.

A nakonec (a to je, kde Většina problémů nastat při sestavování mikroslužeb), pokud vaše počáteční mikroslužbu potřebuje data, která je původně vlastníkem jiných mikroslužeb, nespoléhejte na provedení synchronní požadavky na data. Místo toho replikovat nebo rozšíření dat (pouze atributy, které potřebujete) do databáze počáteční služby pomocí konzistence typu případné (obvykle pomocí události integrace, jak je popsáno v části nadcházející).

Jak jsme uvedli dříve v části [identifikace modelu domény hranice pro každou mikroslužbu](#identifying-domain-model-boundaries-for-each-microservice), duplikování některá data mezi několik mikroslužeb není nesprávný návrhu – naopak, pokud to, které může překládat data do konkrétní jazyk nebo podmínky této další domény nebo ohraničenou kontextu. Například v [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) aplikací mít mikroslužbu, s názvem identity.api, který má na starosti většinu dat uživatele s entitou, pojmenovaného uživatele. Ale pokud budete potřebovat k ukládání dat o uživateli v rámci mikroslužbu řazení, můžete ho uložit jako jiné entity s názvem kupujících. Entity kupujících sdílí stejnou identitu původního uživatele entity, ale může mít pouze několik atributů, které jsou potřeba domény řazení a ne celou uživatelský profil.

Můžete použít libovolný protokol pro komunikaci a asynchronně rozšíří data na mikroslužeb aby bylo možné používat konzistence typu případné. Jak už bylo zmíněno, můžete použít integrace událostí pomocí sběrnice událostí nebo zpráva, že zprostředkovatel nebo i mohl použít HTTP pomocí cyklického dotazování služby jiné místo. Nezáleží. Je důležité pravidlo tak, aby nevytvářela synchronní závislosti mezi vaší mikroslužeb.

Následující části popisují různé styly komunikace můžete zvážit použití v aplikaci na základě mikroslužby.

## <a name="communication-styles"></a>Styly komunikace

Existuje mnoho protokoly a možnosti, které můžete použít pro komunikaci, v závislosti na typu komunikace, kterou chcete použít. Pokud používáte mechanismus synchronní založené na požadavku nebo odpovědi komunikace, jsou protokoly, například HTTP a REST přístupy nejběžnější, zvlášť pokud publikujete vašim službám mimo cluster hostitele nebo mikroslužbu Docker. Pokud jsou komunikaci mezi službami interně (v rámci hostitele nebo mikroslužeb clusteru Docker) můžete také použít binární formát komunikační mechanizmy (jako je vzdálené komunikace Service Fabric nebo WCF pomocí TCP a binární formát). Alternativně můžete použít asynchronní, na základě zpráv komunikace mechanismy, například AMQP.

Existují také více formáty zpráv jako XML nebo JSON nebo i binární formáty, které může být efektivnější. Pokud vaše zvolené binární formát není standard, je pravděpodobně není vhodné veřejně publikovat vašim službám pomocí tohoto formátu. Můžete použít jinou než standardní formát pro interní komunikaci mezi vaší mikroslužeb. Můžete to třeba udělat při komunikaci mezi mikroslužeb v rámci Docker hostitele nebo mikroslužbu clusteru (Docker orchestrators nebo Azure Service Fabric) nebo pro vlastní klientských aplikací, které komunikují s mikroslužeb.

### <a name="requestresponse-communication-with-http-and-rest"></a>Požadavek a odpověď komunikaci přes protokol HTTP a REST 

Pokud klient používá komunikaci požadavků a odpovědí, odešle žádost o služby, potom zpracuje služba žádost a odešle odpověď zpět. Komunikace požadavek a odpověď je velmi dobře vhodné pro dotazování dat v reálném čase uživatelského rozhraní (za provozu uživatelské rozhraní) z klientské aplikace. Proto v architektury mikroslužby pravděpodobně použijete tento komunikační mechanizmus pro většinu dotazů, jak ukazuje obrázek 4-16.

![](./media/image16.png)

**Obrázek 4-16**. Pomocí požadavků a odpovědí komunikaci pomocí protokolu HTTP (synchronní nebo asynchronní)

Pokud klient používá komunikaci požadavek a odpověď, předpokládá, že odpověď budou doručeny v krátkém čase, obvykle menší než druhý nebo pár sekund nejvíce. Pro zpožděné odpovědi, potřebujete implementovat asynchronní komunikaci na základě [zasílání zpráv vzory](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) a [zasílání zpráv technologie](https://en.wikipedia.org/wiki/Message-oriented_middleware), který je jiný přístup, který vám vysvětlíme v další části.

Populární architektury styl pro komunikaci požadavek a odpověď je [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Tento přístup je založena na a úzce kombinovanou, [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protokolu, příkaz HTTP jako GET, POST, přijetí a PUT. Při vytváření služby REST je nejčastěji používané přístup architektury komunikace. Při vývoji webové rozhraní API ASP.NET Core services můžete implementovat služby REST.

Při použití služeb HTTP REST jazyka definice rozhraní je další hodnota. Například pokud použijete [Swagger metadata](https://swagger.io/) Pokud chcete popisují vaše rozhraní API služby, můžete použít nástroje, které generování zástupných procedur klienta, které můžete přímo zjištění a použití vašich služeb.

### <a name="additional-resources"></a>Další zdroje

-   **Martin Fowler. Ryšánková vyspělosti modelu.** Popis modelu REST.
    [*https://martinfowler.com/articles/richardsonMaturityModel.html*](https://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger.** Oficiální web.
    [*https://swagger.io/*](https://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>Nabízení a komunikaci v reálném čase, které jsou založené na protokolu HTTP

Další možností (obvykle pro jiné účely než REST) je v reálném čase a na více komunikace s vyšší úrovně rozhraní, jako například [ASP.NET SignalR](https://www.asp.net/signalr) a protokoly, jako [Websocket](https://en.wikipedia.org/wiki/WebSocket).

Jak ukazuje obrázek 4-17, v reálném čase komunikaci pomocí protokolu HTTP znamená, že můžete mít kódu serveru nabízet obsah připojeným klientům, jakmile data k dispozici, místo aby se server čekat na klienta k žádosti o nová data.

![](./media/image17.png)

**Obrázek 4-17**. 1: 1 zpráv v reálném čase asynchronní komunikaci

Vzhledem k tomu, že komunikace je v reálném čase, klientské aplikace zobrazit změny prakticky okamžitě. To je obvykle provádí protokol třeba Websocket pomocí mnoha připojení Websocket (jeden na každého klienta). Typickým příkladem je, když služba komunikuje změnu skóre sportu hry s mnoha klienta webových aplikací současně.


>[!div class="step-by-step"]
[Předchozí](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
[další](asynchronous-message-based-communication.md)
