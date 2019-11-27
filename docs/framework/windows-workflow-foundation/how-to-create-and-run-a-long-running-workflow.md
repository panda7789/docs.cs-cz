---
title: Jak vytvořit a spustit dlouhodobě běžící pracovní postup
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 10eb4e2947bed9cea89f1cda05272aa3fa0fadaa
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204880"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Jak vytvořit a spustit dlouhodobě běžící pracovní postup

Jednou z ústředních funkcí programovací model Windows Workflow Foundation (WF) je schopnost modulu runtime uchovávat a uvolňovat nečinné pracovní postupy do databáze. Postup, [Jak spustit pracovní postup: spuštění pracovního postupu](how-to-run-a-workflow.md) ukázal základy hostování pracovního postupu pomocí konzolové aplikace. V příkladech se zobrazily počáteční pracovní postupy, obslužné rutiny životního cyklu pracovního postupu a obnovení záložek. Aby bylo možné předvést trvalost pracovního postupu efektivně, je zapotřebí složitější hostitel pracovního postupu, který podporuje spouštění a obnovování více instancí pracovního postupu. Tento krok v tomto kurzu ukazuje, jak vytvořit hostitelskou aplikaci Windows Form, která podporuje spouštění a obnovování více instancí pracovního postupu, trvalý pracovní postup a poskytuje základ pro pokročilé funkce, jako je například sledování a správa verzí, které jsou znázorněné v dalších krocích kurzu.

