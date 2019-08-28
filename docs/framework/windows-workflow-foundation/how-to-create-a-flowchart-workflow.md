---
title: 'Postupy: Vytvoření pracovního postupu vývojového diagramu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 3afac76fc977f992e780d2ebe302c1ed94568835
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044404"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="bf85d-102">Postupy: Vytvoření pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="bf85d-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="bf85d-103">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="bf85d-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="bf85d-104">V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, <xref:System.Activities.Statements.Flowchart> jako je aktivita, a vlastní aktivity z předchozího [postupu: Vytvoření tématu aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="bf85d-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="bf85d-105">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="bf85d-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf85d-106">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="bf85d-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="bf85d-107">Chcete-li dokončit toto téma, je nutné [nejprve provést následující kroky: Vytvoří aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="bf85d-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf85d-108">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bf85d-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="bf85d-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf85d-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="bf85d-110">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="bf85d-111">V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="bf85d-112">V seznamu **pracovních postupů** vyberte **aktivita** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="bf85d-113">Do `FlowchartNumberGuessWorkflow` pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="bf85d-114">Přetáhněte aktivitu **vývojového diagramu** z oddílu **vývojového diagramu** na **panel nástrojů** a přetáhněte ji na popisek **aktivity** na návrhovou plochu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bf85d-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="bf85d-115">Postup vytvoření proměnných a argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf85d-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="bf85d-116">Dvojím kliknutím na **FlowchartNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.</span><span class="sxs-lookup"><span data-stu-id="bf85d-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="bf85d-117">Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="bf85d-118">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="bf85d-119">Do `MaxNumber` pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="bf85d-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="bf85d-120">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="bf85d-121">`MaxNumber` Do pole název, které se nachází pod nově přidaným argumentem, vyberte out v rozevíracím seznamu směr, v rozevíracím seznamu typ argumentu vyberte Int32 a potom stiskněte klávesu ENTER. `Turns`</span><span class="sxs-lookup"><span data-stu-id="bf85d-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="bf85d-122">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="bf85d-123">Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="bf85d-124">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="bf85d-125">Pokud se nezobrazí žádné pole **vytvořit proměnnou** , klikněte <xref:System.Activities.Statements.Flowchart> na aktivitu na ploše návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="bf85d-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="bf85d-126">Do `Guess` pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="bf85d-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="bf85d-127">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="bf85d-128">Do `Target` pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="bf85d-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="bf85d-129">Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="bf85d-130">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf85d-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="bf85d-131">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a umístěte ji na **spouštěcí** uzel, který je v horní části vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="bf85d-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="bf85d-132">Pokud je aktivita **přiřazení** nad počátečním uzlem, zobrazí se kolem počátečního uzlu tři trojúhelníky.</span><span class="sxs-lookup"><span data-stu-id="bf85d-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="bf85d-133">Přetáhněte aktivitu **přiřazení** na trojúhelník, který je přímo pod počátečním uzlem.</span><span class="sxs-lookup"><span data-stu-id="bf85d-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="bf85d-134">Tato akce spojí dvě položky dohromady a určí aktivitu **přiřazení** jako první aktivitu ve vývojovém diagramu.</span><span class="sxs-lookup"><span data-stu-id="bf85d-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf85d-135">Aktivity můžete v pracovním postupu uvést také jako počáteční aktivitu, a to tak, že je ručně propojíte aktivitu s počátečním uzlem.</span><span class="sxs-lookup"><span data-stu-id="bf85d-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="bf85d-136">Provedete to tak, že najedete myší na **spouštěcí** uzel, kliknete na jeden z obdélníků, který se zobrazí, když je ukazatel myši nad **spouštěcím** uzlem, a přetáhnete spojovací čáru dolů na požadovanou aktivitu a umístíte ji na jeden z obdélníků, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="bf85d-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="bf85d-137">Aktivitu můžete také označit jako počáteční aktivitu tak, že na ni kliknete pravým tlačítkem myši a zvolíte **nastavit jako spouštěcí uzel**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="bf85d-138">Zadejte `Target` do pole **do** a následující výraz do pole **Zadejte C# výraz** nebo **Zadejte výraz VB** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="bf85d-139">Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="bf85d-140">Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** na **panelu nástrojů**, přetáhněte ji pod aktivitu **přiřazení** z předchozího kroku a připojte aktivitu **výzvy** k aktivitě **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="bf85d-141">Existují tři způsoby, jak propojit dvě aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf85d-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="bf85d-142">Prvním způsobem je připojení při vyřazení aktivity s **výzvou** v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="bf85d-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="bf85d-143">Při přetahování aktivity **výzvy** k pracovnímu postupu umístěte ukazatel myši na aktivitu **přiřadit** a přetáhněte ji na jeden ze čtyř trojúhelníků, který se zobrazí, když je aktivita **výzvy** nad aktivitou **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="bf85d-144">Druhým způsobem je vyřadit aktivitu **výzvy** do pracovního postupu v požadovaném umístění.</span><span class="sxs-lookup"><span data-stu-id="bf85d-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="bf85d-145">Pak najeďte myší na aktivitu **přiřazení** a přetáhněte jeden z obdélníků, který se zobrazí v poli pro činnost **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="bf85d-146">Přetáhněte myš, aby se propojovací čára z aktivity **přiřazení** připojovala k jednomu z obdélníků aktivity **výzvy** , a pak uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="bf85d-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="bf85d-147">Třetí způsob se velmi podobá prvnímu, s tím rozdílem, že místo přetažení aktivity **výzvy** ze **sady nástrojů**ho přetáhnete z jeho umístění na návrhové ploše pracovního postupu, najeďte myší na aktivitu **přiřazení** a umístíte ho na jednu z těchto možností. zobrazené trojúhelníky.</span><span class="sxs-lookup"><span data-stu-id="bf85d-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="bf85d-148">V **okně Vlastnosti** aktivity **výzvy** zadejte do pole hodnota vlastnosti `"EnterGuess"` **Bookmark** text včetně uvozovek.</span><span class="sxs-lookup"><span data-stu-id="bf85d-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="bf85d-149">Do `Guess` pole hodnota vlastnosti **výsledek** zadejte a do pole vlastnost **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="bf85d-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="bf85d-150">Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="bf85d-151">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a připojte ji pomocí jedné z metod popsaných v předchozím kroku, aby se zobrazila pod aktivitou **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="bf85d-152">`Turns + 1` **C#** Do pole do zadejte a do pole zadejte výraz nebo zadejte výraz VB. `Turns`</span><span class="sxs-lookup"><span data-stu-id="bf85d-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="bf85d-153">Přetáhněte **použitím objektu FlowDecision** z části **vývojového diagramu** v **sadě nástrojů** a připojte ji pod aktivitu **přiřazení** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="bf85d-154">V **okně Vlastnosti**zadejte následující výraz do pole hodnota vlastnosti **podmínky** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="bf85d-155">Přetáhněte další aktivitu **použitím objektu FlowDecision** ze **sady nástrojů** a přetáhněte ji pod první.</span><span class="sxs-lookup"><span data-stu-id="bf85d-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="bf85d-156">Připojte dvě aktivity přetažením z obdélníku, který je označen jako **false** u horní aktivity **použitím objektu FlowDecision** na obdélník v horní části druhé aktivity **použitím objektu FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="bf85d-157">Pokud nevidíte v **použitím objektu FlowDecision**popisky **true** a **false** , najeďte myší na **použitím objektu FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="bf85d-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="bf85d-158">Klikněte na druhou aktivitu **použitím objektu FlowDecision** a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="bf85d-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="bf85d-159">V **okně Vlastnosti**zadejte následující výraz do pole hodnota vlastnosti **podmínky** .</span><span class="sxs-lookup"><span data-stu-id="bf85d-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="bf85d-160">Přetáhněte dvě aktivity **WriteLine** z části **primitiva** v **sadě nástrojů** a přetáhněte je tak, aby byly vedle sebe pod dvěma **použitím objektu FlowDecision** aktivitami.</span><span class="sxs-lookup"><span data-stu-id="bf85d-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="bf85d-161">Připojte **skutečnou** akci nejnižší aktivity **použitím objektu FlowDecision** k aktivitě **WriteLine** a nejvíce vlevo a akci **false** u aktivity napravo napravo.</span><span class="sxs-lookup"><span data-stu-id="bf85d-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="bf85d-162">Klikněte na aktivitu **vywriteline** úplně vlevo a vyberte ji a do pole hodnota vlastnosti **text** v **okně Vlastnosti**zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="bf85d-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="bf85d-163">Připojte řádek **WriteLine** k levé straně aktivity **výzvy** , která je nad ním.</span><span class="sxs-lookup"><span data-stu-id="bf85d-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="bf85d-164">Klikněte na aktivitu napravo od jejího výběru a vyberte ji a do pole hodnota vlastnosti **text** v **okně Vlastnosti**zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="bf85d-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="bf85d-165">Připojte aktivitu **WriteLine** k pravé straně aktivity s **výzvou** nad ní.</span><span class="sxs-lookup"><span data-stu-id="bf85d-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="bf85d-166">Následující příklad znázorňuje dokončený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="bf85d-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Diagram znázorňující dokončený vývojový diagram programovací model Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="bf85d-168">Postup sestavení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf85d-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="bf85d-169">Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="bf85d-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="bf85d-170">Pokyny ke spuštění pracovního postupu najdete v dalším tématu [postup: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="bf85d-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="bf85d-171">Pokud jste již dokončili [postupy: Spusťte krok pracovního](how-to-run-a-workflow.md) postupu s jiným stylem pracovního postupu a přejete si ho spustit pomocí pracovního postupu vývojového diagramu z tohoto kroku, přeskočte dopředu k [ [sestavení a spusťte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) v tématu Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="bf85d-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf85d-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf85d-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="bf85d-173">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="bf85d-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="bf85d-174">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bf85d-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="bf85d-175">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="bf85d-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="bf85d-176">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="bf85d-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="bf85d-177">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf85d-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
