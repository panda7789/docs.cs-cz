---
title: Komunikace mezi službami
description: Přečtěte si, jak cloudové mikroslužby back-end komunikují s ostatními back-end mikroslužbami.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: a5124b8b83f62ff17b1230ead63db26e0c1f2a5b
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087599"
---
# <a name="service-to-service-communication"></a>Komunikace mezi službami

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Při přesunu z front-endu klienta se teď řeší i back-endové mikroslužby navzájem.

Při sestavování nativních cloudových aplikací budete chtít být citlivé na to, jak se vzájemně komunikují služby back-end. V ideálním případě je to lepší komunikace mezi službami. Vyhnutí se ale není vždycky možné, protože back-endové služby se často vzájemně spoléhá na to, že se operace dokončí.

K implementaci komunikace mezi službami je k dispozici několik široce přijatelných přístupů. *Typ interakce komunikace* bude často určovat nejlepší přístup.

Vezměte v úvahu následující typy interakcí:

- *Dotaz* – Pokud volající mikroslužba vyžaduje odpověď od pojmenované mikroslužby, například "Hey", sdělte mi informace nákupčího pro dané ID zákazníka. "

- *Příkaz* – když volající mikroslužba potřebuje k provedení akce jinou mikroslužbu, ale nevyžaduje odpověď, například "Hey", stačí dodávat tuto objednávku. "

- *Událost* – když mikroslužba, která se nazývá Vydavatel, vyvolá událost, u které došlo ke změně stavu nebo k akci. Ostatní mikroslužby nazývané předplatitelé, kteří se zajímají, mohou reagovat na událost odpovídajícím způsobem. Vydavatel a předplatitelé si je vzájemně nevědí.

Systémy mikroslužeb obvykle používají kombinaci těchto typů interakcí při provádění operací, které vyžadují interakci mezi službami. Pojďme se podívat na každý a jak je můžete implementovat.

## <a name="queries"></a>Dotazy

V mnoha případech může být potřeba, aby jedna mikroslužba mohla zadat *dotaz* na jinou a vyžadovat okamžitou reakci na dokončení operace. Mikroslužba nákupního košíku může potřebovat informace o produktu a cenu za přidání položky do košíku. Pro implementaci operací dotazů je k dispozici několik přístupů.

### <a name="requestresponse-messaging"></a>Zasílání zpráv o požadavcích a odpovědích

Jednou z možností implementace tohoto scénáře je pro volající back-end mikroslužba, která umožňuje přímé požadavky HTTP na mikroslužby, které potřebuje k dotazování, zobrazené na obrázku 4-8.

![Přímá komunikace HTTP](./media/direct-http-communication.png)

**Obrázek 4-8**. Přímá komunikace HTTP

I když Přímá volání HTTP mezi mikroslužbami jsou relativně jednoduchá na implementaci, měli byste dbát na to, aby se tento postup minimalizoval. Pro spuštění jsou tato volání vždy *synchronní* a zablokují operaci, dokud není vrácen výsledek nebo dokud nevyprší časový limit požadavku. Jak byly samostatné, nezávislé služby, schopné vyvíjet nezávisle a často je nasazovat, teď se vzájemně navzájem vzájemně nasazují. V rámci zvyšování vzájemného propojení mezi mikroslužby se snižuje přínos jejich architektury.

Spuštění nečasté žádosti, která umožňuje jedno přímé volání HTTP do jiné mikroslužby, může být pro některé systémy přijatelné. Volání s vysokým objemem, která vyvolávají Přímá volání HTTP na více mikroslužeb, se však nedoporučuje. Můžou zvýšit latenci a negativně ovlivnit výkon, škálovatelnost a dostupnost vašeho systému. I horší, dlouhé série přímých komunikací HTTP může vést k podrobným a složitým řetězům synchronních volání mikroslužeb, které jsou znázorněné na obrázku 4-9:

![Řetězení dotazů HTTP](./media/chaining-http-queries.png)

