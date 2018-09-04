---
title: 'Postupy: vytvoření a spuštění dlouhodobého spuštění pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 2c3368bc73d54f2848cad3c1086b1d9733205d2b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556636"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Postupy: vytvoření a spuštění dlouhodobého spuštění pracovního postupu
Jednou z centrální funkcí Windows Workflow Foundation (WF) je modul runtime schopnost zachovat a uvolnit nečinných pracovních postupů k databázi. Kroky v [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) jsme vám ukázali základní informace o hostování pracovního postupu pomocí konzolové aplikace. Příklady zobrazila počáteční pracovní postupy, obslužné rutiny pracovních postupů životního cyklu a obnovení záložky. Ukázání efektivně trvalost pracovního postupu, se vyžaduje složitější hostitele pracovního postupu, který podporuje spouštění a obnovení několika instancí pracovních postupů. Tento krok úvodního kurzu ukazuje, jak vytvořit hostitele formuláře Windows, aplikace, která podporuje spouštění a obnovení několika instancí pracovních postupů, trvalost pracovního postupu a poskytuje základ pro pokročilé funkce, jako je sledování a správy verzí, které jsou jsme vám ukázali v následných kroků v kurzu.  
  
> [!NOTE]
>  Tento kurz – krok a všechny následné kroky použít všechny tři typy pracovních postupů z [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md). Pokud jste neprovedli všechny tři typy můžete stáhnout úplnou verzi kroky z [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [K vytvoření databáze trvalosti](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [Chcete-li přidat odkaz na sestavení DurableInstancing](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [Chcete-li vytvořit formulář hostitele pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Chcete-li přidat vlastnosti a metody helper formuláře](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Ke konfiguraci úložiště instancí, obslužné rutiny pracovních postupů životního cyklu a rozšíření](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Povolit spuštění a obnovení více typy pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Spuštění nového pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Pracovní postup obnovit](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [K ukončení pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> K vytvoření databáze trvalosti  
  
1.  Otevřete SQL Server Management Studio a připojte se k místnímu serveru, třeba **. \SQLEXPRESS**. Klikněte pravým tlačítkem myši **databází** uzlu na místním serveru a vyberte **novou databázi**. Název nové databáze **WF45GettingStartedTutorial**přijměte všechny ostatní hodnoty a vyberte **OK**.  
  
    > [!NOTE]
    >  Ujistěte se, že máte **Create Database** oprávnění na místním serveru před vytvořením databáze.  
  
2.  Zvolte **otevřít**, **souboru** z **souboru** nabídky. Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`  
  
     Vyberte následující dva soubory a klikněte na tlačítko **otevřít**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3.  Zvolte **SqlWorkflowInstanceStoreSchema.sql** z **okno** nabídky. Ujistěte se, že **WF45GettingStartedTutorial** výběru v **dostupných databází** rozevírací seznam a zvolte **Execute** z **dotazu**nabídky.  
  
4.  Zvolte **SqlWorkflowInstanceStoreLogic.sql** z **okno** nabídky. Ujistěte se, že **WF45GettingStartedTutorial** výběru v **dostupných databází** rozevírací seznam a zvolte **Execute** z **dotazu**nabídky.  
  
    > [!WARNING]
    >  Je důležité provést předchozí dva kroky ve správném pořadí. Pokud dotazy provádějí mimo pořadí, dojde k chybám a databáze trvalosti není správně nakonfigurována.  
  
###  <a name="BKMK_AddReference"></a> Chcete-li přidat odkaz na sestavení DurableInstancing  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a vyberte **přidat odkaz**.  
  
2.  Vyberte **sestavení** z **přidat odkaz** a do pole `DurableInstancing` do **hledání sestavení** pole. Tím se filtruje sestavení a usnadňuje vyberte požadované odkazy.  
  
3.  Zaškrtněte políčko vedle **System.Activities.DurableInstancing** a **System.Runtime.DurableInstancing** z **výsledky hledání** seznamu a klikněte na tlačítko **OK**.  
  
###  <a name="BKMK_CreateForm"></a> Chcete-li vytvořit formulář hostitele pracovního postupu  
  
> [!NOTE]
>  Kroky v tomto postupu popisují, jak přidat a nakonfigurovat formuláře ručně. V případě potřeby můžete stáhnout soubory řešení pro tento kurz a přidejte dokončené formuláře do projektu. Stáhněte si kurz soubory, naleznete v tématu [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976). Jakmile se soubory stáhnou, klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a zvolte **přidat odkaz**. Přidejte odkaz na **System.Windows.Forms** a **System.Drawing**. Tyto odkazy jsou přidány automaticky, pokud chcete přidat nového formuláře pomocí **přidat**, **nová položka** nabídky, ale musí přidat ručně, při importu formuláře. Jakmile jsou přidány odkazy, klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **existující položku**. Přejděte `Form` složky v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm.vb**) a klikněte na tlačítko **přidat**. Pokud se rozhodnete importovat formuláři a pak dolů na další část, můžete přeskočit [přidat vlastnosti a metody helper formuláře](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **nová položka**.  
  
2.  V **nainstalováno** šablon klikněte na položku **formuláře Windows**, typ `WorkflowHostForm` v **název** pole a klikněte na tlačítko **přidat**.  
  
3.  Konfigurujte následující vlastnosti ve formuláři.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Velikost|400, 420|  
  
4.  Přidejte následující ovládací prvky do formuláře v pořadí zadaný a nakonfigurujte vlastnosti, podle pokynů.  
  
    |Ovládací prvek|Vlastnosti: hodnota|  
    |-------------|---------------------|  
    |**Tlačítko**|Název: NewGame<br /><br /> Umístění: 13, 13<br /><br /> Velikost: 75, 23<br /><br /> Text: Novou hru|  
    |**Popisek**|Umístění: 94, 18<br /><br /> Text: Číslo od 1 do uhodnout|  
    |**ComboBox**|Název: NumberRange<br /><br /> DropDownStyle: DropDownList<br /><br /> Položek: 10, 100, 1 000<br /><br /> Umístění: 228, 12<br /><br /> Velikost: 143, 21|  
    |**Popisek**|Umístění: 13, 43<br /><br /> Text: Typ pracovního postupu|  
    |**ComboBox**|Název: WorkflowType<br /><br /> DropDownStyle: DropDownList<br /><br /> Položky: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow FlowchartNumberGuessWorkflow,<br /><br /> Umístění: 94, 40<br /><br /> Velikost: 277, 21|  
    |**Popisek**|Název: WorkflowVersion<br /><br /> Umístění: 13, 362<br /><br /> Text: Verze pracovního postupu|  
    |**GroupBox**|Umístění: 13, 67<br /><br /> Velikost: 358, 287<br /><br /> Text: hra|  
  
    > [!NOTE]
    >  Při přidávání následující ovládací prvky, vytvořte z nich skupině.  
  
    |Ovládací prvek|Vlastnosti: hodnota|  
    |-------------|---------------------|  
    |**Popisek**|Umístění: 7, 20<br /><br /> Text: Id Instance pracovního postupu|  
    |**ComboBox**|Název: InstanceId<br /><br /> DropDownStyle: DropDownList<br /><br /> Umístění: 121, 17<br /><br /> Velikost: 227, 21|  
    |**Popisek**|Umístění: 7, 47<br /><br /> Text: odhad|  
    |**TextBox**|Název: odhad<br /><br /> Umístění: 50, 44<br /><br /> Velikost: 65, 20|  
    |**Tlačítko**|Název: EnterGuess<br /><br /> Umístění: 121, 42<br /><br /> Velikost: 75, 23<br /><br /> Text: Zadejte odhad|  
    |**Tlačítko**|Název: QuitGame<br /><br /> Umístění: 274, 42<br /><br /> Velikost: 75, 23<br /><br /> Text: ukončení|  
    |**TextBox**|Název: WorkflowStatus<br /><br /> Umístění: 10, 73<br /><br /> Multiline: True<br /><br /> Jen pro čtení: True<br /><br /> Posuvníky: svislý<br /><br /> Velikost: 338, 208|  
  
5.  Nastavte **AcceptButton** vlastnost formuláře **EnterGuess**.  
  
 Následující příklad ukazuje dokončený formulář.  
  
 ![WF45 Formulář hostitele pracovního postupu kurz Začínáme se službou](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
###  <a name="BKMK_AddHelperMethods"></a> Chcete-li přidat vlastnosti a metody helper formuláře  
 Kroky v této části přidejte do třídy formuláře, která konfigurace uživatelského rozhraní ve formuláři pro podporu spouštění a obnovení workflowů číslo odhad vlastnosti a metody helper.  
  
1.  Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
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
  
3.  Přidejte následující deklarace členů na **WorkflowHostForm** třídy.  
  
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
    >  Pokud váš připojovací řetězec se liší, aktualizujte `connectionString` odkázat na databázi.  
  
4.  Přidat `WorkflowInstanceId` vlastnost `WorkflowFormHost` třídy.  
  
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
  
     `InstanceId` – Pole se seznamem se zobrazí seznam identifikátorů instance trvalá pracovního postupu a `WorkflowInstanceId` vlastnost vrátí aktuálně vybraný pracovní postup.  
  
5.  Přidání obslužné rutiny pro formulář `Load` událostí. Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** formuláře, klikněte na tlačítko **události** ikonu v horní části **vlastnosti** okno a dvakrát klikněte na **zatížení**.  
  
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
  
     Při načtení formuláře, `SqlWorkflowInstanceStore` je nakonfigurován, rozsahu a pracovní postup polí se seznamem typ jsou nastaveny na výchozí hodnoty a instance trvalá pracovního postupu jsou přidány do `InstanceId` – pole se seznamem.  
  
7.  Přidat `SelectedIndexChanged` obslužné rutiny pro `InstanceId`. Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** formuláře, vyberte `InstanceId` – pole se seznamem, klikněte na tlačítko **události** ikonu v horní části **vlastnosti** okna, a dvakrát klikněte na panel **SelectedIndexChanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  Přidejte následující kód, který `InstanceId_SelectedIndexChanged`. Pokaždé, když uživatel vybere pracovního postupu pomocí pole se seznamem touto obslužnou rutinou aktualizace stavové okno.  
  
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
  
     `ListPersistedWorkflows` dotazy v úložišti instancí pro instance trvalá pracovního postupu a přidá ID instance do `cboInstanceId` – pole se seznamem.  
  
10. Přidejte následující `UpdateStatus` metoda a odpovídající delegát třídy formuláře. Tato metoda aktualizuje stav aktuálně spuštěné pracovního postupu stavové okno, ve formuláři.  
  
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
  
11. Přidejte následující `GameOver` metoda a odpovídající delegát třídy formuláře. Po dokončení pracovního postupu, tato metoda aktualizuje formulář, uživatelského rozhraní tak, že odeberete id instance pracovního postupu dokončená z **InstanceId** – pole se seznamem.  
  
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
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> Ke konfiguraci úložiště instancí, obslužné rutiny pracovních postupů životního cyklu a rozšíření  
  
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
  
     Tato metoda nakonfiguruje `WorkflowApplication`, přidá požadované rozšíření a přidá obslužné rutiny pro pracovní postup události životního cyklu.  
  
2.  V `ConfigureWorkflowApplication`, zadejte `SqlWorkflowInstanceStore` pro `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  Dále vytvořte `StringWriter` instance a přidejte ho do `Extensions` kolekce `WorkflowApplication`. Když `StringWriter` se přidá do rozšíření zachytí všechny `WriteLine` výstup aktivity. Při pracovního postupu změní nečinnosti, `WriteLine` výstup může být extrahována z `StringWriter` a zobrazí ve formuláři.  
  
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
  
4.  Přidejte následující obslužnou rutinu pro `Completed` událostí. Po úspěšném dokončení pracovního postupu změní počet přijatých uhodnutelné číslo se zobrazí v okně Stav. Pokud pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení. Na konci obslužné rutiny `GameOver` metoda je volána, která odebere ze seznamu pracovní postup dokončený pracovní postup.  
  
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
  
5.  Přidejte následující `Aborted` a `OnUnhandledException` obslužné rutiny. `GameOver` Metoda není volána z `Aborted` obslužná rutina protože při instanci pracovního postupu byla přerušena, nebyl ukončen a je možné obnovit instanci později.  
  
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
  
6.  Přidejte následující `PersistableIdle` obslužné rutiny. Tato obslužná rutina načte `StringWriter` rozšíření, které jste přidali, extrahuje výstup `WriteLine` aktivity a zobrazí jej v okně Stav.  
  
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
  
     <xref:System.Activities.PersistableIdleAction> Výčet má tři hodnoty: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, a <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> způsobí, že pracovní postup a zachová jej ale nezpůsobí odpojení pracovního postupu. <xref:System.Activities.PersistableIdleAction.Unload> způsobí, že pracovní postup zachovat a být uvolněna.  
  
     V následujícím příkladu je dokončené `ConfigureWorkflowApplication` metody.  
  
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
  
###  <a name="BKMK_WorkflowVersionMap"></a> Povolit spuštění a obnovení více typy pracovních postupů  
 Aby bylo možné obnovit do instance pracovního postupu, že hostitel má poskytnout definici pracovního postupu. V tomto kurzu jsou tři typy pracovních postupů a dalších kroků kurzu zavést více verzí z těchto typů. `WorkflowIdentity` poskytuje způsob pro hostitelskou aplikaci přidružit identifikační údaje trvalé instance práce. Kroky v této části ukazují, jak vytvořit nástroj třídu, která vám pomůže s mapování identita pracovního postupu z trvalé instance práce na odpovídající definici pracovního postupu. Další informace o `WorkflowIdentity` a správy verzí, naleznete v tématu [použití WorkflowIdentity a správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **třídy**. Typ `WorkflowVersionMap` do **název** pole a klikněte na tlačítko **přidat**.  
  
2.  Přidejte následující `using` nebo `Imports` příkazů v horní části souboru k ostatním `using` nebo `Imports` příkazy.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  Nahradit `WorkflowVersionMap` deklarace s následující deklaraci třídy.  
  
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
  
     `WorkflowVersionMap` obsahuje tři identity pracovního postupu, které se mapují do tří definice pracovního postupu z tohoto kurzu a používá v následujících částech se při zahájení a obnovení pracovních postupů.  
  
###  <a name="BKMK_StartWorkflow"></a> Spuštění nového pracovního postupu  
  
1.  Přidat `Click` obslužné rutiny pro `NewGame`. Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** pro formulář a dvakrát klikněte na `NewGame`. A `NewGame_Click` přidání obslužné rutiny a zobrazení se přepne do zobrazení kódu pro formulář. Pokaždé, když uživatel stiskne toto tlačítko je spuštěn nový pracovní postup.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Přidejte následující kód do obslužné rutiny kliknutí. Tento kód vytvoří slovník vstupní argumenty pro pracovní postup, s klíči název argumentu. Tento slovník obsahuje jednu položku, která obsahuje řadu náhodně generované číslo z rozsahu pole se seznamem načíst.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  V dalším kroku přidejte následující kód, který se spustí pracovní postup. `WorkflowIdentity` a odpovídající typu pracovního postupu vybrali definice pracovního postupu se načítají pomocí `WorkflowVersionMap` pomocná třída. Další, nové `WorkflowApplication` pomocí definice pracovního postupu je vytvořena instance `WorkflowIdentity`a slovníku vstupní argumenty.  
  
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
  
4.  Dále přidejte následující kód, který přidá pracovní postup do seznamu pracovního postupu a zobrazí informace o verzi pro pracovní postupy ve formuláři.  
  
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
  
5.  Volání `ConfigureWorkflowApplication` konfigurace instance úložiště, rozšíření a pracovních postupů životního cyklu obslužných rutin pro tento `WorkflowApplication` instance.  
  
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
  
6.  Nakonec proveďte volání `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     V následujícím příkladu je dokončené `NewGame_Click` obslužné rutiny.  
  
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
  
1.  Přidat `Click` obslužné rutiny pro `EnterGuess`. Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** pro formulář a dvakrát klikněte na `EnterGuess`. Pokaždé, když uživatel stiskne toto tlačítko se obnoví pracovní postup.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Přidejte následující kód k zajištění, že pracovní postup je vybrali v seznamu pracovního postupu a že odhad uživatele je platný.  
  
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
  
3.  V dalším kroku načíst `WorkflowApplicationInstance` instance trvalá pracovního postupu. A `WorkflowApplicationInstance` představuje trvalé instance práce, který ještě nebyl přidružen s definicí pracovního postupu. `DefinitionIdentity` z `WorkflowApplicationInstance` obsahuje `WorkflowIdentity` instance trvalá pracovního postupu. V tomto kurzu `WorkflowVersionMap` utility třída se používá k mapování `WorkflowIdentity` k definici pracovního postupu správné. Jakmile je načtena definice pracovního postupu, `WorkflowApplication` je vytvořený pomocí definice pracovního postupu správné.  
  
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
  
4.  Jakmile `WorkflowApplication` je vytvořený, nakonfigurujte úložiště instancí, obslužné rutiny pracovních postupů životního cyklu a rozšíření voláním `ConfigureWorkflowApplication`. Tyto kroky je nutné provést pokaždé, když se nový `WorkflowApplication` se vytvoří a je třeba provést před načtením do instance pracovního postupu `WorkflowApplication`. Po načtení pracovního postupu se obnoví se uživatele.  
  
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
  
5.  A konečně zrušte textové pole odhad a připravte formuláře tak, aby přijímal jiného odhad.  
  
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
  
     V následujícím příkladu je dokončené `EnterGuess_Click` obslužné rutiny.  
  
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
  
###  <a name="BKMK_TerminateWorkflow"></a> K ukončení pracovního postupu  
  
1.  Přidat `Click` obslužné rutiny pro `QuitGame`. Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** pro formulář a dvakrát klikněte na `QuitGame`. Pokaždé, když uživatel stiskne toto tlačítko se ukončí aktuálně vybraného pracovního postupu.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Přidejte následující kód, který `QuitGame_Click` obslužné rutiny. Tento kód nejprve zkontroluje, zda pracovní postup je vybrán v seznamu pracovního postupu. Následně načte do trvalé instanci `WorkflowApplicationInstance`, používá `DefinitionIdentity` k určení definice pracovního postupu správný a potom inicializuje `WorkflowApplication`. Další rozšíření a obslužné rutiny pracovních postupů životního cyklu jsou nakonfigurovány s volání `ConfigureWorkflowApplication`. Jednou `WorkflowApplication` je nakonfigurován, je načten a potom `Terminate` je volána.  
  
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
  
1.  Dvakrát klikněte na panel **Program.cs** (nebo **Module1.vb**) v **Průzkumníka řešení** zobrazíte kód této.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Odstranit nebo okomentovat hostování kódu z existujícího pracovního postupu [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)a nahraďte ho následujícím kódem.  
  
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
  
4.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **vlastnosti**. V **aplikace** kartu, zadejte **aplikace Windows** pro **typ výstupu**. Tento krok je volitelný, ale pokud se nedodrží kromě formuláři se zobrazí v okně konzoly.  
  
5.  Stiskněte kombinaci kláves Ctrl + Shift + B pro sestavení aplikace.  
  
6.  Ujistěte se, že **NumberGuessWorkflowHost** je nastavena jako při spuštění aplikace a stiskněte klávesu Ctrl + F5 spusťte aplikaci.  
  
7.  Vyberte oblast pro využití herních a typ pracovního postupu ke spouštění a klikněte na tlačítko **nová hra**. Zadejte odhad v **odhad** pole a klikněte na tlačítko **Přejít** k odeslání vašeho odhadu. Všimněte si, že výstup `WriteLine` aktivity se zobrazí ve formuláři.  
  
8.  Spustit několik pracovních postupů pomocí pracovního postupu různé typy a počet rozsahů, zadejte několik pokusů a přepínání pracovních postupů tak, že vyberete **Id Instance pracovního postupu** seznamu.  
  
     Všimněte si, že když přepnete do nového pracovního postupu, předchozí pokusů a průběh pracovního postupu nejsou zobrazeny v okně Stav. Z důvodů, proč stavu není k dispozici je, protože není zachycena a uloženy kdekoli. V dalším kroku kurzu [postupy: vytvoření vlastního účastníka sledování](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), vytvoření vlastního účastníka sledování, která ukládá tyto informace.
