---
title: 'Postupy: Aktualizace definice běžící instance pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: d3ff9d217d085e3afe5171cce9d80f8dbc32ff36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969478"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>Postupy: Aktualizace definice běžící instance pracovního postupu

Dynamická aktualizace poskytuje mechanismus pro pracovní postup vývojářům aplikací k aktualizaci pracovního postupu definici trvalé instance práce. Požadovaná změna lze provádět opravy chyb, nové požadavky, nebo tak, aby vyhovovaly neočekávaným změnám. Tento krok úvodního kurzu ukazuje, jak použít ke změně trvalého instance dynamické aktualizace `v1` číslo opakovaně uhodnout pracovního postupu tak, aby odpovídaly nových funkcích uvedených ve [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

> [!NOTE]
> Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>V tomto tématu

- [Chcete-li vytvořit projekt CreateUpdateMaps](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [Chcete-li aktualizovat StateMachineNumberGuessWorkflow](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [Chcete-li aktualizovat FlowchartNumberGuessWorkflow](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [Chcete-li aktualizovat SequentialNumberGuessWorkflow](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [Sestavte a spusťte aplikaci CreateUpdateMaps](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [K vytvoření sestavení aktualizovaný pracovní postup](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [Chcete-li aktualizovat WorkflowVersionMap nové verze](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [Aby se dynamická aktualizace](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [Spusťte aplikaci pomocí aktualizovaných pracovních postupů](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [Povolit od předchozích verzí pracovních postupů](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="BKMK_CreateProject"></a> Chcete-li vytvořit projekt CreateUpdateMaps

1. Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníka řešení** a zvolte **přidat**, **nový projekt**.

2. V **nainstalováno** uzlu, vyberte **Visual C#**, **Windows** (nebo **jazyka Visual Basic**, **Windows**).

    > [!NOTE]
    > V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalováno** uzlu.

     Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework. Vyberte **konzolovou aplikaci** z **Windows** seznamu. Typ **CreateUpdateMaps** do **název** pole a klikněte na tlačítko **OK**.

3. Klikněte pravým tlačítkem na **CreateUpdateMaps** v **Průzkumníka řešení** a zvolte **přidat odkaz**.

4. Vyberte **Framework** z **sestavení** uzlu **přidat odkaz** seznamu. Typ **System.Activities** do **hledání sestavení** pole k filtrování sestavení a usnadňují vyberte požadované odkazy.

5. Zaškrtněte políčko vedle **System.Activities** z **výsledky hledání** seznamu.

6. Typ **serializace** do **hledání sestavení** pole a zaškrtněte políčko vedle **System.Runtime.Serialization** z **výsledky hledání**  seznamu.

7. Typ **oboru názvů System.Xaml** do **hledání sestavení** pole a zaškrtněte políčko vedle **oboru názvů System.Xaml** z **výsledky hledání** seznamu.

8. Klikněte na tlačítko **OK** zavřete **správce odkazů** a přidejte odkazy.

9. Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. Přidejte následující dva řetězce členy k `Program` třídy (nebo `Module1`).

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. Přidejte následující `StartUpdate` metodu `Program` třídy (nebo `Module1`). Tato metoda načte zadaný xaml definici pracovního postupu do `ActivityBuilder`a pak zavolá `DynamicUpdate.PrepareForUpdate`. `PrepareForUpdate` Vytvoří kopii definice pracovního postupu uvnitř `ActivityBuilder`. Po úpravě definice pracovního postupu tuto kopii použít spolu s definici upravenou pracovní postup k vytvoření mapy aktualizace.

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace refers to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. V dalším kroku přidejte následující `CreateUpdateMethod` k `Program` třídy (nebo `Module1`). To vytvoří mapu dynamickou aktualizaci ve volání DynamicUpdateServices.CreateUpdateMap a potom uloží mapa aktualizace pomocí zadaného názvu. Toto mapování aktualizace obsahuje informace potřebné pro modul runtime pracovního postupu aktualizace trvalé instance práce, která byla spuštěna pomocí původní definici pracovního postupu, které jsou součástí `ActivityBuilder` tak, aby nedokončí pomocí definice aktualizovaný pracovní postup.

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. Přidejte následující `SaveUpdatedDefinition` metodu `Program` třídy (nebo `Module1`). Tato metoda šetří definici aktualizovaný pracovní postup po vytvoření mapa aktualizace.

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

### <a name="BKMK_StateMachine"></a> Chcete-li aktualizovat StateMachineNumberGuessWorkflow

1. Přidat `CreateStateMachineUpdateMap` k `Program` třídy (nebo `Module1`).

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. Volání `StartUpdate` a pak získejte odkaz na kořenovém adresáři `StateMachine` aktivity pracovního postupu.

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3. Dále, aktualizujte výrazy dva `WriteLine` aktivity, které se zobrazí, zda je odhad uživatele moc vysoká, nebo příliš malá, aby odpovídaly aktualizace provedené v [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4. V dalším kroku přidejte nové `WriteLine` aktivitu, která zobrazuje zprávu zavřít.

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5. Po aktualizaci pracovního postupu zavolejte `CreateUpdateMaps` a `SaveUpdatedDefinition`. `CreateUpdateMaps` vytvoří a uloží `DynamicUpdateMap`, a `SaveUpdatedDefinition` uloží definice aktualizovaný pracovní postup.

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

    V následujícím příkladu je dokončené `CreateStateMachineUpdateMap` metody.

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="BKMK_Flowchart"></a> Chcete-li aktualizovat FlowchartNumberGuessWorkflow

1. Přidejte následující `CreateFlowchartUpdateMethod` k `Program` třídy (nebo `Module1`). Tato metoda je podobný `CreateStateMachineUpdateMap`. Začíná volání `StartUpdate`, aktualizuje definice pracovního postupu vývojového diagramu a dokončení uložením mapa aktualizace a aktualizovaný pracovní postup definice.

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="BKMK_Sequential"></a> Chcete-li aktualizovat SequentialNumberGuessWorkflow

1. Přidejte následující `CreateSequentialUpdateMethod` k `Program` třídy (nebo `Module1`). Tato metoda je podobný tyto dvě metody. Začíná volání `StartUpdate`, aktualizuje definice sekvenčního pracovního postupu a dokončení uložením mapa aktualizace a aktualizovaný pracovní postup definice.

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="BKMK_CreateUpdateMaps"></a> Sestavte a spusťte aplikaci CreateUpdateMaps

1. Aktualizace `Main` metoda a přidejte následující tři metody volání. Tyto metody jsou přidány v následujících částech. Každá metoda aktualizuje odpovídající číslo odhad pracovní postup a vytvoří `DynamicUpdateMap` , který popisuje aktualizace.

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2. Klikněte pravým tlačítkem na **CreateUpdateMaps** v **Průzkumníka řešení** a zvolte **nastavit jako spouštěný projekt**.

3. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení a CTRL + F5 ke spuštění `CreateUpdateMaps` aplikace.

    > [!NOTE]
    > `CreateUpdateMaps` Aplikace nejsou zobrazeny žádné informace o stavu během spuštění, ale pokud byste se podívat **NumberGuessWorkflowActivities_du** složky a **PreviousVersions** složky se zobrazí soubory definice aktualizovaný pracovní postup a mapy aktualizace.

    Jakmile se vytvoří mapování aktualizace a aktualizovat definice pracovního postupu, dalším krokem je vytvoření sestavení aktualizovaný pracovní postup obsahující aktualizované definice.

### <a name="BKMK_BuildAssembly"></a> K vytvoření sestavení aktualizovaný pracovní postup

1. Spusťte druhou instanci sady Visual Studio 2012.

2. Zvolte **otevřít**, **projekt či řešení** z **souboru** nabídky.

3. Přejděte **NumberGuessWorkflowActivities_du** složku, kterou jste vytvořili v [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)vyberte **NumberGuessWorkflowActivities.csproj** (nebo **vbproj**) a klikněte na tlačítko **otevřít**.

4. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **SequentialNumberGuessWorkflow.xaml** a zvolte **vyjmout z projektu**. Stejnou věc udělat **FlowchartNumberGuessWorkflow.xaml** a **StateMachineNumberGuessWorkflow.xaml**. Tento krok se odebere předchozí verze definice pracovního postupu z projektu.

5. Zvolte **přidat existující položku** z **projektu** nabídky.

6. Přejděte **NumberGuessWorkflowActivities_du** složku, kterou jste vytvořili v [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

7. Zvolte **soubory XAML (\*.xaml;\*. XOML)** z **soubory typu** rozevíracího seznamu.

8. Vyberte **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, a **StateMachineNumberGuessWorkflow_du.xaml** a klikněte na tlačítko  **Přidat**.

    > [!NOTE]
    > CTRL + kliknutí vybrat více položek najednou.

    Tento krok přidává aktualizované verze definice pracovního postupu do projektu.

9. Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.

10. Zvolte **zavřít řešení** z **souboru** nabídky. Soubor řešení pro projekt se nevyžaduje, takže klikněte na tlačítko **ne** ukončit sadu Visual Studio bez uložení souboru řešení. Zvolte **ukončovací** z **souboru** nabídku ukončit sadu Visual Studio.

11. Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowActivities_du\bin\Debug** složky (nebo **bin\Release** v závislosti na nastavení projektu).

12. Přejmenovat **NumberGuessWorkflowActivities.dll** k **NumberGuessWorkflowActivities_v15.dll**a zkopírujte ho do **PreviousVersions** složku, kterou jste vytvořili v [Jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

### <a name="BKMK_UpdateWorkflowVersionMap"></a> Chcete-li aktualizovat WorkflowVersionMap nové verze

1. Přepněte zpět do původní instance sady Visual Studio 2012.

2. Dvakrát klikněte na panel **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projekt tak, aby ho otevřete.

3. Přidejte tři nové identity pracovního postupu pod šest existující deklarace identity pracovního postupu. V tomto kurzu `1.5.0.0` slouží jako `WorkflowIdentity.Version` identit dynamické aktualizace. Tyto nové `v15` pracovního postupu se použije identity poskytnout definici správné pracovního postupu pro dynamicky aktualizovaný pracovní postup trvalé instance.

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4. Přidejte následující kód na konci konstruktoru. Tento kód inicializuje identity pracovního postupu dynamické aktualizace, načte odpovídající definice pracovního postupu a přidá je do slovníku verze pracovního postupu.

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     V následujícím příkladu je dokončené `WorkflowVersionMap` třídy.

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamic Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

5. Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.

### <a name="BKMK_ApplyUpdate"></a> Aby se dynamická aktualizace

1. Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníka řešení** a zvolte **přidat**, **nový projekt**.

2. V **nainstalováno** uzlu, vyberte **Visual C#**, **Windows** (nebo **jazyka Visual Basic**, **Windows**).

    > [!NOTE]
    > V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalováno** uzlu.

    Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework. Vyberte **konzolovou aplikaci** z **Windows** seznamu. Typ **ApplyDynamicUpdate** do **název** pole a klikněte na tlačítko **OK**.

3. Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v **Průzkumníka řešení** a zvolte **přidat odkaz**.

4. Klikněte na tlačítko **řešení** a zaškrtněte políčko vedle položky **NumberGuessWorkflowHost**. Je potřeba tento odkaz tak, aby `ApplyDynamicUpdate` můžete použít `NumberGuessWorkflowHost.WorkflowVersionMap` třídy.

5. Vyberte **Framework** z **sestavení** uzlu **přidat odkaz** seznamu. Typ **System.Activities** do **hledání sestavení** pole. To bude filtrovat sestavení a usnadňují vyberte požadované odkazy.

6. Zaškrtněte políčko vedle **System.Activities** z **výsledky hledání** seznamu.

7. Typ **serializace** do **hledání sestavení** pole a zaškrtněte políčko vedle **System.Runtime.Serialization** z **výsledky hledání**  seznamu.

8. Typ **DurableInstancing** do **hledání sestavení** pole a zaškrtněte políčko vedle **System.Activities.DurableInstancing** a  **System.Runtime.DurableInstancing** z **výsledky hledání** seznamu.

9. Klikněte na tlačítko **OK** zavřete **správce odkazů** a přidejte odkazy.

10. Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v Průzkumníku řešení a zvolte **přidat**, **třídy**. Typ `DynamicUpdateInfo` do **název** pole a klikněte na tlačítko **přidat**.

11. Přidejte následující dva členy k `DynamicUpdateInfo` třídy. V následujícím příkladu je dokončené `DynamicUpdateInfo` třídy. Tato třída obsahuje informace o mapa aktualizace a nové identity pracovního postupu při instance pracovního postupu se aktualizuje.

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. Dvakrát klikněte na panel **Program.cs** (nebo **Module1.vb**) v Průzkumníku řešení.

14. Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. Přidejte následující připojovací řetězec člen, který chcete `Program` třídy (nebo `Module1`).

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > V závislosti na vaší edici systému SQL Server může být jiný server název připojovacího řetězce.

16. Přidejte následující `GetIDs` metodu `Program` třídy (nebo `Module1`). Tato metoda vrátí seznam identifikátorů instance trvalá pracovního postupu.

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. Přidejte následující `LoadMap` metodu `Program` třídy (nebo `Module1`). Tato metoda vytvoří slovník, který mapuje `v1` identity pracovního postupu do mapy aktualizace a nové identity pracovního postupu používá k aktualizaci odpovídající trvalé instance pracovního postupu.

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. Přidejte následující `LoadMaps` metodu `Program` třídy (nebo `Module1`). Tato metoda načte tři mapy aktualizace a vytvoří slovník, který mapuje `v1` identity pracovního postupu do mapy aktualizace.

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. Přidejte následující kód, který `Main`. Tento kód provede trvalá pracovního postupu instance a zkontroluje každý `WorkflowIdentity`. Pokud `WorkflowIdentity` mapuje na `v1` instance pracovního postupu `WorkflowApplication` je nakonfigurovaný s definicí aktualizovaný pracovní postup a identitu aktualizovaný pracovní postup. Dále `WorkflowApplication.Load` volána s instance a mapa aktualizace, která se vztahuje na mapě dynamické aktualizace. Jakmile tuto aktualizaci nenainstalujete, aktualizovanou instanci přetrvává volání `Unload`.

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v **Průzkumníka řešení** a zvolte **nastavit jako spouštěný projekt**.

21. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení a pak stiskněte CTRL + F5 ke spuštění `ApplyDynamicUpdate` aplikace a aktualizovat instance trvalá pracovního postupu. Byste měli vidět výstup podobný následujícímu. Pracovní postupy verze 1.0.0.0 jsou aktualizována na verzi 1.5.0.0, zatímco se neaktualizují verzi 2.0.0.0 pracovních postupů.

    **Kontrola: StateMachineNumberGuessWorkflow; Version=1.0.0.0**\
    **Aktualizace pro: StateMachineNumberGuessWorkflow; Version=1.5.0.0**\
    **Kontrola: StateMachineNumberGuessWorkflow; Version=1.0.0.0**\
    **Aktualizace pro: StateMachineNumberGuessWorkflow; Version=1.5.0.0**\
    **Kontrola: FlowchartNumberGuessWorkflow; Verze = 1.0.0.0**\
    **Aktualizace pro: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0**\
    **Kontrola: FlowchartNumberGuessWorkflow; Verze = 1.0.0.0**\
    **Aktualizace pro: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0**\
    **Kontrola: SequentialNumberGuessWorkflow; Verze = 1.0.0.0**\
    **Aktualizace pro: SequentialNumberGuessWorkflow; Verze = 1.5.0.0**\
    **Kontrola: SequentialNumberGuessWorkflow; Verze = 1.0.0.0**\
    **Aktualizace pro: SequentialNumberGuessWorkflow; Verze = 1.5.0.0**\
    **Kontrola: SequentialNumberGuessWorkflow; Verze = 1.0.0.0**\
    **Aktualizace pro: SequentialNumberGuessWorkflow; Verze = 1.5.0.0**\
    **Kontrola: StateMachineNumberGuessWorkflow; Version=1.0.0.0**\
    **Aktualizace pro: StateMachineNumberGuessWorkflow; Version=1.5.0.0**\
    **Kontrola: FlowchartNumberGuessWorkflow; Verze = 1.0.0.0**\
    **Aktualizace pro: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0**\
    **Kontrola: StateMachineNumberGuessWorkflow; Version=2.0.0.0**\
    **Kontrola: StateMachineNumberGuessWorkflow; Version=2.0.0.0**\
    **Kontrola: FlowchartNumberGuessWorkflow; Verze = 2.0.0.0**\
    **Kontrola: FlowchartNumberGuessWorkflow; Verze = 2.0.0.0**\
    **Kontrola: SequentialNumberGuessWorkflow; Verze = 2.0.0.0**\
    **Kontrola: SequentialNumberGuessWorkflow; Verze = 2.0.0.0**\
    **Stisknutím libovolné klávesy pokračovat...**

### <a name="BKMK_BuildAndRun"></a> Spusťte aplikaci pomocí aktualizovaných pracovních postupů

1. Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **nastavit jako spouštěný projekt**.

2. Stisknutím kláves CTRL + F5 spusťte aplikaci.

3. Klikněte na tlačítko **novou hru** spuštění nového pracovního postupu a poznamenejte si informace o verzi níže se stavové okno, které označuje pracovního postupu `v2` pracovního postupu.

4. Vyberte jednu z `v1` pracovních postupů, které jste spustili na začátku [jak: Hostování několika verzí pracovní postup-souběžně](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) tématu. Všimněte si, že informace o verzi v části stavové okno označuje, že pracovní postup je verze **1.5.0.0** pracovního postupu. Všimněte si, že nejsou k dispozici žádné informace uvedené informace o předchozích pokusů jiné než, zda byly moc vysoká, nebo příliš nízká.

    **Zadejte prosím číslo mezi 1 a 10**\
    **Váš odhad je příliš nízká.**

5. Poznamenejte si, `InstanceId` a pak zadejte pokusů až do dokončení pracovního postupu. Stavové okno zobrazuje informace o obsahu odhad vzhledem k tomu, `WriteLine` činnosti byly aktualizovány pomocí dynamické aktualizace.

    **Zadejte prosím číslo mezi 1 a 10**\
    **Váš odhad je příliš nízká.**\
    **Zadejte prosím číslo mezi 1 a 10**\
    **5 je příliš nízká.**\
    **Zadejte prosím číslo mezi 1 a 10**\
    **7 je příliš vysoká.**\
    **Zadejte prosím číslo mezi 1 a 10**\
    **Blahopřejeme, uhodnout číslo na oplátku 4.**

6. Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, který odpovídá k dokončení pracovního postupu. Pokud jste neprovedli si `InstanceId` je možné identifikovat pomocí souboru správné sledování **datum změny** informace v Průzkumníku Windows. Poslední řádek informace o sledování obsahuje výstup nově přidaný `WriteLine` aktivity.

    **Zadejte prosím číslo mezi 1 a 10**\
    **Váš odhad je příliš nízká.**\
    **Zadejte prosím číslo mezi 1 a 10**\
    **5 je příliš nízká.**\
    **Zadejte prosím číslo mezi 1 a 10**\
    **7 je příliš vysoká.**\
    **Zadejte prosím číslo mezi 1 a 10**\
    **6 je správná. Odhadl na oplátku 4.**

### <a name="BKMK_StartPreviousVersions"></a> Povolit od předchozích verzí pracovních postupů

Pokud vyčerpáte pracovní postupy pro aktualizace, můžete upravit `NumberGuessWorkflowHost` aplikaci, která od předchozích verzí pracovních postupů.

1. Dvakrát klikněte na panel **WorkflowHostForm** v **Průzkumníka řešení**a vyberte **WorkflowType** – pole se seznamem.

2. V **vlastnosti** okna, vyberte **položky** vlastnosti a klikněte na tlačítko se třemi tečkami upravit **položky** kolekce.

3. Přidejte následující tři položky do kolekce.

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    Dokončené `Items` kolekce bude obsahovat šest položek.

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. Dvakrát klikněte na panel **WorkflowHostForm** v **Průzkumníka řešení**a vyberte **zobrazit kód**.

5. Přidejte tři nové případy `switch` (nebo `Select Case`) příkaz v `NewGame_Click` obslužné rutiny pro nové položky v mapování **WorkflowType** – pole se seznamem pro odpovídající identity pracovního postupu.

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

    Následující příklad obsahuje kompletní `switch` (nebo `Select Case`) příkaz.

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
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

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6. Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci. Nyní můžete spustit `v1` verze pracovního postupu, stejně jako aktuální verze. Chcete-li dynamicky aktualizovat tyto nové instance, spusťte **ApplyDynamicUpdate** aplikace.
