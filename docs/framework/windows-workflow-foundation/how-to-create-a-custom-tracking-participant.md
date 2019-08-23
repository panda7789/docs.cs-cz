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
# <a name="how-to-create-a-custom-tracking-participant"></a>Postupy: Vytvoření vlastního účastníka sledování
Sledování pracovního postupu nabízí přehled o stavu provádění pracovního postupu. Modul runtime pracovního postupu generuje záznamy sledování, které popisují události životního cyklu pracovního postupu, události životního cyklu aktivity, obnovení záložek a chyby. Tyto záznamy sledování se spotřebují sledováním účastníků. Programovací model Windows Workflow Foundation (WF) zahrnuje standardního účastníka sledování, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník. Tento krok kurzu popisuje, jak vytvořit vlastního účastníka sledování a profil sledování, který zachycuje výstup `WriteLine` aktivit, aby je bylo možné zobrazit uživateli.  
  
> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li dokončit toto téma, je nutné nejprve dokončit předchozí témata. Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Vytvoření vlastního účastníka sledování  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Třída**. Do `StatusTrackingParticipant` pole **název** zadejte a klikněte na **Přidat**.  
  
2. Do horní části `using` souboru přidejte `Imports`následující příkazy (nebo), které budou `using` příkazy (nebo `Imports`).  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Upravte třídu tak, aby dědila z `TrackingParticipant`. `StatusTrackingParticipant`  
  
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
  
4. Přidejte následující `Track` přepsání metody. Existuje několik různých typů záznamů sledování. Zajímá Vás výstup `WriteLine` aktivit, které jsou obsaženy v záznamech sledování aktivit. `TrackingRecord` Pokud `InstanceId` je aktivita`WriteLine` pro aktivitu, jepřipojenksouborusnázvemzapracovnípostup.`WriteLine` `Text` `ActivityTrackingRecord` V tomto kurzu se soubor uloží do aktuální složky hostitelské aplikace.  
  
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
  
     Pokud není zadán žádný profil sledování, použije se výchozí profil sledování. Při použití výchozího profilu sledování jsou vygenerovány `ActivityStates`záznamy sledování. Protože potřebujeme zachytit text jenom jednou během životního cyklu `WriteLine` aktivity, extrahujeme jenom text `ActivityStates.Executing` ze stavu. Aby bylo [možné vytvořit profil sledování a registrovat účastníka sledování](#to-create-the-tracking-profile-and-register-the-tracking-participant), je vytvořen profil sledování, který určuje, že `WriteLine` budou generovány pouze `ActivityStates.Executing` záznamy sledování.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>Postup vytvoření profilu sledování a registrace účastníka sledování  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.  
  
2. Do horní části `using` souboru přidejte `Imports`následující příkaz (nebo) pomocí příkazů other `using` (nebo `Imports`).  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Přidejte následující kód k `ConfigureWorkflowApplication` hned za kód, který `StringWriter` přidá do rozšíření pracovního postupu a před obslužné rutiny životního cyklu pracovního postupu.  
  
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
  
     Tento profil sledování Určuje, že do vlastního účastníka `WriteLine` sledování se budou `Executing` generovat jenom záznamy stavu aktivity pro aktivity ve stavu.  
  
     Po přidání kódu `ConfigureWorkflowApplication` bude začátek vypadat podobně jako v následujícím příkladu.  
  
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
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.  
  
2. `InstanceId_SelectedIndexChanged` V obslužné rutině přidejte následující kód hned za kód, který vymaže okno stavu.  
  
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
  
     Když se v seznamu pracovních postupů vybere nový pracovní postup, načtou se záznamy sledování pro tento pracovní postup a zobrazí se v okně stav. Následující příklad je dokončená `InstanceId_SelectedIndexChanged` obslužná rutina.  
  
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
  
## <a name="to-build-and-run-the-application"></a>Sestavení a spuštění aplikace  
  
1. Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci.  
  
2. Stisknutím kombinace kláves CTRL + F5 spusťte aplikaci.  
  
3. Vyberte rozsah pro odhad hry a typ pracovního postupu, který chcete spustit, a klikněte na **Nová hra**. V poli **odhad** zadejte odhad a kliknutím na tlačítko **Přejít** odešlete svůj odhad. Všimněte si, že stav pracovního postupu se zobrazí v okně stav. Tento výstup je zachycen z `WriteLine` aktivit. Přepněte na jiný pracovní postup tak, že ho vyberete v poli se seznamem **ID instance pracovního postupu** a Všimněte si, že se odebral stav aktuálního pracovního postupu. Přepněte zpátky na předchozí pracovní postup a Všimněte si, že je stav obnovený, podobně jako v následujícím příkladu.  
  
    > [!NOTE]
    > Pokud přepnete na pracovní postup, který byl spuštěn před povolením sledování, nebude zobrazen žádný stav. Pokud však provedete další odhad, jejich stav bude uložen, protože sledování je nyní povoleno.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > Tyto informace jsou užitečné při určování rozsahu náhodných čísel, ale neobsahují žádné informace o tom, jaké odhady se dřív udělaly. Tyto informace jsou v dalším kroku, [jak: Hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)sebe.

    Poznamenejte si ID instance pracovního postupu a Dohrajte hru do jejího dokončení.
  
4. Otevřete Průzkumníka Windows a přejděte do složky **NumberGuessWorkflowHost\bin\debug** (nebo **bin\Release** v závislosti na nastavení projektu). Všimněte si, že kromě spustitelných souborů projektu jsou soubory s názvy souborů identifikátorů GUID. Identifikujte ten, který odpovídá ID instance pracovního postupu z dokončeného pracovního postupu v předchozím kroku a otevřete ho v programu Poznámkový blok. Informace o sledování obsahují informace podobné následujícímu.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Kromě neexistence odhadů uživatele Tato sledovací data neobsahují informace o konečném odhadu pracovního postupu. Důvodem je, že informace o sledování se skládají pouze `WriteLine` z výstupu pracovního postupu a poslední zobrazená zpráva je provedena `Completed` z obslužné rutiny po dokončení pracovního postupu. V dalším kroku kurzu [: Hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)sebe: existující `WriteLine` aktivity jsou upraveny tak, aby se zobrazily odhadované množství uživatelů, a přidala se další `WriteLine` aktivita, která zobrazí konečné výsledky. Po integraci [těchto změn můžete postupovat takto: Hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) sebe znázorňuje, jak hostovat více verzí pracovního postupu současně.
