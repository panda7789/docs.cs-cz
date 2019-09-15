---
title: 'Postupy: Vytvoření sekvenčního pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989693"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="6e84c-102">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e84c-102">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="6e84c-103">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="6e84c-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6e84c-104">V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, <xref:System.Activities.Statements.Sequence> jako je aktivita, a vlastní aktivity z předchozího [postupu: Vytvoření tématu aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="6e84c-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6e84c-105">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="6e84c-105">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="6e84c-106">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="6e84c-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6e84c-107">Chcete-li dokončit toto téma, je nutné [nejprve provést následující kroky: Vytvoří aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="6e84c-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6e84c-108">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6e84c-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="6e84c-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e84c-109">To create the workflow</span></span>

1. <span data-ttu-id="6e84c-110">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="6e84c-111">V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="6e84c-112">V seznamu **pracovních postupů** vyberte **aktivita** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-112">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="6e84c-113">Do `SequentialNumberGuessWorkflow` pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="6e84c-114">Přetáhněte aktivitu **sekvence** z části **tok řízení** v **sadě nástrojů** a přetáhněte ji na popisek sem přetáhněte **aktivitu** na návrhové ploše pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6e84c-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="6e84c-115">Postup vytvoření proměnných a argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e84c-115">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="6e84c-116">Dvojím kliknutím na **SequentialNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.</span><span class="sxs-lookup"><span data-stu-id="6e84c-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="6e84c-117">Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="6e84c-118">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-118">Click **Create Argument**.</span></span>

4. <span data-ttu-id="6e84c-119">Do `MaxNumber` pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="6e84c-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="6e84c-120">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-120">Click **Create Argument**.</span></span>

6. <span data-ttu-id="6e84c-121">`MaxNumber` Do pole název, které se nachází pod nově přidaným argumentem, vyberte out v rozevíracím seznamu směr, v rozevíracím seznamu typ argumentu vyberte Int32 a potom stiskněte klávesu ENTER. `Turns`</span><span class="sxs-lookup"><span data-stu-id="6e84c-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="6e84c-122">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="6e84c-123">Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="6e84c-124">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-124">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="6e84c-125">Pokud se nezobrazí žádné pole **vytvořit proměnnou** , vyberte ji kliknutím na aktivitu **sekvence** na ploše návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6e84c-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="6e84c-126">Do `Guess` pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6e84c-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="6e84c-127">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="6e84c-127">Click **Create Variable**.</span></span>

12. <span data-ttu-id="6e84c-128">Do `Target` pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6e84c-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="6e84c-129">Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="6e84c-130">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e84c-130">To add the workflow activities</span></span>

1. <span data-ttu-id="6e84c-131">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji na aktivitu **sekvence** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="6e84c-132">Zadejte `Target` do pole **do** a následující výraz do pole **Zadejte C# výraz** nebo **Zadejte výraz VB** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="6e84c-133">Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="6e84c-134">Přetáhněte aktivitu **DoWhile** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do pracovního postupu tak, aby byla pod aktivitou **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="6e84c-135">Do pole hodnota vlastnosti **podmínky** aktivity **DoWhile** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="6e84c-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="6e84c-136">Aktivita spustí své podřízené aktivity a pak vyhodnotí její <xref:System.Activities.Statements.DoWhile.Condition%2A>. <xref:System.Activities.Statements.DoWhile></span><span class="sxs-lookup"><span data-stu-id="6e84c-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="6e84c-137">Pokud se <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí `True`jako, <xref:System.Activities.Statements.DoWhile> pak se aktivity v znovu spustí.</span><span class="sxs-lookup"><span data-stu-id="6e84c-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="6e84c-138">V tomto příkladu je vyhodnocen odhad uživatele a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud není odhad správný.</span><span class="sxs-lookup"><span data-stu-id="6e84c-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="6e84c-139">Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** sady **nástrojů** a přetáhněte ji do aktivity **DoWhile** z předchozího kroku.</span><span class="sxs-lookup"><span data-stu-id="6e84c-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="6e84c-140">V **okně Vlastnosti**zadejte `"EnterGuess"` včetně uvozovek do pole hodnota vlastnosti **Bookmark** pro aktivitu **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="6e84c-141">Do `Guess` pole hodnota vlastnosti **výsledek** zadejte a do pole vlastnost **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="6e84c-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="6e84c-142">Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="6e84c-143">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do aktivity **DoWhile** , aby se protáhla jako aktivita **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e84c-144">Když vyřadíte aktivitu **přiřazení** , Všimněte si, jak Návrhář pracovního postupu automaticky přidá aktivitu **sekvence** , která bude obsahovat aktivitu **výzvy** i nově přidanou aktivitu **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="6e84c-145">`Turns + 1` **C#** Do pole do zadejte a do pole zadejte výraz nebo zadejte výraz VB. `Turns`</span><span class="sxs-lookup"><span data-stu-id="6e84c-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="6e84c-146">Přetáhněte aktivitu **if** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do aktivity **sekvence** tak, aby se doplnila nově přidaným aktivitou **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="6e84c-147">Do pole hodnota vlastnosti **Podmínka** pro aktivitu **if** aktivity zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="6e84c-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="6e84c-148">Přetáhněte jinou položku **if** Activity z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do části **then** první aktivity **if** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="6e84c-149">Do pole nově **přidaná hodnota** vlastnosti **Condition podmínky** aktivity zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="6e84c-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="6e84c-150">Přetáhněte dvě aktivity **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte je tak, aby jedna byla v oddílu **potom** nově přidané aktivity **if** a jedna je v části **Else** .</span><span class="sxs-lookup"><span data-stu-id="6e84c-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="6e84c-151">Kliknutím na aktivitu **WriteLine** v části **pak** ji vyberete a do pole hodnota vlastnosti **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="6e84c-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="6e84c-152">Kliknutím na aktivitu **WriteLine** v části **Else** ji vyberte a do pole hodnota vlastnosti **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="6e84c-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="6e84c-153">Následující příklad znázorňuje dokončený pracovní postup:</span><span class="sxs-lookup"><span data-stu-id="6e84c-153">The following example illustrates the completed workflow:</span></span>

     ![Snímek obrazovky zobrazující dokončený sekvenční pracovní postup](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="6e84c-155">Postup sestavení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e84c-155">To build the workflow</span></span>

1. <span data-ttu-id="6e84c-156">Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="6e84c-156">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="6e84c-157">Pokyny ke spuštění pracovního postupu najdete v dalším tématu [postup: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6e84c-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="6e84c-158">Pokud jste již dokončili [postupy: Spusťte krok pracovního](how-to-run-a-workflow.md) postupu s jiným stylem pracovního postupu a přejete si ho spustit pomocí sekvenčního pracovního postupu z tohoto kroku, přejděte k části [ [Vytvoření a spusťte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) v tématu Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6e84c-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e84c-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e84c-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="6e84c-160">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6e84c-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="6e84c-161">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6e84c-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="6e84c-162">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="6e84c-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="6e84c-163">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="6e84c-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="6e84c-164">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e84c-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
