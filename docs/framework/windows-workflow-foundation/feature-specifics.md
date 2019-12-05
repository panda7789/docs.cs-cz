---
title: Specifické funkce Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 869d6108edaa7f32101b6fe8d077e4eba7eef6b5
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802593"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Specifické funkce Windows Workflow Foundation

.NET Framework 4 přidává k programovací model Windows Workflow Foundation řadu funkcí. Tento dokument popisuje řadu nových funkcí a poskytuje podrobnosti o scénářích, ve kterých mohou být užitečné.

## <a name="messaging-activities"></a>Aktivity zasílání zpráv

Aktivity zasílání zpráv (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) se používají k posílání a přijímání zpráv WCF z pracovního postupu. Aktivity <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> slouží k vytvoření operace služby Windows Communication Foundation (WCF), která je vystavena prostřednictvím WSDL stejně jako standardní webové služby WCF. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> se používají ke využívání webové služby podobné <xref:System.ServiceModel.ChannelFactory>WCF; pro portál Workflow Foundation, který generuje předem konfigurované aktivity, existuje i **Přidat odkaz na službu** prostředí.

### <a name="getting-started-with-messaging-activities"></a>Začínáme s aktivitami zasílání zpráv

- V aplikaci Visual Studio 2012 vytvořte projekt aplikace služby pracovního postupu WCF. Na plátno budou vloženy páry <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>.

- Klikněte pravým tlačítkem na projekt a vyberte **Přidat odkaz na službu**. Přejděte na existující prvek WSDL webové služby a klikněte na tlačítko **OK**. Sestavte projekt, aby se zobrazily vygenerované aktivity (implementované pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply>) ve vaší sadě nástrojů.

