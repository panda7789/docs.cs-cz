---
title: Komunikace v architektuře mikroslužeb
description: Prozkoumejte různé způsoby komunikace mezi mikroslužbami a seznamte se s důsledky synchronních a asynchronních způsobů.
ms.date: 01/30/2020
ms.openlocfilehash: f2d6e78966bb7d5f481de6db0ab1dcfe2812a1b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401653"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikace v architektuře mikroslužeb

V monolitické aplikaci spuštěné v jednom procesu se komponenty vzájemně vyvolávají pomocí metody nebo volání funkcí na úrovni jazyka. Ty mohou být silně spojeny, pokud vytváříte objekty `new ClassName()`s kódem (například ), nebo mohou být vyvolány odděleným způsobem, pokud používáte vkládání závislostí odkazováním na abstrakce spíše než na konkrétní instance objektů. V obou směrech jsou objekty spuštěny ve stejném procesu. Největší výzvou při přechodu z monolitické aplikace na aplikaci založenou na mikroslužbách spočívá ve změně komunikačního mechanismu. Přímý převod z volání metody v procesu do volání Vzdáleného volání na služby způsobí upovídaný a neefektivní komunikaci, která nebude fungovat dobře v distribuovaných prostředích. Výzvy navrhování distribuovaného systému správně jsou dostatečně dobře známé, že existuje i kánek známý jako [Fallacies distribuovaných výpočetních počítačů,](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) který uvádí předpoklady, které vývojáři často dělají při přechodu z monolitických na distribuované návrhy.

Neexistuje jedno řešení, ale několik. Jedno řešení zahrnuje izolaci obchodní mikroslužeb co nejvíce. Potom použijte asynchronní komunikaci mezi interní mikroslužeb a nahradit jemně odstupňované komunikace, která je typická v intraprocesové komunikace mezi objekty s hrubší odstupňované komunikace. Můžete to provést seskupením volání a vrácením dat, která agreguje výsledky více interních volání, klientovi.

Aplikace založená na mikroslužbách je distribuovaný systém spuštěný na více procesech nebo službách, obvykle i na více serverech nebo hostitelích. Každá instance služby je obvykle proces. Proto musí služby komunikovat pomocí meziprocesového komunikačního protokolu, jako je HTTP, AMQP nebo binární protokol, jako je TCP, v závislosti na povaze každé služby.

Komunita mikroslužeb podporuje filozofii "[inteligentní koncové body a hloupé kanály](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" Tento slogan podporuje návrh, který je co nejvíce oddělené mezi mikroslužeb a co nejsoudržnější v rámci jedné mikroslužby. Jak bylo vysvětleno dříve, každá mikroslužba vlastní vlastní data a vlastní logiku domény. Ale mikroslužeb, které tvoří end-to-end aplikace jsou obvykle jednoduše choreografie pomocí rest\* komunikace spíše než složité protokoly, jako je ws a flexibilní komunikace řízené událostmi namísto centralizovaných orchestrátorů obchodního procesu.

Dva běžně používané protokoly jsou požadavek/odpověď HTTP s api prostředků (při dotazování ze všeho nejvíce) a zjednodušené asynchronní zasílání zpráv při komunikaci aktualizací napříč více mikroslužeb. Ty jsou podrobněji vysvětleny v následujících částech.

## <a name="communication-types"></a>Typy komunikace

Klient a služby mohou komunikovat prostřednictvím mnoha různých typů komunikace, z nichž každý cílí na jiný scénář a cíle. Zpočátku mohou být tyto typy komunikace klasifikovány ve dvou osách.

První osa definuje, zda je protokol synchronní nebo asynchronní:

- Synchronní protokol. HTTP je synchronní protokol. Klient odešle požadavek a čeká na odpověď ze služby. To je nezávislé na spuštění kódu klienta, který může být synchronní (vlákno je blokováno) nebo asynchronní (vlákno není blokováno a odpověď nakonec dosáhne zpětného volání). Důležitým bodem je, že protokol (HTTP/HTTPS) je synchronní a klientský kód může pokračovat ve své úloze pouze v případě, že obdrží odpověď serveru HTTP.

