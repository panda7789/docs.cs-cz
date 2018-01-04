---
title: "Postupy: aktualizovat definici spuštěná instance pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86a6e8d22d1e46407082af5d71cd83c179825bb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>Postupy: aktualizovat definici spuštěná instance pracovního postupu
Dynamická aktualizace poskytuje mechanismus pro pracovní postup vývojáři aplikace k aktualizaci definice pracovního postupu instance trvalou pracovního postupu. Požadovaná změna může být implementace oprava chyb, nové požadavky, nebo aby bylo možné ošetřit neočekávané změny. Tento krok v tomto kurzu demonstruje použití dynamické aktualizace k úpravě trvalou instance `v1` číslo uhodnutí pracovního postupu tak, aby odpovídala nové funkce, zavedená v [postup: více verzí pracovní postup-souběžného hostitele ](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
> [!NOTE]
>  Stažení dokončené verze nebo zobrazení na video s návodem kurzu, najdete v tématu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Vytvoření projektu CreateUpdateMaps](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [Chcete-li aktualizovat StateMachineNumberGuessWorkflow](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [Chcete-li aktualizovat FlowchartNumberGuessWorkflow](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [Chcete-li aktualizovat SequentialNumberGuessWorkflow](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [Sestavení a spuštění aplikace CreateUpdateMaps](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [K vytvoření sestavení aktualizované pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [Chcete-li aktualizovat WorkflowVersionMap nové verze](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Použití dynamické aktualizace](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [Ke spuštění aplikace s aktualizované pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [Chcete-li povolit od předchozích verzí pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <a name="BKMK_CreateProject"></a>Vytvoření projektu CreateUpdateMaps  
  
1.  Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníku řešení** a zvolte **přidat**, **nový projekt**.  
  
2.  V **nainstalovaná** uzlu, vyberte **Visual C#**, **Windows** (nebo **jazyka Visual Basic**, **Windows**).  
  
    > [!NOTE]
    >  V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalovaná** uzlu.  
  
     Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework. Vyberte **konzolové aplikace** z **Windows** seznamu. Typ **CreateUpdateMaps** do **název** pole a klikněte na tlačítko **OK**.  
  
3.  Klikněte pravým tlačítkem na **CreateUpdateMaps** v **Průzkumníku řešení** a zvolte **přidat odkaz na**.  
  
4.  Vyberte **Framework** z **sestavení** uzlu **přidat odkaz na** seznamu. Typ **systém.** do **hledání sestavení** pole k filtrování sestavení a snadněji vyberte požadované odkazy.  
  
5.  Zaškrtněte políčko vedle položky **systém.** z **výsledky hledání** seznamu.  
  
6.  Typ **serializace** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Runtime.Serialization** z **výsledky hledání**  seznamu.  
  
7.  Typ **System.Xaml** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Xaml** z **výsledky hledání** seznamu.  
  
8.  Klikněte na tlačítko **OK** zavřete **správce odkazů** a přidejte odkazy.  
  
9. Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
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
  
10. Přidejte následující členy dva řetězce `Program` – třída (nebo `Module1`).  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. Přidejte následující `StartUpdate` metodu `Program` – třída (nebo `Module1`). Tato metoda načte až definice pracovního postupu zadané xaml do `ActivityBuilder`a potom zavolá `DynamicUpdate.PrepareForUpdate`. `PrepareForUpdate`Vytvoří kopii definice pracovního postupu uvnitř `ActivityBuilder`. Po úpravě definice pracovního postupu tato kopie se používá spolu s definice pracovního postupu změny k vytvoření mapy aktualizace.  
  
    ```vb  
    Private Function StartUpdate(name As String) As ActivityBuilder  
        'Create the XamlXmlReaderSettings.  
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()  
        'In the XAML the "local" namespace referes to artifacts that come from   
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
            // In the XAML the "local" namespace referes to artifacts that come from   
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
  
12. V dalším kroku přidejte následující `CreateUpdateMethod` k `Program` – třída (nebo `Module1`). To vytvoří mapu dynamické aktualizace ve volání DynamicUpdateServices.CreateUpdateMap a pak uloží mapy aktualizace pomocí zadaného názvu. Tato aktualizace mapa obsahuje informace potřebné modulem runtime pracovního postupu aktualizace instanci trvalou pracovního postupu, který byl spuštěn s použitím původní definice pracovního postupu, které jsou součástí `ActivityBuilder` tak, aby dokončení pomocí definice aktualizované pracovního postupu.  
  
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
  
13. Přidejte následující `SaveUpdatedDefinition` metodu `Program` – třída (nebo `Module1`). Tato metoda šetří definice aktualizované pracovního postupu po vytvoření mapy aktualizace.  
  
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
  
###  <a name="BKMK_StateMachine"></a>Chcete-li aktualizovat StateMachineNumberGuessWorkflow  
  
1.  Přidat `CreateStateMachineUpdateMap` k `Program` – třída (nebo `Module1`).  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  Ujistěte se, volání `StartUpdate` a potom získat odkaz na kořenovém `StateMachine` aktivity pracovního postupu.  
  
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
  
3.  Potom aktualizujte výrazy dvou `WriteLine` aktivity, které se zobrazí, zda odhad uživatele je příliš vysoká. nebo je příliš málo tak, že budou odpovídat aktualizace provedené v [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
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
  
4.  V dalším kroku přidejte nové `WriteLine` aktivity, která zobrazí zprávu uzavírací.  
  
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
  
5.  Po aktualizaci pracovní postup volání `CreateUpdateMaps` a `SaveUpdatedDefinition`. `CreateUpdateMaps`vytvoří a uloží `DynamicUpdateMap`, a `SaveUpdatedDefinition` uloží pracovní postup aktualizované definice.  
  
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
  
     Následující příklad je dokončené `CreateStateMachineUpdateMap` metoda.  
  
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
  
###  <a name="BKMK_Flowchart"></a>Chcete-li aktualizovat FlowchartNumberGuessWorkflow  
  
1.  Přidejte následující `CreateFlowchartUpdateMethod` k `Program` – třída (nebo `Module1`). Tato metoda je podobná `CreateStateMachineUpdateMap`. Začíná volání `StartUpdate`, aktualizuje definice vývojový diagram pracovního postupu a dokončení uložením aktualizace mapování a pracovní postup aktualizované definice.  
  
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
  
###  <a name="BKMK_Sequential"></a>Chcete-li aktualizovat SequentialNumberGuessWorkflow  
  
1.  Přidejte následující `CreateSequentialUpdateMethod` k `Program` – třída (nebo `Module1`). Tato metoda je podobná tyto dvě metody. Začíná volání `StartUpdate`, aktualizuje definice sekvenčního pracovního postupu a dokončení uložením aktualizace mapování a pracovní postup aktualizované definice.  
  
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
  
###  <a name="BKMK_CreateUpdateMaps"></a>Sestavení a spuštění aplikace CreateUpdateMaps  
  
1.  Aktualizace `Main` metoda a přidejte následující volání tří metod. Tyto metody jsou přidány v následujících částech. Každá metoda aktualizace odpovídající číslo odhad pracovního postupu a vytvoří `DynamicUpdateMap` aktualizace, který popisuje.  
  
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
  
2.  Klikněte pravým tlačítkem na **CreateUpdateMaps** v **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.  
  
3.  Stiskněte klávesy CTRL + SHIFT + B řešení sestavíte a potom CTRL + F5 a spusťte `CreateUpdateMaps` aplikace.  
  
    > [!NOTE]
    >  `CreateUpdateMaps` Aplikace nejsou zobrazeny žádné informace o stavu během spuštění, ale pokud se podíváte **NumberGuessWorkflowActivities_du** složky a **PreviousVersions** složku, zobrazí se soubory definice aktualizované pracovního postupu a mapy aktualizace.  
  
     Po aktualizaci mapu lze vytvořit a aktualizovat definice pracovního postupu, dalším krokem je vytvoření aktualizované pracovního postupu sestavení obsahující aktualizované definice.  
  
###  <a name="BKMK_BuildAssembly"></a>K vytvoření sestavení aktualizované pracovního postupu  
  
1.  Otevřít druhou instanci [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Zvolte **otevřete**, **projekt nebo řešení** z **souboru** nabídky.  
  
3.  Přejděte na **NumberGuessWorkflowActivities_du** složku, kterou jste vytvořili v [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), vyberte **NumberGuessWorkflowActivities.csproj**  (nebo **vbproj**) a klikněte na tlačítko **otevřete**.  
  
4.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **SequentialNumberGuessWorkflow.xaml** a zvolte **vyloučit z projektu**. Stejnou věc udělat **FlowchartNumberGuessWorkflow.xaml** a **StateMachineNumberGuessWorkflow.xaml**. Tento krok odebere předchozí verze definice pracovního postupu z projektu.  
  
5.  Zvolte **přidat existující položku** z **projektu** nabídky.  
  
6.  Přejděte na **NumberGuessWorkflowActivities_du** složku, kterou jste vytvořili v [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
7.  Zvolte **soubory XAML (\*XAML;\*. XOML)** z **soubory typu** rozevíracího seznamu.  
  
8.  Vyberte **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, a **StateMachineNumberGuessWorkflow_du.xaml** a klikněte na tlačítko  **Přidat**.  
  
    > [!NOTE]
    >  CTRL + klikněte na tlačítko vybrat více položek najednou.  
  
     Tento krok přidává aktualizované verze definice pracovního postupu do projektu.  
  
9. Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.  
  
10. Zvolte **zavřít řešení** z **souboru** nabídky. Soubor řešení pro projekt není vyžadována, proto klikněte na **ne** zavřete [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] bez uložení soubor řešení. Zvolte **ukončení** z **soubor** nabídky zavřete [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].  
  
11. Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowActivities_du\bin\Debug** složky (nebo **bin\Release** v závislosti na nastavení projektu).  
  
12. Přejmenování **NumberGuessWorkflowActivities.dll** k **NumberGuessWorkflowActivities_v15.dll**a zkopírujte ho do **PreviousVersions** složku, kterou jste vytvořili v [Postupy: hostování více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a>Chcete-li aktualizovat WorkflowVersionMap nové verze  
  
1.  Přepněte zpět na původní instanci [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Klikněte dvakrát na **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projektu ho otevřete.  
  
3.  Přidejte tři nové identity pracovního postupu pod šesti existující deklarace identity pracovního postupu. V tomto kurzu `1.5.0.0` slouží jako `WorkflowIdentity.Version` pro identity dynamické aktualizace. Tyto nové `v15` pracovního postupu se použije identity zadejte definice správné pracovního postupu pro instance dynamicky aktualizované trvalou pracovního postupu.  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
    'v1.5 (Dynamimc Update) identities.  
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
  
4.  Přidejte následující kód na konci tohoto konstruktoru. Tento kód inicializuje identity dynamická aktualizace pracovního postupu, načte odpovídající definice pracovního postupu a přidá je do slovníku verze pracovního postupu.  
  
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
  
     Následující příklad je dokončené `WorkflowVersionMap` třídy.  
  
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
  
        'v1.5 (Dynamimc Update) identities.  
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
  
5.  Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.  
  
###  <a name="BKMK_ApplyUpdate"></a>Použití dynamické aktualizace  
  
1.  Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníku řešení** a zvolte **přidat**, **nový projekt**.  
  
2.  V **nainstalovaná** uzlu, vyberte **Visual C#**, **Windows** (nebo **jazyka Visual Basic**, **Windows**).  
  
    > [!NOTE]
    >  V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalovaná** uzlu.  
  
     Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework. Vyberte **konzolové aplikace** z **Windows** seznamu. Typ **ApplyDynamicUpdate** do **název** pole a klikněte na tlačítko **OK**.  
  
3.  Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v **Průzkumníku řešení** a zvolte **přidat odkaz na**.  
  
4.  Klikněte na tlačítko **řešení** a zaškrtněte políčko vedle **NumberGuessWorkflowHost**. Tento odkaz je potřeba, aby `ApplyDynamicUpdate` můžete použít `NumberGuessWorkflowHost.WorkflowVersionMap` třídy.  
  
5.  Vyberte **Framework** z **sestavení** uzlu **přidat odkaz na** seznamu. Typ **systém.** do **hledání sestavení** pole. Tato akce filtru sestavení a snadněji vyberte požadované odkazy.  
  
6.  Zaškrtněte políčko vedle položky **systém.** z **výsledky hledání** seznamu.  
  
7.  Typ **serializace** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Runtime.Serialization** z **výsledky hledání**  seznamu.  
  
8.  Typ **DurableInstancing** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Activities.DurableInstancing** a  **System.Runtime.DurableInstancing** z **výsledky hledání** seznamu.  
  
9. Klikněte na tlačítko **OK** zavřete **správce odkazů** a přidejte odkazy.  
  
10. Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v Průzkumníku řešení a zvolte **přidat**, **třída**. Typ `DynamicUpdateInfo` do **název** pole a klikněte na tlačítko **přidat**.  
  
11. Přidejte následující dva členy `DynamicUpdateInfo` třídy. Následující příklad je dokončené `DynamicUpdateInfo` třídy. Tato třída obsahuje informace o aktualizaci mapy a novou identitu pracovního postupu používá, když je aktualizována instance pracovního postupu.  
  
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
  
12. Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. Klikněte dvakrát na **Program.cs** (nebo **Module1.vb**) v Průzkumníku řešení.  
  
14. Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
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
  
15. Následující připojovací řetězec členy přidat `Program` – třída (nebo `Module1`).  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  V závislosti na vaší edicí systému SQL Server může být jiný název připojovacího řetězce serveru.  
  
16. Přidejte následující `GetIDs` metodu `Program` – třída (nebo `Module1`). Tato metoda vrátí seznam identifikátorů instance pracovního postupu trvalý.  
  
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
  
17. Přidejte následující `LoadMap` metodu `Program` – třída (nebo `Module1`). Tato metoda vytvoří slovník, který mapuje `v1` identity pracovního postupu aktualizace Maps a nových identit pracovní postup používá k aktualizaci odpovídající trvalé instancí pracovních postupů.  
  
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
  
18. Přidejte následující `LoadMaps` metodu `Program` – třída (nebo `Module1`). Tato metoda načte tři mapy aktualizace a vytvoří slovník, který mapuje `v1` identity pracovního postupu aktualizace Maps.  
  
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
  
19. Přidejte následující kód, který `Main`. Tento kód opakuje trvalou pracovní postup instancí a ověřuje jednotlivé `WorkflowIdentity`. Pokud `WorkflowIdentity` mapuje `v1` instance pracovního postupu `WorkflowApplication` je nastavena definice aktualizované pracovního postupu a identity aktualizované pracovního postupu. Dále `WorkflowApplication.Load` je volán s instance a mapy aktualizace, která se vztahuje mapy dynamické aktualizace. Po aktualizaci aktualizované instance je zachovat pomocí volání `Unload`.  
  
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
  
20. Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.  
  
21. Stiskněte kombinaci kláves CTRL + SHIFT + B řešení sestavíte a stiskněte klávesu CTRL + F5 a spusťte `ApplyDynamicUpdate` aplikace a aktualizovat instance trvalou pracovního postupu. Měli byste vidět výstup podobný následujícímu. Verze 1.0.0.0 pracovní postupy jsou aktualizovány na verzi 1.5.0.0, při pracovních verzi 2.0.0.0 neaktualizují.  
  
 **Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 1.0.0.0**  
**Aktualizováno za účelem: StateMachineNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: StateMachineNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: SequentialNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: SequentialNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: SequentialNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: StateMachineNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 1.0.0.0**   
**Aktualizováno za účelem: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0**   
**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 2.0.0.0**   
**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 2.0.0.0**   
**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 2.0.0.0**   
**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 2.0.0.0**   
**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 2.0.0.0**   
**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 2.0.0.0**   
**Stisknutím libovolné klávesy pokračujte...**  
  
###  <a name="BKMK_BuildAndRun"></a>Ke spuštění aplikace s aktualizované pracovních postupů  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.  
  
2.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.  
  
3.  Klikněte na tlačítko **novou hru** spustit nový pracovní postup a Všimněte si níže uvedené informace verze se stavové okno, které označuje pracovního postupu `v2` pracovního postupu.  
  
4.  Vyberte jednu z `v1` pracovní postupy, které jste spustili na začátku [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) tématu. Všimněte si, že informace o verzi v okně stav označuje, že pracovní postup je verze **1.5.0.0** pracovního postupu. Všimněte si, že nejsou žádné informace uvedené o předchozí pokusů jiné než zda byly příliš vysoké nebo příliš nízká.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**Vaše odhad je příliš nízká.**  
  
5.  Poznamenejte si `InstanceId` a pak zadejte pokusů až po dokončení pracovního postupu. V okně Stav se zobrazí informace o obsahu, odhad, protože `WriteLine` aktivity aktualizoval dynamické aktualizace.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**Vaše odhad je příliš nízká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**5 je příliš nízká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**7 je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**Blahopřejeme, uhádnout číslo na oplátku 4.**  
  
6.  Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, která odpovídá dokončené pracovního postupu. Pokud jste neprovedli poznámku o `InstanceId` bude pravděpodobně možné identifikovat soubor správné sledování pomocí **datum změny** informace v Průzkumníku Windows. Poslední řádek informace o sledování obsahuje výstup nově přidaný `WriteLine` aktivity.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**Vaše odhad je příliš nízká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**5 je příliš nízká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**7 je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**6 je správná. Uhádnout na oplátku 4.**  
  
###  <a name="BKMK_StartPreviousVersions"></a>Chcete-li povolit od předchozích verzí pracovních postupů  
 Pokud spustíte mimo pracovní postupy pro aktualizace, můžete upravit `NumberGuessWorkflowHost` aplikaci, která od předchozích verzí pracovních postupů.  
  
1.  Klikněte dvakrát na **WorkflowHostForm** v **Průzkumníku řešení**a vyberte **WorkflowType** – pole se seznamem.  
  
2.  V **vlastnosti** vyberte **položky** vlastnost a klikněte na tlačítko se třemi tečkami upravit **položky** kolekce.  
  
3.  Přidejte následující tři položky do kolekce.  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     Dokončené `Items` kolekce bude mít šest položky.  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  Klikněte dvakrát na **WorkflowHostForm** v **Průzkumníku řešení**a vyberte **kód zobrazení**.  
  
5.  Přidejte tři nové případech `switch` (nebo `Select Case`) příkaz v `NewGame_Click` obslužné rutiny pro mapování nové položky v **WorkflowType** – pole se seznamem na odpovídající identity pracovního postupu.  
  
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
  
6.  Stisknutím klávesy CTRL + F5 sestavení a spuštění aplikace. Nyní můžete spustit `v1` verze pracovního postupu, stejně jako aktuální verze. Chcete-li dynamicky aktualizovat tyto nové instance, spusťte **ApplyDynamicUpdate** aplikace.