- [Dokumentace ke službám Workflow Services](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Příklad scénáře aktivity zasílání zpráv

Služba `BestPriceFinder` volá více leteckých služeb a hledá nejlepší cenu za lístek pro konkrétní trasu. Implementace tohoto scénáře by vyžadovala, abyste mohli používat aktivity zpráv pro příjem žádosti o cenu, načítat ceny z back-endové služby a odpovědět na žádost o cenu s nejlepší cenou. Také vyžaduje, abyste k vytvoření obchodní logiky pro výpočet nejlepší ceny použili další připravené aktivity.

## <a name="workflowservicehost"></a>WorkflowServiceHost

<xref:System.ServiceModel.WorkflowServiceHost> je předem připravený hostitel pracovního postupu, který podporuje více instancí, konfigurací a zasílání zpráv WCF (i když pracovní postupy nevyžadují, aby používaly zasílání zpráv, aby je bylo možné hostovat). Integruje se taky se zachováním, sledováním a instancí prostřednictvím sady chování služby. Stejně jako <xref:System.ServiceModel.ServiceHost>WCF, <xref:System.ServiceModel.WorkflowServiceHost> může být v místním prostředí v konzole/WinForms/prostředí WPF nebo ve službě systému Windows nebo v hostovaném webu (jako soubor. xamlx) ve službě IIS nebo WAS.

### <a name="getting-started-with-workflow-service-host"></a>Začínáme s hostitelem služby pracovního postupu

- V sadě Visual Studio 2010 vytvořte projekt aplikace služby pracovního postupu WCF: Tento projekt bude nastaven na použití <xref:System.ServiceModel.WorkflowServiceHost> v prostředí webového hostitele.

- Chcete-li hostovat pracovní postup bez zasílání zpráv, přidejte vlastní <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, která vytvoří instanci na základě zprávy.

- Instance pracovního postupu lze řídit (například pozastaveno nebo ukončeno) přidáním <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> a následným použitím <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Ukázky pro <xref:System.ServiceModel.WorkflowServiceHost> najdete v následujících částech:

  - [Spuštění](./samples/execution.md)

  - Aplikace: [pozastavená Správa instancí](./samples/suspended-instance-management.md)

- [Přehled hostování služeb pracovních postupů](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>Scénář WorkflowServiceHost

Služba BestPriceFinder volá více leteckých služeb a hledá nejlepší cenu za lístek pro konkrétní trasu. Implementace tohoto scénáře by vyžadovala hostování pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost>. Tyto aktivity by také používaly aktivity zpráv pro příjem žádosti o cenu, načetla ceny z back-endové služby a odpovědět na žádost o cenu s nejlepší cenou.

## <a name="correlation"></a>Korelace

Korelace je jednou ze dvou věcí:

- Způsob, jak seskupovat zprávy; To znamená vztah mezi zprávou požadavku a odpovědí.

- Způsob mapování částí dat na instanci služby

### <a name="getting-started"></a>Začínáme

- Chcete-li začít s korelací, vytvořte nový projekt v aplikaci Visual Studio. Vytvořte proměnnou typu <xref:System.ServiceModel.Activities.CorrelationHandle>.

- Příkladem korelace používaného k seskupení zpráv je korelace požadavek-odpověď, která seskupuje zprávy dohromady.

  - V <xref:System.ServiceModel.Activities.Receive> aktivity klikněte na vlastnost <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> a přidejte <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> pomocí popisovač CorrelationHandle vytvořeného v prvním kroku.

  - <xref:System.ServiceModel.Activities.SendReply> aktivitu vytvoříte tak, že kliknete pravým tlačítkem na <xref:System.ServiceModel.Activities.Receive> a kliknete na vytvořit aktivitu SendReply. Vložte ji do pracovního postupu po aktivitě <xref:System.ServiceModel.Activities.Receive>.

- Příkladem mapování částí dat na instanci služby je korelace založená na obsahu, která mapuje část dat (například ID objednávky) do konkrétní instance pracovního postupu.

  - U jakékoli aktivity zasílání zpráv klikněte na vlastnost `CorrelationInitializers` a přidejte <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> proměnné vytvořené výše. Dvakrát klikněte na požadovanou vlastnost ve zprávě (např. ČísloObjednávky) z rozevírací nabídky. Vlastnost `CorrelatesWith` nastavte na výše použitou <xref:System.ServiceModel.Activities.CorrelationHandle> proměnnou.

- [Rámcová dokumentace korelace](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Scénář korelace

Pracovní postup zpracování objednávek se používá ke zpracování nových objednávek a aktualizaci stávajících objednávek, které jsou zpracovávány. Implementace tohoto scénáře by vyžadovala hostování pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> a používání aktivit zasílání zpráv. Bude také vyžadovat korelaci na základě `orderId`, aby bylo zajištěno, že budou aktualizace provedeny ve správném pracovním postupu.

## <a name="simplified-configuration"></a>Zjednodušená konfigurace

Schéma konfigurace WCF je složité a poskytuje uživatelům mnoho obtížnéch funkcí hledání. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]jsme se zaměřili na pomoc uživatelům WCF s konfigurací svých služeb pomocí následujících funkcí:

- Odebrání potřeby explicitní konfigurace podle služby. Pokud neprovedete konfiguraci žádného prvku > služby \<pro vaši službu a služba nedefinuje programově žádný koncový bod, pak se do vaší služby automaticky přidají sada koncových bodů, jednu pro každou základní adresu služby a pro každou smlouvu, kterou služba implementuje.

- Umožňuje uživateli definovat výchozí hodnoty pro vazby a chování WCF, které budou aplikovány na služby bez explicitní konfigurace.

- Standardní koncové body definují opakovaně používané předem nakonfigurované koncové body, které mají pevné hodnoty pro jednu nebo více vlastností koncového bodu (adresa, vazba a kontrakt) a umožňují definovat vlastní vlastnosti.

- Nakonec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umožňuje provádět centrální správu konfigurace klienta WCF, která je užitečná ve scénářích, ve kterých je vybraná konfigurace nebo se změnila po dobu načtení domény aplikace.

### <a name="getting-started"></a>Začínáme

- [Příručka pro vývojáře k WCF 4,0](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Objekt pro vytváření kanálů konfigurace](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Element standardního koncového bodu](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [Vylepšení konfigurace služby v .NET Framework 4](https://blogs.msdn.microsoft.com/endpoint/2009/06/30/service-configuration-improvements-in-net-4/)

- [Běžná chyba uživatele v rozhraní .NET 4: zadání názvu konfigurace služby WF/WCF](https://blogs.msdn.microsoft.com/endpoint/2009/11/09/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name/)

### <a name="simplified-configuration-scenarios"></a>Zjednodušené scénáře konfigurace

- Zkušený vývojář ASMX chce začít používat WCF. WCF se ale jeví jako moc komplikované. Jaké jsou všechny informace, které potřebuji k zápisu do konfiguračního souboru? V rozhraní .NET 4 se můžete rozhodnout, že ještě nemáte konfigurační soubor.

- Existující sada služeb WCF je velmi obtížné nakonfigurovat a udržovat. Konfigurační soubor obsahuje tisíce řádků kódu XML, které jsou mimořádně nebezpečné dotykem. Je potřeba, abyste snížili množství kódu na něco, co je možné spravovat.

## <a name="data-contract-resolver"></a>Překladač kontraktu dat

V rozhraní .NET 3,5 bylo při návrhu známých typů zjištěno několik omezení:

- Přidávání známých typů dynamicky, během serializace nebo deserializace nebylo možné.

- Serializátory nemohly zabývat s neznámými informacemi xsi: Type.

- Uživatelé nedokázali určit, jaký typ xsi: Type by se měl na lince zobrazit, například nastavit velikost instance serializace na malém kabelu.

[DataContractResolver](../wcf/samples/datacontractresolver.md) tyto problémy řeší v rozhraní .NET 4,5.

### <a name="getting-started"></a>Začínáme

- [Dokumentace k rozhraní API překladače kontraktů dat](xref:System.Runtime.Serialization.DataContractResolver)

- [Představení překladače kontraktů dat](https://blogs.msdn.microsoft.com/youssefm/2009/06/05/configuring-known-types-dynamically-introducing-the-datacontractresolver/)

- Ukázky:

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Scénáře překladače kontraktů dat

- Zamezení nutnosti deklarovat desítky <xref:System.Runtime.Serialization.KnownTypeAttribute> objektů ve službě.

- Zmenšení velikosti objektu blob XML.

## <a name="flowchart"></a>Vývojový diagram

Vývojové diagramy jsou dobře známé paradigmaty, které vizuálně reprezentují problémy v doméně. Je to nový styl toku ovládacích prvků, který zavádíme v rozhraní .NET 4. Základní charakteristika vývojového diagramu je, že v daném okamžiku se spustí jenom jedna aktivita. Vývojové diagramy mohou vyjádřit smyčky a alternativní výsledky, ale nemohou nativně expresní souběžné provádění více uzlů.

### <a name="getting-started"></a>Začínáme

- V aplikaci Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte vývojový diagram do návrháře pracovních postupů.

- Funkce vývojového diagramu používá následující třídy:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Ukázky:

  - [Zpracování chyb v aktivitě FlowChart pomocí TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [Proces náboru](./samples/hiring-process.md)

- Dokumentace k Návrháři:

  - [Návrháři aktivit vývojového diagramu](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Scénáře vývojového diagramu

Aktivitu vývojového diagramu lze použít k implementaci odhadované hry. Odhadovaná hra je velmi jednoduchá: počítač vybere náhodné číslo a přehrávač musí toto číslo odhadnout. Když hráč každý odhad odešle, zobrazí mu nápovědu (tzn. "zkusit nižší číslo"). Pokud hráč najde číslo během méně než 7 pokusů, obdrží od počítače speciální congratulation. Tato hra se dá implementovat s kombinací následujících procedurálních aktivit:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Procesní aktivity (sekvence, if, ForEach, přepínač, Assign, DoWhile, while)

Procesní aktivity poskytují mechanismus pro modelování sekvenčního řízení toku pomocí konceptů, které jsou obeznámeny s programátory. Tyto aktivity umožňují tradičně strukturované konstrukce programovacích jazyků a v případě potřeby poskytují jazykovou paritu běžných procedurálních jazyků, C#jako je/vb.

### <a name="getting-started"></a>Začínáme

- V aplikaci Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte procedurální aktivity v Návrháři pracovních postupů.

- Ukázky:

  - [Proces náboru](./samples/hiring-process.md)

  - [Proces nákupu v podniku](./samples/corporate-purchase-process.md)

- Dokumentace k Návrháři:

  - [Návrhář aktivity Parallel](/visualstudio/workflow-designer/parallel-activity-designer)

  - [Návrhář aktivit > ParallelForEach\<T](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Scénáře činnosti procedurálního řízení

- <xref:System.Activities.Statements.Parallel>: systém správy dokumentů v intranetu má pracovní postup schvalování dokumentů. Než bude možné publikovat dokumenty v intranetu, je nutné, aby je uživatelé schválili v několika odděleních. Pro schválení není stanoveno pořadí; k tomu může dojít kdykoli, když je dokument ve fázi schválení "čeká na schválení". Když uživatel dokument pošle k revizi, musí ho schválit jeho přímý nadřízený, správce intranetu a interní komunikační správce.

- <xref:System.Activities.Statements.ParallelForEach%601>: aplikace WF spravuje podnikové koupě v rámci velké společnosti. Podniková pravidla je určují, že před plánováním operací nákupu se vyžadují ocenění tří různých dodavatelů. Zaměstnanec z nákupního oddělení vybere tři dodavatele ze seznamu dodavatelů společnosti. Po výběru a oznámení těchto dodavatelů bude společnost čekat na jejich ekonomické návrhy. Návrhy můžou být v libovolném pořadí. K implementaci tohoto scénáře na WF používáme <xref:System.Activities.Statements.ParallelForEach%601>, který se bude iterovat prostřednictvím naší kolekce dodavatelů a požádat o jejich ekonomické návrhy. Po shromáždění všech nabídek se vybere a zobrazí nejlepší z nich.

## <a name="invokemethod"></a>InvokeMethod

Aktivita <xref:System.Activities.Statements.InvokeMethod> umožňuje vyvolání veřejných metod v objektech nebo typech v oboru. Podporuje vyvolání instance a statických metod s parametry nebo bez parametrů (včetně polí parametrů) a obecných metod. Také umožňuje provádět synchronní a asynchronní provádění metody.

### <a name="getting-started"></a>Začínáme

- V aplikaci Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte aktivitu <xref:System.Activities.Statements.InvokeMethod> v Návrháři postupu a nakonfigurujte pro ni statické a instanční metody.

- Dokumentace návrháře: [Návrhář aktivity InvokeMethod](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>Scénáře InvokeMethod

- Metoda v objektu v oboru musí být vyvolána. Například hodnota musí být přidána do slovníku. Metoda Add instance slovníku je vyvolána a klíč a hodnota jsou k dispozici.

- Metoda musí být vyvolána na starší verzi objektu CLR. Namísto vytvoření vlastní aktivity pro zabalení volání této starší třídy, pokud je v oboru během provádění pracovního postupu, lze použít <xref:System.Activities.Statements.InvokeMethod>.

## <a name="error-handling-activities"></a>Aktivity zpracovávající chyby

Aktivita <xref:System.Activities.Statements.TryCatch> poskytuje mechanismus pro zachycení výjimek, ke kterým dochází během provádění sady obsažených aktivit (podobně jako konstrukce try/catch v C#/VB). <xref:System.Activities.Statements.TryCatch> poskytuje zpracování výjimek na úrovni pracovního postupu. Pokud je vyvolána neošetřená výjimka, je pracovní postup přerušen a blok finally nebude proveden. Toto chování je konzistentní s C#.

### <a name="getting-started"></a>Začínáme

- V aplikaci Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte aktivitu <xref:System.Activities.Statements.TryCatch> v Návrháři pracovních postupů.

- Ukázka: [zpracování chyb v aktivitě vývojového diagramu pomocí TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Dokumentace návrháře: [zpracování chyb návrháři aktivit](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Scénáře zpracování chyb

Je nutné provést sadu aktivit a při výskytu chyby musí být provedena konkrétní logika. Pokud v této logice zpracování chyb zjistíte, že chyba není obnovitelná, výjimka se znovu vyvolá a Nadřazená aktivita (nebo hostitel) se tomuto problému zaměří.

## <a name="pick-activity"></a>Aktivita výběru

Aktivita <xref:System.Activities.Statements.Pick> poskytuje modelování toku řízení založeného na událostech na WF. <xref:System.Activities.Statements.Pick> obsahuje mnoho větví, ve kterých každá větev čeká na určitou událost před spuštěním. V tomto nastavení se <xref:System.Activities.Statements.Pick> chová podobně jako <xref:System.Activities.Statements.Switch%601>, na které aktivita spustí pouze jednu ze sady událostí, kterou naslouchá. Každá větev je řízený událost a událost, ke které dojde, spustí nejprve příslušnou větev. Všechny ostatní větve zruší a zastaví naslouchání pro události.

### <a name="getting-started"></a>Začínáme

- V aplikaci Visual Studio 2012 vytvořte konzolovou aplikaci pracovního postupu. Přidejte aktivitu <xref:System.Activities.Statements.Pick> v Návrháři pracovních postupů.

- Ukázka: [použití aktivity výběru](./samples/using-the-pick-activity.md)

- Dokumentace návrháře: [Návrhář aktivity výběru](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Scénář výběru

Uživatel musí být vyzván k zadání vstupu. Za normálních okolností by vývojář používal volání metody, jako je <xref:System.Console.ReadLine%2A> k zobrazení výzvy k zadání uživatele. Problém s tímto nastavením je, že program čeká, dokud uživatel nezadá něco. V tomto scénáři je potřeba časový limit odblokování blokující aktivity. Běžným scénářem je jeden, který vyžaduje dokončení úkolu v rámci dané doby trvání. Načasování blokující aktivity je scénář, ve kterém nástroj pro výběr přidá hodně hodnot.

## <a name="wcf-routing-service"></a>Směrovací služba WCF

Směrovací služba je navržená jako obecný softwarový směrovač, který umožňuje řídit, jak se zprávy WCF směrují mezi klienty a službami. Směrovací služba umožňuje oddělit klienty od služeb, což vám dává mnohem větší volnost v souvislosti s konfiguracemi, které můžete podporovat, a flexibilitou, kterou máte při zvažování toho, jak vaše služby hostovat. V rozhraní .NET 3,5 byly klienti a služby úzce spojeni. klient musel znát všechny služby, které potřebují ke komunikaci s a kde se nacházejí. Kromě toho WCF v .NET Framework 3,5 má následující omezení:

- Zpracování chyb bylo složité, protože tato logika musela být pevně zakódována do klienta.

- Klienti a služby museli vždy používat stejné vazby.

- Služby byly zřídka dobře vyladěny: klient je snazší, aby mohl komunikovat s jednou službou, která implementuje vše a nepotřebuje vybírat mezi více službami.

Směrovací služba v .NET 4 je navržená tak, aby se tyto problémy lépe vyřešily. Nová směrovací služba má následující funkce:

1. Směrování založené na obsahu (<xref:System.ServiceModel.Dispatcher.MessageFilter> objekty prozkoumají zprávu a určíte, kam se má odeslat.)

2. Přemostění protokolu (přenosová & zpráva)

3. Zpracování chyb (směrovač zachytává výjimky komunikace a převzetí služeb při selhání koncovými body zálohování)

4. Dynamická aktualizace (v paměti) <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> a konfigurace směrování.

### <a name="getting-started"></a>Začínáme

1. Dokumentace: [Směrování](../wcf/feature-details/routing.md)

2. Ukázky: [ukázky&#93; služby &#91;Routing Services WCF](../wcf/samples/routing-services.md)

3. Blog: [pravidla směrování!](https://blogs.msdn.microsoft.com/RoutingRules/)

### <a name="routing-scenarios"></a>Scénáře směrování

Směrovací služba je užitečná v následujících scénářích:

- Klienti můžou komunikovat s více službami, aniž by museli je řešit přímo.

- Klienti mohou provést další logiku na žádost klienta o určení místa směrování

- Rozloží operace, které klient provádí, do více implementací služeb bez refaktoringu klienta.

- Klienti a služby můžou namluvit s různými nastaveními zabezpečení různé vazby.

- U klientů se dá povolit větší robustnost před selháním nebo nedostupností služeb.

## <a name="wcf-discovery"></a>Zjišťování WCF

Zjišťování WCF je technologie architektury, která umožňuje začlenit mechanismus zjišťování do vaší aplikační infrastruktury. Pomocí tohoto nastavení můžete službu zjistit a nakonfigurovat klienty tak, aby vyhledali služby. Klienti už nemusejí být pevně kódované s koncovým bodem, takže vaše aplikace bude robustnější a odolná proti chybám. Zjišťování je ideální platformou pro sestavování možností automatické konfigurace do vaší aplikace.

Produkt je postaven nad standardem WS-Discovery. Je navržený tak, aby byl interoperabilní, rozšiřitelný a obecný. Produkt podporuje dva režimy provozu:

1. Spravované: v případě, že je v síti dostupná nějaká entita o stávajících službách, klienti se dotazují přímo na informace. To je obdobou služby Active Directory.

2. Ad hoc: kde klienti používají zprávy vícesměrového vysílání k vyhledání služeb.

Zprávy zjišťování jsou navíc síťový protokol nezávislá; můžete je použít v jakémkoli protokolu, který podporuje požadavky na režim. Například zprávy vícesměrového vysílání se dají odesílat přes kanál UDP nebo jakoukoli jinou síť, která podporuje zasílání zpráv vícesměrového vysílání. Tyto body návrhu v kombinaci s flexibilitou funkcí umožňují přizpůsobit zjišťování specificky pro vaše řešení.

### <a name="getting-started"></a>Začínáme

- Dokumentace: [zjišťování WCF](../wcf/feature-details/wcf-discovery.md)

- Ukázky: [zjišťování (ukázky)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Scénáře zjišťování

Vývojář nechce, aby se koncovým bodům nezměnil, protože není znám, když bude k dispozici moje služba. Místo toho chce vývojář zvolit službu za běhu. Mezi komponentami v aplikaci je potřeba víc oddálení, odolnost a Automatická konfigurace.

## <a name="tracking"></a>Sledování

Sledování pracovního postupu nabízí přehled o provádění instance pracovního postupu. Události sledování se generují z pracovního postupu na úrovni instance pracovního postupu a při provádění aktivit v rámci pracovního postupu. Účastník sledování pracovního postupu musí být přidán do hostitele pracovního postupu, aby se mohl přihlásit k odběru sledování záznamů. Záznamy sledování se filtrují pomocí sledovacího profilu. .NET Framework poskytuje účastník sledování trasování událostí pro Windows (Event Tracing for Windows) a v souboru Machine. config je nainstalovaný základní profil.

### <a name="getting-started"></a>Začínáme

1. V aplikaci Visual Studio 2010 vytvořte projekt aplikace služby pracovního postupu WCF. Na plátno se umístí pár <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, aby se spustila.

2. Otevřete soubor Web. config a přidejte chování sledování ETW bez profilu.

    1. Použije se výchozí profil.

    2. Otevřete Prohlížeč událostí a povolte analytický kanál v následujícím uzlu: **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**.

    3. Spusťte službu pracovního postupu.

    4. Sledujte události sledování pracovních postupů v prohlížeči událostí.

3. Ukázky: [sledování](./samples/tracking.md)

4. Koncepční dokumentace: [sledování a trasování pracovních postupů](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>Úložiště instancí pracovních postupů SQL

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> je implementace instance na základě SQL Server. Úložiště instancí ukládá stav spuštěné instance společně se všemi daty potřebnými pro načtení a obnovení této instance. Hostitel služby instruuje úložiště instancí, aby uložil stav instance, pokud pracovní postup přetrvává, a nastaví úložiště instancí, aby načetlo stav instance, když se do této instance dorazí zpráva pro tuto instanci nebo když platnost aktivity zpoždění vyprší.

### <a name="getting-started"></a>Začínáme

1. V aplikaci Visual Studio 2012 vytvořte pracovní postup, který obsahuje implicitní nebo explicitní aktivitu <xref:System.Activities.Statements.Persist>. Přidejte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> chování do hostitele služby pracovního postupu. To lze provést v kódu nebo v konfiguračním souboru aplikace.

2. Ukázky: [trvalost](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Koncepční dokumentace: [úložiště instancí pracovních postupů SQL](sql-workflow-instance-store.md)
