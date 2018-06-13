---
title: 'Postupy: vytvoření a spuštění s dlouhým spuštěný pracovní postup'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 63857ac96c85174407a4455d1ec582147bd33e3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520328"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Postupy: vytvoření a spuštění s dlouhým spuštěný pracovní postup
Jedna z centrální funkcí Windows Workflow Foundation (WF) je modul runtime schopnost zachovat a uvolnit nečinnosti pracovní postupy pro databázi. Kroky v [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) ukázán základní informace o hostování pracovního postupu pomocí konzolové aplikace. Příklady byly uvedeny počáteční pracovní postupy, obslužné rutiny životního cyklu pracovního postupu a opětovné záložky. K prokázání efektivně trvalost pracovního postupu, je vyžadován složitější hostitel pracovního postupu spuštění a obnovení několik instancí pracovního postupu, která podporuje. Tento krok v tomto kurzu ukazuje, jak vytvořit hostitele formuláře systému Windows, aplikace, která podporuje spouštění a obnovení více instancí pracovních postupů, trvalost pracovního postupu a poskytuje základ pro pokročilé funkce jako sledování a správa verzí, které jsou ukázáno v kurzu následné kroky.  
  
> [!NOTE]
>  Tento kurz – krok a všechny následné kroky použít všechny tři typy pracovního postupu z [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md). Pokud jste neprovedli všechny tři typy můžete stáhnout dokončenou verzi kroků z [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Stažení dokončené verze nebo zobrazení na video s návodem kurzu, najdete v tématu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [K vytvoření databáze trvalost](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [Chcete-li přidat odkaz na sestavení DurableInstancing](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [Vytvoření pracovního postupu hostitele formuláře](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Chcete-li přidat vlastnosti a metody helper formuláře](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Ke konfiguraci úložiště instance, obslužné rutiny životního cyklu pracovního postupu a rozšíření](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Chcete-li povolit spuštění a obnovení více typů pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Spuštění nového pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Pracovní postup obnovit](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [Ukončit pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> K vytvoření databáze trvalost  
  
1.  Otevřete SQL Server Management Studio a připojte se k místnímu serveru, například **. \SQLEXPRESS**. Klikněte pravým tlačítkem myši **databáze** uzlu na místním serveru a vyberte **novou databázi**. Název nové databáze **WF45GettingStartedTutorial**přijměte všechny ostatní hodnoty a vyberte **OK**.  
  
    > [!NOTE]
    >  Ujistěte se, že máte **Create Database** oprávnění na místním serveru před vytvořením databáze.  
  
2.  Zvolte **otevřete**, **soubor** z **souboru** nabídky. Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
     Vyberte následující dva soubory a klikněte na **otevřete**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3.  Zvolte **SqlWorkflowInstanceStoreSchema.sql** z **okno** nabídky. Ujistěte se, že **WF45GettingStartedTutorial** je vybraný v **dostupné databáze** rozevíracího seznamu a vyberte **Execute** z **dotazu**nabídky.  
  
4.  Zvolte **SqlWorkflowInstanceStoreLogic.sql** z **okno** nabídky. Ujistěte se, že **WF45GettingStartedTutorial** je vybraný v **dostupné databáze** rozevíracího seznamu a vyberte **Execute** z **dotazu**nabídky.  
  
    > [!WARNING]
    >  Je důležité k provedení předchozí dva kroky ve správném pořadí. Pokud dotazy jsou spouštěny mimo pořadí, dojde k chybám a trvalost databáze není správně nakonfigurováno.  
  
###  <a name="BKMK_AddReference"></a> Chcete-li přidat odkaz na sestavení DurableInstancing  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a vyberte **přidat odkaz na**.  
  
2.  Vyberte **sestavení** z **přidat odkaz na** seznam a typ `DurableInstancing` do **hledání sestavení** pole. To filtruje sestavení a usnadňuje vyberte požadované odkazy.  
  
3.  Zaškrtněte políčko vedle položky **System.Activities.DurableInstancing** a **System.Runtime.DurableInstancing** z **výsledky hledání** seznamu a klikněte na tlačítko **OK**.  
  
###  <a name="BKMK_CreateForm"></a> Vytvoření pracovního postupu hostitele formuláře  
  
> [!NOTE]
>  Kroky v tomto postupu popisují, jak přidat a nakonfigurovat formuláře ručně. V případě potřeby můžete stáhnout soubory řešení pro tento kurz a přidejte dokončené formuláře do projektu. Si můžete stáhnout kurz soubory [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976). Po stažení souborů, klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a zvolte **přidat odkaz na**. Přidat odkaz na **System.Windows.Forms** a **System.Drawing**. Tyto odkazy se přidávají automaticky, pokud přidáte nový formulář z **přidat**, **nová položka** nabídce, ale musí být při importu formuláře přidat ručně. Jakmile jsou přidány odkazy, klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **přidat**, **existující položka**. Vyhledejte `Form` složky v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm.vb**) a klikněte na tlačítko **přidat**. Pokud se rozhodnete importovat formuláře a potom dolů na další část, můžete přeskočit [přidat vlastnosti a metody helper formuláře](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **přidat**, **novou položku**.  
  
2.  V **nainstalovaná** šablony vyberte **formuláře Windows**, typ `WorkflowHostForm` v **název** pole a klikněte na tlačítko **přidat**.  
  
3.  Nakonfigurujte následující vlastnosti na formuláři.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Velikost|400, 420|  
  
4.  Přidejte následující ovládací prvky na formuláři v pořadí zadaný a konfigurovat vlastnosti podle pokynů.  
  
    |Ovládací prvek|Vlastnost: hodnota|  
    |-------------|---------------------|  
    |**Tlačítko**|Název: NewGame<br /><br /> Umístění: 13, 13<br /><br /> Velikost: 75, 23<br /><br /> Text: Nová hra|  
    |**Popisek**|Umístění: 94, 18<br /><br /> Text: Číslo od 1 do uhodnout|  
    |**ComboBox**|Název: NumberRange<br /><br /> DropDownStyle: rozevírací seznam<br /><br /> Položek: 10, 100, 1000<br /><br /> Umístění: 228, 12<br /><br /> Velikost: 143, 21|  
    |**Popisek**|Umístění: 13, 43<br /><br /> Text: Typ pracovního postupu|  
    |**ComboBox**|Název: WorkflowType<br /><br /> DropDownStyle: rozevírací seznam<br /><br /> Položky: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow,<br /><br /> Umístění: 94, 40<br /><br /> Velikost: 277, 21|  
    |**Popisek**|Název: WorkflowVersion<br /><br /> Umístění: 13, 362<br /><br /> Text: Verze pracovního postupu|  
    |**GroupBox**|Umístění: 13, 67<br /><br /> Velikost: 358, 287<br /><br /> Text: hra|  
  
    > [!NOTE]
    >  Při přidávání následující ovládací prvky, umístí je do skupině.  
  
    |Ovládací prvek|Vlastnost: hodnota|  
    |-------------|---------------------|  
    |**Popisek**|Umístění: 7, 20<br /><br /> Text: Id Instance pracovního postupu|  
    |**ComboBox**|Název: identifikátor InstanceId<br /><br /> DropDownStyle: rozevírací seznam<br /><br /> Umístění: 121, 17<br /><br /> Velikost: 227, 21|  
    |**Popisek**|Umístění: 7, 47<br /><br /> Text: uhodnout|  
    |**TextBox**|Název: uhodnout<br /><br /> Umístění: 50, 44<br /><br /> Velikost: 65, 20|  
    |**Tlačítko**|Název: EnterGuess<br /><br /> Umístění: 121, 42<br /><br /> Velikost: 75, 23<br /><br /> Text: Odhad zadejte|  
    |**Tlačítko**|Název: QuitGame<br /><br /> Umístění: 274, 42<br /><br /> Velikost: 75, 23<br /><br /> Text: ukončení|  
    |**TextBox**|Název: argument WorkflowStatus<br /><br /> Umístění: 10, 73<br /><br /> Víceřádkových: True<br /><br /> Jen pro čtení: True<br /><br /> Posuvníky: svislé<br /><br /> Velikost: 338, 208|  
  
5.  Nastavte **AcceptButton** vlastnost formuláře **EnterGuess**.  
  
 Následující příklad ilustruje dokončené formuláře.  
  
 ![WF45 Začínáme kurz pracovního postupu hostitele formuláře](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
###  <a name="BKMK_AddHelperMethods"></a> Chcete-li přidat vlastnosti a metody helper formuláře  
 Postup v této části přidejte vlastnosti a pomocné metody do třídy formuláře, nakonfigurujete pro podporu systémem a obnovení workflowů číslo odhad rozhraní formuláře.  
  
1.  Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníku řešení** a zvolte **kód zobrazení**.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3.  Přidejte následující deklarace člena k **WorkflowHostForm** třídy.  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  Pokud připojovací řetězec je jiný, aktualizujte `connectionString` odkazovat na databázi.  
  
4.  Přidat `WorkflowInstanceId` vlastnost, která má `WorkflowFormHost` třídy.  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     `InstanceId` – Pole se seznamem zobrazí seznam identifikátorů instance pracovního postupu trvalý a `WorkflowInstanceId` vlastnost vrací aktuálně vybrané pracovní postup.  
  
5.  Přidejte obslužnou rutinu pro daný formulář `Load` události. Chcete-li přidat obslužná rutina, přepněte na **zobrazení návrhu** formulář, klikněte na **události** ikona v horní části **vlastnosti** okno a poklikejte na soubor **zatížení**.  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  Přidejte následující kód, který `WorkflowHostForm_Load`.  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     Při načtení formuláře, `SqlWorkflowInstanceStore` je nakonfigurován, výchozí hodnoty jsou nastaveny rozsah a pracovní postup typ pole se seznamem a instancí trvalou pracovních postupů jsou přidány do `InstanceId` – pole se seznamem.  
  
7.  Přidat `SelectedIndexChanged` obslužné rutiny pro `InstanceId`. Chcete-li přidat obslužná rutina, přepněte na **zobrazení návrhu** pro daný formulář, vyberte `InstanceId` – pole se seznamem, klikněte na tlačítko **události** ikona v horní části **vlastnosti** okno, a Klikněte dvakrát na **SelectedIndexChanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  Přidejte následující kód, který `InstanceId_SelectedIndexChanged`. Vždy, když uživatel vybere pracovního postupu pomocí pole se seznamem této obslužné rutiny aktualizace stavové okno.  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
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
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
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
    ```  
  
9. Přidejte následující `ListPersistedWorkflows` metodu do třídy formuláře.  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     `ListPersistedWorkflows` dotazuje úložiště instance k instancí trvalou pracovních postupů a přidá ID instance, které chcete `cboInstanceId` – pole se seznamem.  
  
10. Přidejte následující `UpdateStatus` metoda a odpovídající delegát třídy formuláře. Tato metoda aktualizuje stav aktuálně spuštěných pracovních postupů okně Stav na formuláři.  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. Přidejte následující `GameOver` metoda a odpovídající delegát třídy formuláře. Po dokončení pracovního postupu, tato metoda aktualizace formuláře uživatelského rozhraní odebráním id instance pracovního postupu dokončené z **identifikátor InstanceId** – pole se seznamem.  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> Ke konfiguraci úložiště instance, obslužné rutiny životního cyklu pracovního postupu a rozšíření  
  
1.  Přidat `ConfigureWorkflowApplication` metodu do třídy formuláře.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     Tato metoda nakonfiguruje `WorkflowApplication`, přidá požadované rozšíření a přidá obslužné rutiny pro události životního cyklu pracovního postupu.  
  
2.  V `ConfigureWorkflowApplication`, zadejte `SqlWorkflowInstanceStore` pro `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  Dále vytvořte `StringWriter` instance a přidejte ho do `Extensions` kolekce `WorkflowApplication`. Když `StringWriter` se přidá do rozšíření zachycení všechny `WriteLine` výstup aktivity. Když se stane nečinnosti, pracovní postup `WriteLine` výstup lze extrahovat z `StringWriter` a zobrazují na formuláři.  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4.  Přidejte následující obslužnou rutinu pro `Completed` událostí. Když pracovní postup úspěšně dokončí, stane se z počet přijatých tak snadno uhodnout číslo se zobrazí v okně Stav. Pokud pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení. Na konci obslužné rutiny `GameOver` metoda je volána, které dokončené pracovní postup odebere ze seznamu pracovního postupu.  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5.  Přidejte následující `Aborted` a `OnUnhandledException` obslužné rutiny. `GameOver` Metoda není volána z `Aborted` obslužná rutina vzhledem k tomu, že pokud byl přerušen instanci pracovního postupu, není ukončit a je možné obnovit instanci později.  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6.  Přidejte následující `PersistableIdle` obslužné rutiny. Tato rutina načte `StringWriter` extrahuje výstup z rozšíření, která byla přidána `WriteLine` aktivity a zobrazí v okně Stav.  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <xref:System.Activities.PersistableIdleAction> Výčet má tří hodnot: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, a <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> příčiny pracovního postupu zachovat ale nezpůsobí odpojení pracovního postupu. <xref:System.Activities.PersistableIdleAction.Unload> pracovní postup se zachovat a jej odpojit.  
  
     Následující příklad je dokončené `ConfigureWorkflowApplication` metoda.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
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
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
###  <a name="BKMK_WorkflowVersionMap"></a> Chcete-li povolit spuštění a obnovení více typů pracovního postupu  
 Chcete-li obnovit instanci pracovního postupu, hostitel má zajistit definice pracovního postupu. V tomto kurzu existují tři typy pracovního postupu a následné kroky kurzu zavádět několik verzí z těchto typů. `WorkflowIdentity` poskytuje způsob, jak hostitelskou aplikaci přidružení identifikační informace k instanci pracovního postupu trvalý. Postup v této části ukazují, jak vytvořit třídu nástroj vám pomůže při mapování identitu pracovního postupu z instance pracovního postupu trvalou na odpovídající definice pracovního postupu. Další informace o `WorkflowIdentity` a správu verzí, najdete v části [pomocí WorkflowIdentity a správa verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **přidat**, **třída**. Typ `WorkflowVersionMap` do **název** pole a klikněte na tlačítko **přidat**.  
  
2.  Přidejte následující `using` nebo `Imports` příkazy v horní části souboru k ostatním `using` nebo `Imports` příkazy.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  Nahraďte `WorkflowVersionMap` deklarace s následující deklaraci třídy.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
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
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
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
  
     `WorkflowVersionMap` obsahuje tři pracovní postup identit, které jsou mapovány na tři definice pracovního postupu z tohoto kurzu a se používá v následujících částech, když jsou pracovní postupy spuštěny a byl obnoven.  
  
###  <a name="BKMK_StartWorkflow"></a> Spuštění nového pracovního postupu  
  
1.  Přidat `Click` obslužné rutiny pro `NewGame`. Chcete-li přidat obslužná rutina, přepněte na **zobrazení návrhu** pro formulář a poklikejte na soubor `NewGame`. A `NewGame_Click` přidání obslužné rutiny a zobrazení přepne do zobrazení kódu pro daný formulář. Vždy, když uživatel klikne na toto tlačítko je spuštěn nový pracovní postup.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Přidejte následující kód do obslužná rutina kliknutí na. Tento kód vytvoří slovník vstupní argumenty pro pracovní postup, klíčovány pomocí názvu argument. Tohoto slovníku má jednu položku, která obsahuje řadu náhodně generovaným číslem načtena z pole se seznamem rozsahu.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  Dál přidejte následující kód, který spustí pracovní postup. `WorkflowIdentity` a odpovídající typ pracovního postupu vybrali definice pracovního postupu se načítají pomocí `WorkflowVersionMap` pomocná třída. Další, nové `WorkflowApplication` instance je vytvořený pomocí definice pracovního postupu `WorkflowIdentity`a slovníku vstupní argumenty.  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4.  Dál přidejte následující kód, který přidá pracovního postupu do seznamu pracovního postupu a zobrazí informace o verzi pracovního postupu na formuláři.  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5.  Volání `ConfigureWorkflowApplication` konfigurace instance úložiště, rozšíření a pracovní postup životního cyklu obslužných rutin pro tento `WorkflowApplication` instance.  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6.  Nakonec volání `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     Následující příklad je dokončené `NewGame_Click` obslužné rutiny.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
###  <a name="BKMK_ResumeWorkflow"></a> Pracovní postup obnovit  
  
1.  Přidat `Click` obslužné rutiny pro `EnterGuess`. Chcete-li přidat obslužná rutina, přepněte na **zobrazení návrhu** pro formulář a poklikejte na soubor `EnterGuess`. Vždy, když uživatel klikne na toto tlačítko je obnoven běh pracovního postupu.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Přidejte následující kód do Ujistěte se, zda je pracovní postup vybrán v seznamu pracovního postupu, a zda je odhad uživatele platná.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3.  V dalším kroku načíst `WorkflowApplicationInstance` instance trvalou pracovního postupu. A `WorkflowApplicationInstance` představuje instanci trvalou pracovního postupu, který ještě nebyl přidružen definice pracovního postupu. `DefinitionIdentity` z `WorkflowApplicationInstance` obsahuje `WorkflowIdentity` instance trvalou pracovního postupu. V tomto kurzu `WorkflowVersionMap` nástroj třída se používá k mapování `WorkflowIdentity` k definici správné pracovního postupu. Jakmile je načtena definice pracovního postupu, `WorkflowApplication` je vytvořený pomocí definice správné pracovního postupu.  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4.  Jednou `WorkflowApplication` je vytvořen, konfigurovat úložiště instance, obslužné rutiny životního cyklu pracovního postupu a rozšíření voláním `ConfigureWorkflowApplication`. Tyto kroky je nutné provést pokaždé, když nový `WorkflowApplication` je vytvořen, a je třeba provést před k instanci pracovního postupu je načten do `WorkflowApplication`. Po načtení pracovního postupu je pokračuje s odhad uživatele.  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5.  Nakonec vymažte textového pole odhad a příprava formuláře tak, aby přijímal jiné odhad.  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     Následující příklad je dokončené `EnterGuess_Click` obslužné rutiny.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
###  <a name="BKMK_TerminateWorkflow"></a> Ukončit pracovního postupu  
  
1.  Přidat `Click` obslužné rutiny pro `QuitGame`. Chcete-li přidat obslužná rutina, přepněte na **zobrazení návrhu** pro formulář a poklikejte na soubor `QuitGame`. Vždy, když uživatel klikne na toto tlačítko je ukončen aktuálně vybrané pracovní postup.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Přidejte následující kód, který `QuitGame_Click` obslužné rutiny. Tento kód se nejdřív zkontroluje, zda pracovní postup je vybrán v seznamu pracovního postupu. Potom načte z trvalého instance `WorkflowApplicationInstance`, používá `DefinitionIdentity` k určení definice pracovního postupu správný a pak inicializuje `WorkflowApplication`. Další rozšíření a obslužné rutiny životního cyklu pracovního postupu jsou nakonfigurovány s volání `ConfigureWorkflowApplication`. Jednou `WorkflowApplication` je nakonfigurován, je načten a potom `Terminate` je volána.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> Sestavení a spuštění aplikace  
  
1.  Klikněte dvakrát na **Program.cs** (nebo **Module1.vb**) v **Průzkumníku řešení** zobrazíte kód.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Odeberte nebo komentář existující pracovní postup hostování kód z [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)a nahraďte ji následujícím kódem.  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **vlastnosti**. V **aplikace** zadejte **aplikace Windows** pro **výstupní typ**. Tento krok je volitelný, ale pokud není postupovali podle kromě formulář se zobrazí v okně konzoly.  
  
5.  Stisknutím kombinace kláves Ctrl + Shift + B pro sestavení aplikace.  
  
6.  Ujistěte se, že **NumberGuessWorkflowHost** je nastavena jako při spuštění aplikace a stiskněte klávesu Ctrl + F5 a spusťte aplikaci.  
  
7.  Vyberte rozsah hádání hry a typ pracovního postupu spustit, a klikněte na **nové herní**. Zadejte odhad v **odhad** pole a klikněte na tlačítko **přejděte** odeslat vaše odhad. Všimněte si, že výstupem `WriteLine` aktivity se zobrazí na formuláři.  
  
8.  Spusťte několik pracovních postupů pomocí pracovního postupu různé typy a počet rozsahů, zadejte některé pokusů a přepínat mezi výběrem z pracovních postupů **Id Instance pracovního postupu** seznamu.  
  
     Všimněte si, že při přepnutí do nového pracovního postupu předchozí pokusů a průběh pracovního postupu nejsou zobrazeny v okně Stav. Důvod stavu není k dispozici je, protože není zachytit a uložit kdekoli. V dalším kroku kurzu [postupy: vytvoření vlastní sledování účastník](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), vytvoříte vlastní sledování člena, který uloží tyto informace.
