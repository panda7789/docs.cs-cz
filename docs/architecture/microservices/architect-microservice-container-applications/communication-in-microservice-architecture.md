---
title: Komunikace v architektuře mikroslužeb
description: Prozkoumejte různé způsoby komunikace mezi mikroslužbami a porozumět vlivům synchronních a asynchronních způsobů.
ms.date: 09/20/2018
ms.openlocfilehash: add1ff74bee456e0fa7f2fb54d2cf4e536402db4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738024"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikace v architektuře mikroslužeb

V aplikaci monolitické spuštěné v jednom procesu komponenty vyvolávají jednu jinou pomocí metody na úrovni jazyka nebo volání funkcí. Ty mohou být silně spojeny, pokud vytváříte objekty s kódem (například `new ClassName()`), nebo je lze vyvolat odděleným způsobem, pokud používáte vkládání závislostí odkazem na abstrakce namísto konkrétních instancí objektů. V obou případech jsou objekty spuštěné v rámci stejného procesu. Největší výzvou, při změně z aplikace monolitické na aplikaci založenou na mikroslužbách, spočívá v tom, že probíhá změna komunikačního mechanismu. Přímý převod z volání metody v rámci procesu do volání RPC na služby způsobí, že se jedná o chat a neefektivní komunikaci, která v distribuovaných prostředích nebude dobře fungovat. Problémy s návrhem distribuovaného systému jsou dostatečně dobře známé, že se jedná o i Canon, který je známý jako [Fallacies distribuovaného výpočetního](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) prostředí, ve kterém jsou uvedeny předpoklady, které vývojáři často vytvářejí při přechodu z monolitické do distribuovaných návrhů. .

Neexistuje žádné řešení, ale několik. Jedno řešení zahrnuje izolaci podnikových mikroslužeb co nejvíc. Pak můžete použít asynchronní komunikaci mezi interními mikroslužbami a nahradit jemně odstupňovanou komunikaci, která je typická pro komunikaci uvnitř procesu mezi objekty a hrubou komunikací. Můžete to provést seskupením volání a vrácením dat, která agreguje výsledky více vnitřních volání, klientovi.

Aplikace založené na mikroslužbách je distribuovaný systém běžící na více procesech nebo službách, obvykle i na různých serverech nebo hostitelích. Každá instance služby je obvykle proces. Proto musí služby komunikovat pomocí Meziprocesového komunikačního protokolu, jako je HTTP, AMQP nebo binární protokol jako TCP, v závislosti na povaze jednotlivých služeb.

