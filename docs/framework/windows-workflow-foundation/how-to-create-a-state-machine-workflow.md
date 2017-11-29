---
title: "Postupy: vytvoření pracovního postupu stavu počítače"
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
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 797cdc425c0f3088aa2b75c0285ca6bea2dd425b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="570c1-102">Postupy: vytvoření pracovního postupu stavu počítače</span><span class="sxs-lookup"><span data-stu-id="570c1-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="570c1-103">Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="570c1-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="570c1-104">Kroky v tomto tématu procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.StateMachine> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="570c1-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="570c1-105">Pracovní postup modelů číslo hádání hru.</span><span class="sxs-lookup"><span data-stu-id="570c1-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="570c1-106">Každého tématu v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="570c1-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="570c1-107">K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="570c1-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="570c1-108">Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="570c1-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="570c1-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="570c1-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="570c1-110">Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="570c1-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="570c1-111">V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="570c1-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="570c1-112">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="570c1-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="570c1-113">Typ `StateMachineNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="570c1-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="570c1-114">Přetažení **StateMachine** aktivity z **stavu počítače** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** v popisek návrhové ploše pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="570c1-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="570c1-115">Vytvoření proměnné pracovního postupu a argumenty</span><span class="sxs-lookup"><span data-stu-id="570c1-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="570c1-116">Klikněte dvakrát na **StateMachineNumberGuessWorkflow.xaml** v **Průzkumníku řešení** zobrazíte pracovního postupu v návrháři, pokud již není zobrazen.</span><span class="sxs-lookup"><span data-stu-id="570c1-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="570c1-117">Klikněte na tlačítko **argumenty** na straně dolním Návrháře pracovního postupu pro zobrazení **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="570c1-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="570c1-118">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="570c1-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="570c1-119">Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.</span><span class="sxs-lookup"><span data-stu-id="570c1-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="570c1-120">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="570c1-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="570c1-121">Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte  **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="570c1-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="570c1-122">Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="570c1-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="570c1-123">Klikněte na tlačítko **proměnné** na straně dolním Návrháře pracovního postupu pro zobrazení **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="570c1-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="570c1-124">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="570c1-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="570c1-125">Pokud žádné **vytvoření proměnné** políčko se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.StateMachine> aktivity na plochu návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="570c1-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="570c1-126">Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="570c1-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="570c1-127">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="570c1-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="570c1-128">Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="570c1-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="570c1-129">Klikněte na tlačítko **proměnné** v levém dolním straně Návrhář aktivity zavřete **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="570c1-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="570c1-130">Chcete-li přidat aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="570c1-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="570c1-131">Klikněte na tlačítko **State1** ji vyberte.</span><span class="sxs-lookup"><span data-stu-id="570c1-131">Click **State1** to select it.</span></span> <span data-ttu-id="570c1-132">V **vlastnosti – okno**, změnit **DisplayName** k `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="570c1-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="570c1-133">Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="570c1-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="570c1-134">Klikněte dvakrát na nově pojmenovaném **inicializovat cíl** stavu v Návrháři pracovních postupů a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="570c1-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="570c1-135">Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **položka** části stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="570c1-136">Typ `Target` do **k** pole a následující výraz do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.</span><span class="sxs-lookup"><span data-stu-id="570c1-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="570c1-137">Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="570c1-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="570c1-138">Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="570c1-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="570c1-139">Přetažení **stavu** aktivity z **stavový stroj** části **sada nástrojů** do návrháře pracovních postupů a pozastavte ukazatel myši nad **inicializovat cíl** stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="570c1-140">Všimněte si, že kolem se zobrazí čtyři trojúhelníčky **inicializovat cíl** stav, když nový stav je nad ním.</span><span class="sxs-lookup"><span data-stu-id="570c1-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="570c1-141">Vyřaďte nový stav na trojúhelníček, která se nachází bezprostředně pod **inicializovat cíl** stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="570c1-142">To umístí nový stav do pracovního postupu a vytvoří přechod z **inicializovat cíl** do nového stavu stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="570c1-143">Klikněte na tlačítko **State1** ji vyberte Změnit **DisplayName** k `Enter Guess`a potom dvakrát klikněte na stav v Návrháři pracovních postupů a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="570c1-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="570c1-144">Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **položka** části stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="570c1-145">Zadejte následující výraz do **Text** vlastnost pole **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="570c1-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="570c1-146">Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte na **ukončení** části stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="570c1-147">Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.</span><span class="sxs-lookup"><span data-stu-id="570c1-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="570c1-148">Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="570c1-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="570c1-149">Přetažení **FinalState** aktivity z **stavový stroj** části **sada nástrojů**, najeďte myší na **zadejte uhodnout** stavu a umístěte jej na trojúhelníček, který se zobrazí napravo **zadejte uhodnout** stavu tak, aby se vytvoří přechod mezi **zadejte uhodnout** a **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="570c1-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="570c1-150">Výchozí název přechodu je **T2**.</span><span class="sxs-lookup"><span data-stu-id="570c1-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="570c1-151">Klikněte na tlačítko přechodu v Návrháři pracovních postupů, vyberte ho a nastavit jeho **DisplayName** k **uhodnout správné**.</span><span class="sxs-lookup"><span data-stu-id="570c1-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="570c1-152">Potom klikněte na tlačítko a vyberte **FinalState**a přetáhněte jej do právo tak, aby bylo místo pro úplné přechod název zobrazený bez překrytí buď dva stavy.</span><span class="sxs-lookup"><span data-stu-id="570c1-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="570c1-153">To bude usnadňují dokončit zbývající kroky v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="570c1-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="570c1-154">Klikněte dvakrát na nově pojmenovaném **uhodnout správné** přechod v Návrháři pracovních postupů a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="570c1-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="570c1-155">Přetáhněte **readint –** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů** a umístěte jej do **aktivační událost** části přechodu.</span><span class="sxs-lookup"><span data-stu-id="570c1-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="570c1-156">V **vlastnosti – okno** pro **readint –** aktivity, typ `"EnterGuess"` včetně uvozovek do **NázevZáložky** vlastnost hodnota pole a zadejte `Guess`do **výsledek** vlastnost hodnota pole</span><span class="sxs-lookup"><span data-stu-id="570c1-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="570c1-157">Zadejte následující výraz do **uhodnout správné** přechod na **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="570c1-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="570c1-158">Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="570c1-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="570c1-159">Přechod nastane, když je obdržena aktivační událost a <xref:System.Activities.Statements.Transition.Condition%2A>, pokud existuje, jehož výsledkem `True`.</span><span class="sxs-lookup"><span data-stu-id="570c1-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="570c1-160">Pro tento přechod Pokud uživatele `Guess` odpovídá náhodně generované `Target`, pak předá řízení **FinalState** a dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="570c1-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="570c1-161">V závislosti na tom, jestli odhad je správná, měli přechod pracovního postupu k **FinalState** nebo zpět do **zadejte odhad** stavu pro jiné opakujte.</span><span class="sxs-lookup"><span data-stu-id="570c1-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="570c1-162">Obě přechody sdílet stejnou aktivační událost čekání odhad uživatele k přijetí prostřednictvím **readint –** aktivity.</span><span class="sxs-lookup"><span data-stu-id="570c1-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="570c1-163">Tomu se říká sdílené přechod.</span><span class="sxs-lookup"><span data-stu-id="570c1-163">This is called a shared transition.</span></span> <span data-ttu-id="570c1-164">Vytvoření sdílené přechodu, klikněte na kruh označující začátek **uhodnout správné** přechod a přetáhněte ji do požadovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="570c1-165">V takovém případě je přechod vlastní přechodu, takže přetáhněte počáteční bod **uhodnout správné** přechod a umístěte jej zpět na konci **zadejte uhodnout** stavu.</span><span class="sxs-lookup"><span data-stu-id="570c1-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="570c1-166">Po vytvoření přechodu, vyberte ho v Návrháři pracovních postupů a nastavit jeho **DisplayName** vlastnost **uhodnout nesprávné**.</span><span class="sxs-lookup"><span data-stu-id="570c1-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="570c1-167">Sdílené přechody můžete také vytvořit z v Návrháři přechod kliknutím **přidat sdílený aktivační událost přechod** v dolní části návrháře přechod a pak vybrat požadovanou cílového stavu z  **Dostupné stavy připojení** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="570c1-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="570c1-168">Všimněte si, že pokud <xref:System.Activities.Statements.Transition.Condition%2A> přechodu se vyhodnocuje `false` (nebo všechny podmínky přechod sdílené aktivační událost vyhodnocení `false`), přechod nedojde a budou všechny aktivační události pro všechny přechody ze stavu znovu naplánován.</span><span class="sxs-lookup"><span data-stu-id="570c1-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="570c1-169">V tomto kurzu, nemůže tato situace nastat z důvodu způsob, jak jsou nakonfigurované podmínky (máme konkrétní akce na tom, jestli odhad správný nebo nesprávné).</span><span class="sxs-lookup"><span data-stu-id="570c1-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="570c1-170">Dvakrát klikněte **uhodnout nesprávné** přechod v Návrháři pracovních postupů a rozbalte ji.</span><span class="sxs-lookup"><span data-stu-id="570c1-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="570c1-171">Všimněte si, že **aktivační událost** už je nastavené na stejné **readint –** aktivity, která byla používána **uhodnout správné** přechod.</span><span class="sxs-lookup"><span data-stu-id="570c1-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="570c1-172">Zadejte následující výraz do **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="570c1-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="570c1-173">Přetáhněte **Pokud** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **akce** části přechodu.</span><span class="sxs-lookup"><span data-stu-id="570c1-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="570c1-174">Zadejte následující výraz do **Pokud** aktivity **podmínku** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="570c1-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="570c1-175">Přetáhněte dva **WriteLine** aktivity z **primitiv** části **sada nástrojů** a vyřadit je tak, aby jeden **pak** část **Pokud** aktivitu a jeden, je v **Else** části.</span><span class="sxs-lookup"><span data-stu-id="570c1-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="570c1-176">Klikněte na tlačítko **WriteLine** aktivity v **pak** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="570c1-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="570c1-177">Klikněte na tlačítko **WriteLine** aktivity v **Else** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="570c1-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="570c1-178">Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="570c1-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="570c1-179">Následující příklad ilustruje dokončené pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="570c1-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="570c1-180">![Dokončit pracovní postup stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="570c1-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="570c1-181">K vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="570c1-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="570c1-182">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="570c1-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="570c1-183">Pokyny o tom, jak spustit workflow, naleznete v tématu Další [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="570c1-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="570c1-184">Pokud jste již dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiný styl pracovního postupu a chcete spustit pomocí pracovní postup stavu počítače z tohoto kroku, přeskočit na [sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) části [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="570c1-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570c1-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="570c1-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="570c1-186">Windows Workflow Foundation programování</span><span class="sxs-lookup"><span data-stu-id="570c1-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="570c1-187">Navrhování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="570c1-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="570c1-188">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="570c1-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="570c1-189">Postupy: vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="570c1-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="570c1-190">Postupy: spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="570c1-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