**Obrázek 4-9**. Řetězení dotazů HTTP

V návrhu zobrazeném na předchozím obrázku si můžete představit riziko. Co se stane, když dojde k chybě kroku \#3? Nebo krok \#8 se nezdařil? Jak obnovovat? Co když je krok \#6 pomalý, protože podkladová služba je zaneprázdněná? Jak budete pokračovat? I když vše funguje správně, zamyslete se nad latencí tohoto volání, což je součet latence každého kroku.

Velký stupeň spojení na předchozím obrázku naznačuje, že služby nebyly optimálně modelovány. To by behoove týmu, aby znovu navštívilo svůj návrh.

### <a name="materialized-view-pattern"></a>Model materializované zobrazení

Oblíbenou možností pro odebrání spojení s mikroslužbami je [model materializované zobrazení](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). S tímto modelem mikroslužba ukládá svou vlastní místní, denormalizovanou kopii dat, která vlastní jiné služby. Místo nákupního košíku, který se dotazuje na službu Katalog produktů a cenové služby, zachovává svou vlastní místní kopii těchto dat. Tento model eliminuje zbytečné spojení a zlepšuje spolehlivost a dobu odezvy. Celá operace se provádí uvnitř jednoho procesu. Zkoumáme tento model a další otázky k datům v kapitole 5.

### <a name="service-aggregator-pattern"></a>Model Agregátoru služby

Další možností pro odstranění spojení mikroslužeb proti mikroslužbám je [agregátorová mikroslužba](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/), která je znázorněná fialově na obrázku 4-10.

![Služba Agregátoru](./media/aggregator-service.png)

**Obrázek 4-10**. Mikroslužba Agregátoru

Vzorek izoluje operaci, která umožňuje volat více back-endové mikroslužby a soustřeďuje logiku do specializované mikroslužby.  Mikroslužba Agregátoru pro fialovou rezervaci na předchozím obrázku orchestruje pracovní postup pro operaci rezervace. Zahrnuje volání několika mikroslužeb back-end v pořadí podle pořadí. Data z pracovního postupu se agreguje a vrátí volajícímu. I když stále implementuje Přímá volání HTTP, omezuje mikroslužba Agregátoru přímé závislosti mezi back-endové mikroslužby.

### <a name="requestreply-pattern"></a>Vzor požadavků a odpovědí

Dalším přístupem k odkládání synchronních zpráv HTTP je [vzor požadavku na odpověď](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html), který používá komunikaci pomocí fronty. Komunikace pomocí fronty je vždy jednosměrovým kanálem a producent posílá zprávu a příjemce obdrží. V tomto modelu jsou implementovány fronty požadavků i fronta odpovědí, zobrazené na obrázku 4-11.

![Vzor požadavku a odpovědi](./media/request-reply-pattern.png)

**Obrázek 4-11**. Vzor požadavku a odpovědi

V tomto případě producent zprávy vytvoří zprávu založenou na dotazech, která obsahuje jedinečné ID korelace, a umístí ji do fronty požadavků. Nenáročná služba vyřadí zprávy do fronty, zpracuje je a umístí odpověď do fronty odpovědí se stejným ID korelace. Služba producenta vyřadí zprávu, porovná ji s ID korelace a pokračuje ve zpracování. Fronty podrobněji pokrýváme v další části.

## <a name="commands"></a>Příkazy

Dalším typem interakce komunikace je *příkaz*. Mikroslužba může pro provedení akce potřebovat jinou mikroslužbu. Mikroslužba objednávání možná potřebuje, aby mikroslužba expedice vytvořila dodávku pro schválenou objednávku. Na obrázku 4-12 jedna mikroslužba, označovaná jako producent, pošle zprávu jiné mikroslužbě, příjemce a provede to.

![Interakce příkazů s frontou](./media/command-interaction-with-queue.png)

**Obrázek 4-12**. Interakce příkazů s frontou

