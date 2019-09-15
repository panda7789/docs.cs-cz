---
title: 'Postupy: Hostování několika verzí pracovního postupu současně'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989647"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="bbd30-102">Postupy: Hostování několika verzí pracovního postupu současně</span><span class="sxs-lookup"><span data-stu-id="bbd30-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="bbd30-103">`WorkflowIdentity`umožňuje vývojářům aplikací pracovních postupů přidružit název a verzi k definici pracovního postupu a tyto informace budou přidruženy k trvalé instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="bbd30-104">Tyto informace o identitě mohou vývojáři aplikací pracovních postupů použít k povolení scénářů, jako je souběžné spouštění více verzí definice pracovního postupu, a poskytuje základní kámen pro jiné funkce, jako je například dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="bbd30-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="bbd30-105">Tento krok v tomto kurzu ukazuje, jak použít `WorkflowIdentity` k hostování více verzí pracovního postupu současně.</span><span class="sxs-lookup"><span data-stu-id="bbd30-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="bbd30-106">Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bbd30-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="bbd30-107">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="bbd30-107">In this topic</span></span>

<span data-ttu-id="bbd30-108">V tomto kroku kurzu `WriteLine` jsou aktivity v pracovním postupu upraveny tak, aby poskytovaly Další informace a přidala se nová `WriteLine` aktivita.</span><span class="sxs-lookup"><span data-stu-id="bbd30-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="bbd30-109">Kopie původního sestavení pracovního postupu je uložena a hostitelská aplikace je aktualizována tak, aby mohla spustit jak původní, tak i aktualizované pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="bbd30-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="bbd30-110">Vytvoření kopie projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="bbd30-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="bbd30-111">Postup aktualizace pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bbd30-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="bbd30-112">Aktualizace pracovního postupu StateMachine</span><span class="sxs-lookup"><span data-stu-id="bbd30-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="bbd30-113">Aktualizace pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="bbd30-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="bbd30-114">Postup aktualizace sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bbd30-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="bbd30-115">Aktualizace WorkflowVersionMap tak, aby zahrnovalo předchozí verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bbd30-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="bbd30-116">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="bbd30-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="bbd30-117">Než budete postupovat podle kroků v tomto tématu, spusťte aplikaci, spusťte několik pracovních postupů každého typu a proveďte jednu nebo dvě odhady pro každé z nich.</span><span class="sxs-lookup"><span data-stu-id="bbd30-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="bbd30-118">V tomto kroku se používají tyto trvalé pracovní postupy a následující krok, [jak: Aktualizuje definici spuštěné instance](how-to-update-the-definition-of-a-running-workflow-instance.md)pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bbd30-119">Každý krok v kurzu Začínáme závisí na předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="bbd30-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="bbd30-120">Pokud jste nedokončili předchozí kroky, můžete si stáhnout dokončenou verzi kurzu z [programovací model Windows Workflow Foundation (WF45) – začínáme kurzu](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bbd30-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

