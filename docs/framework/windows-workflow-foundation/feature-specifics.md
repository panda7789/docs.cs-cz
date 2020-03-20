---
title: Specifické funkce Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 11bde5edea44f09ef1a5658cdf0e20ec1349c84b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182926"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Specifické funkce Windows Workflow Foundation

Rozhraní .NET Framework 4 přidává do nadace Windows Workflow Foundation řadu funkcí. Tento dokument popisuje řadu nových funkcí a poskytuje podrobnosti o scénářích, ve kterých mohou být užitečné.

## <a name="messaging-activities"></a>Aktivity zasílání zpráv

Aktivity zasílání<xref:System.ServiceModel.Activities.Receive>zpráv <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Send>( <xref:System.ServiceModel.Activities.ReceiveReply>, , , ) se používají k odesílání a přijímání zpráv WCF z pracovního postupu. <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají k vytvoření operace služby WCF (Windows Communication Foundation), která je vystavena prostřednictvím WSDL stejně jako standardní webové služby WCF. <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.ReceiveReply> používají se ke spotřebovávat <xref:System.ServiceModel.ChannelFactory>webové služby podobné WCF ; **prostředí Add Service Reference** existuje také pro Workflow Foundation, který generuje předem nakonfigurované aktivity.

### <a name="getting-started-with-messaging-activities"></a>Začínáme s aktivitami zasílání zpráv

- V sadě Visual Studio 2012 vytvořte projekt aplikace služby WCF Workflow Service. A <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> a pár budou umístěny na plátně.

- Klikněte pravým tlačítkem myši na projekt a vyberte **přidat odkaz na službu**. Přejděte na existující webovou službu WSDL a klepněte na tlačítko **OK**. Sestavte si svůj projekt zobrazit <xref:System.ServiceModel.Activities.Send> generované <xref:System.ServiceModel.Activities.ReceiveReply>aktivity (implementované pomocí a ) v panelu nástrojů.

