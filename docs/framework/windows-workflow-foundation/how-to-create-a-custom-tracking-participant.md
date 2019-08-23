---
title: 'Postupy: Vytvoření vlastního účastníka sledování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 280f68c8b762562a56ce96f45f118702fb0e4d76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962404"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="426b9-102">Postupy: Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="426b9-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="426b9-103">Sledování pracovního postupu nabízí přehled o stavu provádění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="426b9-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="426b9-104">Modul runtime pracovního postupu generuje záznamy sledování, které popisují události životního cyklu pracovního postupu, události životního cyklu aktivity, obnovení záložek a chyby.</span><span class="sxs-lookup"><span data-stu-id="426b9-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="426b9-105">Tyto záznamy sledování se spotřebují sledováním účastníků.</span><span class="sxs-lookup"><span data-stu-id="426b9-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="426b9-106">Programovací model Windows Workflow Foundation (WF) zahrnuje standardního účastníka sledování, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="426b9-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="426b9-107">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="426b9-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="426b9-108">Tento krok kurzu popisuje, jak vytvořit vlastního účastníka sledování a profil sledování, který zachycuje výstup `WriteLine` aktivit, aby je bylo možné zobrazit uživateli.</span><span class="sxs-lookup"><span data-stu-id="426b9-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="426b9-109">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="426b9-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="426b9-110">Chcete-li dokončit toto téma, je nutné nejprve dokončit předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="426b9-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="426b9-111">Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="426b9-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="426b9-112">Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="426b9-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="426b9-113">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Třída**.</span><span class="sxs-lookup"><span data-stu-id="426b9-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="426b9-114">Do `StatusTrackingParticipant` pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="426b9-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="426b9-115">Do horní části `using` souboru přidejte `Imports`následující příkazy (nebo), které budou `using` příkazy (nebo `Imports`).</span><span class="sxs-lookup"><span data-stu-id="426b9-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="426b9-116">Upravte třídu tak, aby dědila z `TrackingParticipant`. `StatusTrackingParticipant`</span><span class="sxs-lookup"><span data-stu-id="426b9-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4. <span data-ttu-id="426b9-117">Přidejte následující `Track` přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="426b9-117">Add the following `Track` method override.</span></span> <span data-ttu-id="426b9-118">Existuje několik různých typů záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="426b9-118">There are several different types of tracking records.</span></span> <span data-ttu-id="426b9-119">Zajímá Vás výstup `WriteLine` aktivit, které jsou obsaženy v záznamech sledování aktivit.</span><span class="sxs-lookup"><span data-stu-id="426b9-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="426b9-120">`TrackingRecord` Pokud `InstanceId` je aktivita`WriteLine` pro aktivitu, jepřipojenksouborusnázvemzapracovnípostup.`WriteLine` `Text` `ActivityTrackingRecord`</span><span class="sxs-lookup"><span data-stu-id="426b9-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="426b9-121">V tomto kurzu se soubor uloží do aktuální složky hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="426b9-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="426b9-122">Pokud není zadán žádný profil sledování, použije se výchozí profil sledování.</span><span class="sxs-lookup"><span data-stu-id="426b9-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="426b9-123">Při použití výchozího profilu sledování jsou vygenerovány `ActivityStates`záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="426b9-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="426b9-124">Protože potřebujeme zachytit text jenom jednou během životního cyklu `WriteLine` aktivity, extrahujeme jenom text `ActivityStates.Executing` ze stavu.</span><span class="sxs-lookup"><span data-stu-id="426b9-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="426b9-125">Aby bylo [možné vytvořit profil sledování a registrovat účastníka sledování](#to-create-the-tracking-profile-and-register-the-tracking-participant), je vytvořen profil sledování, který určuje, že `WriteLine` budou generovány pouze `ActivityStates.Executing` záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="426b9-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="426b9-126">Postup vytvoření profilu sledování a registrace účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="426b9-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="426b9-127">V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="426b9-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="426b9-128">Do horní části `using` souboru přidejte `Imports`následující příkaz (nebo) pomocí příkazů other `using` (nebo `Imports`).</span><span class="sxs-lookup"><span data-stu-id="426b9-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="426b9-129">Přidejte následující kód k `ConfigureWorkflowApplication` hned za kód, který `StringWriter` přidá do rozšíření pracovního postupu a před obslužné rutiny životního cyklu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="426b9-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="426b9-130">Tento profil sledování Určuje, že do vlastního účastníka `WriteLine` sledování se budou `Executing` generovat jenom záznamy stavu aktivity pro aktivity ve stavu.</span><span class="sxs-lookup"><span data-stu-id="426b9-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="426b9-131">Po přidání kódu `ConfigureWorkflowApplication` bude začátek vypadat podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="426b9-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="426b9-132">Zobrazení informací o sledování</span><span class="sxs-lookup"><span data-stu-id="426b9-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="426b9-133">V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="426b9-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="426b9-134">`InstanceId_SelectedIndexChanged` V obslužné rutině přidejte následující kód hned za kód, který vymaže okno stavu.</span><span class="sxs-lookup"><span data-stu-id="426b9-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="426b9-135">Když se v seznamu pracovních postupů vybere nový pracovní postup, načtou se záznamy sledování pro tento pracovní postup a zobrazí se v okně stav.</span><span class="sxs-lookup"><span data-stu-id="426b9-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="426b9-136">Následující příklad je dokončená `InstanceId_SelectedIndexChanged` obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="426b9-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="426b9-137">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="426b9-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="426b9-138">Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="426b9-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="426b9-139">Stisknutím kombinace kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="426b9-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="426b9-140">Vyberte rozsah pro odhad hry a typ pracovního postupu, který chcete spustit, a klikněte na **Nová hra**.</span><span class="sxs-lookup"><span data-stu-id="426b9-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="426b9-141">V poli **odhad** zadejte odhad a kliknutím na tlačítko **Přejít** odešlete svůj odhad.</span><span class="sxs-lookup"><span data-stu-id="426b9-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="426b9-142">Všimněte si, že stav pracovního postupu se zobrazí v okně stav.</span><span class="sxs-lookup"><span data-stu-id="426b9-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="426b9-143">Tento výstup je zachycen z `WriteLine` aktivit.</span><span class="sxs-lookup"><span data-stu-id="426b9-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="426b9-144">Přepněte na jiný pracovní postup tak, že ho vyberete v poli se seznamem **ID instance pracovního postupu** a Všimněte si, že se odebral stav aktuálního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="426b9-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="426b9-145">Přepněte zpátky na předchozí pracovní postup a Všimněte si, že je stav obnovený, podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="426b9-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="426b9-146">Pokud přepnete na pracovní postup, který byl spuštěn před povolením sledování, nebude zobrazen žádný stav.</span><span class="sxs-lookup"><span data-stu-id="426b9-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="426b9-147">Pokud však provedete další odhad, jejich stav bude uložen, protože sledování je nyní povoleno.</span><span class="sxs-lookup"><span data-stu-id="426b9-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="426b9-148">Tyto informace jsou užitečné při určování rozsahu náhodných čísel, ale neobsahují žádné informace o tom, jaké odhady se dřív udělaly.</span><span class="sxs-lookup"><span data-stu-id="426b9-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="426b9-149">Tyto informace jsou v dalším kroku, [jak: Hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)sebe.</span><span class="sxs-lookup"><span data-stu-id="426b9-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="426b9-150">Poznamenejte si ID instance pracovního postupu a Dohrajte hru do jejího dokončení.</span><span class="sxs-lookup"><span data-stu-id="426b9-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="426b9-151">Otevřete Průzkumníka Windows a přejděte do složky **NumberGuessWorkflowHost\bin\debug** (nebo **bin\Release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="426b9-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="426b9-152">Všimněte si, že kromě spustitelných souborů projektu jsou soubory s názvy souborů identifikátorů GUID.</span><span class="sxs-lookup"><span data-stu-id="426b9-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="426b9-153">Identifikujte ten, který odpovídá ID instance pracovního postupu z dokončeného pracovního postupu v předchozím kroku a otevřete ho v programu Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="426b9-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="426b9-154">Informace o sledování obsahují informace podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="426b9-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="426b9-155">Kromě neexistence odhadů uživatele Tato sledovací data neobsahují informace o konečném odhadu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="426b9-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="426b9-156">Důvodem je, že informace o sledování se skládají pouze `WriteLine` z výstupu pracovního postupu a poslední zobrazená zpráva je provedena `Completed` z obslužné rutiny po dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="426b9-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="426b9-157">V dalším kroku kurzu [: Hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)sebe: existující `WriteLine` aktivity jsou upraveny tak, aby se zobrazily odhadované množství uživatelů, a přidala se další `WriteLine` aktivita, která zobrazí konečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="426b9-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="426b9-158">Po integraci [těchto změn můžete postupovat takto: Hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) sebe znázorňuje, jak hostovat více verzí pracovního postupu současně.</span><span class="sxs-lookup"><span data-stu-id="426b9-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