> [!NOTE]
> Tento krok kurzu a následné kroky používají všechny tři typy pracovních postupů v tématu [Postupy: vytvoření pracovního postupu](how-to-create-a-workflow.md). Pokud jste nedokončili všechny tři typy, můžete si stáhnout dokončenou verzi kroků z [programovací model Windows Workflow Foundation (WF45) – začínáme kurzu](https://go.microsoft.com/fwlink/?LinkID=248976).

> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="to-create-the-persistence-database"></a>Vytvoření databáze trvalosti

1. Otevřete SQL Server Management Studio a připojte se k místnímu serveru, například **.\SQLEXPRESS**. Pravým tlačítkem myši klikněte na uzel **databáze** na místním serveru a vyberte možnost **Nová databáze**. Pojmenujte novou databázi **WF45GettingStartedTutorial**, přijměte všechny ostatní hodnoty a vyberte **OK**.

    > [!NOTE]
    > Před vytvořením databáze se ujistěte, že máte na místním serveru oprávnění **vytvořit databázi** .

2. V nabídce **soubor** vyberte **otevřít**, **soubor** . Přejděte do následující složky: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*

    Vyberte následující dva soubory a klikněte na **otevřít**.

    - *SqlWorkflowInstanceStoreLogic. SQL*

    - *SqlWorkflowInstanceStoreSchema. SQL*

3. V nabídce **okno** vyberte **SqlWorkflowInstanceStoreSchema. SQL** . V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .

4. V nabídce **okno** vyberte **SqlWorkflowInstanceStoreLogic. SQL** . V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .

    > [!WARNING]
    > Je důležité provést předchozí dva kroky ve správném pořadí. Pokud jsou dotazy spouštěny mimo pořadí, dojde k chybám a databáze trvalosti není správně nakonfigurována.

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a>Přidání odkazu na DurableInstancing sestavení

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**.

2. V seznamu **Přidat odkaz** vyberte **sestavení** a do pole **vyhledávací sestavení** zadejte `DurableInstancing`. To filtruje sestavení a usnadňuje výběr požadovaných odkazů.

3. Zaškrtněte políčko vedle položky **System. Activities. DurableInstancing** a **System. Runtime. DurableInstancing** ze seznamu **výsledků hledání** a klikněte na tlačítko **OK**.

## <a name="to-create-the-workflow-host-form"></a>Vytvoření formuláře hostitele pracovního postupu

> [!NOTE]
> Kroky v tomto postupu popisují, jak formulář Přidat a nakonfigurovat ručně. V případě potřeby si můžete stáhnout soubory řešení pro kurz a přidat dokončený formulář do projektu. Pokud si chcete stáhnout soubory kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976). Po stažení souborů klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**. Přidejte odkaz na **System. Windows. Forms** a **System. Drawing**. Tyto odkazy jsou přidány automaticky, pokud přidáte nový formulář z nabídky **Přidat**, **Nová položka** , ale je nutné jej přidat ručně při importu formuláře. Až budou odkazy přidány, klikněte pravým tlačítkem myši na **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat**, **existující položka**. Přejděte do složky `Form` v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm. vb**) a klikněte na **Přidat**. Pokud se rozhodnete importovat formulář, můžete přeskočit dolů k další části a [Přidat vlastnosti a pomocné metody formuláře](#to-add-the-properties-and-helper-methods-of-the-form).

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Nová položka**.

2. V seznamu **nainstalované** šablony vyberte možnost **formulář Windows**, do pole **název** zadejte `WorkflowHostForm` a klikněte na tlačítko **Přidat**.

3. Ve formuláři nakonfigurujte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |FormBorderStyle|FixedSingle|
    |MaximizeBox|False|
    |Velikost|400, 420|

4. Do formuláře přidejte následující ovládací prvky v zadaném pořadí a nakonfigurujte vlastnosti jako směrované.

    |Ovládací prvek|Vlastnost: hodnota|
    |-------------|---------------------|
    |**Tlačítko**|Název: NewGame<br /><br /> Umístění: 13, 13<br /><br /> Velikost: 75, 23<br /><br /> Text: nová hra|
    |**Popisek**|Umístění: 94, 18<br /><br /> Text: vyodhaduje číslo od 1 do.|
    |**ComboBox**|Název: NumberRange<br /><br /> DropDownStyle: DropDownList<br /><br /> Položky: 10, 100, 1000<br /><br /> Umístění: 228, 12<br /><br /> Velikost: 143, 21|
    |**Popisek**|Umístění: 13, 43<br /><br /> Text: typ pracovního postupu|
    |**ComboBox**|Název: WorkflowType<br /><br /> DropDownStyle: DropDownList<br /><br /> Položky: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Umístění: 94, 40<br /><br /> Velikost: 277, 21|
    |**Popisek**|Název: WorkflowVersion<br /><br /> Umístění: 13, 362<br /><br /> Text: verze pracovního postupu|
    |**GroupBox**|Umístění: 13, 67<br /><br /> Velikost: 358, 287<br /><br /> Text: hra|

    > [!NOTE]
    > Při přidávání následujících ovládacích prvků Umístěte tyto ovládací prvky do skupinového rámečku.

    |Ovládací prvek|Vlastnost: hodnota|
    |-------------|---------------------|
    |**Popisek**|Umístění: 7, 20<br /><br /> Text: ID instance pracovního postupu|
    |**ComboBox**|Název: InstanceId<br /><br /> DropDownStyle: DropDownList<br /><br /> Umístění: 121, 17<br /><br /> Velikost: 227, 21|
    |**Popisek**|Umístění: 7, 47<br /><br /> Text: odhad|
    |**TextBox**|Název: odhad<br /><br /> Umístění: 50, 44<br /><br /> Velikost: 65, 20|
    |**Tlačítko**|Název: EnterGuess<br /><br /> Umístění: 121, 42<br /><br /> Velikost: 75, 23<br /><br /> Text: zadejte odhad.|
    |**Tlačítko**|Název: QuitGame<br /><br /> Umístění: 274, 42<br /><br /> Velikost: 75, 23<br /><br /> Text: konec|
    |**TextBox**|Název: WorkflowStatus<br /><br /> Umístění: 10, 73<br /><br /> Víceřádkové: pravda<br /><br /> Jen pro čtení: true<br /><br /> Posuvníky: svislé<br /><br /> Velikost: 338, 208|

5. Nastavte vlastnost **AcceptButton** formuláře na **EnterGuess**.

 Následující příklad znázorňuje dokončený formulář.

 ![Snímek obrazovky programovací model Windows Workflow Foundation formuláře hostitele pracovního postupu.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a>Přidání vlastností a pomocných metod formuláře

Kroky v této části přidávají vlastnosti a pomocné metody do třídy formuláře, která konfiguruje uživatelské rozhraní formuláře tak, aby podporovalo spouštění a obnovování počtu vyčíslení pro odhadované pracovní postupy.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.

2. Do horní části souboru přidejte následující příkazy `using` (nebo `Imports`) s jinými příkazy `using` (nebo `Imports`).

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. Do třídy **WorkflowHostForm** přidejte následující deklarace členů.

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > Pokud je váš připojovací řetězec jiný, aktualizujte `connectionString`, aby odkazovaly na vaši databázi.

4. Do `WorkflowFormHost` třídy přidejte vlastnost `WorkflowInstanceId`.

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

    V poli se seznamem `InstanceId` se zobrazí seznam trvalých ID instancí pracovního postupu a vlastnost `WorkflowInstanceId` vrací aktuálně vybraný pracovní postup.

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

6. Přidejte následující kód pro `WorkflowHostForm_Load`.

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
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

    Když se formulář načte, `SqlWorkflowInstanceStore` se nakonfigurují, rozsah a typ pracovního postupu se pole se seznamem nastaví na výchozí hodnoty a trvalé instance pracovního postupu se přidají do pole se seznamem `InstanceId`.

7. Přidejte obslužnou rutinu `SelectedIndexChanged` pro `InstanceId`. Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, vyberte pole se seznamem `InstanceId`, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **SelectedIndexChanged**.

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. Přidejte následující kód pro `InstanceId_SelectedIndexChanged`. Vždy, když uživatel vybere pracovní postup pomocí pole se seznamem, tato obslužná rutina aktualizuje stavové okno.

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
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
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. Do třídy Form přidejte následující metodu `ListPersistedWorkflows`.

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    `ListPersistedWorkflows` se dotazuje úložiště instancí na trvalé instance pracovního postupu a přidá ID instance do pole se seznamem `cboInstanceId`.

10. Do třídy Form přidejte následující metodu `UpdateStatus` a odpovídající delegát. Tato metoda aktualizuje stavové okno ve formuláři se stavem aktuálně spuštěného pracovního postupu.

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
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

11. Do třídy Form přidejte následující metodu `GameOver` a odpovídající delegát. Po dokončení pracovního postupu Tato metoda aktualizuje uživatelské rozhraní formuláře odebráním ID instance dokončeného pracovního postupu z pole se seznamem **InstanceId** .

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
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
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a>Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření

1. Do třídy formuláře přidejte metodu `ConfigureWorkflowApplication`.

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

2. V `ConfigureWorkflowApplication`zadejte `SqlWorkflowInstanceStore` pro `WorkflowApplication`.

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. Dále vytvořte instanci `StringWriter` a přidejte ji do kolekce `Extensions` `WorkflowApplication`. Když se do rozšíření přidá `StringWriter`, zachytí se veškerý výstup aktivity `WriteLine`. Když se pracovní postup přestanou nečinný, může být výstup `WriteLine` z `StringWriter` extrahován a zobrazený ve formuláři.

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. Přidejte následující obslužnou rutinu pro událost `Completed`. Po úspěšném dokončení pracovního postupu se v okně stav zobrazí počet pokusů o odhadované číslo. Pokud se pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení. Na konci obslužné rutiny je volána metoda `GameOver`, která odebere dokončený pracovní postup ze seznamu pracovního postupu.

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. Přidejte následující `Aborted` a `OnUnhandledException` obslužné rutiny. Metoda `GameOver` není volána z obslužné rutiny `Aborted`, protože když je instance pracovního postupu přerušena, nekončí, a je možné instanci obnovit později.

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. Přidejte následující obslužnou rutinu `PersistableIdle`. Tato obslužná rutina načte rozšíření `StringWriter`, které bylo přidáno, extrahuje výstup z aktivit `WriteLine` a zobrazí jej v okně stav.

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
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

    Výčet <xref:System.Activities.PersistableIdleAction> má tři hodnoty: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>a <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> způsobí, že pracovní postup zůstane zachován, ale nezpůsobí, že se pracovní postup uvolní. <xref:System.Activities.PersistableIdleAction.Unload> způsobí, že se pracovní postup uchová a uvolní.

    Následující příklad je dokončená `ConfigureWorkflowApplication` metoda.

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
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
        var sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
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

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a>Povolení spouštění a obnovování více typů pracovních postupů

Aby bylo možné obnovit instanci pracovního postupu, musí hostitel zadat definici pracovního postupu. V tomto kurzu existují tři typy pracovních postupů a další kroky kurzu představují více verzí těchto typů. `WorkflowIdentity` poskytuje, aby mohla hostitelská aplikace přidružit identifikační informace k trvalé instanci pracovního postupu. Kroky v této části ukazují, jak vytvořit třídu nástrojů, která vám pomůže s mapováním identity pracovního postupu z trvalé instance pracovního postupu na odpovídající definici pracovního postupu. Další informace o `WorkflowIdentity` a verzích najdete v tématu [použití identita WorkflowIdentity a správy verzí](using-workflowidentity-and-versioning.md).

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Třída**. Do pole **název** zadejte `WorkflowVersionMap` a klikněte na **Přidat**.

2. Do horní části souboru přidejte následující příkazy `using` nebo `Imports` s ostatními `using` nebo `Imports` příkazy.

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. Nahraďte deklaraci třídy `WorkflowVersionMap` následující deklarací.

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
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

    `WorkflowVersionMap` obsahuje tři identity pracovního postupu, které se mapují na tři definice pracovního postupu z tohoto kurzu a používají se v následujících oddílech při spuštění a obnovení pracovních postupů.

## <a name="to-start-a-new-workflow"></a>Spuštění nového pracovního postupu

1. Přidejte obslužnou rutinu `Click` pro `NewGame`. Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na položku `NewGame`. Je přidána obslužná rutina `NewGame_Click` a zobrazení se přepne do zobrazení kódu pro formulář. Vždy, když uživatel klikne na toto tlačítko, je spuštěn nový pracovní postup.

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

3. Dále přidejte následující kód, který spustí pracovní postup. Definice `WorkflowIdentity` a pracovního postupu odpovídající typu vybraného pracovního postupu se načítají pomocí pomocné třídy `WorkflowVersionMap`. V dalším kroku se vytvoří nová instance `WorkflowApplication` pomocí definice pracovního postupu, `WorkflowIdentity`a slovníku vstupních argumentů.

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
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. Zavolejte `ConfigureWorkflowApplication` ke konfiguraci obslužných rutin pro úložiště instancí, rozšíření a životní cyklus pracovního cyklu pro tuto instanci `WorkflowApplication`.

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. Nakonec zavolejte `Run`.

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     Následující příklad je dokončená obslužná rutina `NewGame_Click`.

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
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

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
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

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a>Obnovení pracovního postupu

1. Přidejte obslužnou rutinu `Click` pro `EnterGuess`. Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na položku `EnterGuess`. Vždy, když uživatel klikne na toto tlačítko, bude pracovní postup obnoven.

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

3. Dále načtěte `WorkflowApplicationInstance` trvalé instance pracovního postupu. `WorkflowApplicationInstance` představuje trvalou instanci pracovního postupu, která ještě nebyla přidružena k definici pracovního postupu. `DefinitionIdentity` `WorkflowApplicationInstance` obsahuje `WorkflowIdentity` trvalé instance pracovního postupu. V tomto kurzu se třída `WorkflowVersionMap` Utility používá k mapování `WorkflowIdentity` na správnou definici pracovního postupu. Po načtení definice pracovního postupu se vytvoří `WorkflowApplication` pomocí správné definice pracovního postupu.

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. Po vytvoření `WorkflowApplication` nakonfigurujte úložiště instancí, obslužné rutiny životního cyklu pracovního postupu a rozšíření tím, že zavoláte `ConfigureWorkflowApplication`. Tyto kroky je nutné provést při každém vytvoření nového `WorkflowApplication` a je třeba je provést před načtením instance pracovního postupu do `WorkflowApplication`. Po načtení je pracovní postup obnovený s odhadem uživatele.

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
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
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    Následující příklad je dokončená obslužná rutina `EnterGuess_Click`.

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

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
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
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

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

## <a name="to-terminate-a-workflow"></a>Ukončení pracovního postupu

1. Přidejte obslužnou rutinu `Click` pro `QuitGame`. Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na položku `QuitGame`. Vždy, když uživatel klikne na toto tlačítko, je ukončen aktuálně vybraný pracovní postup.

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. Do obslužné rutiny `QuitGame_Click` přidejte následující kód. Tento kód nejprve kontroluje, zda je v seznamu pracovních postupů vybrán pracovní postup. Poté načte trvalou instanci do `WorkflowApplicationInstance`, používá `DefinitionIdentity` k určení správné definice pracovního postupu a poté inicializuje `WorkflowApplication`. V dalších rozšířeních a obslužných rutinách životního cyklu pracovního postupu se nakonfigurují volání `ConfigureWorkflowApplication`. Po nakonfigurování `WorkflowApplication` je načtena a poté `Terminate` volána.

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
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
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a>Sestavení a spuštění aplikace

1. Dvakrát klikněte na **program.cs** (nebo **Module1. vb**) v **Průzkumník řešení** pro zobrazení kódu.

2. Do horní části souboru přidejte následující příkaz `using` (nebo `Imports`) s jinými příkazy `using` (nebo `Imports`).

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. Odeberte nebo Odkomentujte existující kód hostování pracovního postupu z tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md)a jeho nahrazení následujícím kódem.

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

7. Vyberte rozsah pro odhad hry a typ pracovního postupu, který chcete spustit, a klikněte na **Nová hra**. V poli **odhad** zadejte odhad a kliknutím na tlačítko **Přejít** odešlete svůj odhad. Všimněte si, že výstup aktivit `WriteLine` se zobrazí ve formuláři.

8. Spusťte několik pracovních postupů pomocí různých typů pracovních postupů a rozsahů čísel, zadejte několik odhadů a přepněte mezi pracovními postupy výběrem ze seznamu **ID instance pracovního postupu** .

    Všimněte si, že když přepnete na nový pracovní postup, předchozí odhad a průběh pracovního postupu se v okně stav nezobrazí. Důvod, proč stav není k dispozici, je, že není zachycen a ukládán nikde. V dalším kroku tohoto kurzu se [naučíte: vytvořit vlastního účastníka sledování](how-to-create-a-custom-tracking-participant.md)a vytvořit vlastního účastníka sledování, který tyto informace uloží.
