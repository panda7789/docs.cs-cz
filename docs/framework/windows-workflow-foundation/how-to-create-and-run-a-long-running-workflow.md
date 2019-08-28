---
title: 'Postupy: Vytvoření a spuštění dlouhotrvajícího pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 15ee10120f4d4c92bdc95cb48cb3cb838f526343
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044380"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Postupy: Vytvoření a spuštění dlouhotrvajícího pracovního postupu

Jednou z ústředních funkcí programovací model Windows Workflow Foundation (WF) je schopnost modulu runtime uchovávat a uvolňovat nečinné pracovní postupy do databáze. Postup [: Spuštění pracovního postupu](how-to-run-a-workflow.md) ukázal základy hostování pracovního postupu pomocí konzolové aplikace. V příkladech se zobrazily počáteční pracovní postupy, obslužné rutiny životního cyklu pracovního postupu a obnovení záložek. Aby bylo možné předvést trvalost pracovního postupu efektivně, je zapotřebí složitější hostitel pracovního postupu, který podporuje spouštění a obnovování více instancí pracovního postupu. Tento krok v tomto kurzu ukazuje, jak vytvořit hostitelskou aplikaci Windows Form, která podporuje spouštění a obnovování více instancí pracovního postupu, trvalý pracovní postup a poskytuje základ pro pokročilé funkce, jako je například sledování a správa verzí, které jsou znázorněné v dalších krocích kurzu.

