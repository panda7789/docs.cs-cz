---
title: 'Postupy: Spuštění pracovního postupu'
description: V tomto článku se dozvíte, jak vytvořit hostitele pracovního postupu a spustit pracovní postup definovaný v předchozím článku v této programovací model Windows Workflow Foundation řadě kurzů.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 86062dd5147e6e354833928fd98bd1f6b5de9114
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421498"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="6568f-103">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-103">How to: Run a Workflow</span></span>
<span data-ttu-id="6568f-104">Toto téma je pokračováním v kurzu programovací model Windows Workflow Foundation Začínáme a popisuje, jak vytvořit hostitele pracovního postupu a spustit pracovní postup definovaný v předchozí části [Postupy: vytvoření pracovního postupu](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="6568f-104">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="6568f-105">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="6568f-105">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6568f-106">Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md) a [Postupy: vytvoření pracovního postupu](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6568f-106">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6568f-107">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6568f-107">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="6568f-108">Vytvoření projektu hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-108">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="6568f-109">Otevřete řešení z předchozí části [Postupy: vytvoření tématu aktivity](how-to-create-an-activity.md) pomocí sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6568f-109">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="6568f-110">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení **WF45GettingStartedTutorial** a vyberte **Přidat**, **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="6568f-110">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="6568f-111">Pokud se okno **Průzkumník řešení** nezobrazí, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="6568f-111">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="6568f-112">V **nainstalovaném** uzlu vyberte **Visual C#**, **Workflow** (nebo **Visual Basic**, **pracovní postup**).</span><span class="sxs-lookup"><span data-stu-id="6568f-112">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="6568f-113">V závislosti na tom, který programovací jazyk je nakonfigurován jako primární jazyk v aplikaci Visual Studio, může být uzel **Visual C#** nebo **Visual Basic** pod uzlem **ostatní jazyky** v **nainstalovaném** uzlu.</span><span class="sxs-lookup"><span data-stu-id="6568f-113">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="6568f-114">V rozevíracím seznamu .NET Framework verze se ujistěte, že je vybraná možnost **.NET Framework 4,5** .</span><span class="sxs-lookup"><span data-stu-id="6568f-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="6568f-115">V seznamu **pracovních postupů** vyberte **Konzolová aplikace pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="6568f-115">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="6568f-116">`NumberGuessWorkflowHost`Do pole **název** zadejte a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="6568f-116">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="6568f-117">Tím se vytvoří aplikace pracovního postupu Starter se základní podporou hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-117">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="6568f-118">Tento základní kód pro hostování se upraví a použije ke spuštění aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-118">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="6568f-119">Klikněte pravým tlačítkem na nově přidaný projekt **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6568f-119">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="6568f-120">V seznamu **Přidat odkaz** vyberte **řešení** , zaškrtněte políčko vedle **NumberGuessWorkflowActivities**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6568f-120">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="6568f-121">V **Průzkumník řešení** klikněte pravým tlačítkem na **Workflow1. XAML** a vyberte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="6568f-121">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="6568f-122">Potvrďte kliknutím na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="6568f-122">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="6568f-123">Úprava kódu hostování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-123">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="6568f-124">Poklikejte na **program.cs** nebo **Module1. vb** v **Průzkumník řešení** pro zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="6568f-124">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="6568f-125">Pokud se okno **Průzkumník řešení** nezobrazí, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="6568f-125">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="6568f-126">Vzhledem k tomu, že tento projekt byl vytvořen pomocí šablony **konzolové aplikace pracovního postupu** , **program.cs** nebo **Module1. vb** obsahuje následující základní kód pro hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-126">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="6568f-127">Tento generovaný kód pro hostování používá <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="6568f-127">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="6568f-128"><xref:System.Activities.WorkflowInvoker>poskytuje jednoduchý způsob, jak vyvolat pracovní postup, jako by šlo o volání metody a dá se použít jenom pro pracovní postupy, které nepoužívají trvalost.</span><span class="sxs-lookup"><span data-stu-id="6568f-128"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="6568f-129"><xref:System.Activities.WorkflowApplication>poskytuje bohatší model pro spouštění pracovních postupů, které obsahují oznámení o událostech životního cyklu, řízení spouštění, opětovném obnovení záložek a persistenci.</span><span class="sxs-lookup"><span data-stu-id="6568f-129"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="6568f-130">V tomto příkladu se používají záložky a <xref:System.Activities.WorkflowApplication> slouží k hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-130">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="6568f-131">Přidejte následující `using` příkaz nebo **importy** na začátek **program.cs** nebo **Module1. vb** pod existující příkazy **using** nebo **Imports** .</span><span class="sxs-lookup"><span data-stu-id="6568f-131">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="6568f-132">Nahraďte řádky kódu, které jsou používány, <xref:System.Activities.WorkflowInvoker> pomocí následujícího základního <xref:System.Activities.WorkflowApplication> hostujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="6568f-132">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="6568f-133">Tento ukázkový hostující kód znázorňuje základní kroky pro hostování a vyvolání pracovního postupu, ale ještě neobsahuje funkce pro úspěšné spuštění pracovního postupu z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6568f-133">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="6568f-134">V následujících krocích se tento základní kód upraví a přidají se další funkce, dokud se aplikace nedokončí.</span><span class="sxs-lookup"><span data-stu-id="6568f-134">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6568f-135">Nahraďte je `Workflow1` v těchto příkladech pomocí `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` nebo v `StateMachineNumberGuessWorkflow` závislosti na tom, který pracovní postup jste dokončili v předchozím postupu [: vytvoření kroku pracovního postupu](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="6568f-135">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="6568f-136">Pokud se nenahradíte, zobrazí `Workflow1` se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="6568f-136">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="6568f-137">Tento kód vytvoří <xref:System.Activities.WorkflowApplication> přihlášení k odběru tří událostí životního cyklu pracovního postupu, spustí pracovní postup s voláním <xref:System.Activities.WorkflowApplication.Run%2A> a potom počká, až se pracovní postup dokončí.</span><span class="sxs-lookup"><span data-stu-id="6568f-137">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="6568f-138">Po dokončení pracovního postupu se <xref:System.Threading.AutoResetEvent> Nastaví a hostitelská aplikace se dokončí.</span><span class="sxs-lookup"><span data-stu-id="6568f-138">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="6568f-139">Nastavení vstupních argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-139">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="6568f-140">Přidejte následující příkaz na začátek **program.cs** nebo **Module1. vb** pod existující `using` `Imports` příkazy nebo.</span><span class="sxs-lookup"><span data-stu-id="6568f-140">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="6568f-141">Nahraďte řádek kódu, který vytvoří nový, <xref:System.Activities.WorkflowApplication> pomocí následujícího kódu, který vytvoří a předá do pracovního postupu slovník parametrů při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="6568f-141">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6568f-142">Nahraďte je `Workflow1` v těchto příkladech pomocí `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` nebo v `StateMachineNumberGuessWorkflow` závislosti na tom, který pracovní postup jste dokončili v předchozím postupu [: vytvoření kroku pracovního postupu](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="6568f-142">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="6568f-143">Pokud se nenahradíte, zobrazí `Workflow1` se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="6568f-143">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="6568f-144">Tento slovník obsahuje jeden element s klíčem `MaxNumber` .</span><span class="sxs-lookup"><span data-stu-id="6568f-144">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="6568f-145">Klíče ve vstupním slovníku odpovídají vstupním argumentům pro kořenovou aktivitu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-145">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="6568f-146">`MaxNumber`používá pracovní postup k určení horní meze pro náhodně generované číslo.</span><span class="sxs-lookup"><span data-stu-id="6568f-146">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="6568f-147">Načtení výstupních argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-147">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="6568f-148">Upravte <xref:System.Activities.WorkflowApplication.Completed%2A> obslužnou rutinu tak, aby načetla a zobrazila počet zapínání pomocí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-148">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="6568f-149">Obnovení záložky</span><span class="sxs-lookup"><span data-stu-id="6568f-149">To resume a bookmark</span></span>

1. <span data-ttu-id="6568f-150">Do vrcholu metody přidejte následující kód `Main` hned po existující <xref:System.Threading.AutoResetEvent> deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6568f-150">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="6568f-151">Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužnou rutinu hned pod stávající tři obslužné rutiny životního cyklu pracovního postupu v `Main` .</span><span class="sxs-lookup"><span data-stu-id="6568f-151">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="6568f-152">Pokaždé, když se pracovní postup nečinný čeká na další odhad, je tato obslužná rutina volána a `idleAction` <xref:System.Threading.AutoResetEvent> je nastavena.</span><span class="sxs-lookup"><span data-stu-id="6568f-152">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="6568f-153">Kód v následujícím kroku používá `idleEvent` a `syncEvent` k určení, zda pracovní postup čeká na další odhad nebo je dokončen.</span><span class="sxs-lookup"><span data-stu-id="6568f-153">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6568f-154">V tomto příkladu hostitelská aplikace používá události automatického resetu v <xref:System.Activities.WorkflowApplication.Completed%2A> <xref:System.Activities.WorkflowApplication.Idle%2A> obslužných rutinách a k synchronizaci hostitelské aplikace s průběhem pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6568f-154">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="6568f-155">Před pokračováním záložky není nutné blokovat a čekat na nečinnost pracovního postupu, ale v tomto příkladu jsou vyžadovány události synchronizace, aby hostitel věděl, zda byl pracovní postup dokončen nebo zda čeká na další uživatelský vstup pomocí <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="6568f-155">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="6568f-156">Další informace najdete v tématu [záložky](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="6568f-156">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="6568f-157">Odeberte volání `WaitOne` a nahraďte ho kódem pro shromáždění vstupu od uživatele a pokračování v <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="6568f-157">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="6568f-158">Odeberte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="6568f-158">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="6568f-159">Nahraďte následujícím příkladem.</span><span class="sxs-lookup"><span data-stu-id="6568f-159">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="to-build-and-run-the-application"></a><a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="6568f-160">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="6568f-160">To build and run the application</span></span>

1. <span data-ttu-id="6568f-161">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="6568f-161">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="6568f-162">Stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6568f-162">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="6568f-163">Zkuste číslo uhodnout v co nejkratší míře.</span><span class="sxs-lookup"><span data-stu-id="6568f-163">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="6568f-164">Chcete-li aplikaci vyzkoušet s jedním z dalších stylů pracovního postupu, nahraďte `Workflow1` v kódu, který vytváří <xref:System.Activities.WorkflowApplication> s `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` nebo `StateMachineNumberGuessWorkflow` , podle toho, který styl pracovního postupu si přejete.</span><span class="sxs-lookup"><span data-stu-id="6568f-164">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="6568f-165">Pokyny k přidání trvalosti do aplikace pracovního postupu naleznete v dalším tématu [Postup: vytvoření a spuštění dlouho běžícího pracovního postupu](how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6568f-165">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="6568f-166">Příklad</span><span class="sxs-lookup"><span data-stu-id="6568f-166">Example</span></span>
 <span data-ttu-id="6568f-167">Následující příklad je úplný výpis kódu pro `Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="6568f-167">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="6568f-168">Nahraďte je `Workflow1` v těchto příkladech pomocí `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` nebo v `StateMachineNumberGuessWorkflow` závislosti na tom, který pracovní postup jste dokončili v předchozím postupu [: vytvoření kroku pracovního postupu](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="6568f-168">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="6568f-169">Pokud se nenahradíte, zobrazí `Workflow1` se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="6568f-169">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="6568f-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="6568f-170">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="6568f-171">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6568f-171">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="6568f-172">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="6568f-172">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="6568f-173">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-173">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="6568f-174">Postupy: Vytvoření a spuštění dlouhodobého pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-174">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="6568f-175">Čekání na zadání v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="6568f-175">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="6568f-176">Hostování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6568f-176">Hosting Workflows</span></span>](hosting-workflows.md)
