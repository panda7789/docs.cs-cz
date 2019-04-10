---
title: 'Postupy: Vytvoření vlastního účastníka sledování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 64320a8f4799e79f54348e5381ed2d8ed49d496b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338173"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="7cd73-102">Postupy: Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="7cd73-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="7cd73-103">Pracovní postup sledování poskytuje přehled o stavu pracovního postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="7cd73-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="7cd73-104">Modul runtime pracovního postupu vysílá záznamy sledování, které popisují pracovního postupu události životního cyklu, události životního cyklu aktivit, záložku obnovení a chyb.</span><span class="sxs-lookup"><span data-stu-id="7cd73-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="7cd73-105">Tyto záznamy sledování se spotřebovávají sledování účastníci.</span><span class="sxs-lookup"><span data-stu-id="7cd73-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="7cd73-106">Windows Workflow Foundation (WF) zahrnuje účastník standardní sledování, který zapíše záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="7cd73-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="7cd73-107">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="7cd73-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="7cd73-108">Tento kurz – krok popisuje postup vytvoření vlastního účastníka sledování a sledování profil, který zachytit výstup `WriteLine` aktivity, aby mohly být zobrazeny uživateli.</span><span class="sxs-lookup"><span data-stu-id="7cd73-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cd73-109">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="7cd73-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="7cd73-110">K dokončení tohoto tématu, musíte nejdřív dokončit předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="7cd73-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="7cd73-111">Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="7cd73-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="7cd73-112">Chcete-li vytvořit vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="7cd73-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="7cd73-113">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **třídy**.</span><span class="sxs-lookup"><span data-stu-id="7cd73-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="7cd73-114">Typ `StatusTrackingParticipant` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="7cd73-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="7cd73-115">Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="7cd73-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="7cd73-116">Upravit `StatusTrackingParticipant` tak, aby dědila z třídy `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="7cd73-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4. <span data-ttu-id="7cd73-117">Přidejte následující `Track` přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="7cd73-117">Add the following `Track` method override.</span></span> <span data-ttu-id="7cd73-118">Existuje několik různých typů sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7cd73-118">There are several different types of tracking records.</span></span> <span data-ttu-id="7cd73-119">Nás zajímá ve výstupu příkazu `WriteLine` aktivity, které jsou obsaženy v aktivitě sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7cd73-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="7cd73-120">Pokud `TrackingRecord` je `ActivityTrackingRecord` pro `WriteLine` aktivity, `Text` z `WriteLine` se připojí k souboru s názvem po `InstanceId` pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="7cd73-121">V tomto kurzu je soubor uložen do aktuální složky hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7cd73-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="7cd73-122">Když se nezadá žádný profil sledování, je použita výchozí profil sledování tracking profile.</span><span class="sxs-lookup"><span data-stu-id="7cd73-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="7cd73-123">Pokud se použije výchozí profil sledování tracking profile, jsou vydávány sledování záznamů pro všechny `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="7cd73-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="7cd73-124">Protože potřebujeme jen k zachycení text jednou během životního cyklu `WriteLine` aktivity, jsme pouze vyextrahovat text z `ActivityStates.Executing` stavu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="7cd73-125">V [k vytvoření sledovacího profilu a registrace účastník sledování](#to-create-the-tracking-profile-and-register-the-tracking-participant), je vytvořen sledovacího profilu, který určuje pouze `WriteLine` `ActivityStates.Executing` jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7cd73-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="7cd73-126">K vytvoření sledovacího profilu a registrace účastník sledování</span><span class="sxs-lookup"><span data-stu-id="7cd73-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="7cd73-127">Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7cd73-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="7cd73-128">Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="7cd73-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="7cd73-129">Přidejte následující kód, který `ConfigureWorkflowApplication` hned za kód, který se přidá `StringWriter` rozšíření pracovního postupu a před obslužné rutiny pracovních postupů životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="7cd73-130">Tento profil sledování Určuje, že stav aktivity pouze záznamy pro `WriteLine` aktivity ve službě `Executing` stavu jsou emitovány do vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="7cd73-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="7cd73-131">Po přidání kódu, začátek `ConfigureWorkflowApplication` bude vypadat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="7cd73-132">Chcete-li zobrazit informace o sledování</span><span class="sxs-lookup"><span data-stu-id="7cd73-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="7cd73-133">Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7cd73-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="7cd73-134">V `InstanceId_SelectedIndexChanged` obslužnou rutinu, přidejte následující kód bezprostředně po kód, který vymaže stav okna.</span><span class="sxs-lookup"><span data-stu-id="7cd73-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="7cd73-135">Při výběru nového pracovního postupu v seznamu pracovního postupu, jsou na sledování záznamy pro daný pracovní postup načte a zobrazí v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="7cd73-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="7cd73-136">V následujícím příkladu je dokončené `InstanceId_SelectedIndexChanged` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="7cd73-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="7cd73-137">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="7cd73-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="7cd73-138">Stiskněte kombinaci kláves Ctrl + Shift + B pro sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7cd73-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="7cd73-139">Stisknutím kláves Ctrl + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7cd73-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="7cd73-140">Vyberte oblast pro využití herních a typ pracovního postupu ke spouštění a klikněte na tlačítko **nová hra**.</span><span class="sxs-lookup"><span data-stu-id="7cd73-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="7cd73-141">Zadejte odhad v **odhad** pole a klikněte na tlačítko **Přejít** k odeslání vašeho odhadu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="7cd73-142">Všimněte si, že stav pracovního postupu se zobrazí v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="7cd73-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="7cd73-143">Tímto výstupem je zachycená z `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="7cd73-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="7cd73-144">Přepnout na jiný pracovní postup výběrem jedné z **Id Instance pracovního postupu** – pole se seznamem a Všimněte si, že stav aktuálního pracovního postupu se odebere.</span><span class="sxs-lookup"><span data-stu-id="7cd73-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="7cd73-145">Přepnout zpět na předchozí pracovní postup a Všimněte si, že stav je obnoveno, podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7cd73-146">Pokud přejdete do pracovního postupu, která byla spuštěna dříve, než bylo povoleno sledování žádný stav se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="7cd73-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="7cd73-147">Nicméně pokud dalších pokusů, jejich stav je uložit, protože je nyní povoleno sledování.</span><span class="sxs-lookup"><span data-stu-id="7cd73-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="7cd73-148">Tyto informace jsou užitečné pro určení rozsahu náhodné číslo, ale neobsahuje žádné informace o tom, jaké pokusů mít dříve provedeny.</span><span class="sxs-lookup"><span data-stu-id="7cd73-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="7cd73-149">Tyto informace jsou v dalším kroku [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="7cd73-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="7cd73-150">Poznamenejte si id instance pracovního postupu a Zahrajte si hru na jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="7cd73-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="7cd73-151">Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="7cd73-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="7cd73-152">Všimněte si, že kromě projekt spustitelné soubory jsou soubory s názvy souborů identifikátor guid.</span><span class="sxs-lookup"><span data-stu-id="7cd73-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="7cd73-153">Identifikovat ten, který odpovídá id instance pracovního postupu z dokončený pracovní postup v předchozím kroku a otevřete v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="7cd73-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="7cd73-154">Informace o sledování obsahuje informace, které jsou podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="7cd73-155">Kromě chybí pokusů uživatele tato data sledování neobsahuje informace o posledním odhad pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="7cd73-156">Důvodem je, že informace o sledování se skládá pouze z `WriteLine` výstup z pracovního postupu, a z Probíhá závěrečná zpráva, která se zobrazí `Completed` obslužná rutina po dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="7cd73-157">V dalším kroku kurzu [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existující `WriteLine` aktivity jsou upraveny pro zobrazení uživatele pokusů a dalších `WriteLine` je aktivita přidána, který zobrazí konečných výsledků.</span><span class="sxs-lookup"><span data-stu-id="7cd73-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="7cd73-158">Jakmile tyto změny jsou integrované, [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) ukazuje, jak hostování několika verzí pracovního postupu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="7cd73-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
