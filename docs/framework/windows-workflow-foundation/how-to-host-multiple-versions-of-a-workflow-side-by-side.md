---
title: "Postupy: hostování více verzí pracovní postup-souběžného"
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
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f6fa267e6400672328714f016a5823d8f1311aa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Postupy: hostování více verzí pracovní postup-souběžného
`WorkflowIdentity`umožňuje vývojářům aplikací pracovního postupu pro definici pracovního postupu přidružení název a verzi a pro tyto informace k být přidružen k instanci pracovního postupu trvalý. Tyto informace identity lze použít vývojáři aplikace pracovního postupu povolit scénáře, jako je vedle sebe spouštění více verzí definice pracovního postupu a poskytuje základním kamenem pro další funkce, jako je například dynamická aktualizace. Tento krok v tomto kurzu ukazuje, jak používat `WorkflowIdentity` k hostování více verzí pracovního postupu ve stejnou dobu.  
  
> [!NOTE]
>  Stažení dokončené verze nebo zobrazení na video s návodem kurzu, najdete v tématu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>V tomto tématu  
 V tomto kroku kurzu `WriteLine` aktivitám v pracovním postupu jsou upravit tak, aby poskytují další informace a nové `WriteLine` je přidána. Je uložená kopie původní sestavení pracovního postupu, a hostitel bude aktualizována tak, aby ho původní i aktualizované pracovních postupů ve stejnou dobu.  
  
