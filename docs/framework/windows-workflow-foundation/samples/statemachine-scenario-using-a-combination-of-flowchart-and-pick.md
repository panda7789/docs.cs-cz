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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a4ff644367f0bcd6562bd8931406a11f39d62df
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="f7187-102">Pomocí kombinace vývojový diagram a vybrat scénář StateMachine</span><span class="sxs-lookup"><span data-stu-id="f7187-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="f7187-103">Tento příklad znázorňuje způsob implementace scénář jednoduchého stopky pomocí kombinace <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="f7187-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="f7187-104">Použije příjem a odesílání uvnitř aktivity vybrat tak, aby naslouchala událostem stopky.</span><span class="sxs-lookup"><span data-stu-id="f7187-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7187-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f7187-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7187-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f7187-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7187-107">Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f7187-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7187-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f7187-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="f7187-109">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f7187-109">Sample Details</span></span>  
 <span data-ttu-id="f7187-110">Následující tabulka uvádí projekty v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="f7187-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="f7187-111">Název projektu</span><span class="sxs-lookup"><span data-stu-id="f7187-111">Project Name</span></span>|<span data-ttu-id="f7187-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f7187-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="f7187-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="f7187-113">StopWatchService</span></span>|<span data-ttu-id="f7187-114">Tento projekt obsahuje implementaci stavového stroje pro ukázku stopky pomocí kombinace <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="f7187-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="f7187-115"><xref:System.Activities.Statements.Pick> Aktivita má 3 <xref:System.Activities.Statements.PickBranch> příkazů v rámci <xref:System.Activities.Statements.Pick.Branches%2A> vlastnost, která naslouchat `GetStart`, `GetStop` a `GetOff` události.</span><span class="sxs-lookup"><span data-stu-id="f7187-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="f7187-116">Aktivace založené na příchozí události, aktivační události pro jednu z větve a odpovídající <xref:System.Activities.Statements.PickBranch.Action%2A> se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="f7187-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="f7187-117">V <xref:System.Activities.Statements.PickBranch.Action%2A> vlastnost, je <xref:System.Activities.Statements.Switch%601> příkaz, který se vyhodnotí, zda je přechod legitimní přechod a pokud je, `currentState` vlastnost je aktualizován přechodu stavu a může odeslat klientovi.</span><span class="sxs-lookup"><span data-stu-id="f7187-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="f7187-118"><xref:System.Activities.Statements.FlowDecision> Aktivity na konci <xref:System.Activities.Statements.Flowchart> vyhodnotí `currentState` vlastnosti k určení, jestli je stav terminálu.</span><span class="sxs-lookup"><span data-stu-id="f7187-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="f7187-119">Pokud se jedná, pracovní postup končí; v opačném případě řízení smyčky zpět na začátek <xref:System.Activities.Statements.Pick> aktivity, kde pracovního postupu čeká na další stopky události.</span><span class="sxs-lookup"><span data-stu-id="f7187-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="f7187-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="f7187-120">StopWatchClient</span></span>|<span data-ttu-id="f7187-121">Toto je jednoduchý sekvenční pracovní postup konzolovou aplikaci, která odešle různé události stopky s jednoduchou odesílat nebo přijímat kombinace aktivity.</span><span class="sxs-lookup"><span data-stu-id="f7187-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f7187-122">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="f7187-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="f7187-123">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení StateMachineWithPick.sln.</span><span class="sxs-lookup"><span data-stu-id="f7187-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f7187-124">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f7187-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f7187-125">Spustit StopWatchService.exe z [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] jako správce kliknutím pravým tlačítkem na soubor .exe a výběrem **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="f7187-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="f7187-126">Přejděte do složky StateMachineWithPick\CS\StopWatchService\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="f7187-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="f7187-127">Klikněte pravým tlačítkem na soubor StopWatchService.exe a vyberte **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="f7187-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="f7187-128">Spuštění klienta aplikace StopWatchClient z uvnitř [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7187-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="f7187-129">V **Průzkumníku řešení**, vyberte **StopWatchClient** projektu a klikněte pravým tlačítkem na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="f7187-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="f7187-130">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f7187-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="f7187-131">Přepnout zpět do okna konzoly pro StopWatchService.exe zobrazíte přechodů mezi stavy.</span><span class="sxs-lookup"><span data-stu-id="f7187-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7187-132">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f7187-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f7187-133">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f7187-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f7187-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f7187-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f7187-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f7187-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`