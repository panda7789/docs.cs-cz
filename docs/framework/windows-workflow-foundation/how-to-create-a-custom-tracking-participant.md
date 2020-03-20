---
title: 'Postupy: Vytvoření vlastního účastníka sledování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: ea7a598a73f131d8ee33e285a39173fbf84a97f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182909"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="4debe-102">Postupy: Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="4debe-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="4debe-103">Sledování pracovního postupu poskytuje přehled o stavu provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4debe-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="4debe-104">Za běhu pracovního postupu vyzařuje záznamy sledování, které popisují události životního cyklu pracovního postupu, události životního cyklu aktivity, obnovení záložek a poruchy.</span><span class="sxs-lookup"><span data-stu-id="4debe-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="4debe-105">Tyto záznamy sledování jsou spotřebovány sledování účastníků.</span><span class="sxs-lookup"><span data-stu-id="4debe-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="4debe-106">Windows Workflow Foundation (WF) zahrnuje standardní sledování účastníka, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="4debe-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="4debe-107">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="4debe-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="4debe-108">Tento krok kurzu popisuje, jak vytvořit vlastní sledování účastníka `WriteLine` a sledování profilu, které zachycují výstup aktivit tak, aby mohly být zobrazeny uživateli.</span><span class="sxs-lookup"><span data-stu-id="4debe-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4debe-109">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="4debe-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="4debe-110">Chcete-li toto téma dokončit, musíte nejprve dokončit předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="4debe-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="4debe-111">Pokud chcete stáhnout dokončenou verzi nebo zobrazit video návod k kurzu, přečtěte si část [Windows Workflow Foundation (WF45) – Kurz začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="4debe-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="4debe-112">Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="4debe-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="4debe-113">Klepněte pravým tlačítkem myši na **numberguessWorkflowHost** v **Průzkumníku řešení** a zvolte **Přidat**, **Třída**.</span><span class="sxs-lookup"><span data-stu-id="4debe-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="4debe-114">Zadejte `StatusTrackingParticipant` do pole **Název** a klepněte na **tlačítko Přidat**.</span><span class="sxs-lookup"><span data-stu-id="4debe-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="4debe-115">Přidejte `using` následující `Imports`příkazy (nebo ) v horní `using` části `Imports`souboru s ostatními příkazy (nebo ).</span><span class="sxs-lookup"><span data-stu-id="4debe-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="4debe-116">Upravte `StatusTrackingParticipant` třídu tak, `TrackingParticipant`aby dědí z .</span><span class="sxs-lookup"><span data-stu-id="4debe-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="4debe-117">Přidejte `Track` následující přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="4debe-117">Add the following `Track` method override.</span></span> <span data-ttu-id="4debe-118">Existuje několik různých typů záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="4debe-118">There are several different types of tracking records.</span></span> <span data-ttu-id="4debe-119">Máme zájem o výstup `WriteLine` y aktivit, které jsou obsaženy v záznamech sledování aktivit.</span><span class="sxs-lookup"><span data-stu-id="4debe-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="4debe-120">Pokud `TrackingRecord` je `ActivityTrackingRecord` pro `WriteLine` aktivitu, `Text` je `WriteLine` připojen k souboru pojmenované `InstanceId` po pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4debe-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="4debe-121">V tomto kurzu je soubor uložen do aktuální složky hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="4debe-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="4debe-122">Pokud není zadán žádný profil sledování, použije se výchozí profil sledování.</span><span class="sxs-lookup"><span data-stu-id="4debe-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="4debe-123">Při použití výchozího profilu sledování jsou záznamy `ActivityStates`sledování vyzařovány pro všechny .</span><span class="sxs-lookup"><span data-stu-id="4debe-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="4debe-124">Vzhledem k tomu, že potřebujeme zachytit text `WriteLine` pouze jednou během životního cyklu `ActivityStates.Executing` aktivity, extrahujeme pouze text ze stavu.</span><span class="sxs-lookup"><span data-stu-id="4debe-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="4debe-125">[Chcete-li vytvořit profil sledování a zaregistrovat účastníka sledování](#to-create-the-tracking-profile-and-register-the-tracking-participant), `WriteLine` `ActivityStates.Executing` je vytvořen profil sledování, který určuje, že jsou emitovány pouze záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="4debe-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="4debe-126">Vytvoření profilu sledování a registrace účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="4debe-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="4debe-127">Klepněte pravým tlačítkem myši na **příkaz WorkflowHostForm** v **Průzkumníku řešení** a zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="4debe-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="4debe-128">Přidejte `using` následující `Imports`příkaz (nebo ) v horní `using` části `Imports`souboru s ostatními příkazy (nebo ).</span><span class="sxs-lookup"><span data-stu-id="4debe-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="4debe-129">Přidejte následující `ConfigureWorkflowApplication` kód těsně za kód, který přidá `StringWriter` rozšíření pracovního postupu a před obslužné rutiny životního cyklu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4debe-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="4debe-130">Tento profil sledování určuje, že `WriteLine` pouze záznamy `Executing` stavu aktivity pro aktivity ve stavu jsou vydávány pro vlastní sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="4debe-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="4debe-131">Po přidání kódu bude `ConfigureWorkflowApplication` začátek vypadat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4debe-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="4debe-132">Zobrazení informací o sledování</span><span class="sxs-lookup"><span data-stu-id="4debe-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="4debe-133">Klepněte pravým tlačítkem myši na **příkaz WorkflowHostForm** v **Průzkumníku řešení** a zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="4debe-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="4debe-134">Do `InstanceId_SelectedIndexChanged` obslužné rutiny přidejte následující kód ihned za kód, který vymaže stavové okno.</span><span class="sxs-lookup"><span data-stu-id="4debe-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="4debe-135">Pokud je v seznamu pracovních postupů vybrán nový pracovní postup, záznamy sledování pro tento pracovní postup se načtou a zobrazí ve stavovém okně.</span><span class="sxs-lookup"><span data-stu-id="4debe-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="4debe-136">Následující příklad je `InstanceId_SelectedIndexChanged` dokončená obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="4debe-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="4debe-137">Vytvoření a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="4debe-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="4debe-138">Stisknutím kláves Ctrl+Shift+B vytvořte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4debe-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="4debe-139">Stisknutím kláves Ctrl+F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4debe-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="4debe-140">Vyberte rozsah pro hádanku a typ pracovního postupu, který chcete spustit, a klepněte na tlačítko **Nová hra**.</span><span class="sxs-lookup"><span data-stu-id="4debe-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="4debe-141">Zadejte do pole **Odhad** odhad a kliknutím na **Přejít** odešlete svůj odhad.</span><span class="sxs-lookup"><span data-stu-id="4debe-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="4debe-142">Všimněte si, že stav pracovního postupu se zobrazí ve stavovém okně.</span><span class="sxs-lookup"><span data-stu-id="4debe-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="4debe-143">Tento výstup je zachycen `WriteLine` z aktivit.</span><span class="sxs-lookup"><span data-stu-id="4debe-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="4debe-144">Přepněte do jiného pracovního postupu tak, že vyberete jeden z pole se seznamem **Id instance pracovního postupu** a všimněte si, že se odebere stav aktuálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4debe-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="4debe-145">Přepněte zpět na předchozí pracovní postup a všimněte si, že stav je obnoven, podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4debe-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4debe-146">Pokud přepnete na pracovní postup, který byl spuštěn před povolením sledování, nezobrazí se žádný stav.</span><span class="sxs-lookup"><span data-stu-id="4debe-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="4debe-147">Pokud však provedete další odhady, jejich stav se uloží, protože sledování je nyní povoleno.</span><span class="sxs-lookup"><span data-stu-id="4debe-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="4debe-148">Tyto informace jsou užitečné pro určení rozsahu náhodného čísla, ale neobsahují žádné informace o tom, jaké odhady byly dříve provedeny.</span><span class="sxs-lookup"><span data-stu-id="4debe-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="4debe-149">Tyto informace jsou v dalším [kroku: Host více verzí pracovního postupu vedle sebe](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="4debe-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="4debe-150">Poznamenejte si ID instance pracovního postupu a přehrajte hru až do jejího dokončení.</span><span class="sxs-lookup"><span data-stu-id="4debe-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="4debe-151">Otevřete Průzkumníka Windows a přejděte do složky **NumberGuessWorkflowHost\bin\debug** (nebo **bin\release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="4debe-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="4debe-152">Všimněte si, že kromě spustitelných souborů projektu existují soubory s názvy souborů GUID.</span><span class="sxs-lookup"><span data-stu-id="4debe-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="4debe-153">Identifikujte ten, který odpovídá ID instance pracovního postupu z dokončeného pracovního postupu v předchozím kroku, a otevřete ho v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="4debe-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="4debe-154">Informace o sledování obsahují informace podobné následujícím.</span><span class="sxs-lookup"><span data-stu-id="4debe-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="4debe-155">Kromě absence dohadů uživatele tato data sledování neobsahuje informace o konečném odhadu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4debe-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="4debe-156">Důvodem je, že informace o `WriteLine` sledování se skládá pouze z výstupu z pracovního `Completed` postupu a poslední zpráva, která se zobrazí, se provádí z obslužné rutiny po dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4debe-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="4debe-157">V dalším kroku [kurzu, Jak: Host více verzí pracovního postupu side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existující `WriteLine` aktivity jsou upraveny `WriteLine` tak, aby zobrazení odhady uživatele a další aktivita je přidána, která zobrazuje konečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="4debe-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="4debe-158">Po integraci těchto [změn: Hostování více verzí pracovního postupu vedle sebe](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) ukazuje, jak hostovat více verzí pracovního postupu současně.</span><span class="sxs-lookup"><span data-stu-id="4debe-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
