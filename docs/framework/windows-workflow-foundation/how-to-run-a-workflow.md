---
title: "Postupy: spuštění pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a41bf5c1f7a12e98ac10295af5b2608c8bf3a46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="4759d-102">Postupy: spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-102">How to: Run a Workflow</span></span>
<span data-ttu-id="4759d-103">Toto téma je pokračování kurzu Windows Workflow Foundation Začínáme a popisuje, jak vytvořit hostitele pracovního postupu a spuštění pracovního postupu definované v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="4759d-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4759d-104">Každého tématu v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="4759d-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="4759d-105">K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) a [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="4759d-105">To complete this topic you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) and [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4759d-106">Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="4759d-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="4759d-107">Vytvoření projektu hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="4759d-108">Otevřete řešení z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu pomocí [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4759d-108">Open the solution from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic by using [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="4759d-109">Klikněte pravým tlačítkem myši **WF45GettingStartedTutorial** řešení v **Průzkumníku řešení** a vyberte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="4759d-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="4759d-110">Pokud **Průzkumníku řešení** se nezobrazí okno, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="4759d-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="4759d-111">V **nainstalovaná** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**).</span><span class="sxs-lookup"><span data-stu-id="4759d-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4759d-112">V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalovaná** uzlu.</span><span class="sxs-lookup"><span data-stu-id="4759d-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="4759d-113">Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4759d-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="4759d-114">Vyberte **pracovního postupu konzolové aplikace** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="4759d-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="4759d-115">Typ `NumberGuessWorkflowHost` do **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="4759d-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="4759d-116">Tím se vytvoří aplikace starter pracovního postupu s základní pracovní postup, který je hostitelem podporu.</span><span class="sxs-lookup"><span data-stu-id="4759d-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="4759d-117">Tento základní hostování kód je upravit a použít ke spuštění aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4759d-117">This basic hosting code is modified and used to run the workflow application.</span></span>  
  
4.  <span data-ttu-id="4759d-118">Klikněte pravým tlačítkem na nově přidaný **NumberGuessWorkflowHost** projektu v **Průzkumníku řešení** a vyberte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="4759d-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="4759d-119">Vyberte **řešení** z **přidat odkaz na** seznamu, zaškrtněte políčko vedle položky **NumberGuessWorkflowActivities**a potom klikněte na **OK** .</span><span class="sxs-lookup"><span data-stu-id="4759d-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="4759d-120">Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníku řešení** a zvolte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="4759d-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="4759d-121">Klikněte na tlačítko **OK** k potvrzení.</span><span class="sxs-lookup"><span data-stu-id="4759d-121">Click **OK** to confirm.</span></span>  
  
### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="4759d-122">Upravit pracovní postup hostování kódu</span><span class="sxs-lookup"><span data-stu-id="4759d-122">To modify the workflow hosting code</span></span>  
  