### <a name="BKMK_BackupCopy"></a><span data-ttu-id="bbd30-121">Vytvoření kopie projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="bbd30-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="bbd30-122">Otevřete řešení **WF45GettingStartedTutorial** v aplikaci Visual Studio 2012, pokud není otevřené.</span><span class="sxs-lookup"><span data-stu-id="bbd30-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="bbd30-123">Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="bbd30-123">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="bbd30-124">Zavřete řešení **WF45GettingStartedTutorial** .</span><span class="sxs-lookup"><span data-stu-id="bbd30-124">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="bbd30-125">Otevřete Průzkumníka Windows a přejděte do složky, kde se nachází soubor řešení kurzu a složky projektu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="bbd30-126">Vytvořte novou složku s názvem **PreviousVersions** ve stejné složce jako **NumberGuessWorkflowHost** a **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="bbd30-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="bbd30-127">Tato složka slouží k zahrnutí sestavení, která obsahují různé verze pracovních postupů použitých v následujících krocích kurzu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="bbd30-128">Přejděte do složky **NumberGuessWorkflowActivities\bin\debug** (nebo **bin\Release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="bbd30-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="bbd30-129">Zkopírujte **NumberGuessWorkflowActivities. dll** a vložte ho do složky **PreviousVersions** .</span><span class="sxs-lookup"><span data-stu-id="bbd30-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="bbd30-130">Přejmenujte **NumberGuessWorkflowActivities. dll** ve složce **PreviousVersions** na **NumberGuessWorkflowActivities_v1. dll**.</span><span class="sxs-lookup"><span data-stu-id="bbd30-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bbd30-131">Kroky v tomto tématu ukazují jeden ze způsobů, jak spravovat sestavení používaná k tomu, aby obsahovalo více verzí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="bbd30-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="bbd30-132">Jiné metody, jako je například silné pojmenování sestavení a jejich registrování v globální mezipaměti sestavení (GAC), lze také použít.</span><span class="sxs-lookup"><span data-stu-id="bbd30-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="bbd30-133">Vytvořte novou složku s názvem **NumberGuessWorkflowActivities_du** ve stejné složce jako **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**a nově přidanou složku **PreviousVersions** a zkopírujte všechny soubory a podsložky ze složky **NumberGuessWorkflowActivities** do nové složky **NumberGuessWorkflowActivities_du** .</span><span class="sxs-lookup"><span data-stu-id="bbd30-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="bbd30-134">Tato záložní kopie projektu pro počáteční verzi aktivit se používá v [tématu Postupy: Aktualizuje definici spuštěné instance](how-to-update-the-definition-of-a-running-workflow-instance.md)pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="bbd30-135">Znovu otevřete řešení **WF45GettingStartedTutorial** v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="bbd30-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a><span data-ttu-id="bbd30-136">Postup aktualizace pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bbd30-136">To update the workflows</span></span>

