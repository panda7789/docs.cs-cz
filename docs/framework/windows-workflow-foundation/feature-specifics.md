---
title: Specifické funkce Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 063d2472443431423cea9b164831cd1e7a669408
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753717"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Specifické funkce Windows Workflow Foundation

[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] Přidá celou řadu funkcí pro Windows Workflow Foundation. Tento dokument popisuje několik nových funkcí a poskytuje podrobnosti o scénářích, ve kterých mohou být užitečné.

## <a name="messaging-activities"></a>Aktivity zasílání zpráv

Zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) se používají k odesílání a příjem zpráv WCF z pracovního postupu. <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají k vytvoření operaci služby Windows Communication Foundation (WCF), který je zveřejněný prostřednictvím WSDL stejně jako standardní webové služby WCF. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> se používají k využívání webové služby WCF podobný <xref:System.ServiceModel.ChannelFactory>; **přidat odkaz na službu** prostředí existuje také pro Workflow Foundation, který generuje předem nakonfigurované aktivity.

### <a name="getting-started-with-messaging-activities"></a>Začínáme se službou zasílání zpráv aktivity

- V sadě Visual Studio 2012 vytvořte projekt aplikace služby pracovního postupu WCF. A <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> pár se umístí na plátně.

- Klikněte pravým tlačítkem na projekt a vyberte **přidat odkaz na službu**. Přejděte do existující webové služby WSDL a klikněte na tlačítko **OK**. Sestavení projektu zobrazíte generované aktivity (implementované pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply>) ve vašem panelu nástrojů.

- [Dokumentace služby pracovního postupu](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Zasílání zpráv aktivity ukázkový scénář

A `BestPriceFinder` služby zdůrazňuje k více službám letecká společnost najít tu nejlepší cenu lístek pro konkrétní trasy. Implementace této situace se vyžaduje použití zpráv aktivit k přijímání požadavků cena, načíst ceny z back endové služby a odpovědět na požadavek cena tu nejlepší cenu. To by také vyžadují, abyste pomocí další aktivity out-of-box můžete vytvořit obchodní logiku pro výpočet tu nejlepší cenu.

## <a name="workflowservicehost"></a>WorkflowServiceHost

<xref:System.ServiceModel.WorkflowServiceHost> Je hostitele pracovního postupu out-of-box, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou potřeba použít zasílání aby bylo možné hostovat pracovních postupů). Je integrován se sadou trvalost, sledování a řízení instance prostřednictvím sady chování služby. Stejně jako jeho WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete v aplikaci konzoly a WinForms nebo WPF nebo služba Windows v místním prostředí nebo web hostovaný (jako soubor .xamlx) v IIS nebo WAS.

### <a name="getting-started-with-workflow-service-host"></a>Začínáme se službou hostitel služby pracovního postupu

- V sadě Visual Studio 2010, vytvořte projekt aplikace služby pracovního postupu WCF: Tento projekt bude nastaven používat <xref:System.ServiceModel.WorkflowServiceHost> v prostředí webového hostitele.

- Abyste mohli hostovat pracovního postupu zasílání zpráv, přidejte vlastní <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , který se vytvoří instance na základě zprávy.

- Instance pracovních postupů je možné řídit (např. pozastaven nebo ukončen) tak, že přidáte <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> k <xref:System.ServiceModel.WorkflowServiceHost> a následným použitím <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Ukázky pro <xref:System.ServiceModel.WorkflowServiceHost> najdete v následujících částech:

  - [Spuštění](./samples/execution.md)

  - Aplikace: [Správa pozastavené instance](./samples/suspended-instance-management.md)

