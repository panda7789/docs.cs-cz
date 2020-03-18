---
title: Komunikace mezi službami
description: Zjistěte, jak back-end cloud nativní mikroslužby komunikovat s ostatními back-end mikroslužeb.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: a5124b8b83f62ff17b1230ead63db26e0c1f2a5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401597"
---
# <a name="service-to-service-communication"></a>Komunikace mezi službami

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Přechod z front-endklienta, nyní řešíme back-end ové mikroslužby komunikovat mezi sebou.

Při vytváření aplikace nativní pro cloud, budete chtít být citliví na to, jak back-endové služby vzájemně komunikují. V ideálním případě, čím méně meziútvarové komunikace, tím lépe. Vyhýbání se však není vždy možné, protože back-endové služby se často spoléhají na sebe k dokončení operace.

Existuje několik široce přijímaných přístupů k implementaci meziútvarové komunikace. *Typ komunikace interakce* bude často určovat nejlepší přístup.

Zvažte následující typy interakcí:

- *Dotaz* – pokud volající mikroslužba vyžaduje odpověď z volané mikroslužby, například "Hey, give me the buyer information for a given customer Id."

- *Příkaz* – když volající mikroslužba potřebuje jinou mikroslužbu k provedení akce, ale nevyžaduje odpověď, například "Hey, just ship this order."

- *Událost* – když mikroslužba, nazývaná vydavatel, vyvolá událost, která se změnila nebo došlo k akci. Ostatní mikroslužby, nazývané předplatitelé, kteří mají zájem, mohou na událost odpovídajícím způsobem reagovat. Vydavatel a odběratelé si nejsou vědomi navzájem.

Mikroslužby systémy obvykle používají kombinaci těchto typů interakce při provádění operací, které vyžadují interakci mezi službami. Podívejme se na ně zblízka a na to, jak byste je mohli implementovat.

## <a name="queries"></a>Dotazy

Mnohokrát, jeden mikroslužeb může být nutné *dotaz* jiné, vyžadující okamžitou odpověď k dokončení operace. Mikroslužba nákupního košíku může potřebovat informace o produktu a cenu pro přidání položky do košíku. Existuje několik přístupů pro implementaci operací dotazu.

### <a name="requestresponse-messaging"></a>Zasílání zpráv požadavku a odpovědi

Jednou z možností pro implementaci tohoto scénáře je pro volání back-end mikroslužeb, aby přímé požadavky HTTP na mikroslužeb, které potřebuje k dotazování, je znázorněno na obrázku 4-8.

![Přímá HTTP komunikace](./media/direct-http-communication.png)

**Obrázek 4-8**. Přímá HTTP komunikace

Zatímco přímé volání HTTP mezi mikroslužbami jsou relativně jednoduché implementovat, je třeba dbát na minimalizaci tohoto praxe. Chcete-li spustit, tato volání jsou vždy *synchronní* a bude blokovat operaci, dokud je vrácen výsledek nebo časový čas požadavku. To, co bylo kdysi soběstačné, nezávislé služby, schopné se vyvíjet nezávisle a nasadit často, se nyní navzájem spojily. Jak se zvyšuje propojení mezi mikroslužbami, jejich architektonické výhody se zmenšují.

Provádění zřídka požadavku, který provede jedno přímé volání HTTP do jiné mikroslužby může být přijatelné pro některé systémy. Volání na vysoké svazek, které vyvolávají přímé volání HTTP na více mikroslužeb však nejsou vhodné. Mohou zvýšit latenci a negativně ovlivnit výkon, škálovatelnost a dostupnost vašeho systému. Ještě horší je, že dlouhá řada přímé http komunikace může vést k hluboké a složité řetězce synchronní volání mikroslužeb, znázorněno na obrázku 4-9:

![Řetězení dotazů HTTP](./media/chaining-http-queries.png)

**Obrázek 4-9**. Řetězení dotazů HTTP

