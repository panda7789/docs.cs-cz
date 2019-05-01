---
title: 'Postupy: Hostování několika verzí pracovního postupu současně'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 061a8c7b73903b763de27e614e9b3067777afe58
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809459"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>Postupy: Hostování několika verzí pracovního postupu současně

`WorkflowIdentity` umožňuje vývojářům aplikací pracovní postup přidružit název a verze definice pracovního postupu a tyto informace k trvalé instance práce. Tyto informace identita umožňuje vývojáři aplikace pracovního postupu povolení scénářů, jako je vedle sebe spuštění více verzí modulu definice pracovního postupu a poskytuje základní kámen pro další funkce, jako je například dynamická aktualizace. Tento krok úvodního kurzu ukazuje, jak používat `WorkflowIdentity` k hostování několika verzí pracovního postupu ve stejnou dobu.

> [!NOTE]
> Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="in-this-topic"></a>V tomto tématu

V tomto kroku kurzu `WriteLine` aktivitám v pracovním postupu jsou upraveny pro poskytnutí dalších informací a nový `WriteLine` je aktivita přidána. Je uložená kopie původního sestavení pracovního postupu a hostitelské aplikace se aktualizuje tak, aby ji můžete spustit původní a aktualizovaný pracovní postupy ve stejnou dobu.

