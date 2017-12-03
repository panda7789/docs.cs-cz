---
title: "Postupy: vytvoření vývojový diagram pracovního postupu"
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3df93a876522ccdc001bc3f6bc8c780bc80dc21b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="95a25-102">Postupy: vytvoření vývojový diagram pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="95a25-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="95a25-103">Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="95a25-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="95a25-104">Kroky v tomto tématu procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.Flowchart> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="95a25-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="95a25-105">Pracovní postup modelů číslo hádání hru.</span><span class="sxs-lookup"><span data-stu-id="95a25-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95a25-106">Každého tématu v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="95a25-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="95a25-107">K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="95a25-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95a25-108">Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="95a25-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="95a25-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="95a25-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="95a25-110">Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="95a25-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="95a25-111">V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="95a25-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="95a25-112">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="95a25-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="95a25-113">Typ `FlowchartNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="95a25-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="95a25-114">Přetažení **vývojový diagram** aktivity z **vývojový diagram** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** v popisek pracovní postup návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="95a25-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="95a25-115">Vytvoření proměnné pracovního postupu a argumenty</span><span class="sxs-lookup"><span data-stu-id="95a25-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="95a25-116">Klikněte dvakrát na **FlowchartNumberGuessWorkflow.xaml** v **Průzkumníku řešení** zobrazíte pracovního postupu v návrháři, pokud již není zobrazen.</span><span class="sxs-lookup"><span data-stu-id="95a25-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="95a25-117">Klikněte na tlačítko **argumenty** na straně dolním Návrháře pracovního postupu pro zobrazení **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="95a25-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="95a25-118">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="95a25-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="95a25-119">Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.</span><span class="sxs-lookup"><span data-stu-id="95a25-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="95a25-120">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="95a25-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="95a25-121">Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte  **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="95a25-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="95a25-122">Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="95a25-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="95a25-123">Klikněte na tlačítko **proměnné** na straně dolním Návrháře pracovního postupu pro zobrazení **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="95a25-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="95a25-124">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="95a25-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="95a25-125">Pokud žádné **vytvoření proměnné** políčko se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.Flowchart> aktivity na plochu návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="95a25-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="95a25-126">Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="95a25-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="95a25-127">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="95a25-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="95a25-128">Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="95a25-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="95a25-129">Klikněte na tlačítko **proměnné** v levém dolním straně Návrhář aktivity zavřete **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="95a25-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="95a25-130">Chcete-li přidat aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="95a25-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="95a25-131">Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a ukazatel myši přesunete **spustit** uzlu, který je v horní části Vývojový diagram.</span><span class="sxs-lookup"><span data-stu-id="95a25-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="95a25-132">Při **přiřadit** aktivity je nad **spustit** uzlu kolem se zobrazí tři trojúhelníčky **spustit** uzlu.</span><span class="sxs-lookup"><span data-stu-id="95a25-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="95a25-133">Vyřaďte **přiřadit** aktivity na trojúhelníček, který je přímo pod **spustit** uzlu.</span><span class="sxs-lookup"><span data-stu-id="95a25-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="95a25-134">To bude propojit dvě položky společně a označí **přiřadit** aktivitu jako první aktivitu v vývojový diagram.</span><span class="sxs-lookup"><span data-stu-id="95a25-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95a25-135">Aktivity můžete také zadat jako výchozí aktivity v pracovním postupu ručně jejich spojením aktivity s počáteční uzel.</span><span class="sxs-lookup"><span data-stu-id="95a25-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="95a25-136">K tomu, najeďte myší **spustit** uzel, klikněte na jednu z obdélníky, které se zobrazí při přesunutí myši **spustit** uzel a přetáhněte připojení řádek dolů požadované aktivity a umístěte jej na jednom z obdélníky, které se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="95a25-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="95a25-137">Můžete také určit a aktivitu jako spouštěcí aktivitu tak, že kliknete pravým tlačítkem na it a výběr **nastavit jako spuštění uzlu**.</span><span class="sxs-lookup"><span data-stu-id="95a25-137">You can also designate and activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="95a25-138">Typ `Target` do **k** pole a následující výraz do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.</span><span class="sxs-lookup"><span data-stu-id="95a25-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="95a25-139">Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="95a25-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="95a25-140">Přetažení **výzva** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů**, vyřaďte níže **přiřadit** aktivity z předchozího kroku a připojte **výzva** aktivitu **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="95a25-141">Existují tři způsoby, jak připojit dvěma aktivitami.</span><span class="sxs-lookup"><span data-stu-id="95a25-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="95a25-142">První způsob je je připojení, jako je vyřadit **výzva** aktivity pro pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="95a25-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="95a25-143">Jako přetahování **výzva** aktivitu do pracovního postupu, najeďte myší **přiřadit** aktivity a umístěte jej do jednoho čtyři trojúhelníčky, které se objeví **výzva** Aktivita je přes **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="95a25-144">Druhý způsob je odpojení **výzva** aktivitu do pracovního postupu v požadovaném umístění.</span><span class="sxs-lookup"><span data-stu-id="95a25-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="95a25-145">Potom najeďte myší **přiřadit** aktivity a přetáhněte jeden obdélníky, které se zobrazí dolů na **výzva** aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="95a25-146">Přetažení myší tak, aby připojení řádek z **přiřadit** aktivity připojen k jednomu z obdélníků z **výzva** aktivity a pak uvolnění tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="95a25-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="95a25-147">Třetí způsob, jakým je velmi podobně jako první, vyjma toho, že existuje několik způsobů **výzva** aktivity z **sada nástrojů**, přetáhněte ji z jeho umístění na návrhovou plochu pracovního postupu, najeďte myší  **Přiřadit** aktivitu a umístěte jej do jednoho trojúhelníčky, které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="95a25-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="95a25-148">V **vlastnosti – okno** pro **výzva** aktivity, typ `"EnterGuess"` včetně uvozovek do **NázevZáložky** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95a25-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="95a25-149">Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** pole vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95a25-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="95a25-150">Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="95a25-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="95a25-151">Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a připojte ho pomocí jedné z metod popsaných v předchozím kroku, tak, aby se níže  **Výzva** aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="95a25-152">Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.</span><span class="sxs-lookup"><span data-stu-id="95a25-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="95a25-153">Přetáhněte **FlowDecision** z **vývojový diagram** části **sada nástrojů** a připojte ho níže **přiřadit** aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="95a25-154">V **vlastnosti – okno**, zadejte následující výraz do **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95a25-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="95a25-155">Přetáhněte další **FlowDecision** aktivity z **sada nástrojů** a umístěte jej pod první z nich.</span><span class="sxs-lookup"><span data-stu-id="95a25-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="95a25-156">Připojení dvě aktivity přetažením z obdélníku, které je označeno **False** nahoře **FlowDecision** aktivitu rámeček v horní části druhý **FlowDecision**aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="95a25-157">Pokud se nezobrazí **True** a **False** popisků na **FlowDecision**, najeďte myší **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="95a25-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="95a25-158">Klikněte na druhý **FlowDecision** aktivity ji vyberte.</span><span class="sxs-lookup"><span data-stu-id="95a25-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="95a25-159">V **vlastnosti – okno**, zadejte následující výraz do **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95a25-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="95a25-160">Přetáhněte dva **WriteLine** aktivity z **primitiv** části **sada nástrojů** a jejich umístění, aby se vedle sebe níže dva **FlowDecision**  aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="95a25-161">Připojení **True** akce dolní **FlowDecision** aktivitu levou krajní **WriteLine** aktivitu a **False** akce úplně vpravo **WriteLine** aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a25-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="95a25-162">Klikněte levou krajní **WriteLine** aktivitu vyberte ho a zadejte následující výraz do **Text** hodnota vlastnosti pole **vlastnosti – okno**.</span><span class="sxs-lookup"><span data-stu-id="95a25-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="95a25-163">Připojení **WriteLine** na levé straně **výzva** aktivity, který je nad ním.</span><span class="sxs-lookup"><span data-stu-id="95a25-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="95a25-164">Klikněte pravou krajní **WriteLine** aktivitu vyberte ho a zadejte následující výraz do **Text** hodnota vlastnosti pole **vlastnosti – okno**.</span><span class="sxs-lookup"><span data-stu-id="95a25-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="95a25-165">Připojení **WriteLine** aktivity na pravé straně **výzva** aktivity nad ním.</span><span class="sxs-lookup"><span data-stu-id="95a25-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="95a25-166">Následující příklad ilustruje dokončené pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="95a25-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="95a25-167">![Dokončit modelu Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="95a25-167">![Completed Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="95a25-168">K vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="95a25-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="95a25-169">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="95a25-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="95a25-170">Pokyny o tom, jak spustit workflow, naleznete v tématu Další [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="95a25-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="95a25-171">Pokud jste již dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiný styl pracovního postupu a chcete spustit pomocí vývojový diagram pracovního postupu z tohoto kroku, přeskočit na [sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)část [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="95a25-171">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a25-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="95a25-172">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="95a25-173">Windows Workflow Foundation programování</span><span class="sxs-lookup"><span data-stu-id="95a25-173">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="95a25-174">Navrhování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="95a25-174">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="95a25-175">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="95a25-175">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="95a25-176">Postupy: vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="95a25-176">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="95a25-177">Postupy: spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="95a25-177">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
