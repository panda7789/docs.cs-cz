---
title: 'Postupy: vytvoření vlastního účastníka sledování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: a9a83f64b7ea0de275631d7d3b8d2755671223ce
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864479"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="15f89-102">Postupy: vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="15f89-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="15f89-103">Pracovní postup sledování poskytuje přehled o stavu pracovního postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="15f89-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="15f89-104">Modul runtime pracovního postupu vysílá záznamy sledování, které popisují pracovního postupu události životního cyklu, události životního cyklu aktivit, záložku obnovení a chyb.</span><span class="sxs-lookup"><span data-stu-id="15f89-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="15f89-105">Tyto záznamy sledování se spotřebovávají sledování účastníci.</span><span class="sxs-lookup"><span data-stu-id="15f89-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="15f89-106">Windows Workflow Foundation (WF) zahrnuje účastník standardní sledování, který zapíše záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="15f89-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="15f89-107">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="15f89-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="15f89-108">Tento kurz – krok popisuje postup vytvoření vlastního účastníka sledování a sledování profil, který zachytit výstup `WriteLine` aktivity, aby mohly být zobrazeny uživateli.</span><span class="sxs-lookup"><span data-stu-id="15f89-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15f89-109">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="15f89-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="15f89-110">K dokončení tohoto tématu, musíte nejdřív dokončit předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="15f89-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="15f89-111">Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="15f89-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="15f89-112">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="15f89-112">In this topic</span></span>  
  
