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
# <a name="how-to-create-a-custom-tracking-participant"></a>Postupy: Vytvoření vlastního účastníka sledování
Sledování pracovního postupu poskytuje přehled o stavu provádění pracovního postupu. Za běhu pracovního postupu vyzařuje záznamy sledování, které popisují události životního cyklu pracovního postupu, události životního cyklu aktivity, obnovení záložek a poruchy. Tyto záznamy sledování jsou spotřebovány sledování účastníků. Windows Workflow Foundation (WF) zahrnuje standardní sledování účastníka, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník. Tento krok kurzu popisuje, jak vytvořit vlastní sledování účastníka `WriteLine` a sledování profilu, které zachycují výstup aktivit tak, aby mohly být zobrazeny uživateli.  
  
> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li toto téma dokončit, musíte nejprve dokončit předchozí témata. Pokud chcete stáhnout dokončenou verzi nebo zobrazit video návod k kurzu, přečtěte si část [Windows Workflow Foundation (WF45) – Kurz začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Vytvoření vlastního účastníka sledování  
  
1. Klepněte pravým tlačítkem myši na **numberguessWorkflowHost** v **Průzkumníku řešení** a zvolte **Přidat**, **Třída**. Zadejte `StatusTrackingParticipant` do pole **Název** a klepněte na **tlačítko Přidat**.  
  
2. Přidejte `using` následující `Imports`příkazy (nebo ) v horní `using` části `Imports`souboru s ostatními příkazy (nebo ).  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Upravte `StatusTrackingParticipant` třídu tak, `TrackingParticipant`aby dědí z .  
  
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
  
4. Přidejte `Track` následující přepsání metody. Existuje několik různých typů záznamů sledování. Máme zájem o výstup `WriteLine` y aktivit, které jsou obsaženy v záznamech sledování aktivit. Pokud `TrackingRecord` je `ActivityTrackingRecord` pro `WriteLine` aktivitu, `Text` je `WriteLine` připojen k souboru pojmenované `InstanceId` po pracovního postupu. V tomto kurzu je soubor uložen do aktuální složky hostitelské aplikace.  
  
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
  
     Pokud není zadán žádný profil sledování, použije se výchozí profil sledování. Při použití výchozího profilu sledování jsou záznamy `ActivityStates`sledování vyzařovány pro všechny . Vzhledem k tomu, že potřebujeme zachytit text `WriteLine` pouze jednou během životního cyklu `ActivityStates.Executing` aktivity, extrahujeme pouze text ze stavu. [Chcete-li vytvořit profil sledování a zaregistrovat účastníka sledování](#to-create-the-tracking-profile-and-register-the-tracking-participant), `WriteLine` `ActivityStates.Executing` je vytvořen profil sledování, který určuje, že jsou emitovány pouze záznamy sledování.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>Vytvoření profilu sledování a registrace účastníka sledování  
  
1. Klepněte pravým tlačítkem myši na **příkaz WorkflowHostForm** v **Průzkumníku řešení** a zvolte **Zobrazit kód**.  
  
2. Přidejte `using` následující `Imports`příkaz (nebo ) v horní `using` části `Imports`souboru s ostatními příkazy (nebo ).  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Přidejte následující `ConfigureWorkflowApplication` kód těsně za kód, který přidá `StringWriter` rozšíření pracovního postupu a před obslužné rutiny životního cyklu pracovního postupu.  
  
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
  
     Tento profil sledování určuje, že `WriteLine` pouze záznamy `Executing` stavu aktivity pro aktivity ve stavu jsou vydávány pro vlastní sledování účastníka.  
  
     Po přidání kódu bude `ConfigureWorkflowApplication` začátek vypadat jako v následujícím příkladu.  
  
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
  
## <a name="to-display-the-tracking-information"></a>Zobrazení informací o sledování  
  
1. Klepněte pravým tlačítkem myši na **příkaz WorkflowHostForm** v **Průzkumníku řešení** a zvolte **Zobrazit kód**.  
  
2. Do `InstanceId_SelectedIndexChanged` obslužné rutiny přidejte následující kód ihned za kód, který vymaže stavové okno.  
  
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
  
     Pokud je v seznamu pracovních postupů vybrán nový pracovní postup, záznamy sledování pro tento pracovní postup se načtou a zobrazí ve stavovém okně. Následující příklad je `InstanceId_SelectedIndexChanged` dokončená obslužná rutina.  
  
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
  
## <a name="to-build-and-run-the-application"></a>Vytvoření a spuštění aplikace  
  
1. Stisknutím kláves Ctrl+Shift+B vytvořte aplikaci.  
  
2. Stisknutím kláves Ctrl+F5 spusťte aplikaci.  
  
3. Vyberte rozsah pro hádanku a typ pracovního postupu, který chcete spustit, a klepněte na tlačítko **Nová hra**. Zadejte do pole **Odhad** odhad a kliknutím na **Přejít** odešlete svůj odhad. Všimněte si, že stav pracovního postupu se zobrazí ve stavovém okně. Tento výstup je zachycen `WriteLine` z aktivit. Přepněte do jiného pracovního postupu tak, že vyberete jeden z pole se seznamem **Id instance pracovního postupu** a všimněte si, že se odebere stav aktuálního pracovního postupu. Přepněte zpět na předchozí pracovní postup a všimněte si, že stav je obnoven, podobně jako v následujícím příkladu.  
  
    > [!NOTE]
    > Pokud přepnete na pracovní postup, který byl spuštěn před povolením sledování, nezobrazí se žádný stav. Pokud však provedete další odhady, jejich stav se uloží, protože sledování je nyní povoleno.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > Tyto informace jsou užitečné pro určení rozsahu náhodného čísla, ale neobsahují žádné informace o tom, jaké odhady byly dříve provedeny. Tyto informace jsou v dalším [kroku: Host více verzí pracovního postupu vedle sebe](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

    Poznamenejte si ID instance pracovního postupu a přehrajte hru až do jejího dokončení.
  
4. Otevřete Průzkumníka Windows a přejděte do složky **NumberGuessWorkflowHost\bin\debug** (nebo **bin\release** v závislosti na nastavení projektu). Všimněte si, že kromě spustitelných souborů projektu existují soubory s názvy souborů GUID. Identifikujte ten, který odpovídá ID instance pracovního postupu z dokončeného pracovního postupu v předchozím kroku, a otevřete ho v poznámkovém bloku. Informace o sledování obsahují informace podobné následujícím.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Kromě absence dohadů uživatele tato data sledování neobsahuje informace o konečném odhadu pracovního postupu. Důvodem je, že informace o `WriteLine` sledování se skládá pouze z výstupu z pracovního `Completed` postupu a poslední zpráva, která se zobrazí, se provádí z obslužné rutiny po dokončení pracovního postupu. V dalším kroku [kurzu, Jak: Host více verzí pracovního postupu side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existující `WriteLine` aktivity jsou upraveny `WriteLine` tak, aby zobrazení odhady uživatele a další aktivita je přidána, která zobrazuje konečné výsledky. Po integraci těchto [změn: Hostování více verzí pracovního postupu vedle sebe](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) ukazuje, jak hostovat více verzí pracovního postupu současně.
