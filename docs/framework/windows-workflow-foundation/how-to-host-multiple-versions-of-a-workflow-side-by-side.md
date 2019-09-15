---
title: 'Postupy: Hostování několika verzí pracovního postupu současně'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989647"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Postupy: Hostování několika verzí pracovního postupu současně

`WorkflowIdentity`umožňuje vývojářům aplikací pracovních postupů přidružit název a verzi k definici pracovního postupu a tyto informace budou přidruženy k trvalé instanci pracovního postupu. Tyto informace o identitě mohou vývojáři aplikací pracovních postupů použít k povolení scénářů, jako je souběžné spouštění více verzí definice pracovního postupu, a poskytuje základní kámen pro jiné funkce, jako je například dynamická aktualizace. Tento krok v tomto kurzu ukazuje, jak použít `WorkflowIdentity` k hostování více verzí pracovního postupu současně.

> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>V tomto tématu

V tomto kroku kurzu `WriteLine` jsou aktivity v pracovním postupu upraveny tak, aby poskytovaly Další informace a přidala se nová `WriteLine` aktivita. Kopie původního sestavení pracovního postupu je uložena a hostitelská aplikace je aktualizována tak, aby mohla spustit jak původní, tak i aktualizované pracovní postupy.

- [Vytvoření kopie projektu NumberGuessWorkflowActivities](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [Postup aktualizace pracovních postupů](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [Aktualizace pracovního postupu StateMachine](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [Aktualizace pracovního postupu vývojového diagramu](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [Postup aktualizace sekvenčního pracovního postupu](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [Aktualizace WorkflowVersionMap tak, aby zahrnovalo předchozí verze pracovního postupu](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [Sestavení a spuštění aplikace](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> Než budete postupovat podle kroků v tomto tématu, spusťte aplikaci, spusťte několik pracovních postupů každého typu a proveďte jednu nebo dvě odhady pro každé z nich. V tomto kroku se používají tyto trvalé pracovní postupy a následující krok, [jak: Aktualizuje definici spuštěné instance](how-to-update-the-definition-of-a-running-workflow-instance.md)pracovního postupu.

> [!NOTE]
> Každý krok v kurzu Začínáme závisí na předchozích krocích. Pokud jste nedokončili předchozí kroky, můžete si stáhnout dokončenou verzi kurzu z [programovací model Windows Workflow Foundation (WF45) – začínáme kurzu](https://go.microsoft.com/fwlink/?LinkID=248976).

### <a name="BKMK_BackupCopy"></a>Vytvoření kopie projektu NumberGuessWorkflowActivities

1. Otevřete řešení **WF45GettingStartedTutorial** v aplikaci Visual Studio 2012, pokud není otevřené.

2. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.

3. Zavřete řešení **WF45GettingStartedTutorial** .

4. Otevřete Průzkumníka Windows a přejděte do složky, kde se nachází soubor řešení kurzu a složky projektu.

5. Vytvořte novou složku s názvem **PreviousVersions** ve stejné složce jako **NumberGuessWorkflowHost** a **NumberGuessWorkflowActivities**. Tato složka slouží k zahrnutí sestavení, která obsahují různé verze pracovních postupů použitých v následujících krocích kurzu.

6. Přejděte do složky **NumberGuessWorkflowActivities\bin\debug** (nebo **bin\Release** v závislosti na nastavení projektu). Zkopírujte **NumberGuessWorkflowActivities. dll** a vložte ho do složky **PreviousVersions** .

7. Přejmenujte **NumberGuessWorkflowActivities. dll** ve složce **PreviousVersions** na **NumberGuessWorkflowActivities_v1. dll**.

    > [!NOTE]
    > Kroky v tomto tématu ukazují jeden ze způsobů, jak spravovat sestavení používaná k tomu, aby obsahovalo více verzí pracovních postupů. Jiné metody, jako je například silné pojmenování sestavení a jejich registrování v globální mezipaměti sestavení (GAC), lze také použít.

8. Vytvořte novou složku s názvem **NumberGuessWorkflowActivities_du** ve stejné složce jako **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**a nově přidanou složku **PreviousVersions** a zkopírujte všechny soubory a podsložky ze složky **NumberGuessWorkflowActivities** do nové složky **NumberGuessWorkflowActivities_du** . Tato záložní kopie projektu pro počáteční verzi aktivit se používá v [tématu Postupy: Aktualizuje definici spuštěné instance](how-to-update-the-definition-of-a-running-workflow-instance.md)pracovního postupu.

9. Znovu otevřete řešení **WF45GettingStartedTutorial** v aplikaci Visual Studio 2012.

### <a name="BKMK_UpdateWorkflows"></a>Postup aktualizace pracovních postupů

V této části se aktualizují definice pracovních postupů. Dvě `WriteLine` aktivity, které poskytují zpětnou vazbu na odhad uživatele, se aktualizují a přidají se nové `WriteLine` aktivity, které po odhadu tohoto počtu poskytují další informace o hře.

#### <a name="BKMK_UpdateStateMachine"></a>Aktualizace pracovního postupu StateMachine

1. V **Průzkumník řešení**v projektu **NumberGuessWorkflowActivities** poklikejte na **StateMachineNumberGuessWorkflow. XAML**.

2. Dvakrát klikněte na **odhad nesprávného** přechodu na stavovém počítači.

3. Aktualizuje v `If` aktivitě levou stranu `WriteLine`. `Text`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. Aktualizujte `WriteLine` v`If`aktivitěnejvícevpravo. `Text`

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.

6. Dvakrát klikněte na **odhad správného** přechodu na Stavový počítač.

7. Přetáhněte aktivitu **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji na **aktivitu akce přetažení** na tento přechod.

8. Do `Text` pole vlastností zadejte následující výraz.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a>Aktualizace pracovního postupu vývojového diagramu

1. V **Průzkumník řešení**v projektu **NumberGuessWorkflowActivities** poklikejte na **FlowchartNumberGuessWorkflow. XAML**.

2. Aktualizuje aktivitu nejvíce `WriteLine`vlevo. `Text`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. Aktualizujte aktivitu, která je nejvíce `WriteLine` vpravo. `Text`

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. Přetáhněte aktivitu **WriteLine** z oddílu **primitivs** v **sadě nástrojů** a umístěte ji na místo odkládacího bodu `True` pro akci na nejvyšší `FlowDecision`úrovni. Aktivita se přidá do vývojového diagramu a propojí `True` se s akcí `FlowDecision`. `WriteLine`

5. Do `Text` pole vlastností zadejte následující výraz.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a>Postup aktualizace sekvenčního pracovního postupu

1. V **Průzkumník řešení**v projektu **NumberGuessWorkflowActivities** poklikejte na **SequentialNumberGuessWorkflow. XAML**.

2. Aktualizuje v `If` aktivitě levou stranu `WriteLine`. `Text`

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. Aktualizujte `WriteLine` aktivitu`If` na nejvyšší úrovni aktivity. `Text`

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. Přetáhněte aktivitu **WriteLine** z oddílu **primitivs** v **sadě nástrojů** a umístěte ji za aktivitu **DoWhile** , aby byla **WriteLine** koncová aktivita v kořenové `Sequence` aktivitě.

5. Do `Text` pole vlastností zadejte následující výraz.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a>Aktualizace WorkflowVersionMap tak, aby zahrnovalo předchozí verze pracovního postupu

1. Poklikejte na **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap. vb**) v rámci projektu **NumberGuessWorkflowHost** a otevřete ho.

2. Do horní části `using` souboru `Imports` `using` přidejtenásledujícípříkazy`Imports`(nebo).

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. Přidejte tři nové identity pracovního postupu hned pod tři existující deklarace identity pracovního postupu. Tyto nové `v1` identity pracovního postupu budou použity k zajištění správné definice pracovního postupu pro pracovní postupy zahájené před provedením aktualizací.

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

4. V konstruktoru aktualizujte vlastnost tří aktuálních identit pracovního postupu na `2.0.0.0`. `Version` `WorkflowVersionMap`

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

    Kód v, který přidá aktuální verze pracovních postupů do slovníku, používá aktuální verze, které jsou odkazovány v projektu, takže kód, který inicializuje definice pracovního postupu, není nutné aktualizovat.

5. Přidejte následující kód do konstruktoru hned za kód, který přidá aktuální verze do slovníku.

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

    Tyto identity pracovního postupu jsou přidruženy k počáteční verzi odpovídajících definicí pracovních postupů.

6. Dále načtěte sestavení, které obsahuje počáteční verzi definice pracovního postupu, a vytvořte a přidejte odpovídající definice pracovního postupu do slovníku.

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

    Následující příklad je úplným seznamem pro aktualizovanou `WorkflowVersionMap` třídu.

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

### <a name="BKMK_BuildAndRun"></a>Sestavení a spuštění aplikace

1. Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci a spusťte klávesovou zkratku CTRL + F5.

2. Kliknutím na **Nová hra**spusťte nový pracovní postup. Verze pracovního postupu se zobrazí v okně stav a v případě, že se aktualizuje aktualizovaná verze z `WorkflowIdentity`přidruženého. Poznamenejte si, `InstanceId` abyste mohli zobrazit soubor sledování pracovního postupu po jeho dokončení a pak zadat odhad, dokud se hra nedokončí. Všimněte si, jak se zobrazí odhad uživatele v informacích zobrazených v okně stav na základě aktualizací `WriteLine` aktivit.

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > Zobrazí se aktualizovaný text z `WriteLine` aktivit, ale výstup konečné `WriteLine` aktivity, která byla přidána v tomto tématu, není. Důvodem je, že okno stavu je aktualizováno `PersistableIdle` obslužnou rutinou. Protože pracovní postup skončí a nepracuje po konečné aktivitě, `PersistableIdle` obslužná rutina není volána. Nicméně podobná zpráva se zobrazí v okně `Completed` stav obslužné rutiny. V případě potřeby lze kód přidat k `Completed` obslužné rutině pro extrakci textu z okna `StringWriter` a jeho zobrazení do stavového okna.

3. Otevřete Průzkumníka Windows a přejděte do složky **NumberGuessWorkflowHost\bin\debug** (nebo **bin\Release** v závislosti na nastavení projektu) a otevřete sledovací soubor pomocí poznámkového bloku, který odpovídá dokončenému pracovnímu postupu. Pokud jste si poznamenali `InstanceId`, že se vám nepovedlo poznamenat, můžete pomocí informací o **změně data** v Průzkumníkovi Windows určit správný sledovací soubor.

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    Aktualizovaný `WriteLine` výstup je obsažen v souboru sledování, včetně výstupu `WriteLine` , který byl přidán v tomto tématu.

4. Přepněte zpět na číslo odhadované aplikace a vyberte jeden z pracovních postupů, které byly spuštěny před provedením aktualizací. Verzi aktuálně vybraného pracovního postupu můžete zjistit tak, že prohlížíte informace o verzi zobrazené pod oknem stav. Zadejte několik odhadů a Všimněte si, že se aktualizace stavu `WriteLine` shodují s výstupem aktivity z předchozí verze a nezahrnují odhad uživatele. Důvodem je, že tyto pracovní postupy používají definici předchozí pracovní postup, která `WriteLine` nemá aktualizace.

    V dalším kroku [: Aktualizujte definici spuštěné instance](how-to-update-the-definition-of-a-running-workflow-instance.md)pracovního postupu, spuštěné `v1` instance pracovního postupu se aktualizují, aby obsahovaly nové funkce jako `v2` instance.