Komunita mikroslužeb podporuje filozofie[inteligentních koncových bodů a Dumb kanálů](https://simplicable.com/new/smart-endpoints-and-dumb-pipes). Tento heslo doporučuje návrh, který je mezi mikroslužbami co nejoddělený a co možno soudržný v rámci jedné mikroslužby. Jak bylo vysvětleno dříve, každá mikroslužba vlastní vlastní data a vlastní logiku domény. Mikroslužby, které sestaví koncovou aplikaci, se obvykle jednoduše choreographed pomocí komunikace REST namísto složitých protokolů, jako je WS-\* a flexibilní komunikace řízená událostmi místo centralizovaného. Orchestrace obchodních procesů.

Mezi tyto dva běžně používané protokoly patří požadavek HTTP/odpověď s rozhraními API prostředků (při dotazování většiny všech) a odlehčené asynchronní zasílání zpráv při komunikaci s aktualizacemi napříč více mikroslužbami. Tyto informace jsou podrobněji vysvětleny v následujících částech.

## <a name="communication-types"></a>Typy komunikace

Klient a služby mohou komunikovat prostřednictvím mnoha různých typů komunikace, přičemž každý z nich cílí na jiný scénář a cíle. Zpočátku lze tyto typy komunikací klasifikovat ve dvou osách.

První osa definuje, zda je protokol synchronní nebo asynchronní:

- Synchronní protokol. HTTP je synchronní protokol. Klient odešle požadavek a počká na odpověď od služby. To je nezávislé na spuštění klientského kódu, které by mohlo být synchronní (vlákno je blokováno) nebo asynchronní (vlákno není blokováno a odpověď bude nakonec k dispozici zpětnému volání). Důležitým bodem je, že protokol (HTTP/HTTPS) je synchronní a klientský kód může v případě, že obdrží odpověď serveru HTTP, pokračovat pouze v jeho úkolu.

- Asynchronní protokol. Další protokoly, jako je AMQP (protokol podporovaný mnoha operačními systémy a cloudová prostředí), používají asynchronní zprávy. Kód klienta nebo odesílatel zprávy obvykle nečeká na odpověď. Pouze pošle zprávu jako při posílání zprávy do fronty RabbitMQ nebo v jakémkoli jiném zprostředkovateli zpráv.

Druhá osa definuje, jestli má komunikace jeden přijímač nebo více přijímačů:

- Jeden přijímač. Každý požadavek musí zpracovat přesně jeden příjemce nebo služba. Příkladem této komunikace je [vzor příkazu](https://en.wikipedia.org/wiki/Command_pattern).

- Více přijímačů. Každý požadavek může být zpracován nulou pro více přijímačů. Tento typ komunikace musí být asynchronní. Příkladem je mechanismus pro [publikování a odběr](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) , který se používá ve vzorcích, jako je [Architektura řízená událostmi](https://microservices.io/patterns/data/event-driven-architecture.html). Vychází z rozhraní sběrnice událostí nebo zprostředkovatele zpráv při rozšiřování aktualizací dat mezi několika mikroslužbami prostřednictvím událostí. obvykle se implementuje prostřednictvím služby Service Bus nebo podobného artefaktu, jako je [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) pomocí [témat a odběrů](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikace založená na mikroslužbách bude často používat kombinaci těchto komunikačních stylů. Nejběžnějším typem je komunikace s jedním přijímačem s synchronním protokolem, jako je HTTP/HTTPS, při volání běžné služby HTTP webového rozhraní API. Mikroslužby také obvykle používají protokoly zpráv pro asynchronní komunikaci mezi mikroslužbami.

Tyto osy jsou vhodné k tomu, abyste měli jasnou možnost komunikačních mechanismů, ale nejedná se o důležité obavy při vytváření mikroslužeb. Asynchronní povaha spuštění klientského vlákna ani asynchronní povaha vybraného protokolu není důležitým bodem při integraci mikroslužeb. Důležité *je* , aby se vaše mikroslužby asynchronně integrují při zachování nezávislosti mikroslužeb, jak je vysvětleno v následující části.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Asynchronní integrace mikroslužeb vynutila autonomii mikroslužby.

Jak už bylo zmíněno, důležitým bodem při sestavování aplikace založené na mikroslužbách je způsob, jakým můžete své mikroslužby integrovat. V ideálním případě byste se měli pokusit minimalizovat komunikaci mezi interními mikroslužbami. Čím méně komunikace mezi mikroslužby, tím lépe. V mnoha případech ale budete muset nějaké mikroslužby integrovat. V takovém případě je třeba toto kritické pravidlo, že komunikace mezi mikroslužbami by měla být asynchronní. To neznamená, že musíte použít konkrétní protokol (například asynchronní zasílání zpráv oproti synchronnímu HTTP). Jenom to znamená, že komunikace mezi mikroslužbami by se měla provádět jenom při asynchronním šíření dat, ale nezáleží na ostatních vnitřních mikroslužbách v rámci operace HTTP/odpovědi počáteční služby.

Pokud je to možné, nikdy nezáleží na synchronní komunikaci (požadavek nebo odpověď) mezi několika mikroslužbami, a to ani u dotazů. Cílem každé mikroslužby je autonomní a k dispozici klientovi klienta, i když ostatní služby, které jsou součástí komplexní aplikace, nejsou v pořádku. Pokud se domníváte, že je třeba provést volání z jedné mikroslužby do ostatních mikroslužeb (například provedení požadavku HTTP na dotaz na data), aby bylo možné poskytnout odpověď klientské aplikaci, máte architekturu, která nebude odolná, pokud se některé mikroslužby selžou.

Kromě toho je třeba mít závislosti HTTP mezi mikroslužbami, například při vytváření dlouhých cyklů požadavků a odpovědí s řetězy požadavků HTTP, jak je znázorněno v první části obrázku 4-15, nejen to znamená, že vaše mikroslužby nejsou autonomní, ale také jejich výkon. mělo dopad na to, že jedna ze služeb v tomto řetězci nefunguje dobře.

Čím více přidáváte synchronní závislosti mezi mikroslužbami, jako jsou požadavky na dotazy, tím horší je celková doba odezvy pro klientské aplikace.

![Diagram znázorňující tři typy komunikace napříč mikroslužbami.](./media/communication-in-microservice-architecture/sync-vs-async-patterns-across-microservices.png)

**Obrázek 4-15**. Anti-vzory a vzory komunikace mezi mikroslužbami

Jak je znázorněno na výše uvedeném diagramu, v části synchronní komunikace je mezi mikroslužbami při obsluze žádosti klienta vytvořeno zřetězení požadavků. Toto je anti-vzor. U mikroslužeb asynchronní komunikace se používají asynchronní zprávy nebo cyklické dotazování http ke komunikaci s dalšími mikroslužbami, ale žádost klienta se poskytuje hned.

Pokud vaše mikroslužba potřebuje vyvolat další akci v jiné mikroslužbě (Pokud je to možné), neprovede tuto akci synchronně a jako součást původní žádosti mikroslužeb a operace odpovědi. Místo toho se provede asynchronně (pomocí asynchronního zasílání zpráv nebo událostí integrace, front atd.). Ale co nejvíc Nevolejte akci synchronně jako součást původní synchronní operace synchronního požadavku a odpovědi.

A konečně (a jedná se o většinu problémů při vytváření mikroslužeb), pokud vaše počáteční mikroslužba potřebuje data, která jsou původně vlastněna jinými mikroslužbami, nespoléhá na to, aby pro tato data prováděla synchronní požadavky. Místo toho replikujte nebo rozšiřujte tato data (pouze atributy, které potřebujete) do databáze počáteční služby, a to pomocí konečné konzistence (obvykle pomocí integračních událostí, jak je vysvětleno v nadcházejících oddílech).

Jak bylo uvedeno výše v části [Identifikace hranic doménových modelů pro jednotlivé mikroslužby](identify-microservice-domain-model-boundaries.md), při duplikaci některých dat napříč několika mikroslužbami není nesprávný návrh, a to v opačném případě, kdy je možné data přeložit do konkrétního jazyk nebo pojem tohoto dalšího doménového nebo vázaného kontextu. Například v [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) máte mikroslužbu s názvem identity. API, která má za následek většinu dat uživatele s entitou s názvem uživatel. Pokud ale potřebujete ukládat data o uživateli v rámci objednávání mikroslužeb, uložte ho jako jinou entitu s názvem kupující. Entita nákupčí sdílí stejnou identitu s původní entitou uživatele, ale může mít jenom několik atributů, které vyžaduje doména řazení, a ne celý profil uživatele.

Můžete použít libovolný protokol pro komunikaci a šíření dat asynchronně napříč mikroslužbami, aby bylo možné zajistit jejich případné konzistenci. Jak už jsme uvedli, mohli byste použít události integrace pomocí sběrnice událostí nebo zprostředkovatele zpráv nebo můžete protokol HTTP použít taky tak, že v něm provedete dotazování dalších služeb. Nezáleží na tom. Důležité pravidlo je nevytvářet synchronní závislosti mezi vašimi mikroslužbami.

V následujících částech se vysvětlují vícenásobné komunikační styly, které můžete zvážit v použití v rámci aplikace založené na mikroslužbách.

## <a name="communication-styles"></a>Styly komunikace

Existuje mnoho protokolů a možností, které můžete použít ke komunikaci v závislosti na typu komunikace, kterou chcete použít. Pokud používáte komunikační mechanismus synchronních požadavků a odpovědí, jsou protokoly, jako jsou přístupy HTTP a REST, nejběžnější, zejména pokud publikujete služby mimo hostitele Docker nebo cluster mikroslužeb. Pokud komunikujete mezi službami interně (v rámci hostitele Docker nebo clusteru mikroslužeb), můžete také použít mechanizmus komunikace v binárním formátu (například WCF pomocí protokolu TCP a binárního formátu). Alternativně můžete použít asynchronní komunikační mechanismy založené na zprávách, jako je AMQP.

K dispozici je také více formátů zpráv, jako JSON nebo XML, nebo i binární formáty, což může být efektivnější. Pokud váš zvolený binární formát není standard, pravděpodobně nebudete mít dobrou představu o tom, že vaše služby budou veřejně publikovat v tomto formátu. Pro interní komunikaci mezi vašimi mikroslužbami můžete použít nestandardní formát. To můžete provést při komunikaci mezi mikroslužbami v rámci hostitele Docker nebo v clusteru mikroslužeb (například orchestrace Docker) nebo pro speciální klientské aplikace, které komunikují s mikroslužbami.

### <a name="requestresponse-communication-with-http-and-rest"></a>Komunikace mezi požadavkem a odpovědí pomocí protokolu HTTP a REST

Když klient používá komunikaci typu požadavek/odpověď, pošle požadavek službě, služba zpracuje požadavek a pošle zpět odpověď. Komunikace mezi požadavkem a odpovědí je obzvláště vhodná pro dotazování dat v UŽIVATELSKÉM rozhraní (živé uživatelské rozhraní) v reálném čase z klientských aplikací. V architektuře mikroslužeb proto pravděpodobně použijete tento komunikační mechanismus pro většinu dotazů, jak je znázorněno na obrázku 4-16.

![Diagram znázorňující komunikace požadavků a odpovědí pro živé dotazy a aktualizace](./media/communication-in-microservice-architecture/request-response-comms-live-queries-updates.png)

**Obrázek 4-16**. Komunikace pomocí požadavků a odpovědí HTTP (synchronní nebo asynchronní)

Pokud klient používá komunikaci typu požadavek/odpověď, předpokládá se, že odpověď dorazí v krátkém čase, obvykle méně než sekunda nebo několik sekund. U opožděných odpovědí musíte implementovat asynchronní komunikaci na základě [vzorů zasílání zpráv](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) a [technologií zasílání zpráv](https://en.wikipedia.org/wiki/Message-oriented_middleware), což je jiný přístup, který vysvětlujeme v další části.

Oblíbeným stylem architektury pro komunikaci mezi požadavkem a odpovědí je [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Tento přístup je založený na a úzce spojený s protokolem [http](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) , přechodu operacemi http, jako je get, post a PUT. REST je nejčastěji používaná komunikace architektury při vytváření služeb. Služby REST můžete implementovat při vývoji ASP.NET Core služeb webového rozhraní API.

K dispozici je další hodnota při používání služby HTTP REST jako jazyk definice rozhraní. Pokud například použijete [metadata Swagger](https://swagger.io/) k popisu rozhraní API služby, můžete použít nástroje, které generují zástupné procedury klienta, které mohou přímo zjišťovat a využívat vaše služby.

### <a name="additional-resources"></a>Další zdroje

- **Martin Fowlera. Richardson model splatnosti** popis modelu REST. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Swagger** Oficiální lokalita. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>Doručování a komunikace v reálném čase na základě HTTP

Další možností (obvykle pro jiné účely než REST) je komunikace v reálném čase a 1: n s architekturami vyšší úrovně, jako jsou například [ASP.NET signály](https://www.asp.net/signalr) a protokoly, jako jsou [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Jak ukazuje obrázek 4-17, komunikace HTTP v reálném čase znamená, že serverový kód přenáší obsah do připojených klientů, protože data budou k dispozici, místo toho, aby server čekal na vyžádání nových dat klientem.

![Diagram znázorňující práci na vyžádání a na základě signálu v reálném čase.](./media/communication-in-microservice-architecture/one-to-many-communication.png)

**Obrázek 4-17**. Komunikace mezi asynchronními zprávami 1:1 v reálném čase

Signaler je dobrým způsobem, jak zajistit komunikaci v reálném čase pro doručování obsahu klientům ze serveru back-end. Vzhledem k tomu, že komunikace probíhá v reálném čase, aplikace klienta zobrazuje změny téměř okamžitě. To se obvykle řídí protokolem, jako jsou WebSockets, a to s využitím mnoha připojení WebSockets (jedna na každého klienta). Typickým příkladem je, že služba komunikuje se změnou skóre sportovní hry na mnoho klientských webových aplikací současně.

>[!div class="step-by-step"]
>[Předchozí](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[Další](asynchronous-message-based-communication.md)