-   [<span data-ttu-id="15f89-113">Chcete-li vytvořit vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="15f89-113">To create the custom tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [<span data-ttu-id="15f89-114">K vytvoření sledovacího profilu a registrace účastník sledování</span><span class="sxs-lookup"><span data-stu-id="15f89-114">To create the tracking profile and register the tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [<span data-ttu-id="15f89-115">Chcete-li zobrazit informace o sledování</span><span class="sxs-lookup"><span data-stu-id="15f89-115">To display the tracking information</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [<span data-ttu-id="15f89-116">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="15f89-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> <span data-ttu-id="15f89-117">Chcete-li vytvořit vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="15f89-117">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="15f89-118">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **třídy**.</span><span class="sxs-lookup"><span data-stu-id="15f89-118">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="15f89-119">Typ `StatusTrackingParticipant` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="15f89-119">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="15f89-120">Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="15f89-120">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="15f89-121">Upravit `StatusTrackingParticipant` tak, aby dědila z třídy `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="15f89-121">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4.  <span data-ttu-id="15f89-122">Přidejte následující `Track` přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="15f89-122">Add the following `Track` method override.</span></span> <span data-ttu-id="15f89-123">Existuje několik různých typů sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="15f89-123">There are several different types of tracking records.</span></span> <span data-ttu-id="15f89-124">Nás zajímá ve výstupu příkazu `WriteLine` aktivity, které jsou obsaženy v aktivitě sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="15f89-124">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="15f89-125">Pokud `TrackingRecord` je `ActivityTrackingRecord` pro `WriteLine` aktivity, `Text` z `WriteLine` se připojí k souboru s názvem po `InstanceId` pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="15f89-125">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="15f89-126">V tomto kurzu je soubor uložen do aktuální složky hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15f89-126">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="15f89-127">Když se nezadá žádný profil sledování, je použita výchozí profil sledování tracking profile.</span><span class="sxs-lookup"><span data-stu-id="15f89-127">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="15f89-128">Pokud se použije výchozí profil sledování tracking profile, jsou vydávány sledování záznamů pro všechny `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="15f89-128">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="15f89-129">Protože potřebujeme jen k zachycení text jednou během životního cyklu `WriteLine` aktivity, jsme pouze vyextrahovat text z `ActivityStates.Executing` stavu.</span><span class="sxs-lookup"><span data-stu-id="15f89-129">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="15f89-130">V [k vytvoření sledovacího profilu a registrace účastník sledování](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), je vytvořen sledovacího profilu, který určuje pouze `WriteLine` `ActivityStates.Executing` jsou vydávány sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="15f89-130">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
###  <a name="BKMK_TrackingProfile"></a> <span data-ttu-id="15f89-131">K vytvoření sledovacího profilu a registrace účastník sledování</span><span class="sxs-lookup"><span data-stu-id="15f89-131">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="15f89-132">Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="15f89-132">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="15f89-133">Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="15f89-133">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="15f89-134">Přidejte následující kód, který `ConfigureWorkflowApplication` hned za kód, který se přidá `StringWriter` rozšíření pracovního postupu a před obslužné rutiny pracovních postupů životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="15f89-134">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="15f89-135">Tento profil sledování Určuje, že stav aktivity pouze záznamy pro `WriteLine` aktivity ve službě `Executing` stavu jsou emitovány do vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="15f89-135">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="15f89-136">Po přidání kódu, začátek `ConfigureWorkflowApplication` bude vypadat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="15f89-136">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
###  <a name="BKMK_DisplayTracking"></a> <span data-ttu-id="15f89-137">Chcete-li zobrazit informace o sledování</span><span class="sxs-lookup"><span data-stu-id="15f89-137">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="15f89-138">Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="15f89-138">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="15f89-139">V `InstanceId_SelectedIndexChanged` obslužnou rutinu, přidejte následující kód bezprostředně po kód, který vymaže stav okna.</span><span class="sxs-lookup"><span data-stu-id="15f89-139">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="15f89-140">Při výběru nového pracovního postupu v seznamu pracovního postupu, jsou na sledování záznamy pro daný pracovní postup načte a zobrazí v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="15f89-140">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="15f89-141">V následujícím příkladu je dokončené `InstanceId_SelectedIndexChanged` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="15f89-141">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="15f89-142">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="15f89-142">To build and run the application</span></span>  
  
1.  <span data-ttu-id="15f89-143">Stiskněte kombinaci kláves Ctrl + Shift + B pro sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="15f89-143">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="15f89-144">Stisknutím kláves Ctrl + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15f89-144">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="15f89-145">Vyberte oblast pro využití herních a typ pracovního postupu ke spouštění a klikněte na tlačítko **nová hra**.</span><span class="sxs-lookup"><span data-stu-id="15f89-145">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="15f89-146">Zadejte odhad v **odhad** pole a klikněte na tlačítko **Přejít** k odeslání vašeho odhadu.</span><span class="sxs-lookup"><span data-stu-id="15f89-146">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="15f89-147">Všimněte si, že stav pracovního postupu se zobrazí v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="15f89-147">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="15f89-148">Tímto výstupem je zachycená z `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="15f89-148">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="15f89-149">Přepnout na jiný pracovní postup výběrem jedné z **Id Instance pracovního postupu** – pole se seznamem a Všimněte si, že stav aktuálního pracovního postupu se odebere.</span><span class="sxs-lookup"><span data-stu-id="15f89-149">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="15f89-150">Přepnout zpět na předchozí pracovní postup a Všimněte si, že stav je obnoveno, podobně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="15f89-150">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15f89-151">Pokud přejdete do pracovního postupu, která byla spuštěna dříve, než bylo povoleno sledování žádný stav se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="15f89-151">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="15f89-152">Nicméně pokud dalších pokusů, jejich stav je uložit, protože je nyní povoleno sledování.</span><span class="sxs-lookup"><span data-stu-id="15f89-152">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
 <span data-ttu-id="15f89-153">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="15f89-153">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="15f89-154">**Váš odhad je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="15f89-154">**Your guess is too high.** </span></span>  
<span data-ttu-id="15f89-155">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="15f89-155">**Please enter a number between 1 and 10**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="15f89-156">Tyto informace jsou užitečné pro určení rozsahu náhodné číslo, ale neobsahuje žádné informace o tom, jaké pokusů mít dříve provedeny.</span><span class="sxs-lookup"><span data-stu-id="15f89-156">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="15f89-157">Tyto informace jsou v dalším kroku [jak: hostitel více verzí pracovní postup-souběžně](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="15f89-157">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
     <span data-ttu-id="15f89-158">Poznamenejte si id instance pracovního postupu a Zahrajte si hru na jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="15f89-158">Make a note of the workflow instance id, and play the game through to its completion.</span></span>  
  
4.  <span data-ttu-id="15f89-159">Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="15f89-159">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="15f89-160">Všimněte si, že kromě projekt spustitelné soubory jsou soubory s názvy souborů identifikátor guid.</span><span class="sxs-lookup"><span data-stu-id="15f89-160">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="15f89-161">Identifikovat ten, který odpovídá id instance pracovního postupu z dokončený pracovní postup v předchozím kroku a otevřete v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="15f89-161">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="15f89-162">Informace o sledování obsahuje informace, které jsou podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="15f89-162">The tracking information contains information similar to the following.</span></span>  
  
 <span data-ttu-id="15f89-163">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="15f89-163">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="15f89-164">**Váš odhad je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="15f89-164">**Your guess is too high.** </span></span>  
<span data-ttu-id="15f89-165">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="15f89-165">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="15f89-166">**Váš odhad je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="15f89-166">**Your guess is too high.** </span></span>  
<span data-ttu-id="15f89-167">**Zadejte prosím číslo mezi 1 a 10** kromě chybí pokusů uživatele, tato data sledování neobsahuje informace o posledním odhad pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="15f89-167">**Please enter a number between 1 and 10**      In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="15f89-168">Důvodem je, že informace o sledování se skládá pouze z `WriteLine` výstup z pracovního postupu, a z Probíhá závěrečná zpráva, která se zobrazí `Completed` obslužná rutina po dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="15f89-168">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="15f89-169">V dalším kroku kurzu [jak: hostitele více verzí pracovní postup-souběžně](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existující `WriteLine` aktivity jsou upraveny pro zobrazení uživatele pokusů a dalších `WriteLine` , který je aktivita přidána Zobrazí konečných výsledků.</span><span class="sxs-lookup"><span data-stu-id="15f89-169">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="15f89-170">Až tyto změny jsou integrované, [jak: hostitel více verzí pracovní postup-souběžně](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) ukazuje, jak hostování několika verzí pracovního postupu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="15f89-170">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