Určitě si můžete představit riziko v designu zobrazeném na předchozím obrázku. Co se \#stane, pokud krok 3 selže? Nebo \#krok 8 selže? Jak se zotavíte? Co když \#je krok 6 pomalý, protože základní služba je zaneprázdněna? Jak budete pokračovat? I v případě, že všechny funguje správně, představte si latence toto volání by vzniklo, což je součet latence každého kroku.

Velký stupeň párování v předchozím obrázku naznačuje, že služby nebyly optimálně modelovány. Bylo by vhodné, aby tým přehodnotil jejich design.

### <a name="materialized-view-pattern"></a>Model materializovaného zobrazení

Oblíbenou možností pro odebrání mikroservisu je [vzor Materialized View](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). S tímto vzorem mikroslužby ukládá vlastní místní, nenormalizované kopie dat, která je vlastněna jinými službami. Místo toho, nákupní košík mikroslužeb dotazování katalogu produktů a ceny mikroslužeb, udržuje vlastní místní kopii těchto dat. Tento vzor eliminuje zbytečné párování a zlepšuje spolehlivost a dobu odezvy. Celá operace se provede uvnitř jednoho procesu. Tento vzor a další obavy týkající se údajů zkoumáme v kapitole 5.

### <a name="service-aggregator-pattern"></a>Vzor agregátoru služeb

Další možností pro odstranění mikroslužeb mikroslužeb připojení je [mikroslužba agregátor](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/), je znázorněno v fialové na obrázku 4-10.

![Agregátor služby](./media/aggregator-service.png)

**Obrázek 4-10**. Mikroslužba agregátoru

Vzor izoluje operaci, která provádí volání více back-endových mikroslužeb, centralizace jeho logiku do specializované mikroslužby.  Fialová agregátor pokladny mikroslužby na předchozí obrázku orchestruje pracovní postup pro operaci pokladny. Zahrnuje volání několika back-endových mikroslužeb v sekvenčním pořadí. Data z pracovního postupu jsou agregována a vrácena volajícímu. Zatímco stále implementuje přímé volání HTTP, agregátor mikroslužby snižuje přímé závislosti mezi back-endmikroslužeb.

### <a name="requestreply-pattern"></a>Vzor požadavku/odpovědi

Dalším přístupem pro oddělení synchronních zpráv HTTP je [vzor požadavku a odpovědi](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html), který používá komunikaci ve frontě. Komunikace pomocí fronty je vždy jednosměrný kanál, přičemž výrobce zprávu odesílá a příjemce ji přijímá. Pomocí tohoto vzoru jsou implementovány fronty požadavků a fronty odpovědí, je znázorněno na obrázku 4-11.

![Vzor požadavku a odpovědi](./media/request-reply-pattern.png)

**Obrázek 4-11**. Vzor požadavku a odpovědi

Zde výrobce zpráv vytvoří zprávu založenou na dotazu, která obsahuje jedinečné ID korelace a umístí ji do fronty požadavků. Náročná služba dequeues zprávy, zpracovává a umístí odpověď do fronty odpovědí se stejným ID korelace. Služba producer dequeues the message, matches it with the correlation ID and continues processing. Fronty podrobně pokrýváme v další části.

## <a name="commands"></a>Příkazy

Dalším typem komunikační interakce je *příkaz*. Mikroslužbu může potřebovat jinou mikroslužbu k provedení akce. Objednávání mikroslužby může potřebovat doprava mikroslužby k vytvoření dodávky pro schválené objednávky. Na obrázku 4-12 jedna mikroslužba, nazývaná Výrobce, odešle zprávu jiné mikroslužbě, spotřebiteli, přikazující mu něco udělat.

![Interakce příkazů s frontou](./media/command-interaction-with-queue.png)

**Obrázek 4-12**. Interakce příkazů s frontou

