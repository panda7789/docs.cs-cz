---
title: 'Postupy: Vytvoření pracovního postupu stavového stroje'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: e93f84f0bacf7ac205294c12c55afcab8d7319b7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989812"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="1241c-102">Postupy: Vytvoření pracovního postupu stavového stroje</span><span class="sxs-lookup"><span data-stu-id="1241c-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="1241c-103">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="1241c-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="1241c-104">V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, <xref:System.Activities.Statements.StateMachine> jako je aktivita, a vlastní aktivity z předchozího [postupu: Vytvoření tématu aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="1241c-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="1241c-105">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="1241c-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1241c-106">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="1241c-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="1241c-107">Chcete-li dokončit toto téma, je nutné [nejprve provést následující kroky: Vytvoří aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="1241c-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1241c-108">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="1241c-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="1241c-109">Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1241c-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="1241c-110">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="1241c-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="1241c-111">V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="1241c-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1241c-112">V seznamu **pracovních postupů** vyberte **aktivita** .</span><span class="sxs-lookup"><span data-stu-id="1241c-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="1241c-113">Do `StateMachineNumberGuessWorkflow` pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1241c-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="1241c-114">Přetáhněte aktivitu **StateMachine** z části **Stavový počítač** v **sadě nástrojů** a přetáhněte ji na popisek **sem přetáhněte aktivitu** na návrhové ploše pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1241c-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="1241c-115">Postup vytvoření proměnných a argumentů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1241c-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="1241c-116">Dvojím kliknutím na **StateMachineNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.</span><span class="sxs-lookup"><span data-stu-id="1241c-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="1241c-117">Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="1241c-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="1241c-118">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="1241c-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="1241c-119">Do `MaxNumber` pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="1241c-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="1241c-120">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="1241c-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="1241c-121">`MaxNumber` Do pole název, které se nachází pod nově přidaným argumentem, vyberte out v rozevíracím seznamu směr, v rozevíracím seznamu typ argumentu vyberte Int32 a potom stiskněte klávesu ENTER. `Turns`</span><span class="sxs-lookup"><span data-stu-id="1241c-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="1241c-122">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="1241c-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="1241c-123">Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="1241c-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="1241c-124">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="1241c-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="1241c-125">Pokud se nezobrazí žádné pole **vytvořit proměnnou** , klikněte <xref:System.Activities.Statements.StateMachine> na aktivitu na ploše návrháře pracovního postupu a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="1241c-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="1241c-126">Do `Guess` pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="1241c-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="1241c-127">Klikněte na **vytvořit proměnnou**.</span><span class="sxs-lookup"><span data-stu-id="1241c-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="1241c-128">Do `Target` pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="1241c-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="1241c-129">Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .</span><span class="sxs-lookup"><span data-stu-id="1241c-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="1241c-130">Přidání aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1241c-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="1241c-131">Klikněte na **State1** a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="1241c-131">Click **State1** to select it.</span></span> <span data-ttu-id="1241c-132">V **okně Vlastnosti**změňte **Zobrazovaný** název na `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="1241c-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="1241c-133">Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="1241c-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="1241c-134">Dvakrát klikněte na nově přejmenovaný **cílový stav inicializace** v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="1241c-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="1241c-135">Přetáhněte aktivitu **přiřazení** z oddílu **primitivních** prvků v **sadě nástrojů** a přetáhněte ji do části pro **zadání** daného stavu.</span><span class="sxs-lookup"><span data-stu-id="1241c-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="1241c-136">Zadejte `Target` do pole **do** a následující výraz do pole **Zadejte C# výraz** nebo **Zadejte výraz VB** .</span><span class="sxs-lookup"><span data-stu-id="1241c-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="1241c-137">Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="1241c-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="1241c-138">Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1241c-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="1241c-139">Přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** do návrháře pracovních postupů a najeďte myší na **cílový stav inicializace** .</span><span class="sxs-lookup"><span data-stu-id="1241c-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="1241c-140">Všimněte si, že kolem **cílového stavu inicializace** se zobrazí čtyři trojúhelníky, když je tento nový stav nad ním.</span><span class="sxs-lookup"><span data-stu-id="1241c-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="1241c-141">Nový stav umístěte na trojúhelník, který je hned pod **cílovým** stavem inicializace.</span><span class="sxs-lookup"><span data-stu-id="1241c-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="1241c-142">Tím se nový stav umístí do pracovního postupu a vytvoří se přechod z **cílového stavu Initialize** do nového stavu.</span><span class="sxs-lookup"><span data-stu-id="1241c-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="1241c-143">Kliknutím na **State1** ho vyberte, změňte **Zobrazovaný** název na `Enter Guess`a pak dvakrát klikněte na stav v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="1241c-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="1241c-144">Přetáhněte aktivitu **WriteLine** z oddílu **primitivních** prvků v **sadě nástrojů** a přetáhněte ji do části pro **zadání** daného stavu.</span><span class="sxs-lookup"><span data-stu-id="1241c-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="1241c-145">Do pole vlastnost **text** v poli **WriteLine**zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="1241c-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="1241c-146">Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do části **Exit** (stav).</span><span class="sxs-lookup"><span data-stu-id="1241c-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="1241c-147">`Turns + 1` **C#** Do pole do zadejte a do pole zadejte výraz nebo zadejte výraz VB. `Turns`</span><span class="sxs-lookup"><span data-stu-id="1241c-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="1241c-148">Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1241c-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="1241c-149">Přetáhněte aktivitu **FinalState** z části **Stavový počítač** v **sadě nástrojů**, najeďte ji na stav **odhadu ENTER** a přetáhněte ji na trojúhelník, který se zobrazí vpravo od stavu **ENTER odhad** , aby byl přechod vytvořené mezi **zadáním odhadu** a **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="1241c-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="1241c-150">Výchozí název přechodu je **T2**.</span><span class="sxs-lookup"><span data-stu-id="1241c-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="1241c-151">Kliknutím na přechod v Návrháři pracovního postupu ho vyberte a nastavte jeho **Zobrazovaný** název na **správný odhad**.</span><span class="sxs-lookup"><span data-stu-id="1241c-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="1241c-152">Potom klikněte na **FinalState**a vyberte ho a přetáhněte ho na pravé straně, aby se zobrazil prostor pro zobrazení úplného názvu přechodu bez překryvu obou stavů.</span><span class="sxs-lookup"><span data-stu-id="1241c-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="1241c-153">To usnadňuje dokončení zbývajících kroků v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="1241c-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="1241c-154">Dvojitým kliknutím na nově přejmenovaný **odhad správného** přechodu v Návrháři pracovního postupu ho rozbalte.</span><span class="sxs-lookup"><span data-stu-id="1241c-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="1241c-155">Přetáhněte aktivitu **ReadInt** z oddílu **NumberGuessWorkflowActivities** **panelu nástrojů** a přetáhněte ji do oddílu **triggeru** přechodu.</span><span class="sxs-lookup"><span data-stu-id="1241c-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="1241c-156">V **okně Vlastnosti** aktivity **ReadInt** zadejte `"EnterGuess"` včetně uvozovek do pole hodnota vlastnosti **Bookmark** a do pole hodnota vlastnosti `Guess` **výsledku** zadejte.</span><span class="sxs-lookup"><span data-stu-id="1241c-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="1241c-157">Do pole **odhad správné** hodnoty vlastnosti **podmínky** přechodu zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="1241c-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="1241c-158">Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1241c-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1241c-159">K přechodu dojde v případě, že událost triggeru je <xref:System.Activities.Statements.Transition.Condition%2A>přijata a je-li k `True`dispozici, je vyhodnocena jako.</span><span class="sxs-lookup"><span data-stu-id="1241c-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="1241c-160">V případě tohoto přechodu se v případě, `Guess` že uživatel odpovídá náhodně `Target`generovanému objektu, řídí průchod **FinalState** a pracovní postup se dokončí.</span><span class="sxs-lookup"><span data-stu-id="1241c-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="1241c-161">V závislosti na tom, zda je odhad správný, by měl pracovní postup přejít buď na **FinalState** , nebo zpět do stavu **zadejte odhad** pro jiný pokus.</span><span class="sxs-lookup"><span data-stu-id="1241c-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="1241c-162">Oba přechody sdílejí stejnou aktivační událost, která čeká na přijetí odhadu uživatele prostřednictvím aktivity **ReadInt** .</span><span class="sxs-lookup"><span data-stu-id="1241c-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="1241c-163">Označuje se jako sdílený přechod.</span><span class="sxs-lookup"><span data-stu-id="1241c-163">This is called a shared transition.</span></span> <span data-ttu-id="1241c-164">Chcete-li vytvořit sdílený přechod, klikněte na kroužek, který indikuje začátek **odhadu správného** přechodu a přetáhněte ho do požadovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="1241c-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="1241c-165">V tomto případě je přechodem Automatický přechod, takže přetáhněte počáteční bod pro **správný** přechod a přetáhněte ho zpátky do dolní části stavu **zadejte odhad** .</span><span class="sxs-lookup"><span data-stu-id="1241c-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="1241c-166">Po vytvoření přechodu ho vyberte v Návrháři pracovních postupů a nastavte jeho vlastnost **DisplayName** na hodnotu **nesprávného odhadu**.</span><span class="sxs-lookup"><span data-stu-id="1241c-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1241c-167">Sdílené přechody je také možné vytvořit v Návrháři přechodu kliknutím na **přidat přechod sdílené triggery** v dolní části návrháře přechodu a následným výběrem požadovaného cílového stavu ze **stavů k připojení** . rozevírací seznam.</span><span class="sxs-lookup"><span data-stu-id="1241c-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1241c-168">Všimněte si, že <xref:System.Activities.Statements.Transition.Condition%2A> Pokud je z přechodu vyhodnocen `false` (nebo všechny podmínky přechodu na sdílený Trigger vyhodnoceny na `false`hodnotu), přechod nebude proveden a všechny aktivační události pro všechny přechody ze stavu budou změněn.</span><span class="sxs-lookup"><span data-stu-id="1241c-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="1241c-169">V tomto kurzu nemůžete k této situaci dojít kvůli způsobu konfigurace podmínek (máme konkrétní akce, ať už je odhad správný nebo nesprávný).</span><span class="sxs-lookup"><span data-stu-id="1241c-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="1241c-170">Poklikejte na **odhad nesprávného** přechodu v Návrháři pracovních postupů a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="1241c-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="1241c-171">Všimněte si, že **Trigger** je již nastaven na stejnou aktivitu **ReadInt** , jakou používal správný přechod **odhad** .</span><span class="sxs-lookup"><span data-stu-id="1241c-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="1241c-172">Do pole hodnota vlastnosti **podmínky** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="1241c-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="1241c-173">Přetáhněte aktivitu **if** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do části **Akce** přechodu.</span><span class="sxs-lookup"><span data-stu-id="1241c-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="1241c-174">Do pole hodnota vlastnosti **Podmínka** pro aktivitu **if** aktivity zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="1241c-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
24. <span data-ttu-id="1241c-175">Přetáhněte dvě aktivity **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte je tak, aby jedna byla v oddílu **then** aktivity **if** a jedna je v části **Else** .</span><span class="sxs-lookup"><span data-stu-id="1241c-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="1241c-176">Kliknutím na aktivitu **WriteLine** v části **pak** ji vyberete a do pole hodnota vlastnosti **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="1241c-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="1241c-177">Kliknutím na aktivitu **WriteLine** v části **Else** ji vyberte a do pole hodnota vlastnosti **text** zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="1241c-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="1241c-178">Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1241c-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="1241c-179">Následující příklad znázorňuje dokončený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="1241c-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="1241c-181">Postup sestavení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1241c-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="1241c-182">Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="1241c-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="1241c-183">Pokyny ke spuštění pracovního postupu najdete v dalším tématu [postup: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1241c-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="1241c-184">Pokud jste již dokončili [postupy: Spusťte krok pracovního](how-to-run-a-workflow.md) postupu s jiným stylem pracovního postupu a přejete si ho spustit pomocí pracovního postupu stavového stroje z tohoto kroku, Přeskočit k [sestavení a spustit](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [aplikaci v tématu Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1241c-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1241c-185">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1241c-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="1241c-186">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="1241c-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="1241c-187">Návrh pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1241c-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="1241c-188">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="1241c-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="1241c-189">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="1241c-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="1241c-190">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1241c-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
