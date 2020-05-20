---
title: 'Postupy: Vytvoření pracovního postupu vývojového diagramu'
description: Tento článek popisuje vytvoření pracovního postupu, který používá předdefinované aktivity a vlastní aktivity z předchozího článku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 6b3fa423200f5c5cfece60f07372ce9678fc0072
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419704"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="e828a-103">Postupy: Vytvoření pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="e828a-103">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="e828a-104">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="e828a-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="e828a-105">V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.Flowchart> aktivita, a vlastní aktivity z předchozího tématu [Postupy: vytvoření aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="e828a-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="e828a-106">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="e828a-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e828a-107">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="e828a-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="e828a-108">Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="e828a-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e828a-109">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e828a-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="e828a-110">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e828a-110">To create the workflow</span></span>  
  
1. <span data-ttu-id="e828a-111">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="e828a-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="e828a-112">V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="e828a-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="e828a-113">V seznamu **pracovních postupů** vyberte **aktivita** .</span><span class="sxs-lookup"><span data-stu-id="e828a-113">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="e828a-114">`FlowchartNumberGuessWorkflow`Do pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="e828a-114">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="e828a-115">Přetáhněte aktivitu **vývojového diagramu** z oddílu **vývojového diagramu** na **panel nástrojů** a přetáhněte ji na popisek **aktivity** na návrhovou plochu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e828a-115">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="e828a-116">Postup vytvoření proměnných a argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e828a-116">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="e828a-117">Dvojím kliknutím na **FlowchartNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.</span><span class="sxs-lookup"><span data-stu-id="e828a-117">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="e828a-118">Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="e828a-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="e828a-119">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="e828a-119">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="e828a-120">`MaxNumber`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="e828a-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="e828a-121">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="e828a-121">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="e828a-122">`Turns`Do pole **název** , které se nachází pod nově přidaným `MaxNumber` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="e828a-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="e828a-123">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="e828a-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="e828a-124">Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="e828a-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="e828a-125">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="e828a-125">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="e828a-126">Pokud se nezobrazí žádné pole **vytvořit proměnnou** , klikněte na <xref:System.Activities.Statements.Flowchart> aktivitu na ploše návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="e828a-126">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="e828a-127">`Guess`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e828a-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="e828a-128">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="e828a-128">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="e828a-129">`Target`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e828a-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="e828a-130">Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="e828a-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="e828a-131">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e828a-131">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="e828a-132">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a umístěte ji na **spouštěcí** uzel, který je v horní části vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="e828a-132">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="e828a-133">Pokud je aktivita **přiřazení** nad **počátečním** uzlem, zobrazí se kolem **počátečního** uzlu tři trojúhelníky.</span><span class="sxs-lookup"><span data-stu-id="e828a-133">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="e828a-134">Přetáhněte aktivitu **přiřazení** na trojúhelník, který je přímo pod **počátečním** uzlem.</span><span class="sxs-lookup"><span data-stu-id="e828a-134">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="e828a-135">Tato akce spojí dvě položky dohromady a určí aktivitu **přiřazení** jako první aktivitu ve vývojovém diagramu.</span><span class="sxs-lookup"><span data-stu-id="e828a-135">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e828a-136">Aktivity můžete v pracovním postupu uvést také jako počáteční aktivitu, a to tak, že je ručně propojíte aktivitu s počátečním uzlem.</span><span class="sxs-lookup"><span data-stu-id="e828a-136">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="e828a-137">Provedete to tak, že najedete myší na **spouštěcí** uzel, kliknete na jeden z obdélníků, který se zobrazí, když je ukazatel myši nad **spouštěcím** uzlem, a přetáhnete spojovací čáru dolů na požadovanou aktivitu a umístíte ji na jeden z obdélníků, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="e828a-137">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="e828a-138">Aktivitu můžete také označit jako počáteční aktivitu tak, že na ni kliknete pravým tlačítkem myši a zvolíte **nastavit jako spouštěcí uzel**.</span><span class="sxs-lookup"><span data-stu-id="e828a-138">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="e828a-139">Do `Target` pole **do** vložte a následující výraz zadejte do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** .</span><span class="sxs-lookup"><span data-stu-id="e828a-139">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="e828a-140">Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="e828a-140">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="e828a-141">Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** na **panelu nástrojů**, přetáhněte ji pod aktivitu **přiřazení** z předchozího kroku a připojte aktivitu **výzvy** k aktivitě **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="e828a-141">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="e828a-142">Existují tři způsoby, jak propojit dvě aktivity.</span><span class="sxs-lookup"><span data-stu-id="e828a-142">There are three ways to connect the two activities.</span></span> <span data-ttu-id="e828a-143">Prvním způsobem je připojení při vyřazení aktivity s **výzvou** v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="e828a-143">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="e828a-144">Při přetahování aktivity **výzvy** k pracovnímu postupu umístěte ukazatel myši na aktivitu **přiřadit** a přetáhněte ji na jeden ze čtyř trojúhelníků, který se zobrazí, když je aktivita **výzvy** nad aktivitou **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="e828a-144">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="e828a-145">Druhým způsobem je vyřadit aktivitu **výzvy** do pracovního postupu v požadovaném umístění.</span><span class="sxs-lookup"><span data-stu-id="e828a-145">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="e828a-146">Pak najeďte myší na aktivitu **přiřazení** a přetáhněte jeden z obdélníků, který se zobrazí v poli pro činnost **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="e828a-146">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="e828a-147">Přetáhněte myš, aby se propojovací čára z aktivity **přiřazení** připojovala k jednomu z obdélníků aktivity **výzvy** , a pak uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="e828a-147">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="e828a-148">Třetí způsob se velmi podobá prvnímu, s tím rozdílem, že místo přetažení aktivity **výzvy** ze **sady nástrojů**ho přetáhnete z jeho umístění na návrhové ploše pracovního postupu, najeďte myší nad aktivitu **přiřadit** a umístěte ho na jeden ze zobrazených trojúhelníků.</span><span class="sxs-lookup"><span data-stu-id="e828a-148">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="e828a-149">V **okně Vlastnosti** aktivity **výzvy** zadejte `"EnterGuess"` do pole hodnota vlastnosti **Bookmark** text včetně uvozovek.</span><span class="sxs-lookup"><span data-stu-id="e828a-149">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="e828a-150">`Guess`Do pole hodnota vlastnosti **výsledek** zadejte a do pole vlastnost **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="e828a-150">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="e828a-151">Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="e828a-151">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="e828a-152">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a připojte ji pomocí jedné z metod popsaných v předchozím kroku, aby se **zobrazila** pod aktivitou výzvy.</span><span class="sxs-lookup"><span data-stu-id="e828a-152">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="e828a-153">Do `Turns` pole **do** zadejte do a vložte `Turns + 1` **výraz jazyka C#** nebo zadejte pole **výrazu VB** .</span><span class="sxs-lookup"><span data-stu-id="e828a-153">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="e828a-154">Přetáhněte **použitím objektu FlowDecision** z části **vývojového diagramu** v **sadě nástrojů** a připojte ji pod aktivitu **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="e828a-154">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="e828a-155">V **okně Vlastnosti**zadejte následující výraz do pole hodnota vlastnosti **podmínky** .</span><span class="sxs-lookup"><span data-stu-id="e828a-155">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="e828a-156">Přetáhněte další aktivitu **použitím objektu FlowDecision** ze **sady nástrojů** a přetáhněte ji pod první.</span><span class="sxs-lookup"><span data-stu-id="e828a-156">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="e828a-157">Připojte dvě aktivity přetažením z obdélníku, který je označen jako **false** u horní aktivity **použitím objektu FlowDecision** na obdélník v horní části druhé aktivity **použitím objektu FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="e828a-157">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="e828a-158">Pokud nevidíte v **použitím objektu FlowDecision**popisky **true** a **false** , najeďte myší na **použitím objektu FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="e828a-158">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="e828a-159">Klikněte na druhou aktivitu **použitím objektu FlowDecision** a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="e828a-159">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="e828a-160">V **okně Vlastnosti**zadejte následující výraz do pole hodnota vlastnosti **podmínky** .</span><span class="sxs-lookup"><span data-stu-id="e828a-160">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="e828a-161">Přetáhněte dvě aktivity **WriteLine** z části **primitiva** v **sadě nástrojů** a přetáhněte je tak, aby byly vedle sebe pod dvěma **použitím objektu FlowDecision** aktivitami.</span><span class="sxs-lookup"><span data-stu-id="e828a-161">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="e828a-162">Připojte **skutečnou** akci nejnižší aktivity **použitím objektu FlowDecision** k aktivitě **WriteLine** a nejvíce vlevo a akci **false** u aktivity napravo napravo. **WriteLine**</span><span class="sxs-lookup"><span data-stu-id="e828a-162">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="e828a-163">Klikněte na aktivitu **vywriteline** úplně vlevo a vyberte ji a do pole hodnota vlastnosti **text** v **okně Vlastnosti**zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="e828a-163">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="e828a-164">Připojte řádek **WriteLine** k levé straně aktivity **výzvy** , která je nad ním.</span><span class="sxs-lookup"><span data-stu-id="e828a-164">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="e828a-165">Klikněte **na aktivitu** napravo od jejího výběru a vyberte ji a do pole hodnota vlastnosti **text** v **okně Vlastnosti**zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="e828a-165">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="e828a-166">Připojte aktivitu **WriteLine** k pravé straně aktivity s **výzvou** nad ní.</span><span class="sxs-lookup"><span data-stu-id="e828a-166">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="e828a-167">Následující příklad znázorňuje dokončený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="e828a-167">The following example illustrates the completed workflow.</span></span>  
  
     ![Diagram znázorňující dokončený vývojový diagram programovací model Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="e828a-169">Postup sestavení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e828a-169">To build the workflow</span></span>  
  
1. <span data-ttu-id="e828a-170">Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="e828a-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="e828a-171">Pokyny ke spuštění pracovního postupu najdete v dalším tématu [Postup: spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e828a-171">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="e828a-172">Pokud jste již dokončili [Postup: spuštění kroku pracovního postupu](how-to-run-a-workflow.md) s jiným stylem pracovního postupu a chcete jej spustit pomocí pracovního postupu vývojového diagramu z tohoto kroku, přeskočte dopředu na [sestavení a spusťte aplikaci v](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e828a-172">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e828a-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="e828a-173">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="e828a-174">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="e828a-174">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="e828a-175">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e828a-175">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="e828a-176">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="e828a-176">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="e828a-177">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="e828a-177">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="e828a-178">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e828a-178">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
