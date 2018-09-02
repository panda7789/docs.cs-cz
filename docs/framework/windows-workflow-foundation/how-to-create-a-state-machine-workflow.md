---
title: 'Postupy: vytvoření pracovního postupu stavového stroje'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8098ab4b056ad6375c248e803134c35d67e3f27b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397710"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="b5e61-102">Postupy: vytvoření pracovního postupu stavového stroje</span><span class="sxs-lookup"><span data-stu-id="b5e61-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="b5e61-103">Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="b5e61-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="b5e61-104">V tomto tématu se provede vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.StateMachine> aktivity a vlastní aktivity z předchozího [jak: vytvořit aktivitu](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="b5e61-105">Pracovní postup modely číslo rozluštění hru.</span><span class="sxs-lookup"><span data-stu-id="b5e61-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5e61-106">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="b5e61-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b5e61-107">K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="b5e61-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5e61-108">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b5e61-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="b5e61-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5e61-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="b5e61-110">Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníka řešení** a vyberte **přidat**, **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="b5e61-111">V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b5e61-112">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="b5e61-113">Typ `StateMachineNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="b5e61-114">Přetáhněte **stavový stroj StateMachine** aktivita z **stavového stroje** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek pracovní postup návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="b5e61-115">Chcete-li vytvořit pracovní postup proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="b5e61-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="b5e61-116">Dvakrát klikněte na panel **StateMachineNumberGuessWorkflow.xaml** v **Průzkumníka řešení** zobrazíte pracovního postupu v návrháři, pokud se už nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="b5e61-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="b5e61-117">Klikněte na tlačítko **argumenty** v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="b5e61-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="b5e61-118">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="b5e61-119">Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.</span><span class="sxs-lookup"><span data-stu-id="b5e61-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="b5e61-120">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="b5e61-121">Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte  **Datový typ Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="b5e61-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="b5e61-122">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="b5e61-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="b5e61-123">Klikněte na tlačítko **proměnné** v levém dolním rohu návrháře postupu provádění zobrazit **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="b5e61-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="b5e61-124">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b5e61-125">Pokud ne **vytvořit proměnnou** pole se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.StateMachine> aktivity na plochu návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="b5e61-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="b5e61-126">Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="b5e61-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="b5e61-127">Klikněte na tlačítko **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="b5e61-128">Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.</span><span class="sxs-lookup"><span data-stu-id="b5e61-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="b5e61-129">Klikněte na tlačítko **proměnné** v levého dolního rohu návrháře aktivit, zavřete **proměnné** podokně.</span><span class="sxs-lookup"><span data-stu-id="b5e61-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="b5e61-130">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5e61-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="b5e61-131">Klikněte na tlačítko **nazvané State1** ji vyberte.</span><span class="sxs-lookup"><span data-stu-id="b5e61-131">Click **State1** to select it.</span></span> <span data-ttu-id="b5e61-132">V **okno vlastností**, změnit **DisplayName** k `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="b5e61-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b5e61-133">Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b5e61-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="b5e61-134">Dvakrát klikněte na nově pojmenovaném **inicializovat cílové** stavu v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="b5e61-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="b5e61-135">Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte ho do **položka** oddíl stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="b5e61-136">Typ `Target` do **k** pole a následující výraz, který **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="b5e61-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="b5e61-137">Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b5e61-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="b5e61-138">Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="b5e61-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="b5e61-139">Přetáhněte **stavu** aktivita z **stavového stroje** část **nástrojů** do návrháře postupu provádění a najeďte myší na **inicializovat cíl** stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="b5e61-140">Všimněte si, že čtyři trojúhelníky zobrazí kolem **inicializovat cílové** stav, když je nový stav nad ním.</span><span class="sxs-lookup"><span data-stu-id="b5e61-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="b5e61-141">Vyřadit nový stav na trojúhelník, který je hned pod **inicializovat cílové** stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="b5e61-142">To umístí nového stavu do pracovního postupu a vytvoří přechod z **inicializovat cílové** stavu do nového stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="b5e61-143">Klikněte na tlačítko **nazvané State1** vybraný a změňte **DisplayName** k `Enter Guess`a potom dvakrát klikněte na stav v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="b5e61-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="b5e61-144">Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho do **položka** oddíl stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="b5e61-145">Zadejte následující výraz do **Text** vlastnosti **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="b5e61-146">Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte na **ukončovací** oddíl stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="b5e61-147">Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="b5e61-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="b5e61-148">Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="b5e61-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="b5e61-149">Přetáhněte **FinalState** aktivity z **stavového stroje** část **nástrojů**, najeďte myší **zadejte odhad** stavu a umístěte ho na trojúhelník, který se zobrazí napravo od **zadejte uhodnout** stavu tak, aby se vytvoří s přechodem mezi **zadejte uhodnout** a **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="b5e61-150">Výchozí název přechodu je **T2**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="b5e61-151">Klikněte na tlačítko přechodu v Návrháři postupu provádění jej vyberte a nastavte jeho **DisplayName** k **odhad správný**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="b5e61-152">Potom klikněte na tlačítko a vyberte **FinalState**a přetáhněte ji na pravé straně tak, aby uvolnil prostor pro úplný přechod název zobrazený aniž zakreslovat buď dva stavy.</span><span class="sxs-lookup"><span data-stu-id="b5e61-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="b5e61-153">To usnadní dokončete zbývající kroky v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="b5e61-154">Dvakrát klikněte na nově pojmenovaném **odhad správný** přechodu v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="b5e61-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="b5e61-155">Přetáhněte **readint –** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **aktivační událost** oddílu přechodu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="b5e61-156">V **okno vlastností** pro **readint –** aktivity, typ `"EnterGuess"` včetně uvozovek do **BookmarkName** vlastnost hodnoty pole a typ `Guess`do **výsledek** vlastnost hodnota – pole</span><span class="sxs-lookup"><span data-stu-id="b5e61-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="b5e61-157">Zadejte následující výraz do **odhad správný** přechod na **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5e61-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="b5e61-158">Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="b5e61-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5e61-159">Přechod nastane aktivační událost přijetí a <xref:System.Activities.Statements.Transition.Condition%2A>, pokud jsou k dispozici, je vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="b5e61-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="b5e61-160">Pro tohoto přechodu je Pokud uživatele `Guess` odpovídá náhodně generované `Target`, pak řízení se předá **FinalState** a dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="b5e61-161">V závislosti na tom, zda je odhad správný, by měl pracovní postup buď na přechod **FinalState** nebo zpět **zadejte odhad** stavu pro jinou akci.</span><span class="sxs-lookup"><span data-stu-id="b5e61-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="b5e61-162">Obě přechody sdílet stejnou spouštěcí událost trigger čekání na odhad uživatele k přijetí prostřednictvím **readint –** aktivity.</span><span class="sxs-lookup"><span data-stu-id="b5e61-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="b5e61-163">Tomu se říká sdílené přechodu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-163">This is called a shared transition.</span></span> <span data-ttu-id="b5e61-164">Vytvořit sdílené přechod, klikněte na kruh, který označuje začátek **odhad správný** přechod a přetáhněte ho do požadovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="b5e61-165">V tomto případě je přechod přechod, takže přetáhněte počáteční bod **odhad správný** přechod a umístěte ho zpátky do dolní části **zadejte uhodnout** stavu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="b5e61-166">Po vytvoření přechodu, vyberte ho v Návrháři pracovních postupů a nastavte jeho **DisplayName** vlastnost **uhodnout nesprávné**.</span><span class="sxs-lookup"><span data-stu-id="b5e61-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5e61-167">Sdílené přechody lze také vytvořit z v rámci přechodu návrháře kliknutím **přidat sdílené triggeru, přechod** v dolní části návrháře přechod a pak vyberete požadovanou cílovou stavu z  **Dostupné stavy připojení** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5e61-168">Všimněte si, že pokud <xref:System.Activities.Statements.Transition.Condition%2A> přechodu vyhodnocen `false` (nebo vyhodnotit všechny podmínky sdílené spouštěcí události přechodu `false`), nedojde k přechodu a budou všechny aktivační události pro všechny přechody ze stavu znovu naplánována.</span><span class="sxs-lookup"><span data-stu-id="b5e61-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="b5e61-169">V tomto kurzu, nemůže tato situace nastat z důvodu způsob, jakým jsou podmínky nakonfigurované (máme konkrétní akce pro Určuje, zda je odhad správný nebo není správná).</span><span class="sxs-lookup"><span data-stu-id="b5e61-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="b5e61-170">Dvakrát klikněte **uhodnout nesprávné** přechodu v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="b5e61-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="b5e61-171">Všimněte si, že **aktivační událost** je již nastaven na stejnou **readint –** aktivitu, která byla použita **odhad správný** přechodu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="b5e61-172">Zadejte následující výraz do **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5e61-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="b5e61-173">Přetáhněte **Pokud** aktivita z **tok řízení** část **nástrojů** a umístěte jej do **akce** části přechodu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="b5e61-174">Zadejte následující výraz do **Pokud** aktivity **podmínku** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5e61-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="b5e61-175">Přetáhněte dva **WriteLine** aktivity z **primitiv** část **nástrojů** a umístit je tak, že jeden je v **pak** část **Pokud** aktivity a jeden je v **Else** oddílu.</span><span class="sxs-lookup"><span data-stu-id="b5e61-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="b5e61-176">Klikněte na tlačítko **WriteLine** aktivity v **pak** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5e61-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="b5e61-177">Klikněte na tlačítko **WriteLine** aktivity v **Else** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5e61-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="b5e61-178">Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="b5e61-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="b5e61-179">Následující příklad ukazuje dokončený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="b5e61-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="b5e61-180">![Dokončení pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="b5e61-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="b5e61-181">K vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5e61-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="b5e61-182">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="b5e61-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="b5e61-183">Návod, jak spustit workflow, najdete dalším tématu s názvem [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b5e61-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="b5e61-184">Pokud jste už dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiným stylem pracovního postupu a chcete ji spustit pomocí pracovní postup stavového stroje z tohoto kroku, přeskočte k části [sestavíte a spustíte aplikaci](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) část [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b5e61-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e61-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5e61-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="b5e61-186">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="b5e61-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="b5e61-187">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b5e61-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="b5e61-188">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="b5e61-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="b5e61-189">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="b5e61-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="b5e61-190">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5e61-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