- [Chcete-li kopii projektu NumberGuessWorkflowActivities](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [Chcete-li aktualizovat pracovní postupy](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

    - [Na aktualizaci pracovního postupu stavový stroj StateMachine](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

    - [Na aktualizaci pracovního postupu vývojového diagramu](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

    - [Chcete-li aktualizovat sekvenčního pracovního postupu](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [Chcete-li aktualizovat WorkflowVersionMap zahrnovat předchozí verze pracovního postupu](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [Sestavení a spuštění aplikace](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> Před provedením kroků v tomto tématu, spusťte aplikaci, spustit několik pracovních postupů u každého typu a provedení jedné nebo dvou pokusů u každé z nich. Tyto trvalý pracovní postupy se používají v tomto kroku a následující krok [jak: Aktualizace definice běžící Instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md).

> [!NOTE]
> Každý krok úvodního kurzu Začínáme závisí na předchozí kroky. Pokud jste neprovedli v předchozích krocích můžete stáhnout úplnou verzi kurzem z [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

### <a name="BKMK_BackupCopy"></a> Chcete-li kopii projektu NumberGuessWorkflowActivities

1. Otevřete **WF45GettingStartedTutorial** řešení ve Visual Studio 2012, pokud není otevřen.

2. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.

3. Zavřít **WF45GettingStartedTutorial** řešení.

4. Otevřete Průzkumníka Windows a přejděte do složky, kde se nachází soubor kurz řešení a složky projektu.

5. Vytvořte novou složku s názvem **PreviousVersions** ve stejné složce jako **NumberGuessWorkflowHost** a **NumberGuessWorkflowActivities**. Tato složka se používá pro jiné sestavení, které obsahují různé verze pracovních postupech, používat v dalších kroků kurzu.

6. Přejděte **NumberGuessWorkflowActivities\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu). Kopírování **NumberGuessWorkflowActivities.dll** a vložte ho do **PreviousVersions** složky.

7. Přejmenovat **NumberGuessWorkflowActivities.dll** v **PreviousVersions** složku **NumberGuessWorkflowActivities_v1.dll**.

    > [!NOTE]
    > Kroky v tomto tématu ukazují jeden způsob, jak spravovat sestavení použít tak, aby obsahovala více verzí pracovních postupů. Také lze použít jiné metody, jako je například silné názvy sestavení a jejich registrace v globální mezipaměti sestavení.

8. Vytvořte novou složku s názvem **NumberGuessWorkflowActivities_du** ve stejné složce jako **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**a nově Přidání **PreviousVersions** složky a zkopírujte všechny soubory a podsložky ze **NumberGuessWorkflowActivities** do nové složky  **NumberGuessWorkflowActivities_du** složky. Tuto záložní kopii projektu pro počáteční verze aktivit se používá v [jak: Aktualizace definice běžící Instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md).

9. Znovu otevřete **WF45GettingStartedTutorial** řešení v sadě Visual Studio 2012.

### <a name="BKMK_UpdateWorkflows"></a> Chcete-li aktualizovat pracovní postupy

 V této části se aktualizují definice pracovního postupu. Dva `WriteLine` aktivity, které váš názor na odhad uživatele jsou aktualizované a nový `WriteLine` je aktivita přidána, která poskytuje další informace o hry po uhodnout číslo.

#### <a name="BKMK_UpdateStateMachine"></a> Na aktualizaci pracovního postupu stavový stroj StateMachine

1. V **Průzkumníka řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **StateMachineNumberGuessWorkflow.xaml**.

2. Dvakrát klikněte **uhodnout nesprávné** přechodu na stavový počítač.

3. Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. Aktualizace `Text` z úplně vpravo `WriteLine` v `If` aktivity.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.

6. Dvakrát klikněte **odhad správný** přechodu na stavový počítač.

7. Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho na **Sem přetáhněte akci aktivitu** popisek Přechod.

8. Zadejte následující výraz do `Text` vlastnosti.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a> Na aktualizaci pracovního postupu vývojového diagramu

1. V **Průzkumníka řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **FlowchartNumberGuessWorkflow.xaml**.

2. Aktualizace `Text` z nejvíce vlevo `WriteLine` aktivity.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. Aktualizace `Text` z úplně vpravo `WriteLine` aktivity.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho na místa přetažení `True` akce horní `FlowDecision` . `WriteLine` Je aktivita přidána do vývojového diagramu a propojit s `True` akce `FlowDecision`.

5. Zadejte následující výraz do `Text` vlastnosti.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a> Chcete-li aktualizovat sekvenčního pracovního postupu

1. V **Průzkumníka řešení**v části **NumberGuessWorkflowActivities** projektu, klikněte dvakrát na **SequentialNumberGuessWorkflow.xaml**.

2. Aktualizace `Text` z nejvíce vlevo `WriteLine` v `If` aktivity.

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. Aktualizace `Text` z úplně vpravo `WriteLine` aktivity v `If` aktivity.

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho po **DoWhile** aktivitu tak, aby  **WriteLine** je poslední aktivita v kořenovém adresáři `Sequence` aktivity.

5. Zadejte následující výraz do `Text` vlastnosti.

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a> Chcete-li aktualizovat WorkflowVersionMap zahrnovat předchozí verze pracovního postupu

1. Dvakrát klikněte na panel **WorkflowVersionMap.cs** (nebo **WorkflowVersionMap.vb**) v části **NumberGuessWorkflowHost** projekt tak, aby ho otevřete.

2. Přidejte následující `using` (nebo `Imports`) příkazy do horní části souboru k ostatním `using` (nebo `Imports`) příkazy.

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. Přidejte tři nové identity pracovního postupu pod tři existující deklarace identity pracovního postupu. Tyto nové `v1` pracovního postupu se použije identity poskytnout definici správné pracovního postupu pro pracovní postupy spuštěné před byly provedeny aktualizace.

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

4. V `WorkflowVersionMap` konstruktoru, aktualizace `Version` vlastnost tři aktuální identity pracovního postupu k `2.0.0.0`.

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

    Kód, který přidá aktuálních verzích pracovních postupů do slovníku používá aktuální verze, které je odkazováno v projektu, takže není potřeba aktualizovat kód, který inicializuje definice pracovního postupu.

5. Přidejte následující kód do konstruktoru hned za kód, který se přidá do slovníku aktuální verze.

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

    Tyto identity pracovního postupu jsou spojeny s počáteční verze odpovídající definice pracovního postupu.

6. V dalším kroku načíst sestavení, které obsahuje počáteční verze definice pracovního postupu a vytvořte a přidejte odpovídající definice pracovního postupu do slovníku.

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

### <a name="BKMK_BuildAndRun"></a> Sestavení a spuštění aplikace

1. Stiskněte kombinaci kláves CTRL + SHIFT + B pro vytvoření aplikace a potom CTRL + F5 ke spuštění.

2. Začněte kliknutím na nový pracovní postup **novou hru**. Verze pracovního postupu se zobrazí v okně Stav a zahrnuje aktualizovanou verzi z přidruženého `WorkflowIdentity`. Poznamenejte si `InstanceId` tak můžete zobrazit soubor sledování pracovního postupu po dokončení a až do dokončení hra, zadejte pokusů. Všimněte si, jak odhad uživatele se zobrazí v informace zobrazené v okně Stav na základě aktualizací na `WriteLine` aktivity.

    ```
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
    > Aktualizovaný text z `WriteLine` aktivity se zobrazí, ale výstup finální `WriteLine` je aktivitou, která byla přidána v tomto tématu. Důvodem je, že se aktualizoval stav okna `PersistableIdle` obslužné rutiny. Protože pracovní postup dokončí a nepřekračuje nečinnosti za poslední aktivitu `PersistableIdle` obslužná rutina není volána. Ale podobná zpráva se zobrazí v okně Stav podle `Completed` obslužné rutiny. V případě potřeby kód může být přidán do `Completed` obslužnou rutinu k extrakci textu z `StringWriter` a zobrazí se stavové okno.

3. Otevřete Průzkumníka Windows a přejděte **NumberGuessWorkflowHost\bin\debug** složky (nebo **bin\release** v závislosti na nastavení projektu) a otevřete soubor sledování pomocí poznámkového bloku, který odpovídá k dokončení pracovního postupu. Pokud jste neprovedli si `InstanceId`, správné sledování souboru lze identifikovat pomocí **datum změny** informace v Průzkumníku Windows.

    ```
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    Aktualizovaný `WriteLine` výstup je obsažený v souboru sledování, včetně výstup `WriteLine` , který byl přidán v tomto tématu.

4. Přepněte zpátky na číslo využití aplikace a vyberte jednu z pracovních postupů, které byla spuštěna dříve, než byly provedeny aktualizace. Zobrazením pod stavové okno se zobrazí informace o verzi můžete identifikovat verzi aktuálně vybraného pracovního postupu. Zadejte několik pokusů a Všimněte si, že stav aktualizuje shodu `WriteLine` aktivity výstup z předchozí verze a nezahrnují odhad uživatele. Důvodem je, že tyto pracovní postupy používají předchozí definice pracovního postupu, který nemá `WriteLine` aktualizace.

    V dalším kroku [jak: Aktualizovat definici spuštění instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md), spouštění `v1` instancí pracovních postupů jsou aktualizovány tak, že obsahují nové funkce, jako `v2` instancí.