<span data-ttu-id="bbd30-137">V této části se aktualizují definice pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="bbd30-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="bbd30-138">Dvě `WriteLine` aktivity, které poskytují zpětnou vazbu na odhad uživatele, se aktualizují a přidají se nové `WriteLine` aktivity, které po odhadu tohoto počtu poskytují další informace o hře.</span><span class="sxs-lookup"><span data-stu-id="bbd30-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a><span data-ttu-id="bbd30-139">Aktualizace pracovního postupu StateMachine</span><span class="sxs-lookup"><span data-stu-id="bbd30-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="bbd30-140">V **Průzkumník řešení**v projektu **NumberGuessWorkflowActivities** poklikejte na **StateMachineNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bbd30-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="bbd30-141">Dvakrát klikněte na **odhad nesprávného** přechodu na stavovém počítači.</span><span class="sxs-lookup"><span data-stu-id="bbd30-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="bbd30-142">Aktualizuje v `If` aktivitě levou stranu `WriteLine`. `Text`</span><span class="sxs-lookup"><span data-stu-id="bbd30-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="bbd30-143">Aktualizujte `WriteLine` v`If`aktivitěnejvícevpravo. `Text`</span><span class="sxs-lookup"><span data-stu-id="bbd30-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="bbd30-144">Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="bbd30-145">Dvakrát klikněte na **odhad správného** přechodu na Stavový počítač.</span><span class="sxs-lookup"><span data-stu-id="bbd30-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="bbd30-146">Přetáhněte aktivitu **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji na **aktivitu akce přetažení** na tento přechod.</span><span class="sxs-lookup"><span data-stu-id="bbd30-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="bbd30-147">Do `Text` pole vlastností zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="bbd30-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a><span data-ttu-id="bbd30-148">Aktualizace pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="bbd30-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="bbd30-149">V **Průzkumník řešení**v projektu **NumberGuessWorkflowActivities** poklikejte na **FlowchartNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bbd30-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="bbd30-150">Aktualizuje aktivitu nejvíce `WriteLine`vlevo. `Text`</span><span class="sxs-lookup"><span data-stu-id="bbd30-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="bbd30-151">Aktualizujte aktivitu, která je nejvíce `WriteLine` vpravo. `Text`</span><span class="sxs-lookup"><span data-stu-id="bbd30-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="bbd30-152">Přetáhněte aktivitu **WriteLine** z oddílu **primitivs** v **sadě nástrojů** a umístěte ji na místo odkládacího bodu `True` pro akci na nejvyšší `FlowDecision`úrovni.</span><span class="sxs-lookup"><span data-stu-id="bbd30-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="bbd30-153">Aktivita se přidá do vývojového diagramu a propojí `True` se s akcí `FlowDecision`. `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="bbd30-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="bbd30-154">Do `Text` pole vlastností zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="bbd30-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a><span data-ttu-id="bbd30-155">Postup aktualizace sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bbd30-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="bbd30-156">V **Průzkumník řešení**v projektu **NumberGuessWorkflowActivities** poklikejte na **SequentialNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bbd30-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="bbd30-157">Aktualizuje v `If` aktivitě levou stranu `WriteLine`. `Text`</span><span class="sxs-lookup"><span data-stu-id="bbd30-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="bbd30-158">Aktualizujte `WriteLine` aktivitu`If` na nejvyšší úrovni aktivity. `Text`</span><span class="sxs-lookup"><span data-stu-id="bbd30-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="bbd30-159">Přetáhněte aktivitu **WriteLine** z oddílu **primitivs** v **sadě nástrojů** a umístěte ji za aktivitu **DoWhile** , aby byla **WriteLine** koncová aktivita v kořenové `Sequence` aktivitě.</span><span class="sxs-lookup"><span data-stu-id="bbd30-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="bbd30-160">Do `Text` pole vlastností zadejte následující výraz.</span><span class="sxs-lookup"><span data-stu-id="bbd30-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a><span data-ttu-id="bbd30-161">Aktualizace WorkflowVersionMap tak, aby zahrnovalo předchozí verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bbd30-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="bbd30-162">Poklikejte na **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap. vb**) v rámci projektu **NumberGuessWorkflowHost** a otevřete ho.</span><span class="sxs-lookup"><span data-stu-id="bbd30-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="bbd30-163">Do horní části `using` souboru `Imports` `using` přidejtenásledujícípříkazy`Imports`(nebo).</span><span class="sxs-lookup"><span data-stu-id="bbd30-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="bbd30-164">Přidejte tři nové identity pracovního postupu hned pod tři existující deklarace identity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="bbd30-165">Tyto nové `v1` identity pracovního postupu budou použity k zajištění správné definice pracovního postupu pro pracovní postupy zahájené před provedením aktualizací.</span><span class="sxs-lookup"><span data-stu-id="bbd30-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

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

4. <span data-ttu-id="bbd30-166">V konstruktoru aktualizujte vlastnost tří aktuálních identit pracovního postupu na `2.0.0.0`. `Version` `WorkflowVersionMap`</span><span class="sxs-lookup"><span data-stu-id="bbd30-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

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

    <span data-ttu-id="bbd30-167">Kód v, který přidá aktuální verze pracovních postupů do slovníku, používá aktuální verze, které jsou odkazovány v projektu, takže kód, který inicializuje definice pracovního postupu, není nutné aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="bbd30-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="bbd30-168">Přidejte následující kód do konstruktoru hned za kód, který přidá aktuální verze do slovníku.</span><span class="sxs-lookup"><span data-stu-id="bbd30-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

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

    <span data-ttu-id="bbd30-169">Tyto identity pracovního postupu jsou přidruženy k počáteční verzi odpovídajících definicí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="bbd30-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="bbd30-170">Dále načtěte sestavení, které obsahuje počáteční verzi definice pracovního postupu, a vytvořte a přidejte odpovídající definice pracovního postupu do slovníku.</span><span class="sxs-lookup"><span data-stu-id="bbd30-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

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

    <span data-ttu-id="bbd30-171">Následující příklad je úplným seznamem pro aktualizovanou `WorkflowVersionMap` třídu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

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

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="bbd30-172">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="bbd30-172">To build and run the application</span></span>

