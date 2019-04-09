---
title: 'Postupy: Vytvoření pracovního postupu vývojového diagramu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 1da81ae47fa9f74b6037b6fcec4dbac5350c4481
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080238"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="d528a-102">Postupy: Vytvoření pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="d528a-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="d528a-103">Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="d528a-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="d528a-104">Toto téma se provede vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.Flowchart> aktivity a vlastní aktivity z předchozího [jak: Vytvořit aktivitu](how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="d528a-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="d528a-105">Pracovní postup modely číslo rozluštění hru.</span><span class="sxs-lookup"><span data-stu-id="d528a-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d528a-106">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="d528a-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="d528a-107">K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="d528a-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d528a-108">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="d528a-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="d528a-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d528a-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="d528a-110">Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníka řešení** a vyberte **přidat**, **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d528a-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="d528a-111">V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="d528a-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="d528a-112">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="d528a-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="d528a-113">Typ `FlowchartNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="d528a-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="d528a-114">Přetáhněte **vývojový diagram** aktivita z **vývojový diagram** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek pracovní postup návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="d528a-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="d528a-115">Chcete-li vytvořit pracovní postup proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="d528a-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="d528a-116">Dvakrát klikněte na panel **FlowchartNumberGuessWorkflow.xaml** v **Průzkumníka řešení** zobrazíte pracovního postupu v návrháři, pokud se už nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="d528a-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="d528a-117">Klikněte na tlačítko **argumenty** v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="d528a-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="d528a-118">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="d528a-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="d528a-119">Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.</span><span class="sxs-lookup"><span data-stu-id="d528a-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="d528a-120">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="d528a-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="d528a-121">Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte  **Datový typ Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d528a-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="d528a-122">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="d528a-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="d528a-123">Klikněte na tlačítko **proměnné** v levém dolním rohu návrháře postupu provádění zobrazit **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="d528a-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="d528a-124">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="d528a-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d528a-125">Pokud ne **vytvořit proměnnou** pole se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.Flowchart> aktivity na plochu návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="d528a-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="d528a-126">Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="d528a-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="d528a-127">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="d528a-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="d528a-128">Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="d528a-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="d528a-129">Klikněte na tlačítko **proměnné** v levého dolního rohu návrháře aktivit, zavřete **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="d528a-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="d528a-130">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d528a-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="d528a-131">Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a najeďte myší **spustit** uzlu, který je v horní části Vývojový diagram.</span><span class="sxs-lookup"><span data-stu-id="d528a-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="d528a-132">Při **přiřadit** činnost je nad **Start** uzlu kolem se zobrazí tři trojúhelníky **Start** uzlu.</span><span class="sxs-lookup"><span data-stu-id="d528a-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="d528a-133">Vyřadit **přiřadit** aktivitu na trojúhelník, který je přímo pod **Start** uzlu.</span><span class="sxs-lookup"><span data-stu-id="d528a-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="d528a-134">To se propojit dvě položky a označí **přiřadit** aktivitu jako první aktivitu ve vývojovém diagramu.</span><span class="sxs-lookup"><span data-stu-id="d528a-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d528a-135">Aktivity mohou také uvedené jako spouštěcí aktivitu v pracovním postupu ručně jejich propojením aktivit k počáteční uzel.</span><span class="sxs-lookup"><span data-stu-id="d528a-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="d528a-136">K tomu, najeďte myší **Start** uzel, klikněte na některou obdélníky, které se zobrazí, když je myš **Start** uzel a přetáhněte připojení řádek dolů požadovanou aktivitu a umístěte ho na jednom z obdélníky, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d528a-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="d528a-137">Můžete taky určit aktivity jako spouštěcí aktivitu tak, že kliknete pravým tlačítkem it a zvolíte **nastavit jako spuštění uzlu**.</span><span class="sxs-lookup"><span data-stu-id="d528a-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="d528a-138">Typ `Target` do **k** pole a následující výraz, který **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="d528a-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="d528a-139">Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d528a-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="d528a-140">Přetáhněte **výzvy** aktivita z **NumberGuessWorkflowActivities** část **nástrojů**, vyřaďte níže **přiřadit** aktivity z předchozího kroku a připojit **výzvy** aktivitu **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="d528a-141">Existují tři způsoby, jak připojit dvěma aktivitami.</span><span class="sxs-lookup"><span data-stu-id="d528a-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="d528a-142">První způsob je jejich připojení, jako je vyřadit **výzvy** aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="d528a-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="d528a-143">Jak přetahujete **výzvy** aktivitu do pracovního postupu, najeďte myší **přiřadit** aktivity a umístěte ho na jednu ze čtyř trojúhelníků, které se objeví **výzvy** Aktivita je přes **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="d528a-144">Druhý způsob je vyřadit **výzvy** aktivitu do pracovního postupu do požadovaného umístění.</span><span class="sxs-lookup"><span data-stu-id="d528a-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="d528a-145">Poté najeďte myší **přiřadit** aktivity a přetáhněte jeden z obdélníky, které se zobrazí dolů na **výzvy** aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="d528a-146">Přetáhněte myší tak, aby připojení řádek z **přiřadit** aktivity se připojí k jedné obdélníků z **výzvy** aktivitu a pak uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="d528a-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="d528a-147">Třetí způsob je velmi podobně jako první, s výjimkou, že místo přetažení **výzvy** aktivita z **nástrojů**, přetáhněte ho z umístění na povrchu návrhu pracovního postupu, najeďte myší  **Přiřadit** aktivitu a umístěte ho na jeden z trojúhelníků, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d528a-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="d528a-148">V **okno vlastností** pro **výzvy** aktivity, typ `"EnterGuess"` včetně uvozovek do **BookmarkName** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d528a-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="d528a-149">Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d528a-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="d528a-150">Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d528a-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="d528a-151">Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a připojte ho pomocí jedné z metod popsaných v předchozím kroku, tak, aby se níže  **Příkazový řádek** aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="d528a-152">Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="d528a-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="d528a-153">Přetáhněte **FlowDecision** z **vývojový diagram** část **nástrojů** a připojte ho níže **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="d528a-154">V **okno vlastností**, zadejte následující výraz do **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d528a-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="d528a-155">Přetáhněte další **FlowDecision** aktivita z **nástrojů** a klesne pod první z nich.</span><span class="sxs-lookup"><span data-stu-id="d528a-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="d528a-156">Propojení dvou aktivit přetažením z obdélník, který je označen **False** nahoře **FlowDecision** aktivity obdélníku, který v horní části druhý **FlowDecision**aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d528a-157">Pokud se nezobrazí **True** a **False** popisků na **FlowDecision**, najeďte myší **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="d528a-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="d528a-158">Klikněte na druhé **FlowDecision** aktivitu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="d528a-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="d528a-159">V **okno vlastností**, zadejte následující výraz do **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d528a-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="d528a-160">Přetáhněte dva **WriteLine** aktivity **primitiv** část **nástrojů** a umístit je tak, že jsou vedle sebe dva **FlowDecision**  aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="d528a-161">Připojit **True** akce dolní **FlowDecision** první aktivitu **WriteLine** aktivitu a **False** akce úplně vpravo **WriteLine** aktivity.</span><span class="sxs-lookup"><span data-stu-id="d528a-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="d528a-162">Klikněte na první **WriteLine** aktivity ho vyberte a zadejte následující výraz do **Text** hodnota vlastnosti pole **okno vlastností**.</span><span class="sxs-lookup"><span data-stu-id="d528a-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="d528a-163">Připojení **WriteLine** na levé straně **výzvy** aktivitu, která je nad ním.</span><span class="sxs-lookup"><span data-stu-id="d528a-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="d528a-164">Klikněte na tlačítko úplně vpravo **WriteLine** aktivity ho vyberte a zadejte následující výraz do **Text** hodnota vlastnosti pole **okno vlastností**.</span><span class="sxs-lookup"><span data-stu-id="d528a-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="d528a-165">Připojit **WriteLine** aktivity na pravé straně **výzvy** aktivity nad ním.</span><span class="sxs-lookup"><span data-stu-id="d528a-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="d528a-166">Následující příklad ukazuje dokončený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="d528a-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="d528a-167">![Dokončení Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="d528a-167">![Completed Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="d528a-168">K vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d528a-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="d528a-169">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="d528a-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="d528a-170">Návod, jak spustit workflow, najdete dalším tématu s názvem [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d528a-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="d528a-171">Pokud jste už dokončili [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md) krok s jiným stylem pracovního postupu a chcete ji spustit pomocí pracovního postupu vývojového diagramu z tohoto kroku, přeskočte k části [sestavíte a spustíte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) část [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d528a-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d528a-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d528a-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="d528a-173">Programování ve Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d528a-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="d528a-174">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d528a-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="d528a-175">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="d528a-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="d528a-176">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="d528a-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="d528a-177">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d528a-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