-   [Vytvořit kopii NumberGuessWorkflowActivities projektu](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [Chcete-li aktualizovat pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [Chcete-li aktualizovat StateMachine pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [Chcete-li aktualizovat vývojový diagram pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [Chcete-li aktualizovat sekvenční pracovní postup](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [Chcete-li aktualizovat WorkflowVersionMap zahrnující předchozí verze pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [Sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  Před postupovat podle kroků v tomto tématu, aplikaci spustit, spusťte několik pracovních postupů každého typu a provedení jednoho nebo dvou pokusů u každé z nich. Tyto trvalou pracovní postupy se používají v tomto kroku a následující krok, [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
> [!NOTE]
>  Každý krok v tomto kurzu Začínáme závisí na předchozí kroky. Pokud jste neprovedli předchozí kroky můžete stáhnout dokončenou verzi kurzem z [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
###  <a name="BKMK_BackupCopy"></a>Vytvořit kopii NumberGuessWorkflowActivities projektu  
  
1.  Otevřete **WF45GettingStartedTutorial** řešení v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Pokud není otevřen.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Zavřít **WF45GettingStartedTutorial** řešení.  
  
4.  Otevřete Průzkumníka Windows a přejděte do složky, kde se nachází soubor kurz řešení a projektu složky.  
  
5.  Vytvořte novou složku s názvem **PreviousVersions** ve stejné složce jako **NumberGuessWorkflowHost** a **NumberGuessWorkflowActivities**. Tato složka se používá k obsahovat sestavení, které obsahují různé verze použit v následné kroky kurzu pracovních postupů.  
  
6.  Přejděte na **NumberGuessWorkflowActivities\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu). Kopírování **NumberGuessWorkflowActivities.dll** a vložte ji do **PreviousVersions** složky.  
  
7.  Přejmenování **NumberGuessWorkflowActivities.dll** v **PreviousVersions** složku pro **NumberGuessWorkflowActivities_v1.dll**.  
  
    > [!NOTE]
    >  Kroky v tomto tématu ukazují jeden způsob, jak spravovat sestavení obsahuje více verzí pracovních postupů. Může také použít jiné metody, jako je například silné názvy sestavení a jejich registrace v globální mezipaměti sestavení.  
  
8.  Vytvořte novou složku s názvem **NumberGuessWorkflowActivities_du** ve stejné složce jako **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**a nově Přidat **PreviousVersions** složku a zkopírujte všechny soubory a podsložky ze **NumberGuessWorkflowActivities** složky do nové  **NumberGuessWorkflowActivities_du** složky. Tento záložní kopii projekt pro počáteční verze aktivity se používá v [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
9. Znovu ho otevřete **WF45GettingStartedTutorial** řešení v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
###  <a name="BKMK_UpdateWorkflows"></a>Chcete-li aktualizovat pracovních postupů  
 V této části jsou aktualizované definice pracovního postupu. Dva `WriteLine` aktivity, které váš názor na odhad uživatele jsou aktualizované a nové `WriteLine` aktivity se přidá, který poskytuje další informace o hry, jakmile je uhádnout číslo.  
  
####  <a name="BKMK_UpdateStateMachine"></a>Chcete-li aktualizovat StateMachine pracovního postupu  
  
1.  V **Průzkumníku řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **StateMachineNumberGuessWorkflow.xaml**.  
  
2.  Dvakrát klikněte **uhodnout nesprávné** přechod na stav stavového stroje.  
  
3.  Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  Aktualizace `Text` z nejvíce vpravo `WriteLine` v `If` aktivity.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.  
  
6.  Dvakrát klikněte **uhodnout správné** přechod na stav stavového stroje.  
  
7.  Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** na **vyřadit akce aktivity sem** popisek Přechod.  
  
8.  Zadejte následující výraz do `Text` pole vlastnosti.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a>Chcete-li aktualizovat vývojový diagram pracovního postupu  
  
1.  V **Průzkumníku řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **FlowchartNumberGuessWorkflow.xaml**.  
  
2.  Aktualizace `Text` z nejvíce vlevo `WriteLine` aktivity.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  Aktualizace `Text` z nejvíce vpravo `WriteLine` aktivity.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej v bodě rozevírací `True` akce nejhornější `FlowDecision` . `WriteLine` Aktivity je přidán do vývojový diagram a propojit s `True` akce `FlowDecision`.  
  
5.  Zadejte následující výraz do `Text` pole vlastnosti.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a>Chcete-li aktualizovat sekvenční pracovní postup  
  
1.  V **Průzkumníku řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **SequentialNumberGuessWorkflow.xaml**.  
  
2.  Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  Aktualizace `Text` z nejvíce vpravo `WriteLine` aktivity v `If` aktivity.  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej po **DoWhile** aktivity tak, aby  **WriteLine** je poslední aktivita v kořenu `Sequence` aktivity.  
  
5.  Zadejte následující výraz do `Text` pole vlastnosti.  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a>Chcete-li aktualizovat WorkflowVersionMap zahrnující předchozí verze pracovního postupu  
  
1.  Klikněte dvakrát na **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projektu ho otevřete.  
  
2.  Přidejte následující `using` (nebo `Imports`) příkazů do horní části souboru k ostatním `using` (nebo `Imports`) příkazy.  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  Přidejte tři nové identity pracovního postupu pod tři existující deklarace identity pracovního postupu. Tyto nové `v1` pracovního postupu se použije identity zadejte definice pracovního postupu správné před byly provedeny aktualizace spustit pracovní postupy.  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 Identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
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
    ```  
  
4.  V `WorkflowVersionMap` konstruktor, aktualizovat `Version` vlastnost tři aktuální identit pracovního postupu, které `2.0.0.0`.  
  
    ```vb  
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
    ```  
  
    ```csharp  
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
    ```  
  
     Kód v tom, že přidá aktuální verze pracovních postupů do slovníku používá aktuální verze, které se odkazuje v projektu, takže není nutné aktualizovat kód, který inicializuje definice pracovního postupu.  
  
5.  Přidejte následující kód bezprostředně za kód, který přidá do slovníku aktuální verze v konstruktoru.  
  
    ```vb  
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
    ```  
  
    ```csharp  
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
    ```  
  
     Tyto pracovní postup identity jsou přidruženy k počáteční verze odpovídající definice pracovního postupu.  
  
6.  V dalším kroku načíst sestavení, které obsahuje počáteční verze definice pracovního postupu, a vytvořit a přidat odpovídající definice pracovního postupu do slovníku.  
  
    ```vb  
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
    ```  
  
    ```csharp  
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
    ```  
  
     V následujícím příkladu je úplný seznam pro aktualizaci `WorkflowVersionMap` třídy.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 Identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
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
  
###  <a name="BKMK_BuildAndRun"></a>Sestavení a spuštění aplikace  
  
1.  Stisknutím kombinace kláves CTRL + SHIFT + B pro sestavení aplikace a potom CTRL + F5 a spusťte.  
  
2.  Spuštění nového pracovního postupu kliknutím **novou hru**. Verze pracovního postupu se zobrazí v okně Stav a odráží aktualizovanou verzi z přidruženého `WorkflowIdentity`. Poznamenejte si `InstanceId` vám umožní zobrazit soubor sledování pro pracovní postup po dokončení, a pak zadejte pokusů, dokud se nedokončí hra. Všimněte si, jak odhad uživatele se zobrazí v informace zobrazené v okně Stav na základě aktualizací do `WriteLine` aktivity.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**5 je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**3 je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**1 je příliš nízká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**Blahopřejeme, uhádnout číslo na oplátku 4.**    
    > [!NOTE]
    >  Aktualizovaný text z `WriteLine` aktivity se zobrazí, ale výstup konečné `WriteLine` aktivity, která byla přidána v tomto tématu není. Je to způsobeno okně Stav se aktualizuje `PersistableIdle` obslužné rutiny. Protože pracovní postup dokončení a nepřekračuje nečinnosti za poslední aktivitu `PersistableIdle` není volána obslužná rutina. Ale podobná zpráva se zobrazí v okně Stav pomocí `Completed` obslužné rutiny. V případě potřeby kódu nebylo možné přidat do `Completed` obslužná rutina rozbalte text z `StringWriter` a zobrazit ji do okna stav.  
  
3.  Otevřete Průzkumníka Windows a přejděte do **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, která odpovídá dokončené pracovního postupu. Pokud jste neprovedli poznámku o `InstanceId`, správné sledování souborů můžete identifikovat pomocí **datum změny** informace v Průzkumníku Windows.  
  
 **Zadejte prosím číslo mezi 1 a 10**  
**5 je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**3 je příliš vysoká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**1 je příliš nízká.**   
**Zadejte prosím číslo mezi 1 a 10**   
**2 je správná. Uhádnout na oplátku 4.**      Aktualizovaný `WriteLine` výstup je obsažený v souboru sledování, včetně výstup `WriteLine` který byl přidán v tomto tématu.  
  
4.  Přepněte zpět na číslo hádání aplikace a vyberte jednu z pracovních postupů, které byla zahájena před aktualizací byly provedeny. Verzi aktuálně vybrané pracovní postup můžete identifikovat pohledem na informace o verzi, který se zobrazí pod stavové okno. Zadejte některé pokusů a Všimněte si, že stav aktualizace shoda `WriteLine` aktivita výstup z předchozí verze a nezahrnují odhad uživatele. Důvodem je, že tyto pracovní postupy používají předchozí definice pracovního postupu, který nemá `WriteLine` aktualizace.  
  
     V dalším kroku [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), na kterém běží `v1` instancí pracovních postupů jsou aktualizovány tak, že obsahují nové funkce, jako `v2` instance.