- Asynchronní protokol. Jiné protokoly, jako je AMQP (protokol podporovaný mnoha operačními systémy a cloudovými prostředími) používají asynchronní zprávy. Klientský kód nebo odesílatel zprávy obvykle nečeká na odpověď. To jen odešle zprávu jako při odesílání zprávy do fronty RabbitMQ nebo jiné zprávy broker.

Druhá osa definuje, zda má komunikace jeden přijímač nebo více přijímačů:

- Jeden přijímač. Každý požadavek musí být zpracován přesně jedním příjemcem nebo službou. Příkladem této komunikace je [vzor příkazu](https://en.wikipedia.org/wiki/Command_pattern).

- Více přijímačů. Každý požadavek může být zpracován nulou na více přijímačů. Tento typ komunikace musí být asynchronní. Příkladem je mechanismus [publikování/odběru](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) používaný ve vzorcích, jako je [architektura řízená událostmi](https://microservices.io/patterns/data/event-driven-architecture.html). To je založeno na rozhraní event-bus nebo zprostředkovatele zpráv při šíření aktualizací dat mezi více mikroslužeb prostřednictvím událostí; obvykle se implementuje prostřednictvím sběrnice service bus nebo podobné artefakty, jako je [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) pomocí témat a [předplatných](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikace založená na mikroslužbách často používá kombinaci těchto stylů komunikace. Nejběžnějším typem je komunikace s jedním přijímačem se synchronním protokolem, jako je HTTP/HTTPS při vyvolání běžné služby HTTP webového rozhraní API. Mikroslužby také obvykle používají protokoly zasílání zpráv pro asynchronní komunikaci mezi mikroslužbami.

Tyto osy jsou dobré vědět, takže máte jasno na možné komunikační mechanismy, ale nejsou důležité obavy při vytváření mikroslužeb. Asynchronní povaha spuštění vlákna klienta ani asynchronní povaha vybraného protokolu nejsou důležitými body při integraci mikroslužeb. Co *je* důležité, je možnost integrovat mikroslužeb asynchronně při zachování nezávislosti mikroslužeb, jak je vysvětleno v následující části.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Asynchronní integrace mikroslužeb vynucuje autonomii mikroslužeb

Jak již bylo zmíněno, důležitým bodem při vytváření aplikace založené na mikroslužbách je způsob, jakým integrovat mikroslužeb. V ideálním případě byste se měli pokusit minimalizovat komunikaci mezi interní mikroslužeb. Čím méně komunikace mezi mikroslužbami, tím lépe. Ale v mnoha případech budete muset nějak integrovat mikroslužeb. Když to potřebujete udělat, kritické pravidlo je, že komunikace mezi mikroslužeb by měla být asynchronní. To neznamená, že budete muset použít konkrétní protokol (například asynchronní zasílání zpráv versus synchronní HTTP). To jen znamená, že komunikace mezi mikroslužeb by měla být provedena pouze šíření dat asynchronně, ale snažte se nezávisí na jiné interní mikroslužeb jako součást počáteční služby http požadavek/odpověď operace.

Pokud je to možné, nikdy nezávisí na synchronní komunikaci (požadavek/odpověď) mezi více mikroslužeb, ani pro dotazy. Cílem každé mikroslužby je být autonomní a k dispozici pro klienta spotřebitele, i v případě, že ostatní služby, které jsou součástí aplikace end-to-end jsou mimo nebo není v pořádku. Pokud si myslíte, že potřebujete volat z jedné mikroslužby do jiných mikroslužeb (jako je provádění požadavku HTTP pro datový dotaz), abyste mohli poskytnout odpověď na klientskou aplikaci, máte architekturu, která nebude odolná, když některé mikroslužby selžou.

Navíc s http závislosti mezi mikroslužeb, jako při vytváření dlouhé cykly požadavků a odpovědí s řetězci požadavků HTTP, jak je znázorněno v první části obrázku 4-15, nejen dělá vaše mikroslužby není autonomní, ale také jejich výkon je ovlivněna, jakmile jedna ze služeb v tomto řetězci nefunguje dobře.

Čím více přidáte synchronní závislosti mezi mikroslužeb, jako jsou požadavky na dotazy, tím horší je celková doba odezvy pro klientské aplikace.

![Diagram znázorňující tři typy komunikace mezi mikroslužbami.](./media/communication-in-microservice-architecture/sync-vs-async-patterns-across-microservices.png)

**Obrázek 4-15**. Anti-patterns a vzory v komunikaci mezi mikroslužbami

Jak je znázorněno na výše uvedeném diagramu, v synchronní komunikaci je vytvořen "řetězec" požadavků mezi mikroslužbami při poskytování požadavku klienta. Tohle je anti-vzor. V asynchronní komunikace mikroslužeb použít asynchronní zprávy nebo http dotazování ke komunikaci s jinými mikroslužeb, ale požadavek klienta je obsluhována ihned.

Pokud vaše mikroslužby potřebuje vyvolat další akci v jiné mikroslužby, pokud je to možné, neprovádějte tuto akci synchronně a jako součást původní mikroslužeb požadavku a odpovědi operace. Místo toho to asynchronně (pomocí asynchronní zasílání zpráv nebo integrační události, fronty, atd.). Ale co nejvíce nevyvolávejte akci synchronně jako součást původní synchronní operace požadavku a odpovědi.

A nakonec (a to je místo, kde většina problémů vznikají při vytváření mikroslužeb), pokud počáteční mikroslužeb potřebuje data, která je původně vlastněna jinými mikroslužbami, nespoléhejte na provádění synchronních požadavků pro tato data. Místo toho replikujte nebo rozšíříte tato data (pouze atributy, které potřebujete) do databáze počáteční služby pomocí konečné konzistence (obvykle pomocí událostí integrace, jak je vysvětleno v nadcházejících částech).

Jak je uvedeno dříve v identifikaci hranice modelu domény pro každou část [mikroslužeb,](identify-microservice-domain-model-boundaries.md) duplikování některých dat v několika mikroslužeb není nesprávný návrh – naopak, když to uděláte, že můžete přeložit data do konkrétního jazyka nebo podmínky této další domény nebo ohraničený kontext. Například v [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) máte mikroslužbu s názvem, `identity-api` která má na starosti většinu `User`dat uživatele s entitou s názvem . Však v případě, že potřebujete ukládat data o uživateli v rámci `Ordering` mikroslužby, uložíte je jako jinou entitu s názvem `Buyer`. Entita `Buyer` sdílí stejnou identitu `User` s původní entitou, ale může `Ordering` mít pouze několik atributů potřebných pro doménu a ne celý profil uživatele.

Můžete použít libovolný protokol ke komunikaci a šíření dat asynchronně mezi mikroslužeb, aby měly konečnou konzistenci. Jak již bylo zmíněno, můžete použít události integrace pomocí sběrnice událostí nebo zprostředkovatele zpráv nebo můžete dokonce použít protokol HTTP dotazováním jiných služeb. Nezáleží. Důležitým pravidlem je nevytvářet synchronní závislosti mezi mikroslužbami.

V následujících částech je vysvětleno více stylů komunikace, které můžete zvážit použití v aplikaci založené na mikroslužbách.

## <a name="communication-styles"></a>Styly komunikace

Existuje mnoho protokolů a možností, které můžete použít pro komunikaci, v závislosti na typu komunikace, který chcete použít. Pokud používáte synchronní mechanismus komunikace založené na požadavcích a odpovědích, jsou nejběžnější protokoly, jako jsou přístupy HTTP a REST, zejména pokud publikujete služby mimo hostitelský nebo cluster mikroslužeb Dockeru. Pokud komunikujete interně mezi službami (v rámci vašeho hostitele Dockeru nebo clusteru mikroslužeb), můžete také chtít použít mechanismy komunikace binárního formátu (jako je WCF pomocí TCP a binárního formátu). Alternativně můžete použít asynchronní, na základě zpráv komunikační mechanismy, jako je například AMQP.

Existuje také více formátů zpráv, jako je JSON nebo XML, nebo dokonce binární formáty, které mohou být efektivnější. Pokud zvolený binární formát není standardem, pravděpodobně není vhodné veřejně publikovat služby pomocí tohoto formátu. Pro interní komunikaci mezi mikroslužbami můžete použít nestandardní formát. Můžete to provést při komunikaci mezi mikroslužeb v rámci hostitele Dockeru nebo clusteru mikroslužeb (například orchestrátory Dockeru) nebo pro proprietární klientské aplikace, které komunikují s mikroslužbami.

### <a name="requestresponse-communication-with-http-and-rest"></a>Komunikace mezi požadavky a odpověďmi s HTTP a REST

Když klient používá komunikaci požadavku a odpovědi, odešle požadavek službě, pak služba zpracuje požadavek a odešle zpět odpověď. Komunikace mezi požadavky a odpověďmi je obzvláště vhodná pro dotazování dat pro uživatelské rozhraní v reálném čase (živé uživatelské rozhraní) z klientských aplikací. Proto v architektuře mikroslužeb budete pravděpodobně používat tento komunikační mechanismus pro většinu dotazů, jak je znázorněno na obrázku 4-16.

![Diagram zobrazující komunikování požadavků a odpovědí pro živé dotazy a aktualizace.](./media/communication-in-microservice-architecture/request-response-comms-live-queries-updates.png)

**Obrázek 4-16**. Použití http komunikace mezi požadavky a odpověďmi (synchronní nebo asynchronní)

Pokud klient používá komunikaci požadavku a odpovědi, předpokládá, že odpověď dorazí v krátkém čase, obvykle méně než sekundu nebo maximálně několik sekund. Pro zpožděné odpovědi je třeba implementovat asynchronní komunikaci na základě [vzorů zasílání zpráv](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) a technologií zasílání [zpráv](https://en.wikipedia.org/wiki/Message-oriented_middleware), což je jiný přístup, který vysvětlujeme v další části.

Populární architektonický styl pro komunikaci mezi požadavky a odezvou je [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Tento přístup je založen na protokolu [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) a pevně s ním spojený, který zahrnuje slovesa HTTP jako GET, POST a PUT. REST je nejčastěji používaný architektonický komunikační přístup při vytváření služeb. Služby REST můžete implementovat při vývoji ASP.NET služby základního webového rozhraní API.

Existuje další hodnota při použití služby HTTP REST jako jazyk definice rozhraní. Například pokud používáte [Metadata Swagger](https://swagger.io/) k popisu rozhraní API služby, můžete použít nástroje, které generují zástupné procedury klientů, které můžete přímo zjistit a využívat vaše služby.

### <a name="additional-resources"></a>Další zdroje

- **Martin fowler. Richardson Maturity Model** Popis modelu REST. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Chvástání** Oficiální stránky. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>Push a komunikace v reálném čase založená na protokolu HTTP

Další možností (obvykle pro jiné účely než REST) je komunikace v reálném čase a 1:N s architekturami vyšší úrovně, jako je [například ASP.NET SignalR](https://www.asp.net/signalr) a protokoly, jako je [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Jak ukazuje obrázek 4-17, komunikace HTTP v reálném čase znamená, že můžete mít kód serveru, který tlačí obsah připojeným klientům, jakmile budou data k dispozici, namísto toho, aby server čekal, až klient požádá o nová data.

![Diagram znázorňující push a real-time comms založené na SignalR.](./media/communication-in-microservice-architecture/one-to-many-communication.png)

**Obrázek 4-17**. Komunikace asynchronních zpráv v reálném čase

SignalR je dobrý způsob, jak dosáhnout komunikace v reálném čase pro odesílání obsahu klientům z back-end serveru. Vzhledem k tomu, že komunikace je v reálném čase, klientské aplikace ukazují změny téměř okamžitě. To je obvykle zpracována protokolem, jako je Například WebSockets, pomocí mnoha připojení WebSockets (jeden na klienta). Typickým příkladem je, když služba komunikuje změnu skóre sportovní hry do mnoha klientských webových aplikací současně.

>[!div class="step-by-step"]
>[Předchozí](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[další](asynchronous-message-based-communication.md)