- [Přehled hostování služeb pracovních postupů](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost Scenario

Služba BestPriceFinder zdůrazňuje k více službám letecká společnost najít tu nejlepší cenu lístek pro konkrétní trasy. Implementace této situace se vyžaduje k hostování pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost>. Aktivit zpráv ho využít také k přijímání požadavků cena, načíst ceny z back endové služby a odpovědět na požadavek cena tu nejlepší cenu.

## <a name="correlation"></a>Korelace

Korelaci je jedním ze dvou kroků:

- Způsob seskupování zpráv najednou; To znamená, o vztah mezi zprávu požadavku a jeho odpověď.

- Způsob mapování část dat na instanci služby

### <a name="getting-started"></a>Začínáme

- Abyste mohli začít s korelací, vytvořte nový projekt v sadě Visual Studio. Vytvořte proměnnou typu <xref:System.ServiceModel.Activities.CorrelationHandle>.

- Příklad korelace společně umožňují seskupovat zprávy je korelaci požadavek-odpověď, která seskupuje zprávy.

  - Na <xref:System.ServiceModel.Activities.Receive> aktivity, klikněte na <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnost a přidejte <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> pomocí rutiny CorrelationHandle vytvořili v prvním kroku požadavků.

  - Vytvoření <xref:System.ServiceModel.Activities.SendReply> kliknutím pravým tlačítkem na aktivitu <xref:System.ServiceModel.Activities.Receive> a kliknutím na "Vytvoření odeslání odpovědi SendReply". Vložte ji do pracovního postupu po <xref:System.ServiceModel.Activities.Receive> aktivity.

- Příklad mapování část dat do instance služby je korelace na základě obsahu, který mapuje část dat (například ID objednávky) na instance určitý pracovní postup.

  - U všech aktivit, zasílání zpráv, klikněte na `CorrelationInitializers` vlastnost a přidejte <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> proměnné vytvořené výše. Dvakrát klikněte na požadovanou vlastnost zprávy (třeba OrderID) z rozevírací nabídky. Nastavte `CorrelatesWith` vlastnost <xref:System.ServiceModel.Activities.CorrelationHandle> proměnné využité nad.

- [Rámcové dokumentaci korelace](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scénář korelace

Pracovního postupu zpracování objednávky se používá k vytvoření nového pořadí a aktualizuje se existující objednávky, které jsou v procesu. Implementace této situace se vyžaduje k hostování pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> a použít pro zasílání zpráv aktivity. Bude také vyžadovat korelace na základě `orderId` zajistit, že jsou provedeny aktualizace správné pracovního postupu.

## <a name="simplified-configuration"></a>Zjednodušená konfigurace

Konfigurační schéma služby WCF je složitá a poskytuje uživatelům s mnoha obtížné najít funkce. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], jsme se zaměřili na pomoc uživatelům WCF svoji službu nakonfigurovat následující funkce:

- Odstraňuje potřebu explicitní za služby konfigurace. Pokud nenakonfigurujete žádné \<služby > prvky pro vaši službu a vaše služba nedefinuje programově libovolný koncový bod a potom sadu koncových bodů se automaticky přidat do vaší služby, za základní adresa služby a za kontraktu implementované vaší služby.

- Umožňuje uživateli zadat výchozí hodnoty pro vazby WCF a chování, které se použijí ke službám bez explicitní konfigurace.

- Standardní koncové body definují opakovaně použitelnými koncovými body, které mají pevné hodnoty pro jeden nebo více vlastností koncový bod (adresa, vazba a kontrakt) a umožňují definovat vlastní vlastnosti.

- Nakonec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umožňuje centrální správu z konfigurace klienta WCF, užitečné v situacích, ve kterých je konfigurace vybrané nebo čas načtení domény aplikace se nemění.

### <a name="getting-started"></a>Začínáme

- [Příručka pro vývojáře k WCF 4.0](https://go.microsoft.com/fwlink/?LinkId=204940)

- [Objekt pro vytváření kanálů konfigurace](https://go.microsoft.com/fwlink/?LinkId=204941)

- [Standardní koncový bod elementu](https://go.microsoft.com/fwlink/?LinkId=204942)

- [Služba konfigurace vylepšení v rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=204943)

- [Běžnou chybou uživatele v rozhraní .NET 4: Chybným zadáním názvu služby konfigurace WF/WCF](https://go.microsoft.com/fwlink/?LinkId=204944)

### <a name="simplified-configuration-scenarios"></a>Zjednodušená konfigurace scénáře

- Pokud chcete začít používat WCF chce, aby vývojáři ASMX. Ale WCF zdá se, že příliš složité! Co je všechny informace, které je potřeba napsat v konfiguračním souboru? V rozhraní .NET 4 můžete i rozhodnete mít konfigurační soubor není vůbec.

- Existující sady služeb WCF je velmi obtížné konfiguraci a údržbu. Konfigurační soubor obsahuje tisíce řádků kódu XML, které jsou velmi nebezpečné dotykového ovládání. Pro snížení velikosti kódu na něco lépe zvládnutelné je potřeba pomoc.

## <a name="data-contract-resolver"></a>Překladač kontraktu dat

V rozhraní .NET 3.5 byly několik omezení v návrhu známé typy:

- Dynamické přidání známé typy, při serializaci nebo deserializaci, nebylo možné.

- Serializátory nelze zacházet s informacemi o neznámé xsi: Type.

- Nebylo možné pro uživatele k určení, jaké xsi: type mají zobrazovat na přenosu, aby, zmenšete velikost serializace instance na lince.

[DataContractResolver](../wcf/samples/datacontractresolver.md) řeší tyto problémy v rozhraní .NET 4.5.

### <a name="getting-started"></a>Začínáme

- [Dokumentace k API překladač kontraktu dat](https://go.microsoft.com/fwlink/?LinkId=204946)

- [Úvod do překladače kontraktů dat](https://go.microsoft.com/fwlink/?LinkId=204947)

- Ukázky:

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scénáře překladač kontraktu dat

- Jak se vyhnout by bylo nutné deklarovat desítky <xref:System.Runtime.Serialization.KnownTypeAttribute> objektů ve službě.

- Zmenšení velikosti objektu XML blob.

## <a name="flowchart"></a>Vývojový diagram

Vývojový diagram je dobře známé paradigma vizuálně znázornit domény problémy. Je nový styl tok řízení, které Zavádíme v rozhraní .NET 4. Základní charakteristik vývojový diagram je, že je v daném okamžiku provést pouze jednu aktivitu. Vývojových diagramů můžete vyjádřit smyčky a alternativní výsledků, ale nejde nativně express souběžné spouštění více uzlů.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 Vytvořte konzolovou aplikaci pracovního postupu. Vývojový diagram přidáte v Návrháři pracovních postupů.

- Vývojový diagram funkce používá následující třídy:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Ukázky:

  - [Zpracování chyb v aktivitě FlowChart pomocí TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [Proces náboru](./samples/hiring-process.md)

- Návrháře dokumentace:

  - [Návrháři aktivit vývojového diagramu](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Vývojový diagram scénáře

Vývojový diagram aktivita slouží k implementaci rozluštění hru. Využití hry je velmi jednoduchý: náhodné číslo vybere počítače a hráč musí odhadnout toto číslo. Když hráč odešle každý odhad, počítač zobrazí mu pomocného parametru (to znamená "zkuste nižší číslo"). Pokud hráč najde číslo menší než 7 pokusů o přihlášení, dostane speciální Blahopřání z počítače. V této hře je možné implementovat pomocí kombinace následujících procedurálních aktivit:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Procedurálních aktivit (pořadí, v případě, ForEach, přepínač, přiřadit, DoWhile, zatímco)

Procedurálních aktivit poskytují mechanismus pro model sekvenční řízení toku pomocí konceptů, které jsou pro programátory srozumitelná. Tyto aktivity povolit tradičně structured programování jazykovým konstrukcím a v případě potřeby a poskytne paritu jazyka common Procedurální jazyků, jako je C# / VB.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 Vytvořte konzolovou aplikaci pracovního postupu. Přidáte procedurálních aktivit v Návrháři pracovních postupů.

- Ukázky:

  - [Proces náboru](./samples/hiring-process.md)

  - [Proces nákupu v podniku](./samples/corporate-purchase-process.md)

- Návrháře dokumentace:

  - [Návrhář aktivity Parallel](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T > návrháře aktivit](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scénáře procedurálních aktivit

- <xref:System.Activities.Statements.Parallel>: Systém správy intranetu dokumentu má pracovní postup schvalování dokumentů. Dokumenty vyžadují schválení uživatelé ve více oblastech, před publikováním na intranetu. Není k dispozici stanovené pořadí pro schválení; mohou probíhat kdykoli dokumentu je ve fázi "čekající schválení". Když uživatel odešle dokumentu ke kontrole ho musí schválit manažerovi s přímým přístupem, správce sítě intranet a správce interní komunikace.

- <xref:System.Activities.Statements.ParallelForEach%601>: WF aplikace spravuje firemní koupí ve velké společnosti. Firemní pravidla určují, že před plánování všechny operace nákupu, je vyžadována ocenění tří různých výrobců. Zaměstnanci z oddělení nákupu vybere tři dodavatelům společnosti dodavatele seznamu. Po těchto dodavatelů byly vybrané a upozornění, bude společnost čekat jejich ekonomické návrhy. Návrhy můžou mít v libovolném pořadí. Tento scénář implementovat v WF, použijeme <xref:System.Activities.Statements.ParallelForEach%601> , který bude iteraci v rámci naší kolekce dodavatelů a požádat o jejich ekonomické návrhy. Když jsou shromážděné všechny nabídky, je ten nejlepší vybrané a zobrazit.

## <a name="invokemethod"></a>InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> Aktivity umožňuje vyvolání veřejných metod v objektech nebo typy v oboru. To podporuje volání instance a statické metody s nebo bez parametrů (včetně pole parametrů) a obecné metody. Umožňuje také synchronního a asynchronního provedení metody.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 Vytvořte konzolovou aplikaci pracovního postupu. Přidat <xref:System.Activities.Statements.InvokeMethod> aktivity v Návrháři pracovních postupů a nakonfigurovat statické a instanci metody na něj.

- Návrháře dokumentace: [Návrhář aktivity InvokeMethod](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>InvokeMethod scénáře

- Metoda v objektu v oboru musí být vyvolána. Například hodnota musí být přidán do slovníku. Vyvolání metody přidat instance slovníku a jsou k dispozici klíč a hodnotu.

- Metody se musí zavolat na objekt starší verze CLR. Místo vytváření vlastní aktivitu pro zabalte volání do starší verze třídy, pokud se nachází v oboru během provádění pracovního postupu <xref:System.Activities.Statements.InvokeMethod> lze použít.

## <a name="error-handling-activities"></a>Chyba zpracování aktivity

<xref:System.Activities.Statements.TryCatch> Aktivita poskytuje mechanismus pro zachycování výjimek, ke kterým dochází při spuštění sady obsažené aktivity (podobně jako bloku Try/Catch konstrukce v jazyce C# /VB). <xref:System.Activities.Statements.TryCatch> nabízí na úrovni pracovního postupu zpracování výjimek. Když dojde k neošetřené výjimce, pracovní postup je zrušen a nakonec nebude provedeno bloku. Toto chování je konzistentní s jazykem C#.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 Vytvořte konzolovou aplikaci pracovního postupu. Přidat <xref:System.Activities.Statements.TryCatch> aktivity v Návrháři pracovních postupů.

- Ukázka: [Zpracování chyb v aktivitě FlowChart pomocí TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Návrháře dokumentace: [Návrháři aktivit zpracování chyb](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Scénáře zpracování chyb

Sada aktivit je nutné spustit a logika specifická pro je potřeba provést, když dojde k chybě. Pokud se během tohoto logiku zpracování chyb nenajde, chyby se nedá vrátit zpátky, bude znovu vyvolána výjimka a Nadřazená aktivita (nebo hostiteli) bude řešit potíže.

## <a name="pick-activity"></a>Výběr aktivity

<xref:System.Activities.Statements.Pick> Aktivita poskytuje modelování v WF toku řízení založené na událostech. <xref:System.Activities.Statements.Pick> obsahuje mnoho větví, kde každá větev čeká čekají na výskyt dřív, než spustíte konkrétní události. V tomto nastavení <xref:System.Activities.Statements.Pick> chová podobně jako <xref:System.Activities.Statements.Switch%601> do které aktivita bude provedena pouze jednu sadu událostí, které naslouchá. Každá větev je řízené událostmi a události, ke které dojde k první běží odpovídající větev. Všechny ostatní větve zrušit a ukončit naslouchání událostem.

### <a name="getting-started"></a>Začínáme

- V sadě Visual Studio 2012 Vytvořte konzolovou aplikaci pracovního postupu. Přidat <xref:System.Activities.Statements.Pick> aktivity v Návrháři pracovních postupů.

- Ukázka: [Použití aktivity Pick](./samples/using-the-pick-activity.md)

- Návrháře dokumentace: [Návrhář aktivity Pick](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Vyberte si scénáře

Uživatel musí být vyzváni k zadání vstupu. Za normálních okolností byste použili vývojář volání metody, například <xref:System.Console.ReadLine%2A> výzvu k zadání uživatele. Problém s tímto nastavením je, že program čeká, dokud uživatel nezadá něco. V tomto scénáři je potřeba vypršení časového limitu pro odblokování blokující aktivity. Běžný scénář, kdy je takový, který se vyžaduje pro dokončení v rámci dané dobu trvání úkolu. Vypršení časového limitu blokující aktivity je scénář, ve kterém výběr přidá spoustu vylepšení.

## <a name="wcf-routing-service"></a>Směrovací služba WCF

Směrovací služba je navržena jako obecný softwaru směrovač, který umožňuje řídit, jak tok zpráv WCF mezi klienty a služby. Směrovací služba umožňuje oddělit klienty od služeb, které dává větší svobodu z hlediska konfigurace, může podporovat a flexibilitu, je nutné při úvahách o tom, jak hostovat vaše služby. V rozhraní .NET 3.5 klienty a služby byly úzce párované; Klient musí vědět o všechny potřebné ke komunikaci a kde se nachází služby. Kromě toho WCF v rozhraní .NET Framework 3.5 mělo následující omezení:

- Zpracování chyb bylo složité, jak tuto logiku, musela být pevně zakódovaný do klienta.

- Služby a klienti měli vždy používat stejné vazby.

- Služby byly jen zřídka a dostaneme: jde snadno můžete mít klienta, obraťte se na jednu službu, která implementuje všechno, co, nikoli vyžadující si vybrat mezi více služeb.

Služba směrování v rozhraní .NET 4 je navržené tak, aby tyto problémy snadněji řešit. Nová služba Směrování má následující funkce:

1. Směrování na základě obsahu (<xref:System.ServiceModel.Dispatcher.MessageFilter> objekty zkontrolovat zprávy k určení, kde má být odeslána.)

2. Protokol přemostění Datacenter (přenosu a zprávy)

3. Zpracování chyb (router zachytí výjimky komunikace a převezme služby při selhání zálohování koncových bodů)

4. (V paměti) dynamickou aktualizaci <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> a konfiguraci směrování.

### <a name="getting-started"></a>Začínáme

1. Dokumentace ke službě: [Směrování](../wcf/feature-details/routing.md)

2. Ukázky: [Směrovací služby &#91;Ukázky WCF&#93;](../wcf/samples/routing-services.md)

3. Blog: [Pravidla směrování!](https://go.microsoft.com/fwlink/?LinkId=204956)

### <a name="routing-scenarios"></a>Scénáře směrování

Směrovací služba je užitečná v následujících scénářích:

- Klienty můžete komunikovat s víc služeb bez nutnosti je řešit všechny přímo.

- Klienty můžete provádět další logiku k určení, kam směruje žádosti klienta

- Rozložit operace, které klient provede do více implementací služby bez refaktoring klienta.

- Služby a klienti mohou mluvit různých vazby s nastavením zabezpečení.

- Klienty je možné povolit bude větší odolnost proti selhání nebo nedostupnosti služby.

## <a name="wcf-discovery"></a>Zjišťování WCF

Zjišťování WCF je technologie rozhraní framework, která umožňuje začlenit zjišťování mechanismus pro vaší aplikační infrastruktury. Můžete to použít zjistitelnost služby a nakonfigurovat vaši klienti pro vyhledání služeb. Klienti už nemusí být obtížné programového s koncovým bodem, provádění vaší aplikace je robustnější a odolnost proti chybám. Zjišťování je ideální platformu pro automatickou konfiguraci funkcí pro sestavení do vaší aplikace.

Produkt je postavený na standardu WS-Discovery. Je navržena tak, aby se interoperabilní, rozšiřitelné a obecné. Produkt podporuje dva režimy činnosti:

1. Spravované: níž se nachází entity v síti informovanosti ohledně existujících služeb, klienti se ho dotazovat přímo na informace. To je obdobou služby Active Directory.

2. Ad-hoc: kde klienti používat zprávy vícesměrového vysílání pro vyhledání služeb.

Kromě toho zjišťování zprávy jsou nezávislá na protokolu sítě; můžete je v horní části libovolného protokolu, který podporuje požadavky dané režimu. Například zjišťování odesílat zprávy vícesměrového vysílání přes kanál protokolu UDP nebo jinou síť, která podporuje zasílání zpráv vícesměrového vysílání. Tyto body, v kombinaci s funkcí flexibilitu, umožňuje přizpůsobit zjišťování speciálně pro vaše řešení návrhu.

### <a name="getting-started"></a>Začínáme

- Dokumentace ke službě: [Zjišťování WCF](../wcf/feature-details/wcf-discovery.md)

- Ukázky: [Zjišťování (Ukázky)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Zjišťování scénáře

Vývojář nechce pevný kód koncové body, protože není známo, kdy bude služba k dispozici. Místo toho vývojář chce vybrat službu za běhu. Další oddělení, odolnosti a Automatická konfigurace je potřeba mezi součástmi aplikace.

## <a name="tracking"></a>Sledování

Pracovní postup sledování poskytuje přehled o spuštění instance pracovního postupu. Sledování události se vysílají z pracovního postupu na úrovni instance pracovního postupu a při spuštění aktivity v rámci pracovního postupu. Sledování účastník pracovního postupu musí být přidán do hostitele pracovního postupu k odběru sledování záznamů. Na sledování záznamy jsou filtrovány pomocí profilu sledování. Rozhraní .NET Framework poskytuje účastník sledování ETW (událost trasování pro Windows) a základní profil je nainstalovaný v souboru machine.config.

### <a name="getting-started"></a>Začínáme

1. V sadě Visual Studio 2010 vytvořte projekt aplikace služby pracovního postupu WCF. A <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> pár se umístí na plátně spustit.

2. Otevřete soubor web.config a přidat trasování událostí pro Windows sledování chování se žádný profil.

    1. Výchozí profil se používá.

    2. Otevřete Prohlížeč událostí a povolení analytického kanálu v následující uzel: **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serverové aplikace – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.

    3. Spuštění služby pracovního postupu.

    4. Sledujte pracovního postupu událostí sledování v prohlížeči událostí.

3. Ukázky: [Sledování](./samples/tracking.md)

4. Rámcové dokumentaci: [Sledování a trasování pracovních postupů](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Úložiště instancí pracovních postupů SQL

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Je implementace úložiště instance systémem SQL Server. Úložiště instance ukládá stav spuštěné instance společně se všechna data potřebná pro načtení a pokračovat v této instanci. Hostitel služby instruuje v úložišti instancí uložit stav instance, pokud pracovní postup se opakuje a nastaví v úložišti instancí načíst stav instance při přijetí e-mailu pro danou instanci nebo aktivitě delay vyprší platnost.

### <a name="getting-started"></a>Začínáme

1. V sadě Visual Studio 2012, vytvořit pracovní postup, který obsahuje implicitní nebo explicitní <xref:System.Activities.Statements.Persist> aktivity. Přidat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> chování na hostitele služby pracovního postupu. To můžete udělat v kódu nebo konfiguračního souboru aplikace.

2. Ukázky: [Uchování](./samples/persistence.md)

3. Rámcové dokumentaci: [Store Instance pracovního postupu SQL](sql-workflow-instance-store.md).
