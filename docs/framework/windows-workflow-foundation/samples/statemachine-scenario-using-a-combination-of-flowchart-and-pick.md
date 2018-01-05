---
title: "Pomocí kombinace vývojový diagram a vybrat scénář StateMachine"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39ae1be025e3b888fff8b46ebbc45832c218dda7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Pomocí kombinace vývojový diagram a vybrat scénář StateMachine
Tento příklad znázorňuje způsob implementace scénář jednoduchého stopky pomocí kombinace <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Pick> aktivity. Použije příjem a odesílání uvnitř aktivity vybrat tak, aby naslouchala událostem stopky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Následující tabulka uvádí projekty v této ukázce.  
  
|Název projektu|Popis|  
|-|-|  
|StopWatchService|Tento projekt obsahuje implementaci stavového stroje pro ukázku stopky pomocí kombinace <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Pick> aktivity.<br /><br /> <xref:System.Activities.Statements.Pick> Aktivita má 3 <xref:System.Activities.Statements.PickBranch> příkazů v rámci <xref:System.Activities.Statements.Pick.Branches%2A> vlastnost, která naslouchat `GetStart`, `GetStop` a `GetOff` události. Aktivace založené na příchozí události, aktivační události pro jednu z větve a odpovídající <xref:System.Activities.Statements.PickBranch.Action%2A> se aktivuje. V <xref:System.Activities.Statements.PickBranch.Action%2A> vlastnost, je <xref:System.Activities.Statements.Switch%601> příkaz, který se vyhodnotí, zda je přechod legitimní přechod a pokud je, `currentState` vlastnost je aktualizován přechodu stavu a může odeslat klientovi.<br /><br /> <xref:System.Activities.Statements.FlowDecision> Aktivity na konci <xref:System.Activities.Statements.Flowchart> vyhodnotí `currentState` vlastnosti k určení, jestli je stav terminálu. Pokud se jedná, pracovní postup končí; v opačném případě řízení smyčky zpět na začátek <xref:System.Activities.Statements.Pick> aktivity, kde pracovního postupu čeká na další stopky události.|  
|StopWatchClient|Toto je jednoduchý sekvenční pracovní postup konzolovou aplikaci, která odešle různé události stopky s jednoduchou odesílat nebo přijímat kombinace aktivity.|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení StateMachineWithPick.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Spustit StopWatchService.exe z [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] jako správce kliknutím pravým tlačítkem na soubor .exe a výběrem **spustit jako správce**.  
  
    1.  Přejděte do složky StateMachineWithPick\CS\StopWatchService\bin\Debug.  
  
    2.  Klikněte pravým tlačítkem na soubor StopWatchService.exe a vyberte **spustit jako správce**.  
  
4.  Spuštění klienta aplikace StopWatchClient z uvnitř [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  V **Průzkumníku řešení**, vyberte **StopWatchClient** projektu a klikněte pravým tlačítkem na **nastavit jako spouštěný projekt**.  
  
    2.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
5.  Přepnout zpět do okna konzoly pro StopWatchService.exe zobrazíte přechodů mezi stavy.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`