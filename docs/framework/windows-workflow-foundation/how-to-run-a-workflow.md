---
title: 'Postupy: Spuštění pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 4a5836c60d5f0ea21b1373b2d9bbbb29e0b6cb9f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360022"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="081c6-102">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-102">How to: Run a Workflow</span></span>
<span data-ttu-id="081c6-103">Toto téma je pokračováním kurzu Windows Workflow Foundation Getting Started a popisuje, jak vytvořit hostitele pracovního postupu a spustit pracovní postup definovaný v předchozím [jak: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="081c6-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
>  <span data-ttu-id="081c6-104">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="081c6-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="081c6-105">K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) a [jak: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="081c6-105">To complete this topic you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) and [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="081c6-106">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="081c6-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="081c6-107">Chcete-li vytvořit projekt hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="081c6-108">Otevřete řešení od předchozího [jak: Vytvořit aktivitu](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu pomocí sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="081c6-108">Open the solution from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2.  <span data-ttu-id="081c6-109">Klikněte pravým tlačítkem myši **WF45GettingStartedTutorial** řešení v **Průzkumníka řešení** a vyberte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="081c6-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="081c6-110">Pokud **Průzkumníka řešení** okno nezobrazí, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="081c6-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3.  <span data-ttu-id="081c6-111">V **nainstalováno** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**).</span><span class="sxs-lookup"><span data-stu-id="081c6-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="081c6-112">V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalováno** uzlu.</span><span class="sxs-lookup"><span data-stu-id="081c6-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="081c6-113">Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="081c6-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="081c6-114">Vyberte **Konzolová aplikace pracovního postupu** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="081c6-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="081c6-115">Typ `NumberGuessWorkflowHost` do **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="081c6-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="081c6-116">Tím vytvoříte základní pracovní postup podpora hostování aplikace starter pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="081c6-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="081c6-117">Tento základní kód hostování je změnit a použít ke spuštění aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="081c6-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4.  <span data-ttu-id="081c6-118">Klikněte pravým tlačítkem na nově přidaných **NumberGuessWorkflowHost** projekt **Průzkumníka řešení** a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="081c6-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="081c6-119">Vyberte **řešení** z **přidat odkaz** seznam, zaškrtněte políčko vedle **NumberGuessWorkflowActivities**a potom klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="081c6-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5.  <span data-ttu-id="081c6-120">Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníka řešení** a zvolte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="081c6-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="081c6-121">Klikněte na tlačítko **OK** potvrďte.</span><span class="sxs-lookup"><span data-stu-id="081c6-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="081c6-122">Chcete-li změnit hostování kódu pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-122">To modify the workflow hosting code</span></span>

1.  <span data-ttu-id="081c6-123">Dvakrát klikněte na panel **Program.cs** nebo **Module1.vb** v **Průzkumníka řešení** zobrazíte kód této.</span><span class="sxs-lookup"><span data-stu-id="081c6-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    >  <span data-ttu-id="081c6-124">Pokud **Průzkumníka řešení** okno nezobrazí, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="081c6-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="081c6-125">Protože tento projekt byl vytvořen pomocí **Konzolová aplikace pracovního postupu** šablony, **Program.cs** nebo **Module1.vb** obsahuje následující základní pracovní postup hostování kód.</span><span class="sxs-lookup"><span data-stu-id="081c6-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

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

     <span data-ttu-id="081c6-126">Tato vygenerována hostování kód používá <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="081c6-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="081c6-127"><xref:System.Activities.WorkflowInvoker> poskytuje jednoduchý způsob pro volání pracovního postupu, jako kdyby byly volání metody a lze použít pouze pro pracovní postupy, které nepoužívají trvalosti.</span><span class="sxs-lookup"><span data-stu-id="081c6-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="081c6-128"><xref:System.Activities.WorkflowApplication> poskytuje širší model pro spouštění pracovních postupů, které obsahuje oznámení o události životního cyklu, řízení provádění, záložku obnovení a trvalost.</span><span class="sxs-lookup"><span data-stu-id="081c6-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="081c6-129">Tento příklad používá záložek a <xref:System.Activities.WorkflowApplication> slouží k hostování pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="081c6-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="081c6-130">Přidejte následující `using` nebo **importy** příkazu v horní části **Program.cs** nebo **Module1.vb** pod řádek **pomocí** nebo **importy** příkazy.</span><span class="sxs-lookup"><span data-stu-id="081c6-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="081c6-131">Nahraďte řádků kódu, které používají <xref:System.Activities.WorkflowInvoker> s následující basic <xref:System.Activities.WorkflowApplication> hostování kódu.</span><span class="sxs-lookup"><span data-stu-id="081c6-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="081c6-132">Tato ukázka hostování kód ukazuje základní kroky pro hostování a volání pracovního postupu, ale ještě neobsahuje funkce k úspěšnému spuštění pracovního postupu v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="081c6-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="081c6-133">V následujících krocích se upraví tento základní kód a další funkce se přidají, dokud se nedokončí aplikace.</span><span class="sxs-lookup"><span data-stu-id="081c6-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="081c6-134">Nahraďte prosím `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup můžete dokončit v předchozím [jak: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="081c6-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="081c6-135">Pokud jste nenahrazují `Workflow1` pak při akci a vytvářet nebo spouštět pracovní postup bude docházet k chybám sestavení.</span><span class="sxs-lookup"><span data-stu-id="081c6-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="081c6-136">Tento kód vytvoří <xref:System.Activities.WorkflowApplication>, přihlásí na tři události životního cyklu pracovního postupu, spustí pracovní postup voláním <xref:System.Activities.WorkflowApplication.Run%2A>a potom počká na dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="081c6-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="081c6-137">Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> a Hostitel aplikace dokončí.</span><span class="sxs-lookup"><span data-stu-id="081c6-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="081c6-138">Chcete-li nastavit vstupní argumenty pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-138">To set input arguments of a workflow</span></span>

1.  <span data-ttu-id="081c6-139">Přidejte následující příkaz v horní části **Program.cs** nebo **Module1.vb** pod řádek `using` nebo `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="081c6-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2.  <span data-ttu-id="081c6-140">Nahraďte řádek kódu, který vytvoří nový <xref:System.Activities.WorkflowApplication> následujícím kódem, které vytváří a předává slovník parametrů do pracovního postupu při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="081c6-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="081c6-141">Nahraďte prosím `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup můžete dokončit v předchozím [jak: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="081c6-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="081c6-142">Pokud jste nenahrazují `Workflow1` pak při akci a vytvářet nebo spouštět pracovní postup bude docházet k chybám sestavení.</span><span class="sxs-lookup"><span data-stu-id="081c6-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="081c6-143">Tento slovník obsahuje jeden element s klíčem `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="081c6-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="081c6-144">Klíče ve slovníku vstupní odpovídají vstupní argumenty kořenové aktivity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="081c6-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="081c6-145">`MaxNumber` tímto pracovním postupem se používá k určení horní mez pro náhodně generovaným číslem.</span><span class="sxs-lookup"><span data-stu-id="081c6-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="081c6-146">K načtení výstupu argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-146">To retrieve output arguments of a workflow</span></span>

1.  <span data-ttu-id="081c6-147">Upravit <xref:System.Activities.WorkflowApplication.Completed%2A> obslužná rutina se má načíst a zobrazit počet zapne používá pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="081c6-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="081c6-148">Chcete-li obnovit záložku</span><span class="sxs-lookup"><span data-stu-id="081c6-148">To resume a bookmark</span></span>

1.  <span data-ttu-id="081c6-149">Přidejte následující kód v horní části `Main` metoda bezprostředně po existující <xref:System.Threading.AutoResetEvent> deklarace.</span><span class="sxs-lookup"><span data-stu-id="081c6-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2.  <span data-ttu-id="081c6-150">Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužná rutina pod existující tři pracovní postup životním cyklu obslužných rutin v `Main`.</span><span class="sxs-lookup"><span data-stu-id="081c6-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="081c6-151">Pokaždé, když pracovního postupu změní nečinnosti čekání na další odhad Tato obslužná rutina se nazývá a `idleAction` <xref:System.Threading.AutoResetEvent> nastavena.</span><span class="sxs-lookup"><span data-stu-id="081c6-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="081c6-152">Tento kód v následujícím kroku použije `idleEvent` a `syncEvent` k určení, zda pracovní postup čeká další uhádnout nebo dokončení.</span><span class="sxs-lookup"><span data-stu-id="081c6-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="081c6-153">V tomto příkladu hostitelská aplikace používá automatické obnovení události v <xref:System.Activities.WorkflowApplication.Completed%2A> a <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny pro synchronizaci hostitelská aplikace se průběh pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="081c6-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="081c6-154">Není nutné a blokovat čekání pracovního postupu na nečinnost před obnovením záložku, ale v tomto příkladu jsou požadované události synchronizace, tak hostitele pozná, zda dokončení pracovního postupu nebo určuje, zda je čekání na další vstupu uživatele s použitím <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="081c6-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="081c6-155">Další informace najdete v tématu [záložky](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="081c6-155">For more information, see [Bookmarks](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>

3.  <span data-ttu-id="081c6-156">Odeberte volání `WaitOne`a nahraďte kód, shromažďovat vstup od uživatele a pokračovat <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="081c6-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="081c6-157">Odeberte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="081c6-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="081c6-158">V následujícím příkladu nahraďte ho.</span><span class="sxs-lookup"><span data-stu-id="081c6-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="081c6-159">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="081c6-159">To build and run the application</span></span>

1.  <span data-ttu-id="081c6-160">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="081c6-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2.  <span data-ttu-id="081c6-161">Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="081c6-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="081c6-162">Došlo k pokusu o uhodnutí číslo na oplátku co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="081c6-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="081c6-163">Pokud chcete vyzkoušet aplikace s jedním z jiné styly pracovního postupu, nahraďte `Workflow1` v kódu, který vytvoří <xref:System.Activities.WorkflowApplication> s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`, v závislosti na styl pracovního postupu, který očekáváte.</span><span class="sxs-lookup"><span data-stu-id="081c6-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="081c6-164">Pokyny ohledně toho, jak přidat do aplikace pracovního postupu, trvalosti najdete v dalším tématu s názvem [jak: Vytvoření a spuštění dlouhodobého spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="081c6-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="081c6-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="081c6-165">Example</span></span>
 <span data-ttu-id="081c6-166">V následujícím příkladu je kompletní kód pro výpis `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="081c6-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
>  <span data-ttu-id="081c6-167">Nahraďte prosím `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup můžete dokončit v předchozím [jak: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="081c6-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="081c6-168">Pokud jste nenahrazují `Workflow1` pak při akci a vytvářet nebo spouštět pracovní postup bude docházet k chybám sestavení.</span><span class="sxs-lookup"><span data-stu-id="081c6-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="081c6-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="081c6-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="081c6-170">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="081c6-170">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
- [<span data-ttu-id="081c6-171">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="081c6-171">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [<span data-ttu-id="081c6-172">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-172">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [<span data-ttu-id="081c6-173">Postupy: Vytvoření a spuštění dlouhodobého spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-173">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="081c6-174">Čekání na zadání v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="081c6-174">Waiting for Input in a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="081c6-175">Hostování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="081c6-175">Hosting Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)