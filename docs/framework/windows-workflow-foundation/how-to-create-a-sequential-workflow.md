---
title: 'Postupy: Vytvoření sekvenčního pracovního postupu'
description: Tento článek vytvoří pracovní postup, který používá předdefinované aktivity, jako je například aktivita sekvence a vlastní aktivity.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: f80ac471fdcc425504b11b5fb17effa888aa9590
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419691"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="aafa2-103">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="aafa2-103">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="aafa2-104">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="aafa2-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="aafa2-105">V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.Sequence> aktivita, a vlastní aktivity z předchozího tématu [Postupy: vytvoření aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="aafa2-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="aafa2-106">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="aafa2-106">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="aafa2-107">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="aafa2-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="aafa2-108">Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="aafa2-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="aafa2-109">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="aafa2-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="aafa2-110">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="aafa2-110">To create the workflow</span></span>

1. <span data-ttu-id="aafa2-111">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="aafa2-112">V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="aafa2-113">V seznamu **pracovních postupů** vyberte **aktivita** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-113">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="aafa2-114">`SequentialNumberGuessWorkflow`Do pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-114">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="aafa2-115">Přetáhněte aktivitu **sekvence** z části **tok řízení** v **sadě nástrojů** a přetáhněte ji na popisek sem přetáhněte **aktivitu** na návrhové ploše pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="aafa2-115">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="aafa2-116">Postup vytvoření proměnných a argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="aafa2-116">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="aafa2-117">Dvojím kliknutím na **SequentialNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.</span><span class="sxs-lookup"><span data-stu-id="aafa2-117">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="aafa2-118">Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="aafa2-119">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-119">Click **Create Argument**.</span></span>

4. <span data-ttu-id="aafa2-120">`MaxNumber`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="aafa2-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="aafa2-121">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-121">Click **Create Argument**.</span></span>

6. <span data-ttu-id="aafa2-122">`Turns`Do pole **název** , které se nachází pod nově přidaným `MaxNumber` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="aafa2-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="aafa2-123">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="aafa2-124">Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="aafa2-125">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-125">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="aafa2-126">Pokud se nezobrazí žádné pole **vytvořit proměnnou** , vyberte ji kliknutím na aktivitu **sekvence** na ploše návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="aafa2-126">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="aafa2-127">`Guess`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="aafa2-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="aafa2-128">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="aafa2-128">Click **Create Variable**.</span></span>

12. <span data-ttu-id="aafa2-129">`Target`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="aafa2-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="aafa2-130">Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="aafa2-131">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="aafa2-131">To add the workflow activities</span></span>

1. <span data-ttu-id="aafa2-132">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji na aktivitu **sekvence** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-132">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="aafa2-133">Do `Target` pole **do** vložte a následující výraz zadejte do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-133">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="aafa2-134">Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-134">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="aafa2-135">Přetáhněte aktivitu **DoWhile** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do pracovního postupu tak, aby byla pod aktivitou **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-135">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="aafa2-136">Do pole hodnota vlastnosti **podmínky** aktivity **DoWhile** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="aafa2-136">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="aafa2-137"><xref:System.Activities.Statements.DoWhile>Aktivita spustí své podřízené aktivity a pak vyhodnotí její <xref:System.Activities.Statements.DoWhile.Condition%2A> .</span><span class="sxs-lookup"><span data-stu-id="aafa2-137">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="aafa2-138">Pokud se <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí jako `True` , pak se aktivity v <xref:System.Activities.Statements.DoWhile> znovu spustí.</span><span class="sxs-lookup"><span data-stu-id="aafa2-138">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="aafa2-139">V tomto příkladu je vyhodnocen odhad uživatele a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud není odhad správný.</span><span class="sxs-lookup"><span data-stu-id="aafa2-139">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="aafa2-140">Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** sady **nástrojů** a přetáhněte ji do aktivity **DoWhile** z předchozího kroku.</span><span class="sxs-lookup"><span data-stu-id="aafa2-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="aafa2-141">V **okně Vlastnosti**zadejte `"EnterGuess"` včetně uvozovek do pole hodnota vlastnosti **Bookmark** pro aktivitu **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-141">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="aafa2-142">`Guess`Do pole hodnota vlastnosti **výsledek** zadejte a do pole vlastnost **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="aafa2-142">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="aafa2-143">Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-143">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="aafa2-144">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do aktivity **DoWhile** , aby se protáhla jako aktivita **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-144">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aafa2-145">Když vyřadíte aktivitu **přiřazení** , Všimněte si, jak Návrhář pracovního postupu automaticky přidá aktivitu **sekvence** , která bude obsahovat aktivitu **výzvy** i nově přidanou aktivitu **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-145">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="aafa2-146">Do `Turns` pole **do** zadejte do a vložte `Turns + 1` **výraz jazyka C#** nebo zadejte pole **výrazu VB** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-146">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="aafa2-147">Přetáhněte aktivitu **if** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do aktivity **sekvence** tak, aby se doplnila nově přidaným aktivitou **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-147">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="aafa2-148">Do pole hodnota vlastnosti **Podmínka** pro aktivitu **if** aktivity zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="aafa2-148">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="aafa2-149">Přetáhněte jinou položku **if** Activity z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do části **then** první aktivity **if** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-149">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="aafa2-150">Do pole nově **přidaná hodnota** vlastnosti **Condition podmínky** aktivity zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="aafa2-150">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="aafa2-151">Přetáhněte dvě aktivity **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte je tak, aby jedna byla v oddílu **potom** nově přidané aktivity **if** a jedna je v části **Else** .</span><span class="sxs-lookup"><span data-stu-id="aafa2-151">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="aafa2-152">Kliknutím na aktivitu **WriteLine** v části **pak** ji vyberete a do pole hodnota vlastnosti **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="aafa2-152">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="aafa2-153">Kliknutím na aktivitu **WriteLine** v části **Else** ji vyberte a do pole hodnota vlastnosti **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="aafa2-153">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="aafa2-154">Následující příklad znázorňuje dokončený pracovní postup:</span><span class="sxs-lookup"><span data-stu-id="aafa2-154">The following example illustrates the completed workflow:</span></span>

     ![Snímek obrazovky zobrazující dokončený sekvenční pracovní postup](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="aafa2-156">Postup sestavení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="aafa2-156">To build the workflow</span></span>

1. <span data-ttu-id="aafa2-157">Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="aafa2-157">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="aafa2-158">Pokyny ke spuštění pracovního postupu najdete v dalším tématu [Postup: spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="aafa2-158">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="aafa2-159">Pokud jste již dokončili [Postup: spuštění kroku pracovního postupu](how-to-run-a-workflow.md) s jiným stylem pracovního postupu a chcete jej spustit pomocí sekvenčního pracovního postupu z tohoto kroku, přeskočte dopředu na [sestavení a spusťte aplikaci v](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="aafa2-159">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aafa2-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="aafa2-160">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="aafa2-161">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="aafa2-161">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="aafa2-162">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="aafa2-162">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="aafa2-163">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="aafa2-163">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="aafa2-164">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="aafa2-164">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="aafa2-165">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="aafa2-165">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