> [!NOTE]
> Tento krok kurzu a následné kroky používají všechny tři typy pracovních postupů v [následujících krocích: Vytvořte pracovní postup](how-to-create-a-workflow.md). Pokud jste nedokončili všechny tři typy, můžete si stáhnout dokončenou verzi kroků z [programovací model Windows Workflow Foundation (WF45) – začínáme kurzu](https://go.microsoft.com/fwlink/?LinkID=248976).

> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>V tomto tématu

- [Vytvoření databáze trvalosti](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)

- [Přidání odkazu na DurableInstancing sestavení](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)

- [Vytvoření formuláře hostitele pracovního postupu](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)

- [Přidání vlastností a pomocných metod formuláře](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)

- [Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)

- [Povolení spouštění a obnovování více typů pracovních postupů](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)

- [Spuštění nového pracovního postupu](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)

- [Obnovení pracovního postupu](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)

- [Ukončení pracovního postupu](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)

- [Sestavení a spuštění aplikace](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)

### <a name="BKMK_CreatePersistenceDatabase"></a>Vytvoření databáze trvalosti

1. Otevřete SQL Server Management Studio a připojte se k místnímu serveru, například **.\SQLEXPRESS**. Pravým tlačítkem myši klikněte na uzel **databáze** na místním serveru a vyberte možnost **Nová databáze**. Pojmenujte novou databázi **WF45GettingStartedTutorial**, přijměte všechny ostatní hodnoty a vyberte **OK**.

    > [!NOTE]
    > Před vytvořením databáze se ujistěte, že máte na místním serveru oprávnění **vytvořit databázi** .

2. V nabídce **soubor** vyberte **otevřít**, **soubor** . Přejděte do následující složky:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`

    Vyberte následující dva soubory a klikněte na **otevřít**.

    - SqlWorkflowInstanceStoreLogic.sql

    - SqlWorkflowInstanceStoreSchema.sql

3. V nabídce **okno** vyberte **SqlWorkflowInstanceStoreSchema. SQL** . V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .

4. V nabídce **okno** vyberte **SqlWorkflowInstanceStoreLogic. SQL** . V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .

    > [!WARNING]
    > Je důležité provést předchozí dva kroky ve správném pořadí. Pokud jsou dotazy spouštěny mimo pořadí, dojde k chybám a databáze trvalosti není správně nakonfigurována.

### <a name="BKMK_AddReference"></a>Přidání odkazu na DurableInstancing sestavení

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**.

2. Vyberte **sestavení** ze seznamu **Přidat odkaz** a zadejte `DurableInstancing` do pole **vyhledávací sestavení** . To filtruje sestavení a usnadňuje výběr požadovaných odkazů.

3. Zaškrtněte políčko vedle položky **System. Activities. DurableInstancing** a **System. Runtime. DurableInstancing** ze seznamu **výsledků hledání** a klikněte na tlačítko **OK**.

### <a name="BKMK_CreateForm"></a>Vytvoření formuláře hostitele pracovního postupu

> [!NOTE]
> Kroky v tomto postupu popisují, jak formulář Přidat a nakonfigurovat ručně. V případě potřeby si můžete stáhnout soubory řešení pro kurz a přidat dokončený formulář do projektu. Pokud si chcete stáhnout soubory kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976). Po stažení souborů klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**. Přidejte odkaz na **System. Windows. Forms** a **System. Drawing**. Tyto odkazy jsou přidány automaticky, pokud přidáte nový formulář z nabídky **Přidat**, **Nová položka** , ale je nutné jej přidat ručně při importu formuláře. Až budou odkazy přidány, klikněte pravým tlačítkem myši na **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat**, **existující položka**. Přejděte `Form` do složky v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm. vb**) a klikněte na **Přidat**. Pokud se rozhodnete importovat formulář, můžete přeskočit dolů k další části a [Přidat vlastnosti a pomocné metody formuláře](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Nová položka**.

2. V seznamu **nainstalované** šablony vyberte možnost **formulář Windows**, do pole `WorkflowHostForm` **název** zadejte a klikněte na tlačítko **Přidat**.

3. Ve formuláři nakonfigurujte následující vlastnosti.

    |Vlastnost|Value|
    |--------------|-----------|
    |FormBorderStyle|FixedSingle|
    |MaximizeBox|False|
    |Velikost|400, 420|

4. Do formuláře přidejte následující ovládací prvky v zadaném pořadí a nakonfigurujte vlastnosti jako směrované.

    |Control|Majetek Value|
    |-------------|---------------------|
    |**Tlačítko**|Jméno: NewGame<br /><br /> Oblasti 13, 13<br /><br /> Hodnota 75, 23<br /><br /> Text: Nová hra|
    |**Popisek**|Oblasti 94, 18<br /><br /> Text: Odhadnout číslo od 1 do|
    |**ComboBox**|Jméno: NumberRange<br /><br /> DropDownStyle: Rozevírací<br /><br /> Položek 10, 100, 1000<br /><br /> Oblasti 228, 12<br /><br /> Hodnota 143, 21|
    |**Popisek**|Oblasti 13, 43<br /><br /> Text: Typ pracovního postupu|
    |**ComboBox**|Jméno: WorkflowType<br /><br /> DropDownStyle: Rozevírací<br /><br /> Položek StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Oblasti 94, 40<br /><br /> Hodnota 277, 21|
    |**Popisek**|Jméno: WorkflowVersion<br /><br /> Oblasti 13, 362<br /><br /> Text: Verze pracovního postupu|
    |**GroupBox**|Oblasti 13, 67<br /><br /> Hodnota 358, 287<br /><br /> Text: Lovu|

    > [!NOTE]
    > Při přidávání následujících ovládacích prvků Umístěte tyto ovládací prvky do skupinového rámečku.

    |Control|Majetek Value|
    |-------------|---------------------|
    |**Popisek**|Oblasti 7, 20<br /><br /> Text: ID instance pracovního postupu|
    |**ComboBox**|Jméno: InstanceId<br /><br /> DropDownStyle: Rozevírací<br /><br /> Oblasti 121, 17<br /><br /> Hodnota 227, 21|
    |**Popisek**|Oblasti 7, 47<br /><br /> Text: Odhalit|
    |**TextBox**|Jméno: Odhalit<br /><br /> Oblasti 50, 44<br /><br /> Hodnota 65, 20|
    |**Tlačítko**|Jméno: EnterGuess<br /><br /> Oblasti 121, 42<br /><br /> Hodnota 75, 23<br /><br /> Text: Zadejte odhad|
    |**Tlačítko**|Jméno: QuitGame<br /><br /> Oblasti 274, 42<br /><br /> Hodnota 75, 23<br /><br /> Text: Ukončit|
    |**TextBox**|Jméno: WorkflowStatus<br /><br /> Oblasti 10, 73<br /><br /> Víceřádkový Pravda<br /><br /> ReadOnly Pravda<br /><br /> Posuvníky Svislé<br /><br /> Hodnota 338, 208|

5. Nastavte vlastnost **AcceptButton** formuláře na **EnterGuess**.

 Následující příklad znázorňuje dokončený formulář.

 ![Snímek obrazovky programovací model Windows Workflow Foundation formuláře hostitele pracovního postupu.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

### <a name="BKMK_AddHelperMethods"></a>Přidání vlastností a pomocných metod formuláře

Kroky v této části přidávají vlastnosti a pomocné metody do třídy formuláře, která konfiguruje uživatelské rozhraní formuláře tak, aby podporovalo spouštění a obnovování počtu vyčíslení pro odhadované pracovní postupy.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.

2. Do horní části `using` souboru přidejte `Imports`následující příkazy (nebo), které budou `using` příkazy (nebo `Imports`).

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

3. Do třídy **WorkflowHostForm** přidejte následující deklarace členů.

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
    > Pokud je váš připojovací řetězec jiný, aktualizujte `connectionString` , aby odkazoval na vaši databázi.

4. `WorkflowInstanceId` Přidejte vlastnost`WorkflowFormHost` do třídy.

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

    V `InstanceId` poli se seznamem se zobrazí seznam trvalých ID instancí pracovního postupu `WorkflowInstanceId` a vlastnost vrátí aktuálně vybraný pracovní postup.

5. Přidejte obslužnou rutinu pro událost `Load` formuláře. Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **načíst**.

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. Přidejte následující kód do `WorkflowHostForm_Load`.

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

    Když je formulář načtený `SqlWorkflowInstanceStore` , je nakonfigurovaný rozsah a typ pracovního postupu pole se seznamem na výchozí hodnoty a trvalé instance pracovního postupu se přidají `InstanceId` do pole se seznamem.

7. Přidejte obslužnou rutinu `InstanceId`pro. `SelectedIndexChanged` Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, vyberte `InstanceId` pole se seznamem, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **SelectedIndexChanged**.

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. Přidejte následující kód do `InstanceId_SelectedIndexChanged`. Vždy, když uživatel vybere pracovní postup pomocí pole se seznamem, tato obslužná rutina aktualizuje stavové okno.

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

9. Do třídy Form `ListPersistedWorkflows` přidejte následující metodu.

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

    `ListPersistedWorkflows`vyhledá v úložišti instancí trvalé instance pracovního postupu a přidá ID instancí do `cboInstanceId` pole se seznamem.

10. Do třídy Form `UpdateStatus` přidejte následující metodu a odpovídající delegát. Tato metoda aktualizuje stavové okno ve formuláři se stavem aktuálně spuštěného pracovního postupu.

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

11. Do třídy Form `GameOver` přidejte následující metodu a odpovídající delegát. Po dokončení pracovního postupu Tato metoda aktualizuje uživatelské rozhraní formuláře odebráním ID instance dokončeného pracovního postupu z pole se seznamem **InstanceId** .

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

### <a name="BKMK_ConfigureWorkflowApplication"></a>Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření

1. `ConfigureWorkflowApplication` Přidejte metodu do třídy Form.

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    Tato metoda konfiguruje `WorkflowApplication`, přidá požadovaná rozšíření a přidá obslužné rutiny pro události životního cyklu pracovního postupu.

2. V `ConfigureWorkflowApplication` Zadejte`SqlWorkflowInstanceStore` pro .`WorkflowApplication`

    ```vb
    'Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. Dále vytvořte `StringWriter` instanci a přidejte ji `Extensions` do kolekce `WorkflowApplication`. Když se přidá do rozšíření, zachytí všechny `WriteLine` výstupy aktivity. `StringWriter` Když je pracovní postup nečinný, `WriteLine` lze výstup extrahovat `StringWriter` z a zobrazeného ve formuláři.

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

4. Přidejte následující obslužnou rutinu pro `Completed` událost. Po úspěšném dokončení pracovního postupu se v okně stav zobrazí počet pokusů o odhadované číslo. Pokud se pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení. Na konci obslužné rutiny `GameOver` je volána metoda, která odebere dokončený pracovní postup ze seznamu pracovního postupu.

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

5. Přidejte následující `Aborted` obslužné rutiny a `OnUnhandledException` . Metoda není volána `Aborted` z obslužné rutiny, protože když je instance pracovního postupu přerušena, nekončí, a je možné instanci obnovit později. `GameOver`

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

6. Přidejte následující `PersistableIdle` obslužnou rutinu. Tato obslužná rutina `StringWriter` načte rozšíření, které bylo přidáno, extrahuje výstup `WriteLine` z aktivit a zobrazí jej v okně stav.

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

    Výčet má tři hodnoty: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>a <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction> <xref:System.Activities.PersistableIdleAction.Persist>způsobí, že pracovní postup zůstane zachován, ale nezpůsobí, že se pracovní postup uvolní. <xref:System.Activities.PersistableIdleAction.Unload>způsobí, že se pracovní postup uchová a uvolní.

    Následující příklad je dokončená `ConfigureWorkflowApplication` metoda.

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

### <a name="BKMK_WorkflowVersionMap"></a>Povolení spouštění a obnovování více typů pracovních postupů

Aby bylo možné obnovit instanci pracovního postupu, musí hostitel zadat definici pracovního postupu. V tomto kurzu existují tři typy pracovních postupů a další kroky kurzu představují více verzí těchto typů. `WorkflowIdentity`poskytuje způsob, jak může hostitelská aplikace přidružit identifikační informace k trvalé instanci pracovního postupu. Kroky v této části ukazují, jak vytvořit třídu nástrojů, která vám pomůže s mapováním identity pracovního postupu z trvalé instance pracovního postupu na odpovídající definici pracovního postupu. Další informace o `WorkflowIdentity` a verzi najdete v tématu [použití identita WorkflowIdentity a správy verzí](using-workflowidentity-and-versioning.md).

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Třída**. Do `WorkflowVersionMap` pole **název** zadejte a klikněte na **Přidat**.

2. Přidejte následující `using` příkazy nebo `Imports` v horní části souboru s ostatními `using` příkazy or `Imports` .

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Activities
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Activities;
    ```

3. Nahraďte `WorkflowVersionMap` deklaraci třídy následující deklarací.

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

    `WorkflowVersionMap`obsahuje tři identity pracovního postupu, které se mapují na tři definice pracovního postupu z tohoto kurzu a používají se v následujících oddílech při spuštění a obnovení pracovních postupů.

### <a name="BKMK_StartWorkflow"></a>Spuštění nového pracovního postupu

1. Přidejte obslužnou rutinu `NewGame`pro. `Click` Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na `NewGame`položku. Přidá `NewGame_Click` se obslužná rutina a zobrazení se přepne do zobrazení kódu pro formulář. Vždy, když uživatel klikne na toto tlačítko, je spuštěn nový pracovní postup.

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. Do obslužné rutiny Click přidejte následující kód. Tento kód vytvoří slovník vstupních argumentů pro pracovní postup, který je označen názvem argumentu. Tento slovník má jednu položku, která obsahuje rozsah náhodně generovaného čísla načteného z pole se seznamem rozsah.

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. Dále přidejte následující kód, který spustí pracovní postup. Definice pracovního postupu `WorkflowVersionMap` aodpovídajícítypuvybranéhopracovníhopostupusenačte`WorkflowIdentity` pomocí pomocné třídy. V dalším kroku se `WorkflowApplication` vytvoří nová instance pomocí definice pracovního postupu, `WorkflowIdentity`a slovníku vstupních argumentů.

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

4. Dále přidejte následující kód, který přidá pracovní postup do seznamu pracovních postupů a zobrazí informace o verzi pracovního postupu ve formuláři.

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

5. Zavolejte `ConfigureWorkflowApplication` ke konfiguraci obslužných rutin pro úložiště instancí, rozšíření a životního cyklu `WorkflowApplication` pracovního postupu pro tuto instanci.

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

6. Nakonec zavolejte `Run`.

    ```vb
    'Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     Následující příklad je dokončená `NewGame_Click` obslužná rutina.

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

### <a name="BKMK_ResumeWorkflow"></a>Obnovení pracovního postupu

1. Přidejte obslužnou rutinu `EnterGuess`pro. `Click` Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na `EnterGuess`položku. Vždy, když uživatel klikne na toto tlačítko, bude pracovní postup obnoven.

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. Přidejte následující kód, abyste se ujistili, že je v seznamu pracovního postupu vybraný pracovní postup a že je odhad uživatele platný.

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

3. V `WorkflowApplicationInstance` dalším kroku načtěte trvalou instanci pracovního postupu. `WorkflowApplicationInstance` Představuje trvalou instanci pracovního postupu, která ještě nebyla přidružena k definici pracovního postupu. `DefinitionIdentity` Z`WorkflowApplicationInstance`obsahujeinstancitrvaléhopracovníhopostupu. `WorkflowIdentity` V tomto kurzu `WorkflowVersionMap` se třída utility používá k `WorkflowIdentity` mapování správné definice pracovního postupu. Po načtení definice pracovního postupu se vytvoří a `WorkflowApplication` pomocí správné definice pracovního postupu.

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

4. Po vytvoření nakonfigurujte úložiště instancí, obslužné rutiny životního cyklu pracovního postupu a rozšíření tím, že zavoláte `ConfigureWorkflowApplication`. `WorkflowApplication` Tyto kroky je nutné provést při každém vytvoření nového `WorkflowApplication` a musí být provedeny před načtením instance pracovního postupu `WorkflowApplication`do. Po načtení je pracovní postup obnovený s odhadem uživatele.

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

5. Nakonec zrušte zaškrtnutí políčka odhad a připravte formulář, abyste mohli akceptovat další odhad.

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

    Následující příklad je dokončená `EnterGuess_Click` obslužná rutina.

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

### <a name="BKMK_TerminateWorkflow"></a>Ukončení pracovního postupu

1. Přidejte obslužnou rutinu `QuitGame`pro. `Click` Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na `QuitGame`položku. Vždy, když uživatel klikne na toto tlačítko, je ukončen aktuálně vybraný pracovní postup.

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. Přidejte následující kód do `QuitGame_Click` obslužné rutiny. Tento kód nejprve kontroluje, zda je v seznamu pracovních postupů vybrán pracovní postup. Poté načte trvalou instanci do a `WorkflowApplicationInstance`, `DefinitionIdentity` používá k určení správné definice pracovního postupu a poté inicializuje `WorkflowApplication`. Dále jsou nakonfigurované obslužné rutiny pro rozšíření a životní cyklus pracovního `ConfigureWorkflowApplication`postupu pro volání. Po nakonfigurování se načte a potom `Terminate` se zavolá. `WorkflowApplication`

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

### <a name="BKMK_BuildAndRun"></a>Sestavení a spuštění aplikace

1. Dvakrát klikněte na **program.cs** (nebo **Module1. vb**) v **Průzkumník řešení** pro zobrazení kódu.

2. Do horní části `using` souboru přidejte `Imports`následující příkaz (nebo) pomocí příkazů other `using` (nebo `Imports`).

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. Odeberte nebo Odkomentujte existující kód hostování pracovního postupu [pomocí postupu: Spusťte pracovní postup](how-to-run-a-workflow.md)a nahraďte ho následujícím kódem.

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

4. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **vlastnosti**. Na kartě **aplikace** zadejte pro **Typ výstupu** **aplikace systému Windows** . Tento krok je nepovinný, ale pokud se nedodržuje, zobrazí se kromě formuláře okno konzoly.

5. Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci.

6. Zajistěte, aby byla aplikace **NumberGuessWorkflowHost** nastavená jako spouštěcí aplikace, a stisknutím kláves CTRL + F5 spusťte aplikaci.

7. Vyberte rozsah pro odhad hry a typ pracovního postupu, který chcete spustit, a klikněte na **Nová hra**. V poli **odhad** zadejte odhad a kliknutím na tlačítko **Přejít** odešlete svůj odhad. Všimněte si, že výstup `WriteLine` aktivit se zobrazí ve formuláři.

8. Spusťte několik pracovních postupů pomocí různých typů pracovních postupů a rozsahů čísel, zadejte několik odhadů a přepněte mezi pracovními postupy výběrem ze seznamu **ID instance pracovního postupu** .

    Všimněte si, že když přepnete na nový pracovní postup, předchozí odhad a průběh pracovního postupu se v okně stav nezobrazí. Důvod, proč stav není k dispozici, je, že není zachycen a ukládán nikde. V dalším kroku kurzu [: Vytvořte vlastního účastníka](how-to-create-a-custom-tracking-participant.md)sledování a vytvořte vlastního účastníka sledování, který tyto informace uloží.
