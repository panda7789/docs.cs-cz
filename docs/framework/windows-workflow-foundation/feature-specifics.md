---
title: "Windows Workflow Foundation funkce podrobností"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e7a223248b574e30c266c3c9ac66bf317f1d19f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation funkce podrobností
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]Přidá do modelu Windows Workflow Foundation celou řadu funkcí. Tento dokument obsahuje několik nových funkcí a uvádí podrobnosti o scénářích, ve kterých mohou být užitečné.  
  
## <a name="messaging-activities"></a>Aktivity zasílání zpráv  
 Zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) se používají k odesílání a příjmu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zprávy z pracovní postup.  <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.SendReply> aktivity se používají pro formuláře [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] operace, který je zveřejněný prostřednictvím WSDL stejně jako standardní služby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] webové služby.  <xref:System.ServiceModel.Activities.Send>a <xref:System.ServiceModel.Activities.ReceiveReply> se používají k využívat webové službou WCF <xref:System.ServiceModel.ChannelFactory>; **přidat odkaz na službu** prostředí existuje taky pro Workflow Foundation, který generuje předem nakonfigurovaná aktivity.  
  
### <a name="getting-started-with-messaging-activities"></a>Začínáme s aktivitami zasílání zpráv  
  
-   V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvoření projektu aplikace služby WCF pracovního postupu. A <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> pár se umístí na plátno.  
  
-   Klikněte pravým tlačítkem na projekt a vyberte **přidat odkaz na službu**.  Přejděte na existující webovou službu WSDL a klikněte na tlačítko **OK**.  Sestavení projektu zobrazíte generovaného aktivity (implementovaná pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply>) ve vašem panelu nástrojů.  
  
-   Ukázky pro tyto aktivity naleznete v následujících částech:  
  
    -   Basic: [služby](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scénáře: [služby](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [Rámcová dokumentace](http://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [Zasílání zpráv dokumentace Návrhář aktivity](http://go.microsoft.com/fwlink/?LinkId=204802)  
  
### <a name="messaging-activities-example-scenario"></a>Příklad scénáře aktivity pro zasílání zpráv  
 A `BestPriceFinder` volání služba k více službám letecká společnost najít nejlepší lístku cena pro daný postup.  Implementace této situace by vyžadovaly používat aktivity zpráva přijmout žádost o ceníku, načtení ceny z back endové služby a odpovědět na požadavek cena s nejlepší cenu.  Bude vám umožní používat ostatní aktivity out-of-box vytvořit obchodní logiku pro výpočet ceny nejlepší také vyžadovat.  
  
## <a name="workflowservicehost"></a>Hostitele služby pracovního postupu  
 <xref:System.ServiceModel.WorkflowServiceHost> Je pracovní postup out-of-box hostitele, který podporuje víc instancí, konfiguraci a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zasílání zpráv (i když pracovních postupů nemusí být hostovaná použít zasílání zpráv).  Je integrován se sadou trvalost, sledování a řízení instance pomocí sady chování služby.  Stejně jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]na <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete samoobslužně hostovaná v konzole nebo WinForms/WPF aplikace nebo služba systému Windows nebo web hostovaný (jako soubor .xamlx) ve službě IIS nebo WAS.  
  
### <a name="getting-started-with-workflow-service-host"></a>Začínáme s hostitele služby pracovního postupu  
  
-   V sadě Visual Studio 2010, vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu aplikace služby pracovního postupu: Tento projekt se nastavit tak, aby pomocí <xref:System.ServiceModel.WorkflowServiceHost> v prostředí webového hostitele.  
  
-   Aby bylo možné hostovat pracovní postup zasílání zpráv, přidejte vlastní <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , vytvoří instanci na základě zprávy.  
  
-   Instance pracovního postupu se dá řídit (např. pozastavený nebo byl ukončen) přidáním <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> k <xref:System.ServiceModel.WorkflowServiceHost> a potom pomocí <xref:System.ServiceModel.Activities.WorkflowControlClient>.  
  
-   Ukázky pro <xref:System.ServiceModel.WorkflowServiceHost> naleznete v následujících částech:  
  
    -   [Provádění](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   Basic: [služby](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scénáře: [služby](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Aplikace: [pozastaveno Správa instancí](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [Rámcová dokumentace hostitele služby pracovního postupu](http://go.microsoft.com/fwlink/?LinkId=204807)  
  
### <a name="workflowservicehost-scenario"></a>Scénář hostitele služby pracovního postupu  
 Služba BestPriceFinder volá k více službám letecká společnost najít nejlepší lístku cena pro daný postup.  Implementace této situace se vyžaduje k hostování pracovní postup <xref:System.ServiceModel.WorkflowServiceHost>.  Využívá také zpráva aktivity přijmout žádost o ceníku, načtení ceny z back endové služby a odpovědět na požadavek cena s nejlepší cenu.  
  
## <a name="correlation"></a>Korelace  
 Existuje korelace je jedním ze dvou akcí:  
  
-   Způsob seskupení zpráv společně; To znamená, o vztah mezi zprávu požadavku a jeho odpovědi.  
  
-   Způsob mapování část dat na instanci služby  
  
### <a name="getting-started"></a>Začínáme  
  
-   Chcete-li začít pracovat s korelace, vytvořte nový projekt v sadě Visual Studio. Vytvoření proměnné typu <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
-   Příklad korelace společně použít na zprávy skupinu je korelace požadavku a odpovědi, které jsou seskupeny dohromady zprávy.  
  
    -   Na <xref:System.ServiceModel.Activities.Receive> aktivity, klikněte na <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnost a přidejte <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> pomocí CorrelationHandle vytvořili v prvním kroku výše.  
  
    -   Vytvořit <xref:System.ServiceModel.Activities.SendReply> kliknutím pravým tlačítkem na aktivitu <xref:System.ServiceModel.Activities.Receive> a kliknutím na možnost "Vytvoření SendReply". Vložte jej do vašeho pracovního postupu po <xref:System.ServiceModel.Activities.Receive> aktivity.  
  
-   Příklad mapování část dat do instance služby je korelace na základě obsahu, která se mapuje na instanci pracovního postupu konkrétní část dat (například ID pořadí).  
  
    -   Na jakékoli činnosti, zasílání zpráv, klikněte na `CorrelationInitializers` vlastnost a přidejte <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> pomocí <xref:System.ServiceModel.Activities.CorrelationHandle> proměnné vytvořené výše. Dvakrát klikněte na požadovanou vlastnost na zprávu (např. OrderID) z rozevírací nabídky. Nastavte `CorrelatesWith` vlastnost, která má <xref:System.ServiceModel.Activities.CorrelationHandle> proměnná používá výše.  
  
-   Ukázky:  
  
    -   Basic: [služby](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scénáře: [služby](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [Korelace rámcová dokumentace](http://go.microsoft.com/fwlink/?LinkId=204939)  
  
### <a name="correlation-scenario"></a>Scénář korelace  
 Pracovní postup pořadí zpracování slouží ke zpracování vytvoření nového pořadí a aktualizace existujících příkazů, které jsou v procesu.  Implementace této situace se vyžaduje k hostování pracovní postup <xref:System.ServiceModel.WorkflowServiceHost> a používat aktivity zasílání zpráv.  Bude také vyžadovat korelace na základě `orderId` zajistit, že jsou provedeny aktualizace správné pracovního postupu.  
  
## <a name="simplified-configuration"></a>Zjednodušená konfigurace  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Schéma konfigurace je složitá a poskytuje uživatelům s mnoha pevný k nalezení funkcí. V [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], jsme se zaměřili na pomoc [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uživatelé konfigurovat své služby s následující funkce:  
  
-   Odebírá potřebu explicitní za služby konfigurace. Pokud nenakonfigurujete žádné \<služby > elementy služby a služby nedefinuje prostřednictvím kódu programu žádný koncový bod a potom sadu koncových bodů se automaticky přidat do vaší služby, jeden jednotlivých základní adresa služby a kontraktu implementované služby.  
  
-   Umožní uživateli zadat výchozí hodnoty pro vazby WCF a chování, které se použijí ke službám s žádná explicitní konfigurace.  
  
-   Standardní koncové body definovat opakovaně použitelné předkonfigurované koncových bodů, které mají pevné hodnoty pro jeden nebo více vlastností koncový bod (adresy, vazby a kontraktu) a umožňují definovat vlastní vlastnosti.  
  
-   Nakonec <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> umožňuje provádět Centrální správa [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguraci klienta, užitečné v situacích, ve kterých je konfigurace vybrali nebo změnit po doba načtení domény aplikace.  
  
### <a name="getting-started"></a>Začínáme  
  
-   [Příručka pro vývojáře pro WCF 4.0](http://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [Postup konfiguračního kanálu](http://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [Element standardní koncového bodu](http://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [Služba konfigurace vylepšení v rozhraní .net Framework 4](http://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [Obvyklou chybou uživatele v rozhraní .NET 4: chybným zadáním názvu WF/WCF služby konfigurace](http://go.microsoft.com/fwlink/?LinkId=204944)  
  
### <a name="simplified-configuration-scenarios"></a>Zjednodušená konfigurace scénáře  
  
-   Vývojář zkušeného ASMX chce začít používat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Ale [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zdá se, že příliš složitý! Co je všechny tyto informace vyžadující zapisovat v konfiguračním souboru? V rozhraní .NET 4 můžete dokonce rozhodnout konfigurační soubor nemá vůbec.  
  
-   Existující sady služby WCF jsou velmi obtížné konfiguraci a údržbu. Konfigurační soubor obsahuje tisíce řádky kód XML, které jsou velmi nebezpečné pro touch. Nápověda je potřeba ke snížení množství tohoto kódu na něco lepší správu bitlockeru.  
  
## <a name="data-contract-resolver"></a>Překladače kontraktů dat  
 V rozhraní .NET 3.5 byly několik omezení v návrhu známé typy:  
  
-   Přidání známé typy dynamicky, při serializaci nebo deserializaci, se nezdařilo.  
  
-   Serializátorů nelze pracují s informacemi o neznámé xsi: Type.  
  
-   Nebylo možné uživatelům určit, jaké xsi: type se mají zobrazovat v drátové síti k instanci, zmenšením velikosti serializace instance v drátové síti.  
  
 [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) řeší tyto problémy v rozhraní .NET 4.5.  
  
### <a name="getting-started"></a>Začínáme  
  
-   [Dokumentace k API překladače kontraktů dat](http://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [Představení překladače kontraktů dat](http://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   Ukázky:  
  
    -   [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### <a name="data-contract-resolver-scenarios"></a>Scénáře překladače kontraktů dat  
  
-   Zamezení museli deklarovat desítkami <xref:System.Runtime.Serialization.KnownTypeAttribute> objekty ve službě.  
  
-   Zmenšení velikosti objektu XML blob.  
  
## <a name="flowchart"></a>Vývojový diagram  
 Vývojový diagram je dobře známé zlepší vizuálně představují domény problémy. Je nový styl toku řízení, které jsme se Představujeme v rozhraní .NET 4. Jádro charakteristik vývojový diagram je, že je v každém okamžiku provést pouze jednu aktivitu. Na vývojových diagramech můžete express smyčky a alternativní výstupy, ale nejde nativně express souběžné provádění více uzlů.  
  
### <a name="getting-started"></a>Začínáme  
  
-   V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvořte konzolovou aplikaci pracovního postupu. Vývojový diagram přidáte v Návrháři pracovních postupů.  
  
-   Vývojový diagram funkce používá následující třídy:  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   Ukázky:  
  
    -   [Selhání zpracování v aktivitě sady vývojový diagram pomocí TryCatch](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [Pomocí kombinace vývojový diagram a vybrat scénář StateMachine](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [Náborové procesu](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   Návrhář dokumentaci:  
  
    -   [Vývojový diagram návrháře aktivit](/visualstudio/workflow-designer/flowchart-activity-designers)  
  
### <a name="flowchart-scenarios"></a>Vývojový diagram scénáře  
 Vývojový diagram aktivity lze použít k implementaci hádání hru. Je velmi jednoduchý hádání herní: počítač vybere náhodné číslo a má přehrávač tak snadno uhodnout toto číslo. Když přehrávač odešle každý odhad, počítač mu zobrazuje nápovědu (tj. "zkoušet na nižší číslo"). Pokud přehrávač najde číslo menší než 7 pokusů o přihlášení, dostane speciální Blahopřání z počítače. Tato hra můžete provedeny s kombinaci následující procedurální aktivity:  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Procedurální aktivity (pořadí, v případě, ForEach, přepínače, přiřazení, DoWhile, zatímco)  
 Procedurální aktivit poskytují mechanismus modelu sekvenční řízení toku pomocí koncepty, které jsou pro programátory v jazyce. Tyto aktivity povolit tradičně structured programování jazykové konstrukty a podle potřeby zadejte jazyk parita s běžné procedurální jazyků, například C# nebo VB.  
  
### <a name="getting-started"></a>Začínáme  
  
-   V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvořte konzolovou aplikaci pracovního postupu. Přidejte procedurální aktivity v Návrháři pracovních postupů.  
  
-   Ukázky:  
  
    -   [Náborové procesu](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [Podnikové nákupní proces](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   Návrhář dokumentaci:  
  
    -   [Návrhář paralelní aktivity](/visualstudio/workflow-designer/parallel-activity-designer)  
  
    -   [ParallelForEach\<T > Návrhář aktivity](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)  
  
### <a name="procedural-activity-scenarios"></a>Scénáře procedurální aktivity  
  
-   <xref:System.Activities.Statements.Parallel>Systém správy dokumentů: intranetu má pracovní postup schvalování dokumentů. Dokumenty vyžadují schválení uživatelé v několika oddělení před publikováním k intranetu. Není k dispozici pořadí zavedených pro schválení; mohou probíhat kdykoli během dokument je ve fázi "schválení čekající na vyřízení". Když uživatel odešle dokument ke kontrole musí být schválen manažerovi přímé, správce sítě intranet a Správce interních komunikací.  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>: Aplikace WF spravuje podnikové koupí v rámci velká společnost. Podnikové pravidla určují, že před plánování všechny operace nákupu, je vyžadována ocenění ze tří různých výrobců. Zaměstnanci z oddělení nákupní vybere tři dodavatelům společnosti dodavatele seznamu. Po těchto dodavatelů byly vybrané a upozornění, bude společnost počkat jejich hospodářského návrhy. Návrhy můžou mít v libovolném pořadí. K implementaci tento scénář v WF, můžeme použít <xref:System.Activities.Statements.ParallelForEach%601> které iteraci v rámci naší kolekce dodavatelů a požádat o jejich hospodářského návrhy. Po shromáždění jsou všechny nabídky, nejlepší vybrané a zobrazit.  
  
## <a name="invokemethod"></a>InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Aktivity umožňuje vyvolání veřejné metody v objektech nebo typy v oboru. Ji podporuje vyvoláním instance a statické metody s nebo bez parametrů (včetně pole parametrů) a obecné metody. Také umožňuje spuštění metody synchronně a asynchronně.  
  
### <a name="getting-started"></a>Začínáme  
  
-   V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvořte konzolovou aplikaci pracovního postupu. Přidat <xref:System.Activities.Statements.InvokeMethod> aktivity v Návrháři pracovních postupů a nakonfigurujte statické a instance metody na něm.  
  
-   Ukázky:  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   Návrhář dokumentace: [InvokeMethod Návrhář aktivity](/visualstudio/workflow-designer/invokemethod-activity-designer)  
  
### <a name="invokemethod-scenarios"></a>InvokeMethod scénáře  
  
-   Musí být volána metoda v objekt v oboru. Například hodnota musí být přidán do slovníku. Je volána metoda přidat instance slovníku a jsou k dispozici klíč a hodnotu.  
  
-   Metoda musí být volána na objekt starší verze CLR. Místo vytváření vlastních aktivit k zabalení volání starší verze třídy, pokud se nachází v oboru během spouštění pracovního postupu <xref:System.Activities.Statements.InvokeMethod> lze použít.  
  
## <a name="error-handling-activities"></a>Chyba zpracování aktivity  
 <xref:System.Activities.Statements.TryCatch> Aktivity poskytuje mechanismus pro zachytávání výjimek, ke kterým došlo během provádění sady obsažené aktivity (podobně jako Try/Catch – konstrukce v C# / VB.). <xref:System.Activities.Statements.TryCatch>poskytuje na úrovni pracovního postupu zpracování výjimek. Pokud je vyvolána neošetřená výjimka, pracovní postup byl přerušen a nakonec nebude provedeno bloku. Toto chování je konzistentní s C#.  
  
### <a name="getting-started"></a>Začínáme  
  
-   V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvořte konzolovou aplikaci pracovního postupu. Přidat <xref:System.Activities.Statements.TryCatch> aktivity v Návrháři pracovních postupů.  
  
-   Ukázky:  
  
    1.  [Selhání zpracování v aktivitě sady vývojový diagram pomocí TryCatch](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [Pomocí procedurální aktivit](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   Návrhář dokumentace: [návrháře aktivit zpracování chyb](/visualstudio/workflow-designer/error-handling-activity-designers)  
  
### <a name="error-handling-scenarios"></a>Chyba zpracování scénáře  
 Je třeba provést sadu aktivit a určitou logiku je třeba provést, když dojde k chybě. Pokud během tohoto zpracování logiky chyb zjistí, že chyba není použitelná pro obnovení, bude znovu vyvolány výjimka, a nadřazené aktivity (nebo hostiteli) se bude zabývat problém.  
  
## <a name="pick-activity"></a>Vyberte aktivitu  
 <xref:System.Activities.Statements.Pick> Poskytuje aktivity toku řízení na základě událostí modelování v WF. <xref:System.Activities.Statements.Pick>obsahuje mnoho větví, kde každá větev čeká na konkrétní událost dřív, než spustíte. V této instalaci <xref:System.Activities.Statements.Pick> se chová podobně jako <xref:System.Activities.Statements.Switch%601> do které aktivita, budou spuštěny pouze jednu sadu událostí naslouchá. U každé větve je vynucená událost a události, která nastane spustí první odpovídající firemní pobočky. Všechny ostatní větve zůstanou zrušte a zastavte naslouchání událostem.  
  
### <a name="getting-started"></a>Začínáme  
  
-   V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvořte konzolovou aplikaci pracovního postupu. Přidat <xref:System.Activities.Statements.Pick> aktivity v Návrháři pracovních postupů.  
  
-   Ukázka: [pomocí vybrat aktivity](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   Návrhář dokumentace: [vyberte Návrhář aktivity](/visualstudio/workflow-designer/pick-activity-designer)  
  
### <a name="pick-scenario"></a>Vybrat scénář  
 Uživatel musí projít vyzváni k zadání vstupu. Za normálních podmínek by zprostředkovatel pomocí volání metody jako <xref:System.Console.ReadLine%2A> výzvou pro vstup uživatele. Problém s tímto nastavením je, že program čeká, dokud uživatel nezadá něco. V tomto scénáři je potřeba vypršení časového limitu odblokovat aktivitu blokování. Obvyklým scénářem je ten, který vyžaduje úlohu provést v rámci dané doby trvání. Vypršení časového limitu blokování aktivity je scénář, kde si vyberte přidá velké hodnoty.  
  
## <a name="wcf-routing-service"></a>Směrovací služby WCF  
 Směrovací služby je navržený jako obecný softwaru směrovač, který umožňuje určit jak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]zprávy tok mezi klienty a služby.  Směrovací služby umožňuje oddělit klienty z vaší služby, který vám dává mnohem větší svobodu z hlediska konfigurace, může podporovat a flexibilitu máte při zvažování řešení pro hostování vaší služby.  V rozhraní .NET 3.5 služby a klienti byly úzce párované; Klient musí vědět o všech služeb ho nepotřebují, aby komunikoval s a kde se nachází. Kromě toho WCF v rozhraní .net Framework 3.5 měl následující omezení:  
  
-   Zpracování chyb byl složitý, jak tuto logiku musel být pevně zakódované do klienta.  
  
-   Služby a klienti měli vždy nutné použít stejné vazby.  
  
-   Služby byly zřídka dobře promítnou: je snazší mají klienta, obraťte se na jednu službu, která implementuje všechno, nemusíte volba mezi více služeb.  
  
 Služba směrování v rozhraní .net 4 je určena k usnadnění tyto problémy vyřešit. Nové směrování služby má následující funkce:  
  
1.  Na základě obsahu směrování (<xref:System.ServiceModel.Dispatcher.MessageFilter> objekty Zkontrolujte zprávu, kde ji by měly být odeslány.)  
  
2.  Protokol přemostění Datacenter (přenos & zprávu)  
  
3.  Zpracování chyb (směrovači zachytí výjimky komunikace a převezme zálohování koncových bodů)  
  
4.  (V paměti) dynamickou aktualizaci <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> a konfigurace směrování.  
  
### <a name="getting-started"></a>Začínáme  
  
1.  Dokumentace: [směrování](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  Ukázky: [směrování služby &#91; Ukázky WCF &#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  Blog: [pravidla směrování!](http://go.microsoft.com/fwlink/?LinkId=204956)  
  
### <a name="routing-scenarios"></a>Scénáře směrování  
 Směrovací služba je užitečné v následujících scénářích:  
  
-   Klienti může kontaktovat na více služeb bez nutnosti jejich vyřešit všechny přímo.  
  
-   Klienty můžete provádět další logiku v požadavku klienta k určení, kam směruje  
  
-   Rozložit operace, které klient provede do více implementace služby bez refaktoring klienta.  
  
-   Služby a klienti můžete nahrát jiný vazby s odlišné nastavení zabezpečení.  
  
-   Klienti se dá nastavit jako větší odolnost proti selhání nebo nedostupnost služby.  
  
## <a name="wcf-discovery"></a>Zjišťování WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Zjišťování je framework technologie, která umožňuje začlenit mechanismus zjišťování k infrastruktuře aplikace. Můžete použít zjistitelnost služby a nakonfigurovat vaši klienti pro vyhledání služeb. Klienti už musí být pevný programového s koncovým bodem, provedení robustnější aplikace a odolnost proti chybám. Zjišťování je ideální platformu k sestavení možnosti automatické konfigurace do vaší aplikace.  
  
 Produkt je postavená na standardní WS-Discovery. Je navržen tak být umožňuje vzájemnou spolupráci, rozšiřitelný a obecné. Produkt podporuje dva režimy činnosti:  
  
1.  Spravované: je entity v síti dobrou stávající služby, klienti dotaz ji přímo pro informace. Toto je obdobou služby Active Directory.  
  
2.  Ad hoc: kde klienti používají zprávy vícesměrového vysílání k vyhledání služeb.  
  
 Kromě toho se zprávy zjišťování bez ohledu na protokol sítě; můžete je v horní části libovolný protokol, který podporuje požadavky na režimu. Například zjišťování vícesměrového vysílání zprávy mohou být odeslány prostřednictvím kanálu UDP nebo jiné sítě, který podporuje vícesměrové zasílání zpráv.  Tyto návrhu body, v kombinaci s funkcí flexibilitu, vám umožní přizpůsobit zjišťování určený speciálně pro vaše řešení.  
  
### <a name="getting-started"></a>Začínáme  
  
-   Dokumentace: [zjišťování WCF](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   Ukázky: [zjišťování (Ukázky)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### <a name="discovery-scenarios"></a>Zjišťování scénáře  
 Vývojář nechce koncových bodů pevný kódu, protože neznámý, kdy bude k dispozici mé služby. Místo toho chce vývojář vybrat službu za běhu. Mezi součástmi v aplikaci je potřeba další oddělení, odolnosti a automatické konfigurace.  
  
## <a name="tracking"></a>Sledování  
 Pracovní postup sledování poskytuje přehled o provádění instanci pracovního postupu.  Sledování události jsou vydávány z pracovního postupu na úrovni instance pracovního postupu a při spuštění aktivity v rámci pracovního postupu. Sledování účastník pracovního postupu musí být přidán do hostitele pracovního postupu k odběru sledování záznamů. Sledování záznamy jsou filtrovány pomocí sledování profilu. .Net Framework poskytuje účastník sledování ETW (trasování událostí pro Windows) a základní profil je nainstalován v souboru machine.config.  
  
### <a name="getting-started"></a>Začínáme  
  
1.  V [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], vytvoření projektu aplikace služby WCF pracovního postupu. A <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> pár se umístí na plátno spustit.  
  
2.  Otevřete soubor web.config a přidejte trasování událostí pro Windows sledování chování s žádný profil.  
  
    1.  Výchozí profil se používá.  
  
    2.  Otevřete Prohlížeč událostí a povolení analytického kanálu v uzlu následující: **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows** , **Serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.  
  
    3.  Spouštění služby pracovního postupu.  
  
    4.  Sledujte pracovním sledování událostí v prohlížeči událostí.  
  
3.  Ukázky: [sledování](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  Rámcová dokumentace: [pracovního postupu pro sledování a trasování](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
  
## <a name="sql-workflow-instance-store"></a>Ukládání Instance pracovního postupu SQL  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Je implementace instance úložiště založené na systému SQL Server. Instance úložiště ukládá stav spuštěné instance a všechny údaje potřebné k načtení a pokračovat v této instanci. Hostitel služby dá pokyn ukládání instance uložit stav instance, pokud pracovní postup potrvá a zadá ukládání instance načíst stav instance při doručení zprávy pro tuto instanci nebo zpoždění aktivity vyprší.  
  
### <a name="getting-started"></a>Začínáme  
  
1.  V [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vytvořit pracovní postup, který obsahuje element implicitního nebo explicitního <xref:System.Activities.Statements.Persist> aktivity. Přidat <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> chování na vašem hostiteli služby pracovního postupu. To lze provést v kódu nebo v konfiguračním souboru aplikace.  
  
2.  Ukázky: [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  Rámcová dokumentace: [úložiště Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).
