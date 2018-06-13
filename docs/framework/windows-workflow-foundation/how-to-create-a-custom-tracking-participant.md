---
title: 'Postupy: vytvoření vlastní sledování účastník'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 6439a056ec1baccf6c059f779a577723761c489b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519529"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Postupy: vytvoření vlastní sledování účastník
Pracovní postup sledování poskytuje přehled o stavu spuštění pracovního postupu. Modul runtime pracovního postupu vysílá sledování záznamy, které popisují pracovního postupu události životního cyklu, události aktivit životního cyklu, obnovení záložku a chyb. Tyto záznamy o sledování jsou spotřebovávána sledování účastníky. Windows Workflow Foundation (WF) obsahuje standardní sledování člena, který zapíše sledování záznamů jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník. Tento kurz – krok popisuje, jak vytvořit vlastní sledování účastník a sledování profil, který zaznamenat výstup `WriteLine` aktivity, aby mohly být zobrazeny pro uživatele.  
  
> [!NOTE]
>  Každého tématu v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív dokončit předchozí témata. Stažení dokončené verze nebo zobrazení na video s návodem kurzu, najdete v tématu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Chcete-li vytvořit vlastní sledování účastník](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [Vytvořit profil sledování a zaregistrovat účastník sledování](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [Chcete-li zobrazit informace o sledování](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [Sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> Chcete-li vytvořit vlastní sledování účastník  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **přidat**, **třída**. Typ `StatusTrackingParticipant` do **název** pole a klikněte na tlačítko **přidat**.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  Změnit `StatusTrackingParticipant` tak, aby se dědí z třídy `TrackingParticipant`.  
  
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
  
4.  Přidejte následující `Track` přepsání metody. Existuje několik různých typů sledování záznamů. Snažíme se ve výstupu `WriteLine` aktivity, které jsou obsaženy v aktivitě sledování záznamů. Pokud `TrackingRecord` je `ActivityTrackingRecord` pro `WriteLine` aktivitu `Text` z `WriteLine` se připojí k souboru s názvem po `InstanceId` pracovního postupu. V tomto kurzu je ukládat do aktuální složky hostitelskou aplikaci.  
  
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
  
     Pokud je zadán žádný profil sledování, použije se výchozí sledovacího profilu. Pokud je použita výchozí sledování profil, jsou pro všechny vygenerované záznamy o sledování `ActivityStates`. Vzhledem k tomu, že musíme zaznamenat text během životního cyklu jednou `WriteLine` aktivitu, jsme pouze rozbalte text z `ActivityStates.Executing` stavu. V [vytvořit profil sledování a zaregistrovat účastník sledování](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), sledování profil je vytvořen pouze určující `WriteLine` `ActivityStates.Executing` jsou vygenerované záznamy o sledování.  
  
###  <a name="BKMK_TrackingProfile"></a> Vytvořit profil sledování a zaregistrovat účastník sledování  
  
1.  Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníku řešení** a zvolte **kód zobrazení**.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  Přidejte následující kód, který `ConfigureWorkflowApplication` bezprostředně za kód, který přidá `StringWriter` rozšíření pracovního postupu a před obslužné rutiny životního cyklu pracovního postupu.  
  
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
  
     Tento profil sledování Určuje, že stav pouze aktivity záznamů pro `WriteLine` aktivity v `Executing` stavu jsou vygenerované účastníkům vlastní sledování.  
  
     Po přidání kód začátek `ConfigureWorkflowApplication` bude vypadat jako v následujícím příkladu.  
  
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
  
###  <a name="BKMK_DisplayTracking"></a> Chcete-li zobrazit informace o sledování  
  
1.  Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníku řešení** a zvolte **kód zobrazení**.  
  
2.  V `InstanceId_SelectedIndexChanged` obslužná rutina, přidejte následující kód ihned po kód, který vymaže stavové okno.  
  
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
  
     Když nový pracovní postup je vybrán v seznamu pracovního postupu, jsou záznamy sledování pro tento pracovní postup načte a zobrazí v okně Stav. Následující příklad je dokončené `InstanceId_SelectedIndexChanged` obslužné rutiny.  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> Sestavení a spuštění aplikace  
  
1.  Stisknutím kombinace kláves Ctrl + Shift + B pro sestavení aplikace.  
  
2.  Stisknutím kombinace kláves Ctrl + F5 a spusťte aplikaci.  
  
3.  Vyberte rozsah hádání hry a typ pracovního postupu spustit, a klikněte na **nové herní**. Zadejte odhad v **odhad** pole a klikněte na tlačítko **přejděte** odeslat vaše odhad. Všimněte si, že stav pracovního postupu se zobrazí v okně Stav. Tento výstup je zachycená z `WriteLine` aktivity. Přepnout na jiný pracovní postup výběrem jedné z **Id Instance pracovního postupu** – pole se seznamem a Všimněte si, že stav aktuálního pracovního postupu je odebráno. Přepněte zpět na předchozí pracovního postupu a Všimněte si, že stav je obnovena, podobně jako v následujícím příkladu.  
  
    > [!NOTE]
    >  Pokud přejdete do pracovního postupu, která byla spuštěna dříve, než bylo povoleno sledování neexistuje stav, který se zobrazí. Ale pokud provedete další pokusů, jejich stav je uložit, protože je nyní povoleno sledování.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**Předpokládaná je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**    
    > [!NOTE]
    >  Tyto informace jsou užitečné pro určení rozsahu náhodné číslo, ale neobsahuje žádné informace o jaké pokusů dříve provedli. Tyto informace jsou v dalším kroku [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
     Poznamenejte si id instance pracovního postupu a hrát hry na její dokončení.  
  
4.  Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu). Upozorňujeme, že kromě projektu existuje spustitelné soubory jsou soubory s názvy souborů identifikátor guid. Určit ten, který odpovídá id instance pracovního postupu z dokončené pracovního postupu v předchozím kroku a otevřete v poznámkovém bloku. Informace o sledování obsahuje informace podobný následujícímu.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**Předpokládaná je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**Předpokládaná je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10** kromě chybí pokusů uživatele, tato data sledování neobsahuje informace o poslední odhad pracovního postupu. Důvodem je, že informace o sledování se skládá jenom z `WriteLine` výstup z pracovního postupu, a je proveden poslední zprávu, která se zobrazí, tak z `Completed` obslužná rutina po dokončení pracovního postupu. V dalším kroku kurzu [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existující `WriteLine` aktivity jsou upravit tak, aby zobrazení pokusů uživatele a další `WriteLine` aktivity se přidá, Zobrazí poslední výsledky. Po integraci tyto změny [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) ukazuje, jak k hostování více verzí pracovního postupu ve stejnou dobu.