Ve většině případů producent nevyžaduje odpověď a zprávu může spustit *a zapomenout* . Pokud je vyžadována odpověď, příjemce pošle samostatnou zprávu zpět producentovi na jiném kanálu. Zpráva příkazu se nejlépe odesílá asynchronně s frontou zpráv. podporováno nezjednodušeným zprostředkovatelem zpráv. V předchozím diagramu si všimněte, jak fronta odděluje a odděluje obě služby.

Fronta zpráv je zprostředkující konstrukce, přes kterou producent a příjemce docházejí zprávu. Fronty implementují asynchronní model zasílání zpráv typu Point-to-Point. Výrobce ví, kde je třeba odeslat a správně směrovat příkazy. Ve frontě je zaručeno, že zpráva je zpracována přes právě jednu z instancí spotřebitele, která je čtena z kanálu. V tomto scénáři může producent nebo služba příjemce škálovat horizontální navýšení kapacity, aniž by to mělo vliv na ostatní. I ty technologie můžou být různorodé na každé straně, což znamená, že mikroslužba Java může volat mikroslužbu [golang](https://golang.org) .

V kapitole 1 se mluvili o *službách zálohování*. Záložní služby jsou pomocné prostředky, na kterých jsou závislé nativní systémy cloudu. Fronty zpráv jsou zálohovací služby. Cloud Azure podporuje dva typy front zpráv, které můžou vaše cloudové nativní systémy využívat k implementaci zasílání zpráv příkazem: Azure Storage front a Azure Service Bus front.

### <a name="azure-storage-queues"></a>Fronty Azure Storage

Fronty Azure Storage nabízejí jednoduchou infrastrukturu ve frontě, která je rychlá, cenově a zálohovaná pomocí účtů úložiště Azure.

[Fronty Azure Storage se zařadí do fronty](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) založené na REST pomocí spolehlivého a trvalého zasílání zpráv. Poskytují minimální sadu funkcí, ale jsou levné a můžou ukládat miliony zpráv. Rozsah jejich kapacity je až 500 TB. Jedna zpráva může mít velikost až 64 KB.

Prostřednictvím ověřených volání přes protokol HTTP nebo HTTPS máte přístup k zprávám odkudkoli na světě. Fronty úložiště můžou škálovat na velké počty souběžných klientů a zpracovávat špičky provozu.

Tato služba má omezení ke službě:

- Není zaručeno pořadí zpráv.

- Zpráva může být zachována po dobu sedmi dní, než bude automaticky odebrána.

- Podpora správy stavů, duplicit duplicit nebo transakcí není k dispozici.

Obrázek 4-13 ukazuje hierarchii Azure Storage fronty.

![Hierarchie fronty úložiště](./media/storage-queue-hierarchy.png)

**Obrázek 4-13**. Hierarchie fronty úložiště

Na předchozím obrázku si všimněte, jak fronty úložiště ukládají své zprávy v podkladovém účtu Azure Storage.

Pro vývojáře nabízí Microsoft několik klientských a serverových knihoven pro zpracování fronty úložiště. Většina hlavních platforem je podporovaná, včetně .NET, Java, JavaScriptu, Ruby, Pythonu a přechodu. Vývojáři by nikdy neměli komunikovat přímo s těmito knihovnami. Provedete to tak, že kód mikroslužby pevně propojíte s Azure Storage Služba front. Je lepší postupovat při izolaci podrobností o implementaci rozhraní API. Zavedení vícevrstvé vrstvy nebo zprostředkujícího rozhraní API, které zpřístupňuje obecné operace a zapouzdřuje konkrétní knihovnu. Toto volné spojení vám umožní odpínat jednu službu Řízení front pro jinou, aniž by bylo nutné provádět změny v kódu služby hlavní.

Fronty Azure Storage jsou ekonomicky výhodné k implementaci příkazů pro zasílání zpráv v cloudových nativních aplikacích. Obzvláště když velikost fronty překročí 80 GB, nebo je jednoduchá sada funkcí přijatelná. Platíte jenom za úložiště zpráv. neexistují žádné pevné hodinové poplatky.

### <a name="azure-service-bus-queues"></a>Fronty Azure Service Bus

V případě složitějších požadavků na zasílání zpráv zvažte Azure Service Bus fronty.

Základem je robustní infrastruktura zpráv, která se šíří, [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) podporuje model zprostředkovaných *zpráv*. Zprávy jsou spolehlivě uloženy ve zprostředkovateli (fronty), dokud je příjemce neobdrží. Fronta garantuje doručování zpráv first-in/first-out (FIFO) a respektuje pořadí, ve kterém byly zprávy přidány do fronty.

Velikost zprávy může být mnohem větší, až do 256 KB. Zprávy jsou po neomezenou dobu uchovávány ve frontě. Service Bus podporuje nejen volání založené na protokolu HTTP, ale také poskytuje úplnou podporu pro [protokol AMPQ](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview). AMPQ je otevřený standard pro dodavatele, který podporuje binární protokol a vyšší úroveň spolehlivosti.

Service Bus poskytuje bohatou sadu funkcí, včetně [podpory transakcí](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) a [funkce zjišťování duplicitních](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection)dat. Fronta garantuje "po doručení" po každé zprávě. Automaticky zahodí zprávu, která již byla odeslána. Pokud je producent nejistý, může znovu odeslat stejnou zprávu a Service Bus garantuje, že bude zpracována pouze jedna kopie. Zjišťování duplicitních dat je bezplatné, protože nemusíte sestavovat další instalace infrastruktury.

Pro vytváření oddílů a relací jsou dvě další podnikové funkce. Konvenční Service Bus fronta se zpracovává pomocí jediného zprostředkovatele zpráv a je uložený v jednom úložišti zpráv. Ale [Service Bus rozdělení](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) do fronty v rámci více zprostředkovatelů zpráv a úložišť zpráv. Celková propustnost již není omezena výkonem jediného zprostředkovatele zpráv nebo úložiště pro zasílání zpráv. Dočasný výpadek úložiště pro zasílání zpráv nezobrazuje nedostupné oddíly rozdělené do oddílů.

[Service Bus relace](https://codingcanvas.com/azure-service-bus-sessions/) poskytují způsob, jak seskupit zprávy související se skupinami. Představte si scénář pracovního postupu, ve kterém se zprávy musí zpracovávat společně a operace skončila na konci. Aby bylo možné využít výhody, musí být relace explicitně povoleny pro frontu a každá související zpráva musí obsahovat stejné ID relace.

Existuje však několik důležitých aspektů: velikost fronty Service Bus je omezena na 80 GB, což je mnohem menší než v případě, že jsou k dispozici z fronty úložiště. Kromě toho Service Bus fronty účtují základní náklady a účtuje se na operaci.

Obrázek 4-14 popisuje architekturu Service Bus fronty na nejvyšší úrovni.

![Service Bus](./media/service-bus-queue.png)

**Obrázek 4-14**. Service Bus

Na předchozím obrázku si všimněte vztahu Point-to-Point. Dvě instance stejného poskytovatele jsou enqueuing zprávy do jedné fronty Service Bus. Každou zprávu spotřebují jenom jedna ze tří instancí příjemců na pravé straně. V dalším kroku se podíváme, jak implementovat zasílání zpráv, kde se stejnou zprávu můžou zajímat různí zákazníci.

## <a name="events"></a>Události

Služba Řízení front zpráv představuje účinný způsob, jak implementovat komunikaci, když producent může asynchronně poslat zprávu příjemce. Co se ale stane, když se stejná zpráva zajímá *mnoho různých uživatelů* ? Vyhrazená fronta zpráv pro každého příjemce by nemusela správně škálovat a měla by být obtížná spravovat.

Pro vyřešení tohoto scénáře se přesunete na třetí typ interakce zprávy, která je v *události*. Jedna mikroslužba oznamuje, že došlo k nějaké akci. Další mikroslužby, pokud to zajímá, reagují na akci nebo na událost.

Událost je proces se dvěma kroky. Pro danou změnu stavu mikroslužba publikuje událost zprostředkovateli zpráv a zpřístupní ji všem dalším zúčastněným mikroslužbám. Zúčastněná mikroslužba je informována o přihlášení k odběru události v zprostředkovateli zpráv. Ke implementaci [komunikace založené na událostech](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications)slouží model [publikování/odběr](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) .

Obrázek 4-15 ukazuje mikroslužbu nákupního košíku, která publikuje událost se dvěma ostatními mikroslužbami k přihlášení.

![Zasílání zpráv řízených událostmi](./media/event-driven-messaging.png)

**Obrázek 4-15**. Zasílání zpráv řízených událostmi

Poznamenejte si součást *Sběrnice událostí* , která je umístěná uprostřed komunikačního kanálu. Jedná se o vlastní třídu, která zapouzdřuje zprostředkovatele zpráv a oddělí ho od příslušné aplikace. Mikroslužby řazení a inventarizace nezávisle provozují událost bez jakýchkoli znalostí ani mikroslužby nákupního košíku. Když je registrovaná událost publikovaná do sběrnice událostí, na ni působí.

S událostmi přesouváme z technologie řízení front zpráv na *témata*. [Téma](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) se podobá frontě, ale podporuje vzor zasílání zpráv 1: n. Jedna mikroslužba publikuje zprávu. U této zprávy se může rozhodnout, že se bude tato zpráva přijímat a reagovat na více než více služeb odběru. Obrázek 4-16 ukazuje architekturu tématu.

![Architektura tématu](./media/topic-architecture.png)

**Obrázek 4-16**. Architektura tématu

Na předchozím obrázku odesílají vydavatelé zprávy do tématu. Na konci předplatitelé obdrží zprávy od předplatných. Uprostřed se v tomto tématu předají zprávy do předplatných založených na sadě *pravidel*, která jsou zobrazená v tmavě modrých polích. Pravidla slouží jako filtr, který předávají konkrétní zprávy do předplatného. Tady se pošle událost "CreateOrder" do předplatného \#1 a předplatné \#3, ale ne do předplatného \#2. Do předplatného \#2 a předplatné \#3 se pošle událost "OrderCompleted".

Cloud Azure podporuje dvě různé služby tématu: Azure Service Bus témata a Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Azure Service Bus témata

[Azure Service Bus témata](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)se koná nad stejným robustním modelem zprostředkovaných zpráv Azure Service Bus fronty. Téma může přijímat zprávy od více nezávislých vydavatelů a odesílat zprávy až 2 000 předplatitelů. Odběry je možné dynamicky přidávat nebo odebírat za běhu bez zastavení systému nebo opětovného vytváření tématu.

K dispozici je také mnoho pokročilých funkcí z front Azure Service Bus, včetně [zjišťování duplicit](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) a [podpory transakcí](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions). Ve výchozím nastavení se Service Bus témata zpracovávají pomocí jediného zprostředkovatele zpráv a ukládají se do jednoho úložiště zpráv. [Service Bus rozdělení na oddíly](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) ale škáluje téma tím, že se rozprostře mezi mnoho zprostředkovatelů zpráv a úložišť zpráv.

[Naplánovaná](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) zpráva o doručení označuje zprávu s určitou dobou pro zpracování. Zpráva se v tématu před časem nezobrazí. [Odložení zprávy](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) umožňuje odložit načtení zprávy na pozdější dobu. Obě možnosti se běžně používají ve scénářích zpracování pracovního postupu, kdy se operace zpracovávají v určitém pořadí. Zpracování přijatých zpráv můžete odložit až do dokončení předchozí práce.

Témata Service Bus jsou robustní a prověřená technologie pro povolení komunikace s publikováním a odběrem v cloudových nativních systémech.

### <a name="azure-event-grid"></a>Azure Event Grid

I když je Azure Service Bus poskytovatel zasílání zpráv s plnou platností, [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) je nový dítě na bloku.

Na první pohled může Event Grid vypadat stejně jako jiný systém zasílání zpráv na základě tématu. Liší se ale v mnoha ohledech. Zaměřuje se na úlohy řízené událostmi, které umožňují zpracování událostí v reálném čase, rozsáhlou integraci Azure a otevřenou platformu na infrastruktuře bez serveru. Je navržený pro moderní cloudové a nativní aplikace bez serveru.

Jako centralizované *obslužné*nebo potrubní Event Grid reaguje na události v prostředcích Azure a z vašich vlastních služeb.

Oznámení událostí jsou publikována v Event Grid tématu, které následně směruje každou událost na předplatné. Předplatitelé mapují na předplatná a spotřebovávají události. Stejně jako u Service Bus Event Grid podporuje *filtrovaný model odběratele* , kde předplatné nastavuje pravidlo pro události, které chce přijmout. Event Grid poskytuje rychlou propustnost s jistotou 10 000 000 událostí za sekundu, které umožňují téměř větší doručování v reálném čase, než Azure Service Bus může generovat.

Sladkou skvrnou pro Event Grid je jeho Hluboká integrace do prostředků infrastruktury Azure. Prostředek Azure, například Cosmos DB, může publikovat integrované události přímo do jiných zúčastněných prostředků Azure – bez nutnosti vlastního kódu. Event Grid může publikovat události z předplatného Azure, skupiny prostředků nebo služby a poskytnout vývojářům jemně odstupňovanou kontrolu nad životním cyklem cloudových prostředků. Event Grid ale nejsou omezené na Azure. Je to otevřená platforma, která může využívat vlastní události HTTP publikované z aplikací nebo služeb třetích stran a události směrování externím předplatitelům.

Při publikování a přihlášení k odběru nativních událostí z prostředků Azure se nevyžaduje žádné kódování. Díky jednoduché konfiguraci můžete integrovat události z jednoho prostředku Azure do jiného, který využívá integrované instalace pro témata a odběry. Obrázek 4-17 ukazuje anatomii Event Grid.

![Event Grid anatomie](./media/event-grid-anatomy.png)

**Obrázek 4-17**. Event Grid anatomie

Hlavním rozdílem mezi EventGrid a Service Bus je základní *vzor výměny zpráv*.

Service Bus implementuje starší *model Pull* ve stylu, ve kterém se předplatitelé pro příjem dat aktivně dotazují na odběr nových zpráv v tématu. Po celou stranu tento přístup umožňuje předplatiteli úplné řízení tempa, při kterém zpracovává zprávy. Řídí, kdy a kolik zpráv se má v daném čase zpracovat. Nepřečtené zprávy zůstávají v předplatném až do zpracování. Významnou nedostatkem je latence mezi tím, kdy se událost generuje, a operací cyklického dotazování, která tuto zprávu vyžádá do předplatitele ke zpracování. Navíc režie konstantního cyklického dotazování pro další událost spotřebovává prostředky a peníze.

EventGrid se ale liší. Implementuje *model push* , ve kterém jsou události odesílány do událostí EventHandler, jak byly přijaty, což poskytuje téměř v reálném čase doručení událostí. Také snižuje náklady, protože služba se aktivuje jenom v případě, že je potřeba spotřebovat událost – neprůběžně jako při cyklickém dotazování. V takovém případě obslužná rutina události musí zpracovat příchozí zatížení a zajistit mechanismy omezování ochrany před zahlcením. Řada služeb Azure, které využívají tyto události, jako jsou Azure Functions a Logic Apps, poskytují automatické možnosti automatického škálování pro zpracování zvýšené zátěže.  

Event Grid je plně spravovaná cloudová služba bez serveru. Dynamicky se škáluje podle vašich přenosů a účtuje se jenom za skutečné využití, a ne na předem zakoupenou kapacitu. Prvních 100 000 operací za měsíc je zdarma – operace se definují jako příchozí události (příchozí oznámení událostí), pokusy o doručení, volání správy a filtrování podle předmětu. S 99,99% dostupností EventGrid garantuje doručení události během 24 hodin s integrovanou funkcí opakování pro neúspěšné doručení. Nedoručené zprávy lze pro rozlišení přesunout do fronty nedoručených zpráv.  Na rozdíl od Azure Service Bus je Event Grid vyladěno pro rychlý výkon a nepodporuje funkce jako objednané zasílání zpráv, transakce a relace.

### <a name="streaming-messages-in-the-azure-cloud"></a>Streamování zpráv v cloudu Azure

Azure Service Bus a Event Grid poskytuje skvělou podporu pro aplikace, které zveřejňují jednotlivé diskrétní události, jako je nový dokument, vložen do Cosmos DB. Ale co dělat v případě, že systém nativní pro Cloud potřebuje zpracovat *Stream souvisejících událostí*? [Datové proudy událostí](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) jsou složitější. Typicky se jedná o časově uspořádané, vzájemně seřazené a musí být zpracovávány jako skupina.

[Centrum událostí Azure](https://azure.microsoft.com/services/event-hubs/) je platforma pro streamování dat a služba pro příjem událostí, která shromažďuje, transformuje a ukládá události. Je vyladěný tak, aby zachytával streamovaná data, například nepřetržitá oznámení o událostech emitovaných z kontextu telemetrie. Služba je vysoce škálovatelná a může ukládat a [zpracovávat miliony událostí za sekundu](https://docs.microsoft.com/azure/event-hubs/event-hubs-about). Znázorněné na obrázku 4-18 je často předním dveřem pro kanál událostí, která odpojuje datový proud ingestuje od spotřeby událostí.

![Centrum událostí Azure](./media/azure-event-hub.png)

**Obrázek 4-18**. Centrum událostí Azure

Centrum událostí podporuje nízkou latenci a konfigurovatelné časové uchovávání. Na rozdíl od front a témat Event Hubs uchovat data událostí poté, co je uživatel přečte. Tato funkce umožňuje jiným datovým službám (interním i externím) přehrávat data pro další analýzu. Události uložené v centru událostí se odstraní jenom po vypršení doby uchování, což je ve výchozím nastavení jeden den, ale dá se konfigurovat.

Centrum událostí podporuje společné protokoly pro publikování událostí, včetně protokolu HTTPS a AMQP. Podporuje také Kafka 1,0. [Stávající aplikace Kafka můžou komunikovat s centrem událostí](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) pomocí protokolu Kafka, který poskytuje alternativu ke správě rozsáhlých clusterů Kafka. Spousta Open Source nativních systémů se Kafka přidaných v cloudu.

Event Hubs implementuje streamování zpráv prostřednictvím [děleného](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) dodavatelského modelu, ve kterém každý příjemce přečte jenom určitou podmnožinu nebo oddíl datového proudu zpráv. Tento model umožňuje obrovské horizontální škálování pro zpracování událostí a poskytuje další funkce zaměřené na streamy, které nejsou ve frontách a tématech dostupné. Oddíl je seřazená posloupnost událostí, která se nachází v centru událostí. Jakmile přijdete o novější události, přidají se na konec této sekvence. Obrázek 4-19 ukazuje dělení do oddílů v centru událostí.

![Vytváření oddílů centra událostí](./media/event-hub-partitioning.png)

**Obrázek 4-19**. Vytváření oddílů centra událostí

Místo čtení ze stejného prostředku každá skupina uživatelů čte celou podmnožinu nebo oddíl datového proudu zpráv.

V případě cloudových nativních aplikací, které musí streamovat velký počet událostí, může být centrum událostí Azure robustní a dostupné řešení.

>[!div class="step-by-step"]
>[Předchozí](front-end-communication.md)
>[Další](rest-grpc.md)
