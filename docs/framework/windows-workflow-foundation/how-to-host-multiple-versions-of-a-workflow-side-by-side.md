---
title: 'Postupy: Hostování několika verzí pracovního postupu současně'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 4fc4565db58d008f52bc047d26118fc849648770
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329450"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="df784-102">Postupy: Hostování několika verzí pracovního postupu současně</span><span class="sxs-lookup"><span data-stu-id="df784-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
`WorkflowIdentity` <span data-ttu-id="df784-103">umožňuje vývojářům aplikací pracovní postup přidružit název a verze definice pracovního postupu a tyto informace k trvalé instance práce.</span><span class="sxs-lookup"><span data-stu-id="df784-103">provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="df784-104">Tyto informace identita umožňuje vývojáři aplikace pracovního postupu povolení scénářů, jako je vedle sebe spuštění více verzí modulu definice pracovního postupu a poskytuje základní kámen pro další funkce, jako je například dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="df784-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="df784-105">Tento krok úvodního kurzu ukazuje, jak používat `WorkflowIdentity` k hostování několika verzí pracovního postupu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="df784-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
>  <span data-ttu-id="df784-106">Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="df784-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="df784-107">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="df784-107">In this topic</span></span>  
 <span data-ttu-id="df784-108">V tomto kroku kurzu `WriteLine` aktivitám v pracovním postupu jsou upraveny pro poskytnutí dalších informací a nový `WriteLine` je aktivita přidána.</span><span class="sxs-lookup"><span data-stu-id="df784-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="df784-109">Je uložená kopie původního sestavení pracovního postupu a hostitelské aplikace se aktualizuje tak, aby ji můžete spustit původní a aktualizovaný pracovní postupy ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="df784-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="df784-110">Chcete-li kopii projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="df784-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="df784-111">Chcete-li aktualizovat pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="df784-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="df784-112">Na aktualizaci pracovního postupu stavový stroj StateMachine</span><span class="sxs-lookup"><span data-stu-id="df784-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="df784-113">Na aktualizaci pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="df784-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="df784-114">Chcete-li aktualizovat sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df784-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="df784-115">Chcete-li aktualizovat WorkflowVersionMap zahrnovat předchozí verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df784-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="df784-116">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="df784-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="df784-117">Před provedením kroků v tomto tématu, spusťte aplikaci, spustit několik pracovních postupů u každého typu a provedení jedné nebo dvou pokusů u každé z nich.</span><span class="sxs-lookup"><span data-stu-id="df784-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="df784-118">Tyto trvalý pracovní postupy se používají v tomto kroku a následující krok [jak: Aktualizace definice běžící Instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="df784-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="df784-119">Každý krok úvodního kurzu Začínáme závisí na předchozí kroky.</span><span class="sxs-lookup"><span data-stu-id="df784-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="df784-120">Pokud jste neprovedli v předchozích krocích můžete stáhnout úplnou verzi kurzem z [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="df784-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="BKMK_BackupCopy"></a> <span data-ttu-id="df784-121">Chcete-li kopii projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="df784-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1. <span data-ttu-id="df784-122">Otevřete **WF45GettingStartedTutorial** řešení ve Visual Studio 2012, pokud není otevřen.</span><span class="sxs-lookup"><span data-stu-id="df784-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>  
  
2. <span data-ttu-id="df784-123">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="df784-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="df784-124">Zavřít **WF45GettingStartedTutorial** řešení.</span><span class="sxs-lookup"><span data-stu-id="df784-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4. <span data-ttu-id="df784-125">Otevřete Průzkumníka Windows a přejděte do složky, kde se nachází soubor kurz řešení a složky projektu.</span><span class="sxs-lookup"><span data-stu-id="df784-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5. <span data-ttu-id="df784-126">Vytvořte novou složku s názvem **PreviousVersions** ve stejné složce jako **NumberGuessWorkflowHost** a **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="df784-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="df784-127">Tato složka se používá pro jiné sestavení, které obsahují různé verze pracovních postupech, používat v dalších kroků kurzu.</span><span class="sxs-lookup"><span data-stu-id="df784-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6. <span data-ttu-id="df784-128">Přejděte **NumberGuessWorkflowActivities\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="df784-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="df784-129">Kopírování **NumberGuessWorkflowActivities.dll** a vložte ho do **PreviousVersions** složky.</span><span class="sxs-lookup"><span data-stu-id="df784-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7. <span data-ttu-id="df784-130">Přejmenovat **NumberGuessWorkflowActivities.dll** v **PreviousVersions** složku **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="df784-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df784-131">Kroky v tomto tématu ukazují jeden způsob, jak spravovat sestavení použít tak, aby obsahovala více verzí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="df784-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="df784-132">Také lze použít jiné metody, jako je například silné názvy sestavení a jejich registrace v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="df784-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="df784-133">Vytvořte novou složku s názvem **NumberGuessWorkflowActivities_du** ve stejné složce jako **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**a nově Přidání **PreviousVersions** složky a zkopírujte všechny soubory a podsložky ze **NumberGuessWorkflowActivities** do nové složky  **NumberGuessWorkflowActivities_du** složky.</span><span class="sxs-lookup"><span data-stu-id="df784-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="df784-134">Tuto záložní kopii projektu pro počáteční verze aktivit se používá v [jak: Aktualizace definice běžící Instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="df784-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="df784-135">Znovu otevřete **WF45GettingStartedTutorial** řešení v sadě Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="df784-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="df784-136">Chcete-li aktualizovat pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="df784-136">To update the workflows</span></span>
 <span data-ttu-id="df784-137">V této části se aktualizují definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df784-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="df784-138">Dva `WriteLine` aktivity, které váš názor na odhad uživatele jsou aktualizované a nový `WriteLine` je aktivita přidána, která poskytuje další informace o hry po uhodnout číslo.</span><span class="sxs-lookup"><span data-stu-id="df784-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="df784-139">Na aktualizaci pracovního postupu stavový stroj StateMachine</span><span class="sxs-lookup"><span data-stu-id="df784-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="df784-140">V **Průzkumníka řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="df784-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="df784-141">Dvakrát klikněte **uhodnout nesprávné** přechodu na stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="df784-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="df784-142">Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="df784-143">Aktualizace `Text` z úplně vpravo `WriteLine` v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="df784-144">Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="df784-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="df784-145">Dvakrát klikněte **odhad správný** přechodu na stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="df784-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="df784-146">Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho na **Sem přetáhněte akci aktivitu** popisek Přechod.</span><span class="sxs-lookup"><span data-stu-id="df784-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="df784-147">Zadejte následující výraz do `Text` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df784-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="df784-148">Na aktualizaci pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="df784-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="df784-149">V **Průzkumníka řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **FlowchartNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="df784-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="df784-150">Aktualizace `Text` z nejvíce vlevo `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="df784-151">Aktualizace `Text` z úplně vpravo `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="df784-152">Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho na místa přetažení `True` akce horní `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="df784-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="df784-153">`WriteLine` Je aktivita přidána do vývojového diagramu a propojit s `True` akce `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="df784-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="df784-154">Zadejte následující výraz do `Text` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df784-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a> <span data-ttu-id="df784-155">Chcete-li aktualizovat sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df784-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="df784-156">V **Průzkumníka řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **SequentialNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="df784-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="df784-157">Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="df784-158">Aktualizace `Text` z úplně vpravo `WriteLine` aktivity v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="df784-159">Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho po **DoWhile** aktivitu tak, aby  **WriteLine** je poslední aktivita v kořenovém adresáři `Sequence` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="df784-160">Zadejte následující výraz do `Text` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df784-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="df784-161">Chcete-li aktualizovat WorkflowVersionMap zahrnovat předchozí verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df784-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="df784-162">Dvakrát klikněte na panel **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projekt tak, aby ho otevřete.</span><span class="sxs-lookup"><span data-stu-id="df784-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="df784-163">Přidejte následující `using` (nebo `Imports`) příkazy do horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="df784-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="df784-164">Přidejte tři nové identity pracovního postupu pod tři existující deklarace identity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df784-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="df784-165">Tyto nové `v1` pracovního postupu se použije identity poskytnout definici správné pracovního postupu pro pracovní postupy spuštěné před byly provedeny aktualizace.</span><span class="sxs-lookup"><span data-stu-id="df784-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="df784-166">V `WorkflowVersionMap` konstruktoru, aktualizace `Version` vlastnost tři aktuální identity pracovního postupu k `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="df784-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

     <span data-ttu-id="df784-167">Kód, který přidá aktuálních verzích pracovních postupů do slovníku používá aktuální verze, které je odkazováno v projektu, takže není potřeba aktualizovat kód, který inicializuje definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df784-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="df784-168">Přidejte následující kód do konstruktoru hned za kód, který se přidá do slovníku aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="df784-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

     <span data-ttu-id="df784-169">Tyto identity pracovního postupu jsou spojeny s počáteční verze odpovídající definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df784-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="df784-170">V dalším kroku načíst sestavení, které obsahuje počáteční verze definice pracovního postupu a vytvořte a přidejte odpovídající definice pracovního postupu do slovníku.</span><span class="sxs-lookup"><span data-stu-id="df784-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="df784-171">V následujícím příkladu je úplný seznam pro aktualizaci `WorkflowVersionMap` třídy.</span><span class="sxs-lookup"><span data-stu-id="df784-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

### <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="df784-172">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="df784-172">To build and run the application</span></span>

1. <span data-ttu-id="df784-173">Stiskněte kombinaci kláves CTRL + SHIFT + B pro vytvoření aplikace a potom CTRL + F5 ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="df784-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="df784-174">Začněte kliknutím na nový pracovní postup **novou hru**.</span><span class="sxs-lookup"><span data-stu-id="df784-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="df784-175">Verze pracovního postupu se zobrazí v okně Stav a zahrnuje aktualizovanou verzi z přidruženého `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="df784-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="df784-176">Poznamenejte si `InstanceId` tak můžete zobrazit soubor sledování pracovního postupu po dokončení a až do dokončení hra, zadejte pokusů.</span><span class="sxs-lookup"><span data-stu-id="df784-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="df784-177">Všimněte si, jak odhad uživatele se zobrazí v informace zobrazené v okně Stav na základě aktualizací na `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="df784-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

 **<span data-ttu-id="df784-178">Zadejte prosím číslo mezi 1 a 10</span><span class="sxs-lookup"><span data-stu-id="df784-178">Please enter a number between 1 and 10</span></span>**  
**<span data-ttu-id="df784-179">5 je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="df784-179">5 is too high.</span></span>**  
**<span data-ttu-id="df784-180">Zadejte prosím číslo mezi 1 a 10</span><span class="sxs-lookup"><span data-stu-id="df784-180">Please enter a number between 1 and 10</span></span>**  
**<span data-ttu-id="df784-181">3 je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="df784-181">3 is too high.</span></span>**  
**<span data-ttu-id="df784-182">Zadejte prosím číslo mezi 1 a 10</span><span class="sxs-lookup"><span data-stu-id="df784-182">Please enter a number between 1 and 10</span></span>**  
**<span data-ttu-id="df784-183">1 je příliš nízká.</span><span class="sxs-lookup"><span data-stu-id="df784-183">1 is too low.</span></span>**  
**<span data-ttu-id="df784-184">Zadejte prosím číslo mezi 1 a 10</span><span class="sxs-lookup"><span data-stu-id="df784-184">Please enter a number between 1 and 10</span></span>**  
**<span data-ttu-id="df784-185">Blahopřejeme, uhodnout číslo na oplátku 4.</span><span class="sxs-lookup"><span data-stu-id="df784-185">Congratulations, you guessed the number in 4 turns.</span></span>**  

    > [!NOTE]
    >  <span data-ttu-id="df784-186">Aktualizovaný text z `WriteLine` aktivity se zobrazí, ale výstup finální `WriteLine` je aktivitou, která byla přidána v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="df784-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="df784-187">Důvodem je, že se aktualizoval stav okna `PersistableIdle` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="df784-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="df784-188">Protože pracovní postup dokončí a nepřekračuje nečinnosti za poslední aktivitu `PersistableIdle` obslužná rutina není volána.</span><span class="sxs-lookup"><span data-stu-id="df784-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="df784-189">Ale podobná zpráva se zobrazí v okně Stav podle `Completed` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="df784-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="df784-190">V případě potřeby kód může být přidán do `Completed` obslužnou rutinu k extrakci textu z `StringWriter` a zobrazí se stavové okno.</span><span class="sxs-lookup"><span data-stu-id="df784-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="df784-191">Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, který odpovídá k dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df784-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="df784-192">Pokud jste neprovedli si `InstanceId`, správné sledování souboru lze identifikovat pomocí **datum změny** informace v Průzkumníku Windows.</span><span class="sxs-lookup"><span data-stu-id="df784-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

 <span data-ttu-id="df784-193">**Zadejte prosím číslo mezi 1 a 10**
**5 je příliš vysoká.** 
 **Zadejte prosím číslo mezi 1 a 10**
**3 je příliš vysoká.** 
 **Zadejte prosím číslo mezi 1 a 10**
**1 je příliš nízká.** 
 **Zadejte prosím číslo mezi 1 a 10**
**je 2 správná. Odhadl na oplátku 4.**</span><span class="sxs-lookup"><span data-stu-id="df784-193">**Please enter a number between 1 and 10**
**5 is too high.**
**Please enter a number between 1 and 10**
**3 is too high.**
**Please enter a number between 1 and 10**
**1 is too low.**
**Please enter a number between 1 and 10**
**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="df784-194">Aktualizovaný `WriteLine` výstup je obsažený v souboru sledování, včetně výstup `WriteLine` , který byl přidán v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="df784-194">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="df784-195">Přepněte zpátky na číslo využití aplikace a vyberte jednu z pracovních postupů, které byla spuštěna dříve, než byly provedeny aktualizace.</span><span class="sxs-lookup"><span data-stu-id="df784-195">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="df784-196">Zobrazením pod stavové okno se zobrazí informace o verzi můžete identifikovat verzi aktuálně vybraného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="df784-196">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="df784-197">Zadejte několik pokusů a Všimněte si, že stav aktualizuje shodu `WriteLine` aktivity výstup z předchozí verze a nezahrnují odhad uživatele.</span><span class="sxs-lookup"><span data-stu-id="df784-197">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="df784-198">Důvodem je, že tyto pracovní postupy používají předchozí definice pracovního postupu, který nemá `WriteLine` aktualizace.</span><span class="sxs-lookup"><span data-stu-id="df784-198">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

     <span data-ttu-id="df784-199">V dalším kroku [jak: Aktualizovat definici spuštění instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md), spouštění `v1` instancí pracovních postupů jsou aktualizovány tak, že obsahují nové funkce, jako `v2` instancí.</span><span class="sxs-lookup"><span data-stu-id="df784-199">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