Nejčastěji producent nevyžaduje odpověď a může *oheň-a-zapomenout* na zprávu. Pokud je potřeba odpověď, příjemce odešle samostatnou zprávu zpět producent na jiném kanálu. Zpráva příkazu je nejlépe odeslána asynchronně s frontou zpráv. podporovány zjednodušené zprávy zprostředkovatele. V předchozím diagramu si všimněte, jak fronta odděluje a odděluje obě služby.

Fronta zpráv je zprostředkující konstrukce, jehož prostřednictvím výrobce a příjemce předat zprávu. Fronty implementují asynchronní vzor zasílání zpráv typu point-to-point. Výrobce ví, kam musí být příkaz odeslán a trasy vhodně. Fronta zaručuje, že zpráva je zpracována přesně jedním z instancí příjemce, které jsou čtení z kanálu. V tomto scénáři může výrobce nebo spotřebitelská služba horizontální navýšení kapacity bez ovlivnění druhého. Také technologie mohou být různorodé na každé straně, což znamená, že můžeme mít mikroslužbu Java volání [mikroslužby Golang.](https://golang.org)

V kapitole 1 jsme hovořili o *podpůrné služby*. Podpůrné služby jsou pomocné prostředky, na kterých závisí cloudové nativní systémy. Fronty zpráv jsou podpůrné služby. Cloud Azure podporuje dva typy front zpráv, které můžou vaše cloudové nativní systémy využívat k implementaci zasílání příkazů: Fronty úložiště Azure a Fronty služby Azure Service Bus.

### <a name="azure-storage-queues"></a>Fronty Azure Storage

Fronty úložišť Azure nabízejí jednoduchou infrastrukturu front, která je rychlá, cenově dostupná a podporovaná účty úložiště Azure.

[Fronty úložiště Azure](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) jsou vybaveny mechanismem frontzaložené na rest se spolehlivým a trvalým zasíláním zpráv. Poskytují minimální sadu funkcí, ale jsou levné a ukládají miliony zpráv. Jejich kapacita se pohybuje až 500 TB. Jedna zpráva může mít velikost až 64 kB.

Ke zprávám můžete přistupovat odkudkoli na světě prostřednictvím ověřených volání pomocí protokolu HTTP nebo HTTPS. Fronty úložiště můžete škálovat na velký počet souběžných klientů pro zpracování špičky provozu.

To znamená, že existují omezení se službou:

- Objednávka zpráv není zaručena.

- Zpráva může přetrvávat pouze sedm dní, než bude automaticky odebrána.

- Podpora správy stavu, vyhledávání duplicit nebo transakcí není k dispozici.

Obrázek 4-13 znázorňuje hierarchii fronty úložiště Azure.

![Hierarchie fronty úložiště](./media/storage-queue-hierarchy.png)

**Obrázek 4-13**. Hierarchie fronty úložiště

Na předchozím obrázku si všimněte, jak fronty úložiště ukládají své zprávy ve podkladovém účtu úložiště Azure.

Pro vývojáře poskytuje společnost Microsoft několik knihoven na straně klienta a serveru pro zpracování fronty úložiště. Většina hlavních platforem je podporována, včetně .NET, Java, JavaScript, Ruby, Python a Go. Vývojáři by nikdy komunikovat přímo s těmito knihovnami. Pokud tak učiníte, bude úzce spárovat kód mikroslužeb na službu Azure Storage Queue. Je lepší praxe izolovat podrobnosti implementace rozhraní API. Zavést zprostředkovatelskou vrstvu nebo zprostředkující rozhraní API, které zveřejňuje obecné operace a zapouzdřuje konkrétní knihovnu. Tato volná spojka umožňuje vyměnit jednu službu řazení do fronty za jinou, aniž byste museli provádět změny v kódu hlavní linky.

Fronty azure storage jsou ekonomickou možností implementace zasílání zpráv příkazů ve vašich aplikacích nativních pro cloud. Zvláště když velikost fronty překročí 80 GB nebo je přijatelná jednoduchá sada funkcí. Platíte pouze za ukládání zpráv; neexistují žádné pevné hodinové poplatky.

### <a name="azure-service-bus-queues"></a>Fronty služby Azure Service Bus

Pro složitější požadavky na zasílání zpráv, zvažte fronty Azure Service Bus.

Azure [Service Bus,](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) která se nachází na robustní infrastruktuře zpráv, podporuje *zprostředkovaný model zasílání zpráv*. Zprávy jsou spolehlivě uloženy v zprostředkovateli (fronty), dokud přijaté spotřebitelem. Fronta zaručuje doručení zpráv FIFO první dovnitř/první ven (, respektování pořadí, ve kterém byly zprávy přidány do fronty.

Velikost zprávy může být mnohem větší, až 256 KB. Zprávy jsou trvalé ve frontě po neomezenou dobu. Service Bus podporuje nejen volání založená na protokolu HTTP, ale také poskytuje plnou podporu pro [protokol AMPQ](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview). AMPQ je otevřený standard napříč dodavateli, který podporuje binární protokol a vyšší stupeň spolehlivosti.

Service Bus poskytuje bohatou sadu funkcí, včetně [podpory transakcí](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) a funkce [vyhledávání duplicit](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection). Fronta zaručuje "maximálně jednou doručení" na zprávu. Automaticky zahodí zprávu, která již byla odeslána. Pokud výrobce je na pochybách, může znovu odeslat stejnou zprávu a Service Bus zaručuje, že budou zpracovány pouze jednu kopii. Vyhledávání duplicit vás osvobozuje od nutnosti vytvářet další infrastrukturu.

Další dvě podnikové funkce jsou dělení a relace. Konvenční fronta service bus je zpracována jedním zprostředkovatelem zpráv a uložena v jednom úložišti zpráv. Ale [dělení service bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) šíří fronty přes více zprostředkovatelů zpráv a úložiště zpráv. Celková propustnost již není omezena výkonem jednoho zprostředkovatele zpráv nebo úložiště zasílání zpráv. Dočasný výpadek úložiště zpráv nevykresluje rozdělenou frontu nek dispozici.

[Relace služby Service Bus](https://codingcanvas.com/azure-service-bus-sessions/) poskytují způsob, jak zprávy související se skupinou. Představte si scénář pracovního postupu, kde zprávy musí být zpracovány společně a operace dokončena na konci. Chcete-li využít výhod, musí být relace explicitně povoleny pro frontu a každá související zpráva musí obsahovat stejné ID relace.

Existují však některé důležité upozornění: Velikost front service bus je omezena na 80 GB, což je mnohem menší než to, co je k dispozici z front úložiště. Kromě toho service bus fronty za následek základní náklady a poplatek za operaci.

Obrázek 4-14 popisuje architekturu fronty service bus na vysoké úrovni.

![Fronta služby Service Bus](./media/service-bus-queue.png)

**Obrázek 4-14**. Fronta služby Service Bus

Na předchozím obrázku si poznamenejte vztah mezi bodem a bodem. Dvě instance stejného zprostředkovatele zařazují zprávy do jedné fronty služby Service Bus. Každá zpráva je spotřebována pouze jednou ze tří instancí příjemce na pravé straně. Dále diskutujeme o tom, jak implementovat zasílání zpráv, kde mohou mít všichni různí spotřebitelé zájem o stejnou zprávu.

## <a name="events"></a>Akce

Řízení front zpráv je efektivní způsob implementace komunikace, kde může výrobce asynchronně odeslat spotřebiteli zprávu. Co se však stane, když *mnoho různých spotřebitelů* má zájem o stejnou zprávu? Vyhrazená fronta zpráv pro každého spotřebitele by se dobře neškálovat a bylo by obtížné je spravovat.

Chcete-li tento scénář vyřešit, přesuneme se na třetí typ interakce se zprávou, *událost*. Jedna mikroslužba oznamuje, že došlo k akci. Ostatní mikroslužby, pokud máte zájem, reagovat na akci nebo událost.

Eventing je dvoustupňový proces. Pro danou změnu stavu mikroslužby publikuje událost zprostředkovatele zpráv, zpřístupní ji jakékoli jiné zainteresované mikroslužby. Zainteresovaná mikroslužba je upozorněna přihlášením k odběru události v zprostředkovateli zpráv. Vzor [Publikování/přihlášení k odběru](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) slouží k implementaci [komunikace založené na událostech](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications).

Obrázek 4-15 ukazuje nákupní košík mikroslužeb publikování události s dvěma dalšími mikroslužeb k odběru.

![Zasílání zpráv řízených událostmi](./media/event-driven-messaging.png)

**Obrázek 4-15**. Zasílání zpráv řízených událostmi

Všimněte si součásti *sběrnice událostí,* která je uprostřed komunikačního kanálu. Je to vlastní třída, která zapouzdřuje zprostředkovatele zpráv a odděluje ji od podkladové aplikace. Objednávání a inventář mikroslužeb nezávisle provozovat událost bez znalosti o sobě navzájem, ani nákupní košík mikroslužeb. Když je registrovaná událost zveřejněna na sběrnici události, jednají podle ní.

S eventing, jsme se přesunout z fronty technologie na *témata*. [Téma](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) je podobné fronty, ale podporuje jeden-k-n zasílání zpráv vzor. Jedna mikroslužba publikuje zprávu. Více přihlášení k odběru mikroslužeb můžete zvolit přijímat a jednat na tuto zprávu. Obrázek 4-16 ukazuje architekturu tématu.

![Architektura tématu](./media/topic-architecture.png)

**Obrázek 4-16**. Architektura tématu

Na předchozím obrázku vydavatelé posílají zprávy k tématu. Na konci odběratelé přijímat zprávy z odběrů. Ve středu téma předává zprávy odběrům na základě sady *pravidel*zobrazených v tmavě modrých polích. Pravidla fungují jako filtr, který předává konkrétní zprávy předplatnému. Zde "CreateOrder" událost by být \#odeslány \#předplatné 1 a \#předplatné 3, ale ne předplatné 2. Událost "OrderCompleted" by byla \#odeslána \#na předplatné 2 a předplatné 3.

Cloud Azure podporuje dvě různé tematické služby: Témata azure service busu a Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Téma služby Azure Service Bus

Nad stejným robustním modelem zprostředkovaných zpráv front Azure Service Bus jsou [témata Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Téma může přijímat zprávy od více nezávislých vydavatelů a odesílat zprávy až 2 000 odběratelům. Odběry lze dynamicky přidávat nebo odebírat za běhu bez zastavení systému nebo opětovné vytvoření tématu.

Mnoho pokročilých funkcí z front Azure Service Bus jsou k dispozici také pro témata, včetně [vyhledávání duplicit](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) a [podporu transakcí](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions). Ve výchozím nastavení service bus témata jsou zpracovány zprostředkovatele jedné zprávy a uloženy v jednom úložišti zpráv. Ale [dělení service bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) škáluje téma tím, že šíří mezi mnoho zprostředkovatelů zpráv a úložiště zpráv.

[Plánované doručení zprávy](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) označí zprávu s určitým časem zpracování. Zpráva se v tématu do té doby nezobrazí. [Odložení zprávy](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) umožňuje odložit načtení zprávy na pozdější dobu. Obě se běžně používají ve scénářích zpracování pracovního postupu, kde jsou operace zpracovány v určitém pořadí. Zpracování přijatých zpráv můžete odložit, dokud nebude dokončena předchozí práce.

Témata služby Service Bus jsou robustní a osvědčenou technologií umožňující publikování/odběr komunikace ve vašich cloudových nativních systémech.

### <a name="azure-event-grid"></a>Azure Event Grid

Zatímco Azure Service Bus je bitva-testovány zasílání zpráv broker s úplnou sadou podnikových funkcí, [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) je nové dítě na bloku.

Na první pohled může Event Grid vypadat jako další systém zasílání zpráv založený na tématech. Nicméně, je to jiné v mnoha ohledech. Zaměřuje se na úlohy založené na událostech a umožňuje zpracování událostí v reálném čase, hlubokou integraci Azure a otevřenou platformu – to vše na infrastruktuře bez serveru. Je navržen pro současné aplikace nativní pro cloud a bez serveru.

Jako centralizovaný *backplane událostí*nebo kanálu event grid reaguje na události uvnitř prostředků Azure a z vašich vlastních služeb.

Oznámení událostí jsou publikována v tématu mřížky událostí, které zase směruje každou událost k předplatnému. Předplatitelé mapovat odběry a využívat události. Stejně jako Service Bus, Event Grid podporuje *filtrovaný model odběratele,* kde předplatné nastaví pravidlo pro události, které chce přijímat. Event Grid poskytuje rychlou propustnost se zárukou 10 milionů událostí za sekundu, což umožňuje téměř doručení v reálném čase – mnohem víc, než dokáže služba Azure Service Bus generovat.

Sweet spot pro Event Grid je jeho hluboká integrace do struktury infrastruktury Azure. Prostředek Azure, jako je Cosmos DB, můžete publikovat předdefinované události přímo do jiných zainteresovaných prostředků Azure – bez nutnosti vlastního kódu. Event Grid můžete publikovat události z předplatného Azure, skupiny prostředků nebo služby, poskytuje vývojářům jemně odstupňovanou kontrolu nad životním cyklem cloudových prostředků. Služba Event Grid se však neomezuje jen na Azure. Je to otevřená platforma, která může využívat vlastní události HTTP publikované z aplikací nebo služeb třetích stran a směrovat události externím odběratelům.

Při publikování a přihlášení k odběru nativních událostí z prostředků Azure není vyžadováno žádné kódování. S jednoduchou konfigurací můžete integrovat události z jednoho prostředku Azure do jiného s využitím integrované instalace pro témata a předplatná. Obrázek 4-17 ukazuje anatomii Event Grid.

![Anatomie sítě událostí](./media/event-grid-anatomy.png)

**Obrázek 4-17**. Anatomie sítě událostí

Hlavní rozdíl mezi EventGrid a Service Bus je základní *vzor výměny zpráv*.

Service Bus implementuje starší *model vyžádat* styl, ve kterém příjem odběratel aktivně dotazování odběr tématu pro nové zprávy. Na druhou stranu, tento přístup dává účastníkovi plnou kontrolu nad tempem, při kterém zpracovává zprávy. Určuje, kdy a kolik zpráv se má v daném okamžiku zpracovat. Nepřečtené zprávy zůstávají v předplatném, dokud nebudou zpracovány. Významným nedostatkem je latence mezi čas generování události a dotazování operace, která vyžádá tuto zprávu odběratele pro zpracování. Také režie konstantní dotazování pro další událost spotřebovává prostředky a peníze.

EventGrid se však liší. Implementuje *model push,* ve kterém jsou události odesílány do EventHandlers jako přijaté, což poskytuje doručení událostí téměř v reálném čase. Snižuje také náklady, protože služba se aktivuje pouze v případě, že je potřeba ke spotřebování události – ne nepřetržitě jako u dotazování. To znamená, že obslužná rutina události musí zpracovat příchozí zatížení a poskytnout mechanismy omezení, aby se ochránila před zahlcením. Mnoho služeb Azure, které tyto události spotřebovávají, jako jsou funkce Azure a logic apps, poskytuje funkce automatického škálování pro zpracování zvýšených zatížení.  

Event Grid je plně spravovaná cloudová služba bez serveru. Dynamicky se škáluje na základě vašeho provozu a účtuje vám pouze za skutečné využití, nikoli za předem zakoupenou kapacitu. Prvních 100 000 operací za měsíc je zdarma – operace jsou definovány jako příchozí přenos událostí (oznámení o příchozích událostech), pokusy o doručení předplatného, volání správy a filtrování podle předmětu. S 99,99% dostupností eventgrid zaručuje doručení události během 24 hodin, s integrovanou funkcí opakování pro neúspěšné doručení. Nedoručené zprávy lze přesunout do fronty "nedoručené písmeno" pro řešení.  Na rozdíl od Azure Service Bus je Event Grid vyladěný pro rychlý výkon a nepodporuje funkce, jako je objednané zasílání zpráv, transakce a relace.

### <a name="streaming-messages-in-the-azure-cloud"></a>Streamování zpráv v cloudu Azure

Azure Service Bus a Event Grid poskytují skvělou podporu pro aplikace, které zveřejňují jednotlivé samostatné události, jako je nový dokument, který byl vložen do databáze Cosmos. Ale co když váš cloud nativní systém potřebuje zpracovat *proud souvisejících událostí?* [Datové proudy událostí](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) jsou složitější. Obvykle jsou časově uspořádané, vzájemně propojené a musí být zpracovány jako skupina.

[Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) je platforma pro streamování dat a služba pro ingestování událostí, která shromažďuje, transformuje a ukládá události. Je vyladěný pro sběr dat streamování, jako jsou například nepřetržité oznámení událostí vyzařované z kontextu telemetrie. Služba je vysoce škálovatelná a může ukládat a [zpracovávat miliony událostí za sekundu](https://docs.microsoft.com/azure/event-hubs/event-hubs-about). Zobrazeno na obrázku 4-18, je to často přední dveře pro kanál událostí, oddělení datového proudu od spotřeby událostí.

![Azure Event Hub](./media/azure-event-hub.png)

**Obrázek 4-18**. Azure Event Hub

Event Hub podporuje nízkou latenci a konfigurovatelné uchovávání času. Na rozdíl od front a témat uchovávejte centra událostí data událostí po přečtení spotřebitelem. Tato funkce umožňuje dalším službám analýzy dat, interním i externím, přehrát data pro další analýzu. Události uložené v centru událostí jsou odstraněny pouze po vypršení doby uchovávání, což je ve výchozím nastavení jeden den, ale konfigurovatelné.

Centrum událostí podporuje běžné protokoly pro publikování událostí včetně protokolů HTTPS a AMQP. Podporuje také Kafku 1.0. [Existující aplikace Kafka mohou komunikovat s Event Hub](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) pomocí protokolu Kafka poskytující alternativu ke správě velkých clusterů Kafka. Kafka zahrnuje mnoho cloudových systémů s otevřeným zdrojovým kódem.

Event Hubs implementuje streamování zpráv prostřednictvím [modelu rozděleného spotřebitele,](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) ve kterém každý příjemce čte pouze určitou podmnožinu nebo oddíl datového proudu zpráv. Tento vzor umožňuje obrovské horizontální škálování pro zpracování událostí a poskytuje další funkce zaměřené na datový proud, které nejsou k dispozici ve frontách a tématech. Oddíl je seřazená posloupnost událostí, která se nachází v centru událostí. Při doručení novějších událostí jsou přidány na konec této sekvence.Obrázek 4-19 znázorňuje dělení v centru událostí.

![Dělení centra událostí](./media/event-hub-partitioning.png)

**Obrázek 4-19**. Dělení centra událostí

Místo čtení ze stejného prostředku, každá skupina spotřebitelů čte přes podmnožinu nebo oddíl datového proudu zpráv.

Pro aplikace nativní pro cloud, které musí streamovat velký počet událostí, azure event hub může být robustní a cenově dostupné řešení.

>[!div class="step-by-step"]
>[Předchozí](front-end-communication.md)
>[další](rest-grpc.md)
