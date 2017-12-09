---
title: "Postupy: hostování více verzí pracovní postup-souběžného"
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
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f6fa267e6400672328714f016a5823d8f1311aa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="e7294-102">Postupy: hostování více verzí pracovní postup-souběžného</span><span class="sxs-lookup"><span data-stu-id="e7294-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
<span data-ttu-id="e7294-103">`WorkflowIdentity`umožňuje vývojářům aplikací pracovního postupu pro definici pracovního postupu přidružení název a verzi a pro tyto informace k být přidružen k instanci pracovního postupu trvalý.</span><span class="sxs-lookup"><span data-stu-id="e7294-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="e7294-104">Tyto informace identity lze použít vývojáři aplikace pracovního postupu povolit scénáře, jako je vedle sebe spouštění více verzí definice pracovního postupu a poskytuje základním kamenem pro další funkce, jako je například dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="e7294-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="e7294-105">Tento krok v tomto kurzu ukazuje, jak používat `WorkflowIdentity` k hostování více verzí pracovního postupu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="e7294-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7294-106">Stažení dokončené verze nebo zobrazení na video s návodem kurzu, najdete v tématu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e7294-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="e7294-107">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="e7294-107">In this topic</span></span>  
 <span data-ttu-id="e7294-108">V tomto kroku kurzu `WriteLine` aktivitám v pracovním postupu jsou upravit tak, aby poskytují další informace a nové `WriteLine` je přidána.</span><span class="sxs-lookup"><span data-stu-id="e7294-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="e7294-109">Je uložená kopie původní sestavení pracovního postupu, a hostitel bude aktualizována tak, aby ho původní i aktualizované pracovních postupů ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="e7294-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="e7294-110">Vytvořit kopii NumberGuessWorkflowActivities projektu</span><span class="sxs-lookup"><span data-stu-id="e7294-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="e7294-111">Chcete-li aktualizovat pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e7294-111">To update the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="e7294-112">Chcete-li aktualizovat StateMachine pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e7294-112">To update the StateMachine workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="e7294-113">Chcete-li aktualizovat vývojový diagram pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e7294-113">To update the Flowchart workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="e7294-114">Chcete-li aktualizovat sekvenční pracovní postup</span><span class="sxs-lookup"><span data-stu-id="e7294-114">To update the Sequential workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="e7294-115">Chcete-li aktualizovat WorkflowVersionMap zahrnující předchozí verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e7294-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="e7294-116">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e7294-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="e7294-117">Před postupovat podle kroků v tomto tématu, aplikaci spustit, spusťte několik pracovních postupů každého typu a provedení jednoho nebo dvou pokusů u každé z nich.</span><span class="sxs-lookup"><span data-stu-id="e7294-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="e7294-118">Tyto trvalou pracovní postupy se používají v tomto kroku a následující krok, [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="e7294-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7294-119">Každý krok v tomto kurzu Začínáme závisí na předchozí kroky.</span><span class="sxs-lookup"><span data-stu-id="e7294-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="e7294-120">Pokud jste neprovedli předchozí kroky můžete stáhnout dokončenou verzi kurzem z [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e7294-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
###  <a name="BKMK_BackupCopy"></a><span data-ttu-id="e7294-121">Vytvořit kopii NumberGuessWorkflowActivities projektu</span><span class="sxs-lookup"><span data-stu-id="e7294-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1.  <span data-ttu-id="e7294-122">Otevřete **WF45GettingStartedTutorial** řešení v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Pokud není otevřen.</span><span class="sxs-lookup"><span data-stu-id="e7294-122">Open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] if it is not open.</span></span>  
  
2.  <span data-ttu-id="e7294-123">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="e7294-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="e7294-124">Zavřít **WF45GettingStartedTutorial** řešení.</span><span class="sxs-lookup"><span data-stu-id="e7294-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4.  <span data-ttu-id="e7294-125">Otevřete Průzkumníka Windows a přejděte do složky, kde se nachází soubor kurz řešení a projektu složky.</span><span class="sxs-lookup"><span data-stu-id="e7294-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5.  <span data-ttu-id="e7294-126">Vytvořte novou složku s názvem **PreviousVersions** ve stejné složce jako **NumberGuessWorkflowHost** a **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="e7294-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="e7294-127">Tato složka se používá k obsahovat sestavení, které obsahují různé verze použit v následné kroky kurzu pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e7294-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6.  <span data-ttu-id="e7294-128">Přejděte na **NumberGuessWorkflowActivities\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="e7294-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="e7294-129">Kopírování **NumberGuessWorkflowActivities.dll** a vložte ji do **PreviousVersions** složky.</span><span class="sxs-lookup"><span data-stu-id="e7294-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7.  <span data-ttu-id="e7294-130">Přejmenování **NumberGuessWorkflowActivities.dll** v **PreviousVersions** složku pro **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="e7294-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7294-131">Kroky v tomto tématu ukazují jeden způsob, jak spravovat sestavení obsahuje více verzí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e7294-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="e7294-132">Může také použít jiné metody, jako je například silné názvy sestavení a jejich registrace v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7294-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>  
  
8.  <span data-ttu-id="e7294-133">Vytvořte novou složku s názvem **NumberGuessWorkflowActivities_du** ve stejné složce jako **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**a nově Přidat **PreviousVersions** složku a zkopírujte všechny soubory a podsložky ze **NumberGuessWorkflowActivities** složky do nové  **NumberGuessWorkflowActivities_du** složky.</span><span class="sxs-lookup"><span data-stu-id="e7294-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="e7294-134">Tento záložní kopii projekt pro počáteční verze aktivity se používá v [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="e7294-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
9. <span data-ttu-id="e7294-135">Znovu ho otevřete **WF45GettingStartedTutorial** řešení v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7294-135">Re-open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
###  <a name="BKMK_UpdateWorkflows"></a><span data-ttu-id="e7294-136">Chcete-li aktualizovat pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e7294-136">To update the workflows</span></span>  
 <span data-ttu-id="e7294-137">V této části jsou aktualizované definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e7294-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="e7294-138">Dva `WriteLine` aktivity, které váš názor na odhad uživatele jsou aktualizované a nové `WriteLine` aktivity se přidá, který poskytuje další informace o hry, jakmile je uhádnout číslo.</span><span class="sxs-lookup"><span data-stu-id="e7294-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>  
  
####  <a name="BKMK_UpdateStateMachine"></a><span data-ttu-id="e7294-139">Chcete-li aktualizovat StateMachine pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e7294-139">To update the StateMachine workflow</span></span>  
  
1.  <span data-ttu-id="e7294-140">V **Průzkumníku řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="e7294-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="e7294-141">Dvakrát klikněte **uhodnout nesprávné** přechod na stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="e7294-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>  
  
3.  <span data-ttu-id="e7294-142">Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  <span data-ttu-id="e7294-143">Aktualizace `Text` z nejvíce vpravo `WriteLine` v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  <span data-ttu-id="e7294-144">Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e7294-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
6.  <span data-ttu-id="e7294-145">Dvakrát klikněte **uhodnout správné** přechod na stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="e7294-145">Double-click the **Guess Correct** transition on the state machine.</span></span>  
  
7.  <span data-ttu-id="e7294-146">Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** na **vyřadit akce aktivity sem** popisek Přechod.</span><span class="sxs-lookup"><span data-stu-id="e7294-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>  
  
8.  <span data-ttu-id="e7294-147">Zadejte následující výraz do `Text` pole vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7294-147">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a><span data-ttu-id="e7294-148">Chcete-li aktualizovat vývojový diagram pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e7294-148">To update the Flowchart workflow</span></span>  
  
1.  <span data-ttu-id="e7294-149">V **Průzkumníku řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **FlowchartNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="e7294-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="e7294-150">Aktualizace `Text` z nejvíce vlevo `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="e7294-151">Aktualizace `Text` z nejvíce vpravo `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="e7294-152">Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej v bodě rozevírací `True` akce nejhornější `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="e7294-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="e7294-153">`WriteLine` Aktivity je přidán do vývojový diagram a propojit s `True` akce `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="e7294-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>  
  
5.  <span data-ttu-id="e7294-154">Zadejte následující výraz do `Text` pole vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7294-154">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a><span data-ttu-id="e7294-155">Chcete-li aktualizovat sekvenční pracovní postup</span><span class="sxs-lookup"><span data-stu-id="e7294-155">To update the Sequential workflow</span></span>  
  
1.  <span data-ttu-id="e7294-156">V **Průzkumníku řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **SequentialNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="e7294-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="e7294-157">Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="e7294-158">Aktualizace `Text` z nejvíce vpravo `WriteLine` aktivity v `If` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="e7294-159">Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej po **DoWhile** aktivity tak, aby  **WriteLine** je poslední aktivita v kořenu `Sequence` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>  
  
5.  <span data-ttu-id="e7294-160">Zadejte následující výraz do `Text` pole vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7294-160">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a><span data-ttu-id="e7294-161">Chcete-li aktualizovat WorkflowVersionMap zahrnující předchozí verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e7294-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>  
  
1.  <span data-ttu-id="e7294-162">Klikněte dvakrát na **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projektu ho otevřete.</span><span class="sxs-lookup"><span data-stu-id="e7294-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
2.  <span data-ttu-id="e7294-163">Přidejte následující `using` (nebo `Imports`) příkazů do horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="e7294-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="e7294-164">Přidejte tři nové identity pracovního postupu pod tři existující deklarace identity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e7294-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="e7294-165">Tyto nové `v1` pracovního postupu se použije identity zadejte definice pracovního postupu správné před byly provedeny aktualizace spustit pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="e7294-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>  
  
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
  
4.  <span data-ttu-id="e7294-166">V `WorkflowVersionMap` konstruktor, aktualizovat `Version` vlastnost tři aktuální identit pracovního postupu, které `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="e7294-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>  
  
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
  
     <span data-ttu-id="e7294-167">Kód v tom, že přidá aktuální verze pracovních postupů do slovníku používá aktuální verze, které se odkazuje v projektu, takže není nutné aktualizovat kód, který inicializuje definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e7294-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>  
  
5.  <span data-ttu-id="e7294-168">Přidejte následující kód bezprostředně za kód, který přidá do slovníku aktuální verze v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e7294-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>  
  
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
  
     <span data-ttu-id="e7294-169">Tyto pracovní postup identity jsou přidruženy k počáteční verze odpovídající definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e7294-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>  
  
6.  <span data-ttu-id="e7294-170">V dalším kroku načíst sestavení, které obsahuje počáteční verze definice pracovního postupu, a vytvořit a přidat odpovídající definice pracovního postupu do slovníku.</span><span class="sxs-lookup"><span data-stu-id="e7294-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>  
  
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
  
     <span data-ttu-id="e7294-171">V následujícím příkladu je úplný seznam pro aktualizaci `WorkflowVersionMap` třídy.</span><span class="sxs-lookup"><span data-stu-id="e7294-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a><span data-ttu-id="e7294-172">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e7294-172">To build and run the application</span></span>  
  
1.  <span data-ttu-id="e7294-173">Stisknutím kombinace kláves CTRL + SHIFT + B pro sestavení aplikace a potom CTRL + F5 a spusťte.</span><span class="sxs-lookup"><span data-stu-id="e7294-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>  
  
2.  <span data-ttu-id="e7294-174">Spuštění nového pracovního postupu kliknutím **novou hru**.</span><span class="sxs-lookup"><span data-stu-id="e7294-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="e7294-175">Verze pracovního postupu se zobrazí v okně Stav a odráží aktualizovanou verzi z přidruženého `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="e7294-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="e7294-176">Poznamenejte si `InstanceId` vám umožní zobrazit soubor sledování pro pracovní postup po dokončení, a pak zadejte pokusů, dokud se nedokončí hra.</span><span class="sxs-lookup"><span data-stu-id="e7294-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="e7294-177">Všimněte si, jak odhad uživatele se zobrazí v informace zobrazené v okně Stav na základě aktualizací do `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e7294-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>  
  
 <span data-ttu-id="e7294-178">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="e7294-178">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e7294-179">**5 je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="e7294-179">**5 is too high.** </span></span>  
<span data-ttu-id="e7294-180">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="e7294-180">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e7294-181">**3 je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="e7294-181">**3 is too high.** </span></span>  
<span data-ttu-id="e7294-182">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="e7294-182">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e7294-183">**1 je příliš nízká.** </span><span class="sxs-lookup"><span data-stu-id="e7294-183">**1 is too low.** </span></span>  
<span data-ttu-id="e7294-184">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="e7294-184">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e7294-185">**Blahopřejeme, uhádnout číslo na oplátku 4.**</span><span class="sxs-lookup"><span data-stu-id="e7294-185">**Congratulations, you guessed the number in 4 turns.**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="e7294-186">Aktualizovaný text z `WriteLine` aktivity se zobrazí, ale výstup konečné `WriteLine` aktivity, která byla přidána v tomto tématu není.</span><span class="sxs-lookup"><span data-stu-id="e7294-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="e7294-187">Je to způsobeno okně Stav se aktualizuje `PersistableIdle` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="e7294-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="e7294-188">Protože pracovní postup dokončení a nepřekračuje nečinnosti za poslední aktivitu `PersistableIdle` není volána obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="e7294-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="e7294-189">Ale podobná zpráva se zobrazí v okně Stav pomocí `Completed` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="e7294-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="e7294-190">V případě potřeby kódu nebylo možné přidat do `Completed` obslužná rutina rozbalte text z `StringWriter` a zobrazit ji do okna stav.</span><span class="sxs-lookup"><span data-stu-id="e7294-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>  
  
3.  <span data-ttu-id="e7294-191">Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, která odpovídá dokončené pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e7294-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="e7294-192">Pokud jste neprovedli poznámku o `InstanceId`, správné sledování souborů můžete identifikovat pomocí **datum změny** informace v Průzkumníku Windows.</span><span class="sxs-lookup"><span data-stu-id="e7294-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>  
  
 <span data-ttu-id="e7294-193">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="e7294-193">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e7294-194">**5 je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="e7294-194">**5 is too high.** </span></span>  
<span data-ttu-id="e7294-195">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="e7294-195">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e7294-196">**3 je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="e7294-196">**3 is too high.** </span></span>  
<span data-ttu-id="e7294-197">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="e7294-197">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e7294-198">**1 je příliš nízká.** </span><span class="sxs-lookup"><span data-stu-id="e7294-198">**1 is too low.** </span></span>  
<span data-ttu-id="e7294-199">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="e7294-199">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e7294-200">**2 je správná. Uhádnout na oplátku 4.**</span><span class="sxs-lookup"><span data-stu-id="e7294-200">**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="e7294-201">Aktualizovaný `WriteLine` výstup je obsažený v souboru sledování, včetně výstup `WriteLine` který byl přidán v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e7294-201">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>  
  
4.  <span data-ttu-id="e7294-202">Přepněte zpět na číslo hádání aplikace a vyberte jednu z pracovních postupů, které byla zahájena před aktualizací byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="e7294-202">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="e7294-203">Verzi aktuálně vybrané pracovní postup můžete identifikovat pohledem na informace o verzi, který se zobrazí pod stavové okno.</span><span class="sxs-lookup"><span data-stu-id="e7294-203">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="e7294-204">Zadejte některé pokusů a Všimněte si, že stav aktualizace shoda `WriteLine` aktivita výstup z předchozí verze a nezahrnují odhad uživatele.</span><span class="sxs-lookup"><span data-stu-id="e7294-204">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="e7294-205">Důvodem je, že tyto pracovní postupy používají předchozí definice pracovního postupu, který nemá `WriteLine` aktualizace.</span><span class="sxs-lookup"><span data-stu-id="e7294-205">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>  
  
     <span data-ttu-id="e7294-206">V dalším kroku [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), na kterém běží `v1` instancí pracovních postupů jsou aktualizovány tak, že obsahují nové funkce, jako `v2` instance.</span><span class="sxs-lookup"><span data-stu-id="e7294-206">In the next step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
