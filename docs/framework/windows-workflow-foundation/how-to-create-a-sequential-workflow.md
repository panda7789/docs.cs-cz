---
title: "Postupy: Vytvoření sekvenčního pracovního postupu"
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
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3bf6d8b499903522ee09021bb9339ece6a5894eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="93935-102">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="93935-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="93935-103">Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="93935-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="93935-104">Kroky v tomto tématu procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.Sequence> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="93935-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="93935-105">Pracovní postup modelů číslo hádání hru.</span><span class="sxs-lookup"><span data-stu-id="93935-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93935-106">Každého tématu v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="93935-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="93935-107">K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="93935-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93935-108">Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="93935-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="93935-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="93935-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="93935-110">Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="93935-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="93935-111">V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="93935-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="93935-112">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="93935-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="93935-113">Typ `SequentialNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="93935-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="93935-114">Přetažení **pořadí** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** v popisek pracovní postup návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="93935-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="93935-115">Vytvoření proměnné pracovního postupu a argumenty</span><span class="sxs-lookup"><span data-stu-id="93935-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="93935-116">Klikněte dvakrát na **SequentialNumberGuessWorkflow.xaml** v **Průzkumníku řešení** zobrazíte pracovního postupu v návrháři, pokud již není zobrazen.</span><span class="sxs-lookup"><span data-stu-id="93935-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="93935-117">Klikněte na tlačítko **argumenty** na straně dolním Návrháře pracovního postupu pro zobrazení **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="93935-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="93935-118">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="93935-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="93935-119">Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.</span><span class="sxs-lookup"><span data-stu-id="93935-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="93935-120">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="93935-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="93935-121">Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte  **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="93935-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="93935-122">Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="93935-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="93935-123">Klikněte na tlačítko **proměnné** na straně dolním Návrháře pracovního postupu pro zobrazení **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="93935-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="93935-124">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="93935-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="93935-125">Pokud žádné **vytvoření proměnné** políčko se zobrazí, klikněte na tlačítko **pořadí** aktivity na plochu návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="93935-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="93935-126">Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="93935-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="93935-127">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="93935-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="93935-128">Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="93935-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="93935-129">Klikněte na tlačítko **proměnné** v levém dolním straně Návrhář aktivity zavřete **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="93935-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="93935-130">Chcete-li přidat aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="93935-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="93935-131">Přetažení **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="93935-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="93935-132">Typ `Target` do **k** pole a následující výraz do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.</span><span class="sxs-lookup"><span data-stu-id="93935-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="93935-133">Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="93935-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="93935-134">Přetáhněte **DoWhile** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej pro pracovní postup tak, aby se níže **přiřadit** aktivita.</span><span class="sxs-lookup"><span data-stu-id="93935-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3.  <span data-ttu-id="93935-135">Zadejte následující výraz do **DoWhile** aktivity **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93935-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="93935-136">A <xref:System.Activities.Statements.DoWhile> aktivita provede jeho podřízené aktivity a vyhodnocuje jeho <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="93935-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="93935-137">Pokud <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí jako `True`, pak aktivity v <xref:System.Activities.Statements.DoWhile> provést znovu.</span><span class="sxs-lookup"><span data-stu-id="93935-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="93935-138">V tomto příkladu je odhad uživatele vyhodnotit a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud odhad je správný.</span><span class="sxs-lookup"><span data-stu-id="93935-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4.  <span data-ttu-id="93935-139">Přetáhněte **výzva** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů** a umístěte jej do **DoWhile** aktivity v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="93935-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5.  <span data-ttu-id="93935-140">V **vlastnosti – okno**, typ `"EnterGuess"` včetně uvozovek do **NázevZáložky** hodnota vlastnosti pole pro **výzva** aktivity.</span><span class="sxs-lookup"><span data-stu-id="93935-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="93935-141">Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** pole vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93935-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="93935-142">Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="93935-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6.  <span data-ttu-id="93935-143">Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **DoWhile** aktivity, které se řídí **Výzva** aktivity.</span><span class="sxs-lookup"><span data-stu-id="93935-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93935-144">Když vyřadíte **přiřadit** aktivity, Všimněte si, jak automaticky přidá návrháře pracovních postupů **pořadí** aktivity tak, aby obsahovala i **výzva** aktivity a nově přidaný **Přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="93935-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7.  <span data-ttu-id="93935-145">Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.</span><span class="sxs-lookup"><span data-stu-id="93935-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8.  <span data-ttu-id="93935-146">Přetáhněte **Pokud** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **pořadí** aktivity, které se řídí Nově přidaná **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="93935-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="93935-147">Zadejte následující výraz do **Pokud** aktivity **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93935-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="93935-148">Přetáhněte další **Pokud** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **pak** část první **Pokud** aktivity.</span><span class="sxs-lookup"><span data-stu-id="93935-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="93935-149">Zadejte následující výraz do nově přidaný **Pokud** aktivity **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93935-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="93935-150">Přetáhněte dva **WriteLine** aktivity z **primitiv** části **sada nástrojů** a vyřadit je tak, aby jeden **pak** část nově přidaný **Pokud** aktivitu a jeden, je v **Else** části.</span><span class="sxs-lookup"><span data-stu-id="93935-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="93935-151">Klikněte na tlačítko **WriteLine** aktivity v **pak** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93935-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="93935-152">Klikněte na tlačítko **WriteLine** aktivity v **Else** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93935-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="93935-153">Následující příklad ilustruje dokončené pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93935-153">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="93935-154">![Dokončit sekvenční pracovní postup](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="93935-154">![Completed Sequential Workflow](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="93935-155">K vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="93935-155">To build the workflow</span></span>  
  
1.  <span data-ttu-id="93935-156">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="93935-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="93935-157">Pokyny o tom, jak spustit workflow, naleznete v tématu Další [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="93935-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="93935-158">Pokud jste již dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiný styl pracovního postupu a chcete spustit pomocí sekvenčního pracovního postupu z tohoto kroku, přeskočit na [sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)část [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="93935-158">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93935-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="93935-159">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="93935-160">Windows Workflow Foundation programování</span><span class="sxs-lookup"><span data-stu-id="93935-160">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="93935-161">Navrhování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="93935-161">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="93935-162">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="93935-162">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="93935-163">Postupy: vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="93935-163">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="93935-164">Postupy: spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="93935-164">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
