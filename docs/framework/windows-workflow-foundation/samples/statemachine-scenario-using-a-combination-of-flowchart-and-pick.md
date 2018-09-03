---
title: Scénář stavového stroje s využitím kombinace FlowChart a Pick
ms.date: 03/30/2017
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
ms.openlocfilehash: b0f8e884a8a6c62c4e7edaf5cc9727bf7bfe8603
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483928"
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Scénář stavového stroje s využitím kombinace FlowChart a Pick
Tato ukázka předvádí, jak implementovat jednoduché stopky scénář využívá kombinaci <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Pick> aktivity. Využívá přijímání a odesílání v rámci aktivity Pick tak, aby naslouchala událostem stopky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na stránku (stahování) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Následující tabulka obsahuje seznam projektů v této ukázce.  
  
|Název projektu|Popis|  
|-|-|  
|StopWatchService|Tento projekt obsahuje implementace stavového stroje pro ukázku stopky pomocí kombinace <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Pick> aktivity.<br /><br /> <xref:System.Activities.Statements.Pick> Aktivita má 3 <xref:System.Activities.Statements.PickBranch> příkazů v rámci <xref:System.Activities.Statements.Pick.Branches%2A> vlastnost, která naslouchat `GetStart`, `GetStop` a `GetOff` události. Aktivovat podle příchozí události, aktivační události pro jeden z větve a odpovídající <xref:System.Activities.Statements.PickBranch.Action%2A> se aktivuje. V <xref:System.Activities.Statements.PickBranch.Action%2A> vlastnost, je <xref:System.Activities.Statements.Switch%601> příkaz, který se vyhodnotí, zda tento přechod je legitimní přechodu a pokud ano, `currentState` vlastnost je aktualizovat, aby přechodu stavu a může odeslat klientovi.<br /><br /> <xref:System.Activities.Statements.FlowDecision> Aktivity na konci <xref:System.Activities.Statements.Flowchart> vyhodnotí `currentState` a určí, zda je stav terminálu. Pokud se jedná, ukončení pracovního postupu; jinak kontrolujete zpět na začátek smyčky <xref:System.Activities.Statements.Pick> kde pracovní postup počká na další události stopky aktivity.|  
|StopWatchClient|Toto je konzolová aplikace jednoduchý sekvenční pracovní postup, který odesílá různé události stopky v jednoduchém odesílat ani přijímat kombinace aktivity.|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení StateMachineWithPick.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Spustit StopWatchService.exe z [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] jako správce tak, že kliknete pravým tlačítkem na soubor .exe a výběr **spustit jako správce**.  
  
    1.  Přejděte do složky StateMachineWithPick\CS\StopWatchService\bin\Debug.  
  
    2.  Klikněte pravým tlačítkem na soubor StopWatchService.exe a vyberte **spustit jako správce**.  
  
4.  Spuštění klientské aplikace StopWatchClient v rámci [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  V **Průzkumníka řešení**, vyberte **StopWatchClient** projektu a klikněte pravým tlačítkem na **nastavit jako spouštěný projekt**.  
  
    2.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
5.  Přepněte zpět do okna konzoly pro StopWatchService.exe zobrazíte přechodů mezi stavy.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`