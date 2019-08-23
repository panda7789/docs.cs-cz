---
title: 'Postupy: Spuštění pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 3badda7afeb25b44b0de574f97452d05efe75bfc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962290"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="89eb9-102">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-102">How to: Run a Workflow</span></span>
<span data-ttu-id="89eb9-103">Toto téma je pokračováním v kurzu programovací model Windows Workflow Foundation Začínáme a popisuje, jak vytvořit hostitele pracovního postupu a spustit pracovní postup definovaný v předchozím [postupu: Vytvořte téma pracovního](how-to-create-a-workflow.md) postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="89eb9-104">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="89eb9-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="89eb9-105">Chcete-li dokončit toto téma, je [nutné nejprve provést následující kroky: Vytvoření aktivity](how-to-create-an-activity.md) a [postup: Vytvořte pracovní postup](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="89eb9-105">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="89eb9-106">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="89eb9-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="89eb9-107">Vytvoření projektu hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-107">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="89eb9-108">Otevřete řešení z předchozího [postupu: Vytvoření tématu aktivity](how-to-create-an-activity.md) pomocí sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="89eb9-108">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="89eb9-109">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení **WF45GettingStartedTutorial** a vyberte **Přidat**, **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="89eb9-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="89eb9-110">Pokud se okno **Průzkumník řešení** nezobrazí, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="89eb9-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="89eb9-111">V **nainstalovaném** uzlu vyberte možnost **Visual C#** , **Workflow** (nebo **Visual Basic**, **pracovní postup**).</span><span class="sxs-lookup"><span data-stu-id="89eb9-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="89eb9-112">V závislosti na tom, který programovací jazyk je nakonfigurován jako primární jazyk v aplikaci Visual Studio, může být uzel **vizuálu C#**  nebo **Visual Basic** pod uzlem **ostatní jazyky** v **nainstalovaném** uzlu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="89eb9-113">V rozevíracím seznamu .NET Framework verze se ujistěte, že je vybraná možnost **.NET Framework 4,5** .</span><span class="sxs-lookup"><span data-stu-id="89eb9-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="89eb9-114">V seznamu **pracovních postupů** vyberte **Konzolová aplikace pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="89eb9-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="89eb9-115">Do `NumberGuessWorkflowHost` pole **název** zadejte a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="89eb9-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="89eb9-116">Tím se vytvoří aplikace pracovního postupu Starter se základní podporou hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="89eb9-117">Tento základní kód pro hostování se upraví a použije ke spuštění aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="89eb9-118">Klikněte pravým tlačítkem na nově přidaný projekt **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="89eb9-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="89eb9-119">V seznamu **Přidat odkaz** vyberte **řešení** , zaškrtněte políčko vedle **NumberGuessWorkflowActivities**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="89eb9-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="89eb9-120">V **Průzkumník řešení** klikněte pravým tlačítkem na **Workflow1. XAML** a vyberte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="89eb9-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="89eb9-121">Potvrďte kliknutím na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="89eb9-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="89eb9-122">Úprava kódu hostování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-122">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="89eb9-123">Poklikejte na **program.cs** nebo **Module1. vb** v **Průzkumník řešení** pro zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    >  <span data-ttu-id="89eb9-124">Pokud se okno **Průzkumník řešení** nezobrazí, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="89eb9-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="89eb9-125">Vzhledem k tomu, že tento projekt byl vytvořen pomocí šablony **konzolové aplikace pracovního postupu** , **program.cs** nebo **Module1. vb** obsahuje následující základní kód pro hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

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

     <span data-ttu-id="89eb9-126">Tento generovaný kód pro hostování <xref:System.Activities.WorkflowInvoker>používá.</span><span class="sxs-lookup"><span data-stu-id="89eb9-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="89eb9-127"><xref:System.Activities.WorkflowInvoker>poskytuje jednoduchý způsob, jak vyvolat pracovní postup, jako by šlo o volání metody a dá se použít jenom pro pracovní postupy, které nepoužívají trvalost.</span><span class="sxs-lookup"><span data-stu-id="89eb9-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="89eb9-128"><xref:System.Activities.WorkflowApplication>poskytuje bohatší model pro spouštění pracovních postupů, které obsahují oznámení o událostech životního cyklu, řízení spouštění, opětovném obnovení záložek a persistenci.</span><span class="sxs-lookup"><span data-stu-id="89eb9-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="89eb9-129">V tomto příkladu se používají <xref:System.Activities.WorkflowApplication> záložky a slouží k hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="89eb9-130">Přidejte `using` následující příkaz nebo **importy** na začátek **program.cs** nebo **Module1. vb** pod existující příkazy **using** nebo Imports .</span><span class="sxs-lookup"><span data-stu-id="89eb9-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="89eb9-131">Nahraďte řádky kódu, které jsou <xref:System.Activities.WorkflowInvoker> používány, pomocí následujícího <xref:System.Activities.WorkflowApplication> základního hostujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="89eb9-132">Tento ukázkový hostující kód znázorňuje základní kroky pro hostování a vyvolání pracovního postupu, ale ještě neobsahuje funkce pro úspěšné spuštění pracovního postupu z tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="89eb9-133">V následujících krocích se tento základní kód upraví a přidají se další funkce, dokud se aplikace nedokončí.</span><span class="sxs-lookup"><span data-stu-id="89eb9-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="89eb9-134">Nahraďte `Workflow1` je v těchto příkladech `SequentialNumberGuessWorkflow`pomocí `FlowchartNumberGuessWorkflow`, `StateMachineNumberGuessWorkflow`nebo v závislosti na tom, který pracovní postup jste dokončili v předchozím [postupu: Vytvořte krok pracovního](how-to-create-a-workflow.md) postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="89eb9-135">Pokud se nenahradíte `Workflow1` , zobrazí se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="89eb9-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="89eb9-136">Tento kód vytvoří <xref:System.Activities.WorkflowApplication>přihlášení k odběru tří událostí životního cyklu pracovního postupu, spustí pracovní postup s <xref:System.Activities.WorkflowApplication.Run%2A>voláním a potom počká, až se pracovní postup dokončí.</span><span class="sxs-lookup"><span data-stu-id="89eb9-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="89eb9-137">Po dokončení <xref:System.Threading.AutoResetEvent> pracovního postupu se nastaví a hostitelská aplikace se dokončí.</span><span class="sxs-lookup"><span data-stu-id="89eb9-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="89eb9-138">Nastavení vstupních argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-138">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="89eb9-139">Přidejte následující příkaz na začátek **program.cs** nebo **Module1. vb** pod existující `using` příkazy nebo `Imports` .</span><span class="sxs-lookup"><span data-stu-id="89eb9-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="89eb9-140">Nahraďte řádek kódu, který vytvoří nový <xref:System.Activities.WorkflowApplication> , pomocí následujícího kódu, který vytvoří a předá do pracovního postupu slovník parametrů při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="89eb9-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="89eb9-141">Nahraďte `Workflow1` je v těchto příkladech `SequentialNumberGuessWorkflow`pomocí `FlowchartNumberGuessWorkflow`, `StateMachineNumberGuessWorkflow`nebo v závislosti na tom, který pracovní postup jste dokončili v předchozím [postupu: Vytvořte krok pracovního](how-to-create-a-workflow.md) postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="89eb9-142">Pokud se nenahradíte `Workflow1` , zobrazí se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="89eb9-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="89eb9-143">Tento slovník obsahuje jeden element s klíčem `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="89eb9-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="89eb9-144">Klíče ve vstupním slovníku odpovídají vstupním argumentům pro kořenovou aktivitu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="89eb9-145">`MaxNumber`používá pracovní postup k určení horní meze pro náhodně generované číslo.</span><span class="sxs-lookup"><span data-stu-id="89eb9-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="89eb9-146">Načtení výstupních argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-146">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="89eb9-147"><xref:System.Activities.WorkflowApplication.Completed%2A> Upravte obslužnou rutinu tak, aby načetla a zobrazila počet zapínání pomocí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="89eb9-148">Obnovení záložky</span><span class="sxs-lookup"><span data-stu-id="89eb9-148">To resume a bookmark</span></span>

1. <span data-ttu-id="89eb9-149">Do vrcholu `Main` metody přidejte následující kód hned po existující <xref:System.Threading.AutoResetEvent> deklaraci.</span><span class="sxs-lookup"><span data-stu-id="89eb9-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="89eb9-150">Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužnou rutinu hned pod stávající tři obslužné rutiny životního cyklu `Main`pracovního postupu v.</span><span class="sxs-lookup"><span data-stu-id="89eb9-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="89eb9-151">Pokaždé, když se pracovní postup nečinný čeká na další odhad, je tato obslužná rutina volána a `idleAction` <xref:System.Threading.AutoResetEvent> je nastavena.</span><span class="sxs-lookup"><span data-stu-id="89eb9-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="89eb9-152">Kód v následujícím kroku používá `idleEvent` a `syncEvent` k určení, zda pracovní postup čeká na další odhad nebo je dokončen.</span><span class="sxs-lookup"><span data-stu-id="89eb9-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="89eb9-153">V tomto příkladu hostitelská aplikace používá události automatického resetu v <xref:System.Activities.WorkflowApplication.Completed%2A> obslužných rutinách a <xref:System.Activities.WorkflowApplication.Idle%2A> k synchronizaci hostitelské aplikace s průběhem pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="89eb9-154">Není nutné a blokovat čekání pracovního postupu na nečinnost před obnovením záložku, ale v tomto příkladu jsou požadované události synchronizace, tak hostitele pozná, zda dokončení pracovního postupu nebo určuje, zda je čekání na další vstupu uživatele s použitím <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="89eb9-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="89eb9-155">Další informace najdete v tématu [záložky](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="89eb9-155">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="89eb9-156">Odeberte volání `WaitOne`a nahraďte ho kódem pro shromáždění vstupu od uživatele a pokračování v <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="89eb9-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="89eb9-157">Odeberte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="89eb9-158">Nahraďte následujícím příkladem.</span><span class="sxs-lookup"><span data-stu-id="89eb9-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="89eb9-159">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="89eb9-159">To build and run the application</span></span>

1. <span data-ttu-id="89eb9-160">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="89eb9-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="89eb9-161">Stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89eb9-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="89eb9-162">Zkuste číslo uhodnout v co nejkratší míře.</span><span class="sxs-lookup"><span data-stu-id="89eb9-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="89eb9-163">Chcete-li aplikaci vyzkoušet s jedním z dalších stylů pracovního postupu, nahraďte `Workflow1` v kódu, který <xref:System.Activities.WorkflowApplication> vytváří s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`nebo `StateMachineNumberGuessWorkflow`, podle toho, který styl pracovního postupu si přejete.</span><span class="sxs-lookup"><span data-stu-id="89eb9-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="89eb9-164">Pokyny, jak přidat trvalost do aplikace pracovního postupu, najdete v dalším tématu [postup: Vytvořte a spusťte dlouhodobě běžící pracovní](how-to-create-and-run-a-long-running-workflow.md)postup.</span><span class="sxs-lookup"><span data-stu-id="89eb9-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="89eb9-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="89eb9-165">Example</span></span>
 <span data-ttu-id="89eb9-166">Následující příklad je úplný výpis kódu pro `Main` metodu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="89eb9-167">Nahraďte `Workflow1` je v těchto příkladech `SequentialNumberGuessWorkflow`pomocí `FlowchartNumberGuessWorkflow`, `StateMachineNumberGuessWorkflow`nebo v závislosti na tom, který pracovní postup jste dokončili v předchozím [postupu: Vytvořte krok pracovního](how-to-create-a-workflow.md) postupu.</span><span class="sxs-lookup"><span data-stu-id="89eb9-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="89eb9-168">Pokud se nenahradíte `Workflow1` , zobrazí se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.</span><span class="sxs-lookup"><span data-stu-id="89eb9-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="89eb9-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89eb9-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="89eb9-170">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="89eb9-170">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="89eb9-171">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="89eb9-171">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="89eb9-172">Postupy: Vytvořit pracovní postup</span><span class="sxs-lookup"><span data-stu-id="89eb9-172">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="89eb9-173">Postupy: Vytvoření a spuštění dlouhého běžícího pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-173">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="89eb9-174">Čekání na zadání v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="89eb9-174">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="89eb9-175">Hostování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="89eb9-175">Hosting Workflows</span></span>](hosting-workflows.md)
