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
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="20b1b-102">Postupy: aktualizovat definici spuštěná instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="20b1b-102">How to: Update the Definition of a Running Workflow Instance</span></span>
<span data-ttu-id="20b1b-103">Dynamická aktualizace poskytuje mechanismus pro pracovní postup vývojáři aplikace k aktualizaci definice pracovního postupu instance trvalou pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="20b1b-104">Požadovaná změna může být implementace oprava chyb, nové požadavky, nebo aby bylo možné ošetřit neočekávané změny.</span><span class="sxs-lookup"><span data-stu-id="20b1b-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="20b1b-105">Tento krok v tomto kurzu demonstruje použití dynamické aktualizace k úpravě trvalou instance `v1` číslo uhodnutí pracovního postupu tak, aby odpovídala nové funkce, zavedená v [postup: více verzí pracovní postup-souběžného hostitele ](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="20b1b-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20b1b-106">Stažení dokončené verze nebo zobrazení na video s návodem kurzu, najdete v tématu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="20b1b-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="20b1b-107">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="20b1b-107">In this topic</span></span>  
  
-   [<span data-ttu-id="20b1b-108">Vytvoření projektu CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="20b1b-108">To create the CreateUpdateMaps project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [<span data-ttu-id="20b1b-109">Chcete-li aktualizovat StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20b1b-109">To update StateMachineNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [<span data-ttu-id="20b1b-110">Chcete-li aktualizovat FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20b1b-110">To update FlowchartNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [<span data-ttu-id="20b1b-111">Chcete-li aktualizovat SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20b1b-111">To update SequentialNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [<span data-ttu-id="20b1b-112">Sestavení a spuštění aplikace CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="20b1b-112">To build and run the CreateUpdateMaps application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [<span data-ttu-id="20b1b-113">K vytvoření sestavení aktualizované pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="20b1b-113">To build the updated workflow assembly</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [<span data-ttu-id="20b1b-114">Chcete-li aktualizovat WorkflowVersionMap nové verze</span><span class="sxs-lookup"><span data-stu-id="20b1b-114">To update WorkflowVersionMap with the new versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="20b1b-115">Použití dynamické aktualizace</span><span class="sxs-lookup"><span data-stu-id="20b1b-115">To apply the dynamic updates</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [<span data-ttu-id="20b1b-116">Ke spuštění aplikace s aktualizované pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20b1b-116">To run the application with the updated workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [<span data-ttu-id="20b1b-117">Chcete-li povolit od předchozích verzí pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20b1b-117">To enable starting previous versions of the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <a name="BKMK_CreateProject"></a><span data-ttu-id="20b1b-118">Vytvoření projektu CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="20b1b-118">To create the CreateUpdateMaps project</span></span>  
  
1.  <span data-ttu-id="20b1b-119">Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníku řešení** a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="20b1b-120">V **nainstalovaná** uzlu, vyberte **Visual C#**, **Windows** (nebo **jazyka Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="20b1b-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20b1b-121">V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalovaná** uzlu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="20b1b-122">Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20b1b-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="20b1b-123">Vyberte **konzolové aplikace** z **Windows** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="20b1b-124">Typ **CreateUpdateMaps** do **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="20b1b-125">Klikněte pravým tlačítkem na **CreateUpdateMaps** v **Průzkumníku řešení** a zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="20b1b-126">Vyberte **Framework** z **sestavení** uzlu **přidat odkaz na** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="20b1b-127">Typ **systém.** do **hledání sestavení** pole k filtrování sestavení a snadněji vyberte požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>  
  
5.  <span data-ttu-id="20b1b-128">Zaškrtněte políčko vedle položky **systém.** z **výsledky hledání** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
6.  <span data-ttu-id="20b1b-129">Typ **serializace** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Runtime.Serialization** z **výsledky hledání**  seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="20b1b-130">Typ **System.Xaml** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Xaml** z **výsledky hledání** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="20b1b-131">Klikněte na tlačítko **OK** zavřete **správce odkazů** a přidejte odkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-131">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
9. <span data-ttu-id="20b1b-132">Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
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
  
10. <span data-ttu-id="20b1b-133">Přidejte následující členy dva řetězce `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. <span data-ttu-id="20b1b-134">Přidejte následující `StartUpdate` metodu `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-135">Tato metoda načte až definice pracovního postupu zadané xaml do `ActivityBuilder`a potom zavolá `DynamicUpdate.PrepareForUpdate`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="20b1b-136">`PrepareForUpdate`Vytvoří kopii definice pracovního postupu uvnitř `ActivityBuilder`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="20b1b-137">Po úpravě definice pracovního postupu tato kopie se používá spolu s definice pracovního postupu změny k vytvoření mapy aktualizace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>  
  
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
  
12. <span data-ttu-id="20b1b-138">V dalším kroku přidejte následující `CreateUpdateMethod` k `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-139">To vytvoří mapu dynamické aktualizace ve volání DynamicUpdateServices.CreateUpdateMap a pak uloží mapy aktualizace pomocí zadaného názvu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="20b1b-140">Tato aktualizace mapa obsahuje informace potřebné modulem runtime pracovního postupu aktualizace instanci trvalou pracovního postupu, který byl spuštěn s použitím původní definice pracovního postupu, které jsou součástí `ActivityBuilder` tak, aby dokončení pomocí definice aktualizované pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>  
  
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
  
13. <span data-ttu-id="20b1b-141">Přidejte následující `SaveUpdatedDefinition` metodu `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-142">Tato metoda šetří definice aktualizované pracovního postupu po vytvoření mapy aktualizace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-142">This method saves the updated workflow definition once the update map is created.</span></span>  
  
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
  
###  <a name="BKMK_StateMachine"></a><span data-ttu-id="20b1b-143">Chcete-li aktualizovat StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20b1b-143">To update StateMachineNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="20b1b-144">Přidat `CreateStateMachineUpdateMap` k `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  <span data-ttu-id="20b1b-145">Ujistěte se, volání `StartUpdate` a potom získat odkaz na kořenovém `StateMachine` aktivity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>  
  
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
  
3.  <span data-ttu-id="20b1b-146">Potom aktualizujte výrazy dvou `WriteLine` aktivity, které se zobrazí, zda odhad uživatele je příliš vysoká. nebo je příliš málo tak, že budou odpovídat aktualizace provedené v [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="20b1b-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
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
  
4.  <span data-ttu-id="20b1b-147">V dalším kroku přidejte nové `WriteLine` aktivity, která zobrazí zprávu uzavírací.</span><span class="sxs-lookup"><span data-stu-id="20b1b-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>  
  
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
  
5.  <span data-ttu-id="20b1b-148">Po aktualizaci pracovní postup volání `CreateUpdateMaps` a `SaveUpdatedDefinition`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="20b1b-149">`CreateUpdateMaps`vytvoří a uloží `DynamicUpdateMap`, a `SaveUpdatedDefinition` uloží pracovní postup aktualizované definice.</span><span class="sxs-lookup"><span data-stu-id="20b1b-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>  
  
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
  
     <span data-ttu-id="20b1b-150">Následující příklad je dokončené `CreateStateMachineUpdateMap` metoda.</span><span class="sxs-lookup"><span data-stu-id="20b1b-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>  
  
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
  
###  <a name="BKMK_Flowchart"></a><span data-ttu-id="20b1b-151">Chcete-li aktualizovat FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20b1b-151">To update FlowchartNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="20b1b-152">Přidejte následující `CreateFlowchartUpdateMethod` k `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-153">Tato metoda je podobná `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="20b1b-154">Začíná volání `StartUpdate`, aktualizuje definice vývojový diagram pracovního postupu a dokončení uložením aktualizace mapování a pracovní postup aktualizované definice.</span><span class="sxs-lookup"><span data-stu-id="20b1b-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
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
  
###  <a name="BKMK_Sequential"></a><span data-ttu-id="20b1b-155">Chcete-li aktualizovat SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="20b1b-155">To update SequentialNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="20b1b-156">Přidejte následující `CreateSequentialUpdateMethod` k `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-157">Tato metoda je podobná tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="20b1b-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="20b1b-158">Začíná volání `StartUpdate`, aktualizuje definice sekvenčního pracovního postupu a dokončení uložením aktualizace mapování a pracovní postup aktualizované definice.</span><span class="sxs-lookup"><span data-stu-id="20b1b-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
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
  
###  <a name="BKMK_CreateUpdateMaps"></a><span data-ttu-id="20b1b-159">Sestavení a spuštění aplikace CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="20b1b-159">To build and run the CreateUpdateMaps application</span></span>  
  
1.  <span data-ttu-id="20b1b-160">Aktualizace `Main` metoda a přidejte následující volání tří metod.</span><span class="sxs-lookup"><span data-stu-id="20b1b-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="20b1b-161">Tyto metody jsou přidány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="20b1b-161">These methods are added in the following sections.</span></span> <span data-ttu-id="20b1b-162">Každá metoda aktualizace odpovídající číslo odhad pracovního postupu a vytvoří `DynamicUpdateMap` aktualizace, který popisuje.</span><span class="sxs-lookup"><span data-stu-id="20b1b-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>  
  
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
  
2.  <span data-ttu-id="20b1b-163">Klikněte pravým tlačítkem na **CreateUpdateMaps** v **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
3.  <span data-ttu-id="20b1b-164">Stiskněte klávesy CTRL + SHIFT + B řešení sestavíte a potom CTRL + F5 a spusťte `CreateUpdateMaps` aplikace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20b1b-165">`CreateUpdateMaps` Aplikace nejsou zobrazeny žádné informace o stavu během spuštění, ale pokud se podíváte **NumberGuessWorkflowActivities_du** složky a **PreviousVersions** složku, zobrazí se soubory definice aktualizované pracovního postupu a mapy aktualizace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>  
  
     <span data-ttu-id="20b1b-166">Po aktualizaci mapu lze vytvořit a aktualizovat definice pracovního postupu, dalším krokem je vytvoření aktualizované pracovního postupu sestavení obsahující aktualizované definice.</span><span class="sxs-lookup"><span data-stu-id="20b1b-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>  
  
###  <a name="BKMK_BuildAssembly"></a><span data-ttu-id="20b1b-167">K vytvoření sestavení aktualizované pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="20b1b-167">To build the updated workflow assembly</span></span>  
  
1.  <span data-ttu-id="20b1b-168">Otevřít druhou instanci [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20b1b-168">Open a second instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="20b1b-169">Zvolte **otevřete**, **projekt nebo řešení** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="20b1b-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>  
  
3.  <span data-ttu-id="20b1b-170">Přejděte na **NumberGuessWorkflowActivities_du** složku, kterou jste vytvořili v [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), vyberte **NumberGuessWorkflowActivities.csproj**  (nebo **vbproj**) a klikněte na tlačítko **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>  
  
4.  <span data-ttu-id="20b1b-171">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **SequentialNumberGuessWorkflow.xaml** a zvolte **vyloučit z projektu**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="20b1b-172">Stejnou věc udělat **FlowchartNumberGuessWorkflow.xaml** a **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="20b1b-173">Tento krok odebere předchozí verze definice pracovního postupu z projektu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-173">This step removes the previous versions of the workflow definitions from the project.</span></span>  
  
5.  <span data-ttu-id="20b1b-174">Zvolte **přidat existující položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="20b1b-174">Choose **Add Existing Item** from the **Project** menu.</span></span>  
  
6.  <span data-ttu-id="20b1b-175">Přejděte na **NumberGuessWorkflowActivities_du** složku, kterou jste vytvořili v [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="20b1b-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
7.  <span data-ttu-id="20b1b-176">Zvolte **soubory XAML (\*XAML;\*. XOML)** z **soubory typu** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>  
  
8.  <span data-ttu-id="20b1b-177">Vyberte **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, a **StateMachineNumberGuessWorkflow_du.xaml** a klikněte na tlačítko  **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20b1b-178">CTRL + klikněte na tlačítko vybrat více položek najednou.</span><span class="sxs-lookup"><span data-stu-id="20b1b-178">CTRL+Click to select multiple items at a time.</span></span>  
  
     <span data-ttu-id="20b1b-179">Tento krok přidává aktualizované verze definice pracovního postupu do projektu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-179">This step adds the updated versions of the workflow definitions to the project.</span></span>  
  
9. <span data-ttu-id="20b1b-180">Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="20b1b-180">Press CTRL+SHIFT+B to build the project.</span></span>  
  
10. <span data-ttu-id="20b1b-181">Zvolte **zavřít řešení** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="20b1b-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="20b1b-182">Soubor řešení pro projekt není vyžadována, proto klikněte na **ne** zavřete [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] bez uložení soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="20b1b-182">A solution file for the project is not required, so click **No** to close [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] without saving a solution file.</span></span> <span data-ttu-id="20b1b-183">Zvolte **ukončení** z **soubor** nabídky zavřete [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20b1b-183">Choose **Exit** from the **File** menu to close [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].</span></span>  
  
11. <span data-ttu-id="20b1b-184">Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowActivities_du\bin\Debug** složky (nebo **bin\Release** v závislosti na nastavení projektu).</span><span class="sxs-lookup"><span data-stu-id="20b1b-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>  
  
12. <span data-ttu-id="20b1b-185">Přejmenování **NumberGuessWorkflowActivities.dll** k **NumberGuessWorkflowActivities_v15.dll**a zkopírujte ho do **PreviousVersions** složku, kterou jste vytvořili v [Postupy: hostování více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="20b1b-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a><span data-ttu-id="20b1b-186">Chcete-li aktualizovat WorkflowVersionMap nové verze</span><span class="sxs-lookup"><span data-stu-id="20b1b-186">To update WorkflowVersionMap with the new versions</span></span>  
  
1.  <span data-ttu-id="20b1b-187">Přepněte zpět na původní instanci [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20b1b-187">Switch back to the initial instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="20b1b-188">Klikněte dvakrát na **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projektu ho otevřete.</span><span class="sxs-lookup"><span data-stu-id="20b1b-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
3.  <span data-ttu-id="20b1b-189">Přidejte tři nové identity pracovního postupu pod šesti existující deklarace identity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="20b1b-190">V tomto kurzu `1.5.0.0` slouží jako `WorkflowIdentity.Version` pro identity dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="20b1b-191">Tyto nové `v15` pracovního postupu se použije identity zadejte definice správné pracovního postupu pro instance dynamicky aktualizované trvalou pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>  
  
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
  
4.  <span data-ttu-id="20b1b-192">Přidejte následující kód na konci tohoto konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="20b1b-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="20b1b-193">Tento kód inicializuje identity dynamická aktualizace pracovního postupu, načte odpovídající definice pracovního postupu a přidá je do slovníku verze pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>  
  
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
  
     <span data-ttu-id="20b1b-194">Následující příklad je dokončené `WorkflowVersionMap` třídy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-194">The following example is the completed `WorkflowVersionMap` class.</span></span>  
  
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
  
5.  <span data-ttu-id="20b1b-195">Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="20b1b-195">Press CTRL+SHIFT+B to build the project.</span></span>  
  
###  <a name="BKMK_ApplyUpdate"></a><span data-ttu-id="20b1b-196">Použití dynamické aktualizace</span><span class="sxs-lookup"><span data-stu-id="20b1b-196">To apply the dynamic updates</span></span>  
  
1.  <span data-ttu-id="20b1b-197">Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníku řešení** a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="20b1b-198">V **nainstalovaná** uzlu, vyberte **Visual C#**, **Windows** (nebo **jazyka Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="20b1b-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20b1b-199">V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalovaná** uzlu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="20b1b-200">Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20b1b-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="20b1b-201">Vyberte **konzolové aplikace** z **Windows** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="20b1b-202">Typ **ApplyDynamicUpdate** do **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="20b1b-203">Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v **Průzkumníku řešení** a zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="20b1b-204">Klikněte na tlačítko **řešení** a zaškrtněte políčko vedle **NumberGuessWorkflowHost**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="20b1b-205">Tento odkaz je potřeba, aby `ApplyDynamicUpdate` můžete použít `NumberGuessWorkflowHost.WorkflowVersionMap` třídy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>  
  
5.  <span data-ttu-id="20b1b-206">Vyberte **Framework** z **sestavení** uzlu **přidat odkaz na** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="20b1b-207">Typ **systém.** do **hledání sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="20b1b-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="20b1b-208">Tato akce filtru sestavení a snadněji vyberte požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-208">This will filter the assemblies and make the desired references easier to select.</span></span>  
  
6.  <span data-ttu-id="20b1b-209">Zaškrtněte políčko vedle položky **systém.** z **výsledky hledání** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="20b1b-210">Typ **serializace** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Runtime.Serialization** z **výsledky hledání**  seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="20b1b-211">Typ **DurableInstancing** do **hledání sestavení** pole a zaškrtněte políčko vedle položky **System.Activities.DurableInstancing** a  **System.Runtime.DurableInstancing** z **výsledky hledání** seznamu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>  
  
9. <span data-ttu-id="20b1b-212">Klikněte na tlačítko **OK** zavřete **správce odkazů** a přidejte odkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-212">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
10. <span data-ttu-id="20b1b-213">Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v Průzkumníku řešení a zvolte **přidat**, **třída**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="20b1b-214">Typ `DynamicUpdateInfo` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>  
  
11. <span data-ttu-id="20b1b-215">Přidejte následující dva členy `DynamicUpdateInfo` třídy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="20b1b-216">Následující příklad je dokončené `DynamicUpdateInfo` třídy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="20b1b-217">Tato třída obsahuje informace o aktualizaci mapy a novou identitu pracovního postupu používá, když je aktualizována instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>  
  
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
  
12. <span data-ttu-id="20b1b-218">Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. <span data-ttu-id="20b1b-219">Klikněte dvakrát na **Program.cs** (nebo **Module1.vb**) v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="20b1b-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>  
  
14. <span data-ttu-id="20b1b-220">Přidejte následující `using` (nebo `Imports`) příkazy v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="20b1b-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
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
  
15. <span data-ttu-id="20b1b-221">Následující připojovací řetězec členy přidat `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="20b1b-222">V závislosti na vaší edicí systému SQL Server může být jiný název připojovacího řetězce serveru.</span><span class="sxs-lookup"><span data-stu-id="20b1b-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
16. <span data-ttu-id="20b1b-223">Přidejte následující `GetIDs` metodu `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-224">Tato metoda vrátí seznam identifikátorů instance pracovního postupu trvalý.</span><span class="sxs-lookup"><span data-stu-id="20b1b-224">This method returns a list of persisted workflow instance ids.</span></span>  
  
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
  
17. <span data-ttu-id="20b1b-225">Přidejte následující `LoadMap` metodu `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-226">Tato metoda vytvoří slovník, který mapuje `v1` identity pracovního postupu aktualizace Maps a nových identit pracovní postup používá k aktualizaci odpovídající trvalé instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="20b1b-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>  
  
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
  
18. <span data-ttu-id="20b1b-227">Přidejte následující `LoadMaps` metodu `Program` – třída (nebo `Module1`).</span><span class="sxs-lookup"><span data-stu-id="20b1b-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="20b1b-228">Tato metoda načte tři mapy aktualizace a vytvoří slovník, který mapuje `v1` identity pracovního postupu aktualizace Maps.</span><span class="sxs-lookup"><span data-stu-id="20b1b-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>  
  
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
  
19. <span data-ttu-id="20b1b-229">Přidejte následující kód, který `Main`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-229">Add the following code to `Main`.</span></span> <span data-ttu-id="20b1b-230">Tento kód opakuje trvalou pracovní postup instancí a ověřuje jednotlivé `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="20b1b-231">Pokud `WorkflowIdentity` mapuje `v1` instance pracovního postupu `WorkflowApplication` je nastavena definice aktualizované pracovního postupu a identity aktualizované pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="20b1b-232">Dále `WorkflowApplication.Load` je volán s instance a mapy aktualizace, která se vztahuje mapy dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="20b1b-233">Po aktualizaci aktualizované instance je zachovat pomocí volání `Unload`.</span><span class="sxs-lookup"><span data-stu-id="20b1b-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>  
  
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
  
20. <span data-ttu-id="20b1b-234">Klikněte pravým tlačítkem na **ApplyDynamicUpdate** v **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
21. <span data-ttu-id="20b1b-235">Stiskněte kombinaci kláves CTRL + SHIFT + B řešení sestavíte a stiskněte klávesu CTRL + F5 a spusťte `ApplyDynamicUpdate` aplikace a aktualizovat instance trvalou pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="20b1b-236">Měli byste vidět výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-236">You should see output similar to the following.</span></span> <span data-ttu-id="20b1b-237">Verze 1.0.0.0 pracovní postupy jsou aktualizovány na verzi 1.5.0.0, při pracovních verzi 2.0.0.0 neaktualizují.</span><span class="sxs-lookup"><span data-stu-id="20b1b-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>  
  
 <span data-ttu-id="20b1b-238">**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="20b1b-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>  
<span data-ttu-id="20b1b-239">**Aktualizováno za účelem: StateMachineNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-240">**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-241">**Aktualizováno za účelem: StateMachineNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-242">**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-243">**Aktualizováno za účelem: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-244">**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-245">**Aktualizováno za účelem: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-246">**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-247">**Aktualizováno za účelem: SequentialNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-248">**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-249">**Aktualizováno za účelem: SequentialNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-250">**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-251">**Aktualizováno za účelem: SequentialNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-252">**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-253">**Aktualizováno za účelem: StateMachineNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-254">**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="20b1b-255">**Aktualizováno za účelem: FlowchartNumberGuessWorkflow; Verze = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="20b1b-256">**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="20b1b-257">**Probíhá kontrola: StateMachineNumberGuessWorkflow; Verzi = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="20b1b-258">**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="20b1b-259">**Probíhá kontrola: FlowchartNumberGuessWorkflow; Verzi = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="20b1b-260">**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="20b1b-261">**Probíhá kontrola: SequentialNumberGuessWorkflow; Verzi = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="20b1b-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="20b1b-262">**Stisknutím libovolné klávesy pokračujte...**</span><span class="sxs-lookup"><span data-stu-id="20b1b-262">**Press any key to continue . . .**</span></span>  
  
###  <a name="BKMK_BuildAndRun"></a><span data-ttu-id="20b1b-263">Ke spuštění aplikace s aktualizované pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20b1b-263">To run the application with the updated workflows</span></span>  
  
1.  <span data-ttu-id="20b1b-264">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="20b1b-265">Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="20b1b-265">Press CTRL+F5 to run the application.</span></span>  
  
3.  <span data-ttu-id="20b1b-266">Klikněte na tlačítko **novou hru** spustit nový pracovní postup a Všimněte si níže uvedené informace verze se stavové okno, které označuje pracovního postupu `v2` pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>  
  
4.  <span data-ttu-id="20b1b-267">Vyberte jednu z `v1` pracovní postupy, které jste spustili na začátku [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="20b1b-268">Všimněte si, že informace o verzi v okně stav označuje, že pracovní postup je verze **1.5.0.0** pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="20b1b-269">Všimněte si, že nejsou žádné informace uvedené o předchozí pokusů jiné než zda byly příliš vysoké nebo příliš nízká.</span><span class="sxs-lookup"><span data-stu-id="20b1b-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>  
  
 <span data-ttu-id="20b1b-270">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="20b1b-270">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="20b1b-271">**Vaše odhad je příliš nízká.**</span><span class="sxs-lookup"><span data-stu-id="20b1b-271">**Your guess is too low.**</span></span>  
  
5.  <span data-ttu-id="20b1b-272">Poznamenejte si `InstanceId` a pak zadejte pokusů až po dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="20b1b-273">V okně Stav se zobrazí informace o obsahu, odhad, protože `WriteLine` aktivity aktualizoval dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>  
  
 <span data-ttu-id="20b1b-274">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="20b1b-274">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="20b1b-275">**Vaše odhad je příliš nízká.** </span><span class="sxs-lookup"><span data-stu-id="20b1b-275">**Your guess is too low.** </span></span>  
<span data-ttu-id="20b1b-276">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="20b1b-276">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="20b1b-277">**5 je příliš nízká.** </span><span class="sxs-lookup"><span data-stu-id="20b1b-277">**5 is too low.** </span></span>  
<span data-ttu-id="20b1b-278">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="20b1b-278">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="20b1b-279">**7 je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="20b1b-279">**7 is too high.** </span></span>  
<span data-ttu-id="20b1b-280">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="20b1b-280">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="20b1b-281">**Blahopřejeme, uhádnout číslo na oplátku 4.**</span><span class="sxs-lookup"><span data-stu-id="20b1b-281">**Congratulations, you guessed the number in 4 turns.**</span></span>  
  
6.  <span data-ttu-id="20b1b-282">Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, která odpovídá dokončené pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="20b1b-283">Pokud jste neprovedli poznámku o `InstanceId` bude pravděpodobně možné identifikovat soubor správné sledování pomocí **datum změny** informace v Průzkumníku Windows.</span><span class="sxs-lookup"><span data-stu-id="20b1b-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="20b1b-284">Poslední řádek informace o sledování obsahuje výstup nově přidaný `WriteLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="20b1b-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>  
  
 <span data-ttu-id="20b1b-285">**Zadejte prosím číslo mezi 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="20b1b-285">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="20b1b-286">**Vaše odhad je příliš nízká.** </span><span class="sxs-lookup"><span data-stu-id="20b1b-286">**Your guess is too low.** </span></span>  
<span data-ttu-id="20b1b-287">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="20b1b-287">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="20b1b-288">**5 je příliš nízká.** </span><span class="sxs-lookup"><span data-stu-id="20b1b-288">**5 is too low.** </span></span>  
<span data-ttu-id="20b1b-289">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="20b1b-289">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="20b1b-290">**7 je příliš vysoká.** </span><span class="sxs-lookup"><span data-stu-id="20b1b-290">**7 is too high.** </span></span>  
<span data-ttu-id="20b1b-291">**Zadejte prosím číslo mezi 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="20b1b-291">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="20b1b-292">**6 je správná. Uhádnout na oplátku 4.**</span><span class="sxs-lookup"><span data-stu-id="20b1b-292">**6 is correct. You guessed it in 4 turns.**</span></span>  
  
###  <a name="BKMK_StartPreviousVersions"></a><span data-ttu-id="20b1b-293">Chcete-li povolit od předchozích verzí pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="20b1b-293">To enable starting previous versions of the workflows</span></span>  
 <span data-ttu-id="20b1b-294">Pokud spustíte mimo pracovní postupy pro aktualizace, můžete upravit `NumberGuessWorkflowHost` aplikaci, která od předchozích verzí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="20b1b-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>  
  
1.  <span data-ttu-id="20b1b-295">Klikněte dvakrát na **WorkflowHostForm** v **Průzkumníku řešení**a vyberte **WorkflowType** – pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="20b1b-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>  
  
2.  <span data-ttu-id="20b1b-296">V **vlastnosti** vyberte **položky** vlastnost a klikněte na tlačítko se třemi tečkami upravit **položky** kolekce.</span><span class="sxs-lookup"><span data-stu-id="20b1b-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>  
  
3.  <span data-ttu-id="20b1b-297">Přidejte následující tři položky do kolekce.</span><span class="sxs-lookup"><span data-stu-id="20b1b-297">Add the following three items to the collection.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     <span data-ttu-id="20b1b-298">Dokončené `Items` kolekce bude mít šest položky.</span><span class="sxs-lookup"><span data-stu-id="20b1b-298">The completed `Items` collection will have six items.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  <span data-ttu-id="20b1b-299">Klikněte dvakrát na **WorkflowHostForm** v **Průzkumníku řešení**a vyberte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="20b1b-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="20b1b-300">Přidejte tři nové případech `switch` (nebo `Select Case`) příkaz v `NewGame_Click` obslužné rutiny pro mapování nové položky v **WorkflowType** – pole se seznamem na odpovídající identity pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="20b1b-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>  
  
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
  
     <span data-ttu-id="20b1b-301">Následující příklad obsahuje kompletní `switch` (nebo `Select Case`) příkaz.</span><span class="sxs-lookup"><span data-stu-id="20b1b-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>  
  
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
  
6.  <span data-ttu-id="20b1b-302">Stisknutím klávesy CTRL + F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="20b1b-303">Nyní můžete spustit `v1` verze pracovního postupu, stejně jako aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="20b1b-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="20b1b-304">Chcete-li dynamicky aktualizovat tyto nové instance, spusťte **ApplyDynamicUpdate** aplikace.</span><span class="sxs-lookup"><span data-stu-id="20b1b-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