- [Dokumentace služeb pracovního postupu](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Scénář příklad aktivit zasílání zpráv

Služba `BestPriceFinder` volá na více leteckých služeb najít nejlepší cenu letenky pro konkrétní trasu. Implementace tohoto scénáře by vyžadovala použití aktivitzprávy k přijetí požadavku na cenu, načtení cen ze služeb back-end a odpovědi na požadavek na cenu s nejlepší cenou. To by také vyžadovat, abyste použít jiné out-of-box aktivity k vytvoření obchodní logiky pro výpočet nejlepší ceny.

## <a name="workflowservicehost"></a>Workflowservicehost

Jedná <xref:System.ServiceModel.WorkflowServiceHost> se o out-of-box workflow hostitele, který podporuje více instancí, konfigurace a WCF zasílání zpráv (i když pracovní postupy nejsou nutné používat zasílání zpráv, aby byly hostovány). Také integruje s trvalost, sledování a řízení instancí prostřednictvím sady chování služby. Stejně jako WCF <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.WorkflowServiceHost> , může být vlastní hostované v konzoli / WinForms / WPF aplikace nebo služby Systému Windows, nebo web-hostované (jako soubor Xamlx) ve službě IIS nebo WAS.

### <a name="getting-started-with-workflow-service-host"></a>Začínáme s hostitelem služby pracovního postupu

- V sadě Visual Studio 2010 vytvořte projekt aplikace služby WCF <xref:System.ServiceModel.WorkflowServiceHost> Workflow Service: tento projekt bude nastaven pro použití v prostředí webhostingu.

- Chcete-li být hostitelem pracovního postupu <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> bez zasílání zpráv, přidejte vlastní, která vytvoří instanci na základě zprávy.

- Instance pracovního postupu lze ovládat (např. pozastaveno nebo <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> ukončeno) přidáním a a <xref:System.ServiceModel.WorkflowServiceHost> potom pomocí <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Vzorky <xref:System.ServiceModel.WorkflowServiceHost> pro tyto vzorky naleznete v následujících oddílech:

  - [Spouštěcí](./samples/execution.md)

  - Aplikace: [Správa pozastavených instancí](./samples/suspended-instance-management.md)

- [Přehled služeb hostování pracovního postupu](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Scénář WorkflowServiceHost

Služba BestPriceFinder volá na více leteckých služeb najít nejlepší cenu letenky pro konkrétní trasu. Implementace tohoto scénáře by vyžadovala hostování <xref:System.ServiceModel.WorkflowServiceHost>pracovního postupu v aplikaci . To by také použít zprávy aktivity přijímat žádost o cenu, načíst ceny z back-end služby a odpověď na žádost o cenu s nejlepší cenou.

## <a name="correlation"></a>Korelace

Korelace je jedna ze dvou věcí:

- Způsob seskupení zpráv dohromady; to znamená vztah mezi zprávou požadavku a její odpovědí.

- Způsob mapování části dat na instanci služby

### <a name="getting-started"></a>Začínáme

- Chcete-li začít s korelací, vytvořte nový projekt v sadě Visual Studio. Vytvořte proměnnou <xref:System.ServiceModel.Activities.CorrelationHandle>typu .

- Příkladem korelace používané ke skupině zpráv dohromady je požadavek odpověď korelace, která seskupuje zprávy dohromady.

  - Na <xref:System.ServiceModel.Activities.Receive> aktivitu klikněte <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> na vlastnost <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> a přidejte pomocí CorrelationHandle vytvořené v prvním kroku výše.

  - Vytvořte <xref:System.ServiceModel.Activities.SendReply> aktivitu kliknutím pravým <xref:System.ServiceModel.Activities.Receive> tlačítkem myši na tlačítko "Vytvořit sendreply". Po aktivitě jej <xref:System.ServiceModel.Activities.Receive> vložte do pracovního postupu.

- Příkladem mapování části dat na instanci služby je korelace založená na obsahu, která mapuje část dat (například ID objednávky) na konkrétní instanci pracovního postupu.

  - Při jakékoli aktivitě zasílání `CorrelationInitializers` zpráv klikněte <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> na <xref:System.ServiceModel.Activities.CorrelationHandle> vlastnost a přidejte pomocí výše vytvořené proměnné. Poklepejte na požadovanou vlastnost na zprávě (např. Nastavte `CorrelatesWith` vlastnost na <xref:System.ServiceModel.Activities.CorrelationHandle> proměnnou použitou výše.

- [Koncepční dokumentace korelace](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scénář korelace

Pracovní postup zpracování objednávek se používá ke zpracování nového vytváření objednávek a aktualizaci existujících objednávek, které jsou v procesu. Implementace tohoto scénáře by vyžadovala hostování <xref:System.ServiceModel.WorkflowServiceHost> pracovního postupu v aktivitách zasílání zpráv a jejich použití. To by také vyžadovat `orderId` korelace na základě zajistit, že aktualizace jsou prováděny na správný pracovní postup.

## <a name="simplified-configuration"></a>Zjednodušená konfigurace

Schéma konfigurace WCF je složité a poskytuje uživatelům mnoho funkcí, které se těžko nacházejí. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]aplikaci jsme se zaměřili na pomoc uživatelům WCF při konfiguraci jejich služeb s následujícími funkcemi:

- Odstranění potřeby explicitní konfigurace pro službu. Pokud nenakonfigurujete žádné \<prvky služby> pro vaši službu a vaše služba nedefinuje programově žádný koncový bod, bude automaticky přidána sada koncových bodů do vaší služby, jedna na adresu základny služby a na smlouvu implementovanou vaší službou.

- Umožňuje uživateli definovat výchozí hodnoty pro vazby WCF a chování, které budou použity pro služby bez explicitní konfigurace.

- Standardní koncové body definují opakovaně použitelné předkonfigurované koncové body, které mají pevné hodnoty pro jednu nebo více vlastností koncového bodu (adresa, vazba a smlouva) a umožňují definování vlastních vlastností.

- Nakonec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umožňuje provést centrální správu konfigurace klienta WCF, užitečné ve scénářích, ve kterých je konfigurace vybrána nebo změněna po době načítání domény aplikace.

### <a name="getting-started"></a>Začínáme

- [Průvodce vývojářem wcf 4.0](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Objekt pro vytváření kanálů konfigurace](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Standardní prvek koncového bodu](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [Vylepšení konfigurace služby v rozhraní .NET Framework 4](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [Běžná chyba uživatele v rozhraní .NET 4: Chybné zadání názvu konfigurace služby WF/WCF](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>Zjednodušené scénáře konfigurace

- Zkušený vývojář ASMX chce začít používat WCF. Nicméně, WCF se zdá příliš složité! Jaké jsou všechny tyto informace, které potřebuji k zápisu do konfiguračního souboru? V rozhraní .NET 4 se dokonce můžete rozhodnout, že konfigurační soubor vůbec nebudete mít.

- Existující sadu služeb WCF je velmi obtížné konfigurovat a udržovat. Konfigurační soubor má tisíce řádků kódu XML, které jsou velmi nebezpečné na dotek. Nápověda je potřeba snížit toto množství kódu na něco lépe spravovatelné.

## <a name="data-contract-resolver"></a>Překladač kontraktů dat

V rozhraní .NET 3.5 existovalo několik omezení v návrhu známých typů:

- Dynamické přidání známých typů během serializace nebo deserializace nebylo možné.

- Serializátory nemohly řešit neznámé informace typu xsi:type.

- Nebylo možné, aby uživatelé specifikovali, jaký typ xsi:by chtěli mít v drátě, například zmenšit velikost instance serializace v drátu.

[DataContractResolver](../wcf/samples/datacontractresolver.md) řeší tyto problémy v .NET 4.5.

### <a name="getting-started"></a>Začínáme

- [Dokumentace rozhraní API překladače kontraktů dat](xref:System.Runtime.Serialization.DataContractResolver)

- [Představujeme překladač kontraktů dat](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- Vzorky:

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scénáře překladače kontraktu dat

- Vyhněte se nutnosti deklarovat desítky <xref:System.Runtime.Serialization.KnownTypeAttribute> objektů ve službě.

- Zmenšení velikosti objektu blob XML.

## <a name="flowchart"></a>Vývojový diagram

Vývojový diagram je dobře známé paradigma vizuálně představují problémy domény. Jedná se o nový styl toku řízení, který zavádíme v rozhraní .NET 4. Základní charakteristikou vývojového diagramu je, že v daném okamžiku je spuštěna pouze jedna aktivita. Vývojové diagramy mohou vyjadřovat smyčky a alternativní výsledky, ale nemohou nativně vyjádřit souběžné provádění více uzlů.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte vývojový diagram do návrháře pracovního postupu.

- Funkce vývojového diagramu používá následující třídy:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Vzorky:

  - [Zpracování chyb v aktivitě FlowChart pomocí TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [Proces náboru](./samples/hiring-process.md)

- Dokumentace návrháře:

  - [Návrháři aktivit vývojového diagramu](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Scénáře vývojového diagramu

Vývojový diagram aktivity lze použít k implementaci hádání hry. Hádání hra je velmi jednoduchá: počítač vybere náhodné číslo a hráč musí uhodnout, že číslo. Když hráč odešle každý odhad, počítač jim ukáže nápovědu (tj. "zkuste nižší číslo"). Pokud hráč najde číslo v méně než 7 pokusech, obdrží speciální gratulaci z počítače. Tato hra může být realizován s kombinací následujících procedurálních činností:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Procedurální činnosti (Sekvence, If, ForEach, Switch, Assign, DoWhile, While)

Procedurální aktivity poskytují mechanismus pro modelování sekvenčního toku řízení pomocí konceptů, které jsou programátorům známé. Tyto aktivity umožňují tradičně strukturované konstrukce programovacích jazyků a v případě potřeby poskytují paritu jazyka s běžnými procedurálními jazyky, jako je c# a visual basic.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte procedurální aktivity do návrháře pracovního postupu.

- Vzorky:

  - [Proces náboru](./samples/hiring-process.md)

  - [Proces nákupu v podniku](./samples/corporate-purchase-process.md)

- Dokumentace návrháře:

  - [Návrhář aktivity Parallel](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T> Návrhář aktivity](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scénáře procedurální aktivity

- <xref:System.Activities.Statements.Parallel>: Systém správy dokumentů v intranetu má pracovní postup schvalování dokumentů. Dokumenty musí být schváleny lidmi v několika odděleních, než mohou být publikovány do intranetu. Neexistuje zavedený příkaz pro schválení; mohou nastat kdykoli, zatímco dokument je ve fázi "schválení čeká" . Když uživatel odešle dokument ke kontrole, musí být schválen jejich přímým správcem, správcem sítě intranet a interním správcem komunikace.

- <xref:System.Activities.Statements.ParallelForEach%601>: Aplikace WF spravuje firemní nákupy v rámci velké společnosti. Podniková pravidla určují, že před plánováním jakékoli nákupní operace je vyžadováno ocenění tří různých dodavatelů. Zaměstnanec nákupního oddělení vybere ze seznamu dodavatelů společnosti tři dodavatele. Poté, co tito dodavatelé byli vybráni a oznámeno, bude společnost čekat na své ekonomické návrhy. Návrhy mohou být v libovolném pořadí. Chcete-li implementovat tento scénář <xref:System.Activities.Statements.ParallelForEach%601> v WF, použijeme, který bude iterate prostřednictvím naší kolekce dodavatelů a požádat o jejich ekonomické návrhy. Po shromáždění všech nabídek je vybrána a zobrazena nejlepší nabídka.

## <a name="invokemethod"></a>InvokeMethod

Aktivita <xref:System.Activities.Statements.InvokeMethod> umožňuje vyvolání veřejných metod v objektech nebo typech v oboru. Podporuje vyvolání instance a statické metody s nebo bez parametrů (včetně pole parametrů) a obecné metody. Umožňuje také provádění metody synchronně a asynchronně.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte <xref:System.Activities.Statements.InvokeMethod> aktivitu v návrháři pracovního postupu a nakonfigurujte na ní statické metody a metody instancí.

- Dokumentace návrháře: [InvokeMethod Návrhář aktivity](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Scénáře invokemethod

- Metoda v objektu v oboru musí být vyvolána. Například je třeba přidat hodnotu do slovníku. Add Metoda instance slovníku je vyvolána a klíč a hodnota jsou k dispozici.

- Metoda musí být vyvolána na starší objekt CLR. Místo vytváření vlastní aktivity zabalit volání této starší třídy, pokud je <xref:System.Activities.Statements.InvokeMethod> v oboru během provádění pracovního postupu, lze použít.

## <a name="error-handling-activities"></a>Činnosti zpracování chyb

Aktivita <xref:System.Activities.Statements.TryCatch> poskytuje mechanismus pro zachycení výjimky, ke kterým dochází při provádění sadu obsažené aktivity (podobně jako Try/Catch konstrukce v jazyce C# a Visual Basic). <xref:System.Activities.Statements.TryCatch>poskytuje zpracování výjimek na úrovni pracovního postupu. Při vyvolání neošetřené výjimky je přerušeno pracovní ho sazí a finally blok nebude proveden. Toto chování je konzistentní s C#.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte <xref:System.Activities.Statements.TryCatch> aktivitu do návrháře pracovního postupu.

- Ukázka: [Zpracování chyb v aktivitě vývojového diagramu pomocí trycatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Dokumentace návrháře: [Návrháři aktivit zpracování chyb](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Při zpracování scénářů došlo k chybě.

Sada aktivit musí být provedena a konkrétní logiku je třeba provést, když dojde k chybě. Pokud během této logiky zpracování chyb je zjištěno, že chyba není obnovitelná, výjimka bude znovu vyvolána a nadřazená aktivita (nebo hostitel) bude problém řešit.

## <a name="pick-activity"></a>Aktivita vyskladnění

Aktivita <xref:System.Activities.Statements.Pick> poskytuje modelování toku řízení založené na událostech v wf. <xref:System.Activities.Statements.Pick>obsahuje mnoho větví, kde každá větev čeká na konkrétní událost dojít před spuštěním. V tomto nastavení <xref:System.Activities.Statements.Pick> se chová podobně <xref:System.Activities.Statements.Switch%601> jako a, které aktivita spustí pouze jednu sadu událostí, které naslouchá. Každá větev je řízena událostmi a událost, ke které dojde, nejprve spustí odpovídající větev. Všechny ostatní větve zrušit a přestat naslouchat události.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte <xref:System.Activities.Statements.Pick> aktivitu do návrháře pracovního postupu.

- Ukázka: [Použití aktivity vyskladnění](./samples/using-the-pick-activity.md)

- Dokumentace návrháře: [Návrhář aktivit výběru](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Scénář výběru

Uživatel musí být vyzván k zadání vstupu. Za normálních okolností by vývojář použít <xref:System.Console.ReadLine%2A> volání metody jako výzvu k zadání vstupu uživatele. Problém s tímto nastavením je, že program čeká, dokud uživatel zadá něco. V tomto scénáři je zapotřebí časový limit k odblokování blokování aktivity. Běžný scénář je takový, který vyžaduje dokončení úkolu v daném časovém období. Vypršení časového nastavení blokování aktivity je scénář, kde Pick přidá velké množství hodnoty.

## <a name="wcf-routing-service"></a>Služba směrování WCF

Služba směrování je navržena jako obecný softwarový směrovač, který umožňuje řídit, jak zprávy WCF proudí mezi klienty a službami. Služba směrování umožňuje oddělit klienty od vašich služeb, což vám dává mnohem větší svobodu, pokud jde o konfigurace, které můžete podporovat, a flexibilitu, kterou máte při zvažování, jak hostovat své služby. V rozhraní .NET 3.5 byli klienti a služby úzce spojeni; klient musel vědět o všech službách, se kterými potřeboval mluvit a kde se nacházeli. Kromě toho WCF v rozhraní .NET Framework 3.5 měl následující omezení:

- Zpracování chyb bylo složité, protože tato logika musela být pevně zakódována do klienta.

- Klienti a služby museli vždy používat stejné vazby.

- Služby byly zřídka dobře zohledněny: je snazší mít klienta mluvit s jednou službou, která implementuje vše, spíše než muset vybrat mezi více službami.

Služba směrování v rozhraní .NET 4 je navržena tak, aby tyto problémy snadněji řešit. Nová služba směrování má následující funkce:

1. Směrování založené<xref:System.ServiceModel.Dispatcher.MessageFilter> na obsahu ( objekty prověří zprávu a určí, kam má být odeslána.)

2. Přemostění protokolu (přenos & zprávy)

3. Zpracování chyb (směrovač zachytí výjimky komunikace a převezme služby při selhání do záložních koncových bodů)

4. Dynamická (v paměti) aktualizace <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> a konfigurace směrování.

### <a name="getting-started"></a>Začínáme

1. Dokumentace: [Směrování](../wcf/feature-details/routing.md)

2. Ukázky: [Služby směrování &#91;ukázky WCF&#93;](../wcf/samples/routing-services.md)

3. Blog: [Pravidla směrování!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>Scénáře směrování

Služba směrování je užitečná v následujících scénářích:

- Klienti mohou mluvit s více službami, aniž by je museli řešit všechny přímo.

- Klienti mohou provádět další logiku na požadavek klienta k určení, kam směrovat

- Rozkládají operace klientprovádí do více implementací služby bez refaktoringu klienta.

- Klienti a služby mohou mluvit různými vazbami s různým nastavením zabezpečení.

- Klienti mohou být povoleny být robustnější proti selhání nebo nedostupnosti služeb.

## <a name="wcf-discovery"></a>Zjišťování WCF

WCF Discovery je technologie architektury, která umožňuje začlenit mechanismus zjišťování do infrastruktury aplikací. Můžete použít k tomu, aby vaše služba zjistitelné a nakonfigurovat své klienty pro vyhledávání služeb. Klienti již nemusí být pevně zakódováni s koncovým bodem, takže vaše aplikace robustnější a odolné proti chybám. Discovery je perfektní platforma pro vytváření možností automatické konfigurace do vaší aplikace.

Produkt je postaven na standardu WS-Discovery. Je navržen tak, aby byl interoperabilní, rozšiřitelný a obecný. Výrobek podporuje dva režimy provozu:

1. Spravováno: pokud je v síti entita s vědomím existujících služeb, klienti se o to přímo dotazují na informace. To je obdobou služby Active Directory.

2. Ad-hoc: kde klienti používají zprávy vícesměrového vysílání k vyhledání služeb.

Zprávy zjišťování jsou navíc agnostik síťového protokolu; můžete je použít na vrcholu libovolný protokol, který podporuje požadavky na režim. Zprávy o zjišťování vícesměrového vysílání lze například odesílat prostřednictvím kanálu UDP nebo jiné sítě, která podporuje zasílání zpráv vícesměrového vysílání. Tyto body návrhu v kombinaci s flexibilitou funkcí umožňují přizpůsobit zjišťování konkrétně vašemu řešení.

### <a name="getting-started"></a>Začínáme

- Dokumentace: [Zjišťování WCF](../wcf/feature-details/wcf-discovery.md)

- Ukázky: [Zjišťování (ukázky)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Scénáře zjišťování

Vývojář nechce pevné koncové body kódu, protože není známo, kdy bude moje služba k dispozici. Místo toho vývojář chce zvolit službu za běhu. Mezi součástmi v aplikaci je zapotřebí více oddělení, robustnosti a automatické konfigurace.

## <a name="tracking"></a>Sledování

Sledování pracovního postupu poskytuje přehled o provádění instance pracovního postupu. Události sledování jsou vydávány z pracovního postupu na úrovni instance pracovního postupu a při spuštění aktivit v rámci pracovního postupu. Účastník sledování pracovního postupu musí být přidán do hostitele pracovního postupu, aby se přihlásil ke sledování záznamů. Záznamy sledování jsou filtrovány pomocí profilu sledování. Rozhraní .NET Framework poskytuje účastníka sledování ETW (Event Tracing for Windows) a v souboru machine.config je nainstalován základní profil.

### <a name="getting-started"></a>Začínáme

1. V sadě Visual Studio 2010 vytvořte projekt aplikace služby WCF Workflow Service. A <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> a pár budou umístěny na plátně začít.

2. Otevřete web.config a přidejte chování sledování ETW bez profilu.

    1. Používá se výchozí profil.

    2. Otevřete prohlížeč událostí a povolte analytický kanál v následujícím uzlu: **Prohlížeč událostí**, **Protokoly aplikací a služeb**, **Microsoft**, **Windows**, **Application Server-Applications .** Klepněte pravým tlačítkem myši na **službu Analytick** a vyberte **příkaz Povolit protokol**.

    3. Spusťte službu pracovního postupu.

    4. Sledujte události sledování pracovního postupu v prohlížeči událostí.

3. Ukázky: [Sledování](./samples/tracking.md)

4. Koncepční dokumentace: [Sledování a trasování pracovního postupu](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Úložiště instancí pracovních postupů SQL

Jedná <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> se o implementaci úložiště instancí založenou na serveru SQL Server. Úložiště instance ukládá stav spuštěné instance spolu se všemi daty potřebnými k načtení a obnovení této instance. Hostitel služby dá pokyn úložišti instance, aby uložilo stav instance, pokud pracovní postup přetrvává, a instruuje úložiště instancí, aby načetlo stav instance, když pro tuto instanci dorazí zpráva nebo vyprší platnost aktivity zpoždění.

### <a name="getting-started"></a>Začínáme

1. V Sadě Visual Studio 2012 vytvořte pracovní <xref:System.Activities.Statements.Persist> postup, který obsahuje implicitní nebo explicitní aktivitu. Přidejte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> chování do hostitele služby pracovního postupu. To lze provést v kódu nebo v konfiguračním souboru aplikace.

2. Ukázky: [Perzistence](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Koncepční dokumentace: [Úložiště instancí pracovního postupu SQL](sql-workflow-instance-store.md).
