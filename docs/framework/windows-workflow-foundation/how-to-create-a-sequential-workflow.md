---
title: 'Postupy: Vytvoření sekvenčního pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 3991c16e00f1cbb4f8c1f2c8391f89ea51c1e6f2
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463797"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="6b98a-102">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6b98a-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="6b98a-103">Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="6b98a-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6b98a-104">Toto téma se provede vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.Sequence> aktivity a vlastní aktivity z předchozího [jak: Vytvořit aktivitu](how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="6b98a-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6b98a-105">Pracovní postup modely číslo rozluštění hru.</span><span class="sxs-lookup"><span data-stu-id="6b98a-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b98a-106">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="6b98a-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6b98a-107">K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="6b98a-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b98a-108">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6b98a-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-workflow"></a><span data-ttu-id="6b98a-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6b98a-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="6b98a-110">Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníka řešení** a vyberte **přidat**, **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="6b98a-111">V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="6b98a-112">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="6b98a-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="6b98a-113">Typ `SequentialNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="6b98a-114">Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek pracovní postup návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="6b98a-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="6b98a-115">Chcete-li vytvořit pracovní postup proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="6b98a-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="6b98a-116">Dvakrát klikněte na panel **SequentialNumberGuessWorkflow.xaml** v **Průzkumníka řešení** zobrazíte pracovního postupu v návrháři, pokud se už nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="6b98a-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="6b98a-117">Klikněte na tlačítko **argumenty** v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="6b98a-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="6b98a-118">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="6b98a-119">Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.</span><span class="sxs-lookup"><span data-stu-id="6b98a-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="6b98a-120">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="6b98a-121">Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte  **Datový typ Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="6b98a-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="6b98a-122">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="6b98a-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="6b98a-123">Klikněte na tlačítko **proměnné** v levém dolním rohu návrháře postupu provádění zobrazit **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="6b98a-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="6b98a-124">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="6b98a-125">Pokud ne **vytvořit proměnnou** pole se zobrazí, klikněte na tlačítko **pořadí** aktivity na plochu návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="6b98a-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="6b98a-126">Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="6b98a-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="6b98a-127">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="6b98a-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="6b98a-128">Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="6b98a-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="6b98a-129">Klikněte na tlačítko **proměnné** v levého dolního rohu návrháře aktivit, zavřete **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="6b98a-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="6b98a-130">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6b98a-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="6b98a-131">Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte ho do **pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b98a-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="6b98a-132">Typ `Target` do **k** pole a následující výraz, který **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="6b98a-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="6b98a-133">Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6b98a-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="6b98a-134">Přetáhněte **DoWhile** aktivita z **tok řízení** část **nástrojů** a umístěte ho na pracovní postup tak, aby byl pod **přiřadit** aktivita.</span><span class="sxs-lookup"><span data-stu-id="6b98a-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3.  <span data-ttu-id="6b98a-135">Zadejte následující výraz do **DoWhile** aktivity **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b98a-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="6b98a-136">A <xref:System.Activities.Statements.DoWhile> aktivita spustí jeho podřízených aktivit a vyhodnocuje jeho <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="6b98a-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="6b98a-137">Pokud <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí jako `True`, pak aktivity <xref:System.Activities.Statements.DoWhile> proveďte znovu.</span><span class="sxs-lookup"><span data-stu-id="6b98a-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="6b98a-138">V tomto příkladu je vyhodnocen odhad uživatele a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud je odhad správný.</span><span class="sxs-lookup"><span data-stu-id="6b98a-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4.  <span data-ttu-id="6b98a-139">Přetáhněte **výzvy** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **DoWhile** aktivity v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="6b98a-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5.  <span data-ttu-id="6b98a-140">V **okno vlastností**, typ `"EnterGuess"` včetně uvozovek do **BookmarkName** pole s hodnotou pro vlastnost **výzvy** aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b98a-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="6b98a-141">Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b98a-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="6b98a-142">Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6b98a-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6.  <span data-ttu-id="6b98a-143">Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte jej do **DoWhile** aktivitu tak, že následuje **Výzvy** aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b98a-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6b98a-144">Když přetáhnete **přiřadit** aktivita, Všimněte si, jak automaticky přidá návrháře postupu provádění **pořadí** aktivitu tak, aby obsahovala obě **výzvy** aktivity a nově přidané **Přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b98a-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7.  <span data-ttu-id="6b98a-145">Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="6b98a-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8.  <span data-ttu-id="6b98a-146">Přetáhněte **Pokud** aktivita z **tok řízení** část **nástrojů** a umístěte jej do **pořadí** aktivitu tak, že následuje nově přidané **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b98a-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="6b98a-147">Zadejte následující výraz do **Pokud** aktivity **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b98a-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="6b98a-148">Přetáhněte další **Pokud** aktivita z **tok řízení** část **nástrojů** a umístěte jej do **pak** část první **Pokud** aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b98a-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="6b98a-149">Zadejte následující výraz do nově přidaný **Pokud** aktivity **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b98a-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="6b98a-150">Přetáhněte dva **WriteLine** aktivity z **primitiv** část **nástrojů** a umístit je tak, že jeden je v **pak** část nově přidaný **Pokud** aktivity a jeden je v **Else** oddílu.</span><span class="sxs-lookup"><span data-stu-id="6b98a-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="6b98a-151">Klikněte na tlačítko **WriteLine** aktivity v **pak** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b98a-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="6b98a-152">Klikněte na tlačítko **WriteLine** aktivity v **Else** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b98a-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="6b98a-153">Následující příklad ukazuje dokončený pracovní postup:</span><span class="sxs-lookup"><span data-stu-id="6b98a-153">The following example illustrates the completed workflow:</span></span>  
  
     ![Snímek obrazovky zobrazující dokončené sekvenční pracovní postup.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a><span data-ttu-id="6b98a-155">K vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6b98a-155">To build the workflow</span></span>  
  
1.  <span data-ttu-id="6b98a-156">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="6b98a-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="6b98a-157">Návod, jak spustit workflow, najdete dalším tématu s názvem [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6b98a-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="6b98a-158">Pokud jste už dokončili [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md) krok s jiným stylem pracovního postupu a chcete ji spustit pomocí sekvenčního pracovního postupu v tomto kroku, přeskočte k části [sestavíte a spustíte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) část [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6b98a-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b98a-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b98a-159">See also</span></span>
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="6b98a-160">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6b98a-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="6b98a-161">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6b98a-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="6b98a-162">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="6b98a-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="6b98a-163">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="6b98a-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="6b98a-164">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6b98a-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