1. <span data-ttu-id="bbd30-173">Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci a spusťte klávesovou zkratku CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bbd30-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="bbd30-174">Kliknutím na **Nová hra**spusťte nový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="bbd30-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="bbd30-175">Verze pracovního postupu se zobrazí v okně stav a v případě, že se aktualizuje aktualizovaná verze z `WorkflowIdentity`přidruženého.</span><span class="sxs-lookup"><span data-stu-id="bbd30-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="bbd30-176">Poznamenejte si, `InstanceId` abyste mohli zobrazit soubor sledování pracovního postupu po jeho dokončení a pak zadat odhad, dokud se hra nedokončí.</span><span class="sxs-lookup"><span data-stu-id="bbd30-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="bbd30-177">Všimněte si, jak se zobrazí odhad uživatele v informacích zobrazených v okně stav na základě aktualizací `WriteLine` aktivit.</span><span class="sxs-lookup"><span data-stu-id="bbd30-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > <span data-ttu-id="bbd30-178">Zobrazí se aktualizovaný text z `WriteLine` aktivit, ale výstup konečné `WriteLine` aktivity, která byla přidána v tomto tématu, není.</span><span class="sxs-lookup"><span data-stu-id="bbd30-178">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="bbd30-179">Důvodem je, že okno stavu je aktualizováno `PersistableIdle` obslužnou rutinou.</span><span class="sxs-lookup"><span data-stu-id="bbd30-179">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="bbd30-180">Protože pracovní postup skončí a nepracuje po konečné aktivitě, `PersistableIdle` obslužná rutina není volána.</span><span class="sxs-lookup"><span data-stu-id="bbd30-180">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="bbd30-181">Nicméně podobná zpráva se zobrazí v okně `Completed` stav obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="bbd30-181">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="bbd30-182">V případě potřeby lze kód přidat k `Completed` obslužné rutině pro extrakci textu z okna `StringWriter` a jeho zobrazení do stavového okna.</span><span class="sxs-lookup"><span data-stu-id="bbd30-182">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="bbd30-183">Otevřete Průzkumníka Windows a přejděte do složky **NumberGuessWorkflowHost\bin\debug** (nebo **bin\Release** v závislosti na nastavení projektu) a otevřete sledovací soubor pomocí poznámkového bloku, který odpovídá dokončenému pracovnímu postupu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="bbd30-184">Pokud jste si poznamenali `InstanceId`, že se vám nepovedlo poznamenat, můžete pomocí informací o **změně data** v Průzkumníkovi Windows určit správný sledovací soubor.</span><span class="sxs-lookup"><span data-stu-id="bbd30-184">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="bbd30-185">Aktualizovaný `WriteLine` výstup je obsažen v souboru sledování, včetně výstupu `WriteLine` , který byl přidán v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="bbd30-185">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="bbd30-186">Přepněte zpět na číslo odhadované aplikace a vyberte jeden z pracovních postupů, které byly spuštěny před provedením aktualizací.</span><span class="sxs-lookup"><span data-stu-id="bbd30-186">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="bbd30-187">Verzi aktuálně vybraného pracovního postupu můžete zjistit tak, že prohlížíte informace o verzi zobrazené pod oknem stav.</span><span class="sxs-lookup"><span data-stu-id="bbd30-187">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="bbd30-188">Zadejte několik odhadů a Všimněte si, že se aktualizace stavu `WriteLine` shodují s výstupem aktivity z předchozí verze a nezahrnují odhad uživatele.</span><span class="sxs-lookup"><span data-stu-id="bbd30-188">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="bbd30-189">Důvodem je, že tyto pracovní postupy používají definici předchozí pracovní postup, která `WriteLine` nemá aktualizace.</span><span class="sxs-lookup"><span data-stu-id="bbd30-189">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="bbd30-190">V dalším kroku [: Aktualizujte definici spuštěné instance](how-to-update-the-definition-of-a-running-workflow-instance.md)pracovního postupu, spuštěné `v1` instance pracovního postupu se aktualizují, aby obsahovaly nové funkce jako `v2` instance.</span><span class="sxs-lookup"><span data-stu-id="bbd30-190">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