1.  <span data-ttu-id="4759d-123">Klikněte dvakrát na **Program.cs** nebo **Module1.vb** v **Průzkumníku řešení** zobrazíte kód.</span><span class="sxs-lookup"><span data-stu-id="4759d-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="4759d-124">Pokud **Průzkumníku řešení** se nezobrazí okno, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="4759d-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
     <span data-ttu-id="4759d-125">Protože tento projekt bylo vytvořeno pomocí **pracovního postupu konzolové aplikace** šablony, **Program.cs** nebo **Module1.vb** obsahuje následující hostování základní pracovní postup kód.</span><span class="sxs-lookup"><span data-stu-id="4759d-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>  
  
    ```vb  
    ' Create and cache the workflow definition  
    Activity workflow1 = new Workflow1()  
    WorkflowInvoker.Invoke(workflow1)  
    ```  
  
    ```csharp  
    // Create and cache the workflow definition  
    Activity workflow1 = new Workflow1();  
    WorkflowInvoker.Invoke(workflow1);  
    ```  
  
     <span data-ttu-id="4759d-126">Tato vygenerována hostování kód používá <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="4759d-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="4759d-127"><xref:System.Activities.WorkflowInvoker>poskytuje jednoduchý způsob pro vyvolání pracovního postupu, jako by byly volání metody a lze použít pouze pro pracovní postupy, které nepoužívají trvalost.</span><span class="sxs-lookup"><span data-stu-id="4759d-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="4759d-128"><xref:System.Activities.WorkflowApplication>poskytuje bohatší model pro spouštění pracovních postupů, které obsahuje oznámení o události životního cyklu, řízení provádění, obnovení záložku a trvalost.</span><span class="sxs-lookup"><span data-stu-id="4759d-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="4759d-129">Tento příklad používá záložky a <xref:System.Activities.WorkflowApplication> se používá k hostování pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="4759d-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="4759d-130">Přidejte následující `using` nebo **importy** příkaz v horní části **Program.cs** nebo **Module1.vb** pod existující **pomocí** nebo **importy** příkazy.</span><span class="sxs-lookup"><span data-stu-id="4759d-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     <span data-ttu-id="4759d-131">Nahraďte řádky kódu, které používají <xref:System.Activities.WorkflowInvoker> s následující basic <xref:System.Activities.WorkflowApplication> hostování kódu.</span><span class="sxs-lookup"><span data-stu-id="4759d-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="4759d-132">Tato ukázka hostování kód ukazuje základní kroky pro hostování a vyvolání pracovní postup, ale ještě neobsahuje funkce k úspěšnému spuštění pracovního postupu z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4759d-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="4759d-133">V následujících krocích je-li změnit tento základní kód a další funkce se přidají, dokud se nedokončí aplikace.</span><span class="sxs-lookup"><span data-stu-id="4759d-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4759d-134">Nahraďte `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup dokončit v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) krok.</span><span class="sxs-lookup"><span data-stu-id="4759d-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="4759d-135">Pokud jste nenahrazují `Workflow1` pak při akci a sestavení nebo spusťte pracovní postup bude docházet k chybám sestavení.</span><span class="sxs-lookup"><span data-stu-id="4759d-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     <span data-ttu-id="4759d-136">Tento kód vytvoří <xref:System.Activities.WorkflowApplication>, jako odběratel u tři události životního cyklu pracovního postupu, spustí pracovní postup pomocí volání <xref:System.Activities.WorkflowApplication.Run%2A>a potom čeká na dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4759d-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="4759d-137">Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> je sada a hostitele dokončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="4759d-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>  
  
### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="4759d-138">Chcete-li nastavit vstupní argumenty pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-138">To set input arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="4759d-139">Přidejte následující příkaz v horní části **Program.cs** nebo **Module1.vb** pod existující `using` nebo `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="4759d-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  <span data-ttu-id="4759d-140">Nahraďte řádek kódu, který vytvoří nový <xref:System.Activities.WorkflowApplication> s následujícím kódem, který vytvoří a předává slovník parametrů do pracovního postupu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="4759d-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4759d-141">Nahraďte `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup dokončit v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) krok.</span><span class="sxs-lookup"><span data-stu-id="4759d-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="4759d-142">Pokud jste nenahrazují `Workflow1` pak při akci a sestavení nebo spusťte pracovní postup bude docházet k chybám sestavení.</span><span class="sxs-lookup"><span data-stu-id="4759d-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="4759d-143">Tento slovník obsahuje jeden element s klíčem `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="4759d-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="4759d-144">Klíče ve slovníku vstupní odpovídají vstupní argumenty na kořenové aktivity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4759d-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="4759d-145">`MaxNumber`v tomto pracovním postupu se používá k určení horní mez pro náhodně generovaným číslem.</span><span class="sxs-lookup"><span data-stu-id="4759d-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="4759d-146">Načíst výstup argumenty pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-146">To retrieve output arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="4759d-147">Změnit <xref:System.Activities.WorkflowApplication.Completed%2A> obslužná rutina načtení a zobrazuje počet oplátku používá pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="4759d-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a><span data-ttu-id="4759d-148">Chcete-li obnovit záložky</span><span class="sxs-lookup"><span data-stu-id="4759d-148">To resume a bookmark</span></span>  
  
