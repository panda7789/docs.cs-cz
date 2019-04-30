---
title: 'Postupy: Vytvoření vlastního účastníka sledování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 64320a8f4799e79f54348e5381ed2d8ed49d496b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945558"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Postupy: Vytvoření vlastního účastníka sledování
Pracovní postup sledování poskytuje přehled o stavu pracovního postupu provádění. Modul runtime pracovního postupu vysílá záznamy sledování, které popisují pracovního postupu události životního cyklu, události životního cyklu aktivit, záložku obnovení a chyb. Tyto záznamy sledování se spotřebovávají sledování účastníci. Windows Workflow Foundation (WF) zahrnuje účastník standardní sledování, který zapíše záznamy sledování jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník. Tento kurz – krok popisuje postup vytvoření vlastního účastníka sledování a sledování profil, který zachytit výstup `WriteLine` aktivity, aby mohly být zobrazeny uživateli.  
  
> [!NOTE]
>  Každé téma v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív dokončit předchozí témata. Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Chcete-li vytvořit vlastní sledování účastník  
  
1. Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **třídy**. Typ `StatusTrackingParticipant` do **název** pole a klikněte na tlačítko **přidat**.  
  
2. Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Upravit `StatusTrackingParticipant` tak, aby dědila z třídy `TrackingParticipant`.  
  
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
  
4. Přidejte následující `Track` přepsání metody. Existuje několik různých typů sledování záznamů. Nás zajímá ve výstupu příkazu `WriteLine` aktivity, které jsou obsaženy v aktivitě sledování záznamů. Pokud `TrackingRecord` je `ActivityTrackingRecord` pro `WriteLine` aktivity, `Text` z `WriteLine` se připojí k souboru s názvem po `InstanceId` pracovního postupu. V tomto kurzu je soubor uložen do aktuální složky hostitelskou aplikaci.  
  
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
  
     Když se nezadá žádný profil sledování, je použita výchozí profil sledování tracking profile. Pokud se použije výchozí profil sledování tracking profile, jsou vydávány sledování záznamů pro všechny `ActivityStates`. Protože potřebujeme jen k zachycení text jednou během životního cyklu `WriteLine` aktivity, jsme pouze vyextrahovat text z `ActivityStates.Executing` stavu. V [k vytvoření sledovacího profilu a registrace účastník sledování](#to-create-the-tracking-profile-and-register-the-tracking-participant), je vytvořen sledovacího profilu, který určuje pouze `WriteLine` `ActivityStates.Executing` jsou vydávány sledování záznamů.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>K vytvoření sledovacího profilu a registrace účastník sledování  
  
1. Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.  
  
2. Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Přidejte následující kód, který `ConfigureWorkflowApplication` hned za kód, který se přidá `StringWriter` rozšíření pracovního postupu a před obslužné rutiny pracovních postupů životního cyklu.  
  
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
  
     Tento profil sledování Určuje, že stav aktivity pouze záznamy pro `WriteLine` aktivity ve službě `Executing` stavu jsou emitovány do vlastní sledování účastník.  
  
     Po přidání kódu, začátek `ConfigureWorkflowApplication` bude vypadat jako v následujícím příkladu.  
  
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
  
## <a name="to-display-the-tracking-information"></a>Chcete-li zobrazit informace o sledování  
  
1. Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.  
  
2. V `InstanceId_SelectedIndexChanged` obslužnou rutinu, přidejte následující kód bezprostředně po kód, který vymaže stav okna.  
  
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
  
     Při výběru nového pracovního postupu v seznamu pracovního postupu, jsou na sledování záznamy pro daný pracovní postup načte a zobrazí v okně Stav. V následujícím příkladu je dokončené `InstanceId_SelectedIndexChanged` obslužné rutiny.  
  
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
  
1. Stiskněte kombinaci kláves Ctrl + Shift + B pro sestavení aplikace.  
  
2. Stisknutím kláves Ctrl + F5 spusťte aplikaci.  
  
3. Vyberte oblast pro využití herních a typ pracovního postupu ke spouštění a klikněte na tlačítko **nová hra**. Zadejte odhad v **odhad** pole a klikněte na tlačítko **Přejít** k odeslání vašeho odhadu. Všimněte si, že stav pracovního postupu se zobrazí v okně Stav. Tímto výstupem je zachycená z `WriteLine` aktivity. Přepnout na jiný pracovní postup výběrem jedné z **Id Instance pracovního postupu** – pole se seznamem a Všimněte si, že stav aktuálního pracovního postupu se odebere. Přepnout zpět na předchozí pracovní postup a Všimněte si, že stav je obnoveno, podobně jako v následujícím příkladu.  
  
    > [!NOTE]
    > Pokud přejdete do pracovního postupu, která byla spuštěna dříve, než bylo povoleno sledování žádný stav se zobrazí. Nicméně pokud dalších pokusů, jejich stav je uložit, protože je nyní povoleno sledování.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > Tyto informace jsou užitečné pro určení rozsahu náhodné číslo, ale neobsahuje žádné informace o tom, jaké pokusů mít dříve provedeny. Tyto informace jsou v dalším kroku [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

    Poznamenejte si id instance pracovního postupu a Zahrajte si hru na jeho dokončení.
  
4. Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu). Všimněte si, že kromě projekt spustitelné soubory jsou soubory s názvy souborů identifikátor guid. Identifikovat ten, který odpovídá id instance pracovního postupu z dokončený pracovní postup v předchozím kroku a otevřete v poznámkovém bloku. Informace o sledování obsahuje informace, které jsou podobné následujícímu.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Kromě chybí pokusů uživatele tato data sledování neobsahuje informace o posledním odhad pracovního postupu. Důvodem je, že informace o sledování se skládá pouze z `WriteLine` výstup z pracovního postupu, a z Probíhá závěrečná zpráva, která se zobrazí `Completed` obslužná rutina po dokončení pracovního postupu. V dalším kroku kurzu [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existující `WriteLine` aktivity jsou upraveny pro zobrazení uživatele pokusů a dalších `WriteLine` je aktivita přidána, který zobrazí konečných výsledků. Jakmile tyto změny jsou integrované, [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) ukazuje, jak hostování několika verzí pracovního postupu ve stejnou dobu.