1.  <span data-ttu-id="4759d-149">Přidejte následující kód v horní části `Main` metoda bezprostředně za existující <xref:System.Threading.AutoResetEvent> deklarace.</span><span class="sxs-lookup"><span data-stu-id="4759d-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  <span data-ttu-id="4759d-150">Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužných rutin pod existující tři pracovní postup životního cyklu obslužných rutin v `Main`.</span><span class="sxs-lookup"><span data-stu-id="4759d-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     <span data-ttu-id="4759d-151">Pokaždé, když pracovní postup bude nečinnosti čekání na další odhad, se nazývá této obslužné rutiny a `idleAction` <xref:System.Threading.AutoResetEvent> nastavena.</span><span class="sxs-lookup"><span data-stu-id="4759d-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="4759d-152">Kód v následujícím kroku používá `idleEvent` a `syncEvent` k určení, zda pracovní postup se čeká na další odhad nebo dokončení.</span><span class="sxs-lookup"><span data-stu-id="4759d-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4759d-153">V tomto příkladu používá hostitelskou aplikaci automatickým vynulováním události v <xref:System.Activities.WorkflowApplication.Completed%2A> a <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny pro synchronizaci hostitelskou aplikaci s průběh pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4759d-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="4759d-154">Není nutné blokovat a počkejte, pracovní postup na nečinnost před obnovením záložku, ale v tomto příkladu události synchronizace jsou vyžaduje, aby hostitel věděli, jestli dokončení pracovního postupu nebo jestli je čekání na další vstup uživatele pomocí <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="4759d-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="4759d-155">[Záložky](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="4759d-155"> [Bookmarks](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
3.  <span data-ttu-id="4759d-156">Odeberte volání `WaitOne`a nahraďte ji metodou kód shromažďovat vstup od uživatele a obnovit <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="4759d-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>  
  
     <span data-ttu-id="4759d-157">Odeberte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="4759d-157">Remove the following line of code.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     <span data-ttu-id="4759d-158">Nahraďte ji následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4759d-158">Replace it with the following example.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="4759d-159">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="4759d-159">To build and run the application</span></span>  
  
1.  <span data-ttu-id="4759d-160">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="4759d-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="4759d-161">Stisknutím klávesy CTRL + F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4759d-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="4759d-162">Zkuste tak snadno uhodnout číslo na nejmenším oplátku míře.</span><span class="sxs-lookup"><span data-stu-id="4759d-162">Try to guess the number in as few turns as possible.</span></span>  
  
     <span data-ttu-id="4759d-163">Pokud chcete vyzkoušet aplikace s jedním z dalších styly pracovního postupu, nahraďte `Workflow1` v kódu, který vytvoří <xref:System.Activities.WorkflowApplication> s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`, v závislosti na styl pracovního postupu, který požadavky.</span><span class="sxs-lookup"><span data-stu-id="4759d-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="4759d-164">Pokyny o tom, jak přidat trvalost do aplikace pracovního postupu, naleznete v dalším tématu [postupy: vytvoření a spuštění dlouhém pracovním postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="4759d-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4759d-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="4759d-165">Example</span></span>  
 <span data-ttu-id="4759d-166">V následujícím příkladu je úplný výpis pro kódu `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="4759d-166">The following example is the complete code listing for the `Main` method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4759d-167">Nahraďte `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup dokončit v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) krok.</span><span class="sxs-lookup"><span data-stu-id="4759d-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="4759d-168">Pokud jste nenahrazují `Workflow1` pak při akci a sestavení nebo spusťte pracovní postup bude docházet k chybám sestavení.</span><span class="sxs-lookup"><span data-stu-id="4759d-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="4759d-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="4759d-169">See Also</span></span>  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [<span data-ttu-id="4759d-170">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="4759d-170">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="4759d-171">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="4759d-171">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="4759d-172">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-172">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="4759d-173">Postupy: Vytvoření a spuštění dlouhodobého pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-173">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [<span data-ttu-id="4759d-174">Čekání na zadání v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="4759d-174">Waiting for Input in a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [<span data-ttu-id="4759d-175">Hostování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4759d-175">Hosting Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)
