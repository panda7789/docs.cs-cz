---
title: 'Postupy: Spuštění pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 06ac34f5ba5d95bd9f000a35036cf288d3c8f7f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319921"
---
# <a name="how-to-run-a-workflow"></a>Postupy: Spuštění pracovního postupu
Toto téma je pokračováním kurzu Windows Workflow Foundation Getting Started a popisuje, jak vytvořit hostitele pracovního postupu a spustit pracovní postup definovaný v předchozím [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md) tématu.

> [!NOTE]
>  Každé téma v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](how-to-create-an-activity.md) a [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md).

> [!NOTE]
>  Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Chcete-li vytvořit projekt hostitele pracovního postupu  
  
1. Otevřete řešení od předchozího [jak: Vytvořit aktivitu](how-to-create-an-activity.md) tématu pomocí sady Visual Studio 2012.  
  
2. Klikněte pravým tlačítkem myši **WF45GettingStartedTutorial** řešení v **Průzkumníka řešení** a vyberte **přidat**, **nový projekt**.  
  
    > [!TIP]
    >  Pokud **Průzkumníka řešení** okno nezobrazí, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.

3. V **nainstalováno** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**).

    > [!NOTE]
    >  V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalováno** uzlu.

     Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework. Vyberte **Konzolová aplikace pracovního postupu** z **pracovního postupu** seznamu. Typ `NumberGuessWorkflowHost` do **název** pole a klikněte na tlačítko **OK**. Tím vytvoříte základní pracovní postup podpora hostování aplikace starter pracovního postupu. Tento základní kód hostování je změnit a použít ke spuštění aplikace pracovního postupu.

4. Klikněte pravým tlačítkem na nově přidaných **NumberGuessWorkflowHost** projekt **Průzkumníka řešení** a vyberte **přidat odkaz**. Vyberte **řešení** z **přidat odkaz** seznam, zaškrtněte políčko vedle **NumberGuessWorkflowActivities**a potom klikněte na tlačítko **OK** .

5. Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníka řešení** a zvolte **odstranit**. Klikněte na tlačítko **OK** potvrďte.

### <a name="to-modify-the-workflow-hosting-code"></a>Chcete-li změnit hostování kódu pracovního postupu

1. Dvakrát klikněte na panel **Program.cs** nebo **Module1.vb** v **Průzkumníka řešení** zobrazíte kód této.

    > [!TIP]
    >  Pokud **Průzkumníka řešení** okno nezobrazí, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.

     Protože tento projekt byl vytvořen pomocí **Konzolová aplikace pracovního postupu** šablony, **Program.cs** nebo **Module1.vb** obsahuje následující základní pracovní postup hostování kód.

    ```vb
    ' Create and cache the workflow definition
    Activity workflow1 = new Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     Tato vygenerována hostování kód používá <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> poskytuje jednoduchý způsob pro volání pracovního postupu, jako kdyby byly volání metody a lze použít pouze pro pracovní postupy, které nepoužívají trvalosti. <xref:System.Activities.WorkflowApplication> poskytuje širší model pro spouštění pracovních postupů, které obsahuje oznámení o události životního cyklu, řízení provádění, záložku obnovení a trvalost. Tento příklad používá záložek a <xref:System.Activities.WorkflowApplication> slouží k hostování pracovního postupu. Přidejte následující `using` nebo **importy** příkazu v horní části **Program.cs** nebo **Module1.vb** pod řádek **pomocí** nebo **importy** příkazy.

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Nahraďte řádků kódu, které používají <xref:System.Activities.WorkflowInvoker> s následující basic <xref:System.Activities.WorkflowApplication> hostování kódu. Tato ukázka hostování kód ukazuje základní kroky pro hostování a volání pracovního postupu, ale ještě neobsahuje funkce k úspěšnému spuštění pracovního postupu v tomto tématu. V následujících krocích se upraví tento základní kód a další funkce se přidají, dokud se nedokončí aplikace.

    > [!NOTE]
    >  Nahraďte prosím `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup můžete dokončit v předchozím [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md) kroku. Pokud jste nenahrazují `Workflow1` pak při akci a vytvářet nebo spouštět pracovní postup bude docházet k chybám sestavení.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Tento kód vytvoří <xref:System.Activities.WorkflowApplication>, přihlásí na tři události životního cyklu pracovního postupu, spustí pracovní postup voláním <xref:System.Activities.WorkflowApplication.Run%2A>a potom počká na dokončení pracovního postupu. Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> a Hostitel aplikace dokončí.

### <a name="to-set-input-arguments-of-a-workflow"></a>Chcete-li nastavit vstupní argumenty pracovního postupu

1. Přidejte následující příkaz v horní části **Program.cs** nebo **Module1.vb** pod řádek `using` nebo `Imports` příkazy.

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Nahraďte řádek kódu, který vytvoří nový <xref:System.Activities.WorkflowApplication> následujícím kódem, které vytváří a předává slovník parametrů do pracovního postupu při jeho vytvoření.

    > [!NOTE]
    >  Nahraďte prosím `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup můžete dokončit v předchozím [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md) kroku. Pokud jste nenahrazují `Workflow1` pak při akci a vytvářet nebo spouštět pracovní postup bude docházet k chybám sestavení.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Tento slovník obsahuje jeden element s klíčem `MaxNumber`. Klíče ve slovníku vstupní odpovídají vstupní argumenty kořenové aktivity pracovního postupu. `MaxNumber` tímto pracovním postupem se používá k určení horní mez pro náhodně generovaným číslem.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>K načtení výstupu argumentů pracovního postupu

1. Upravit <xref:System.Activities.WorkflowApplication.Completed%2A> obslužná rutina se má načíst a zobrazit počet zapne používá pracovní postup.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Chcete-li obnovit záložku

1. Přidejte následující kód v horní části `Main` metoda bezprostředně po existující <xref:System.Threading.AutoResetEvent> deklarace.

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužná rutina pod existující tři pracovní postup životním cyklu obslužných rutin v `Main`.

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Pokaždé, když pracovního postupu změní nečinnosti čekání na další odhad Tato obslužná rutina se nazývá a `idleAction` <xref:System.Threading.AutoResetEvent> nastavena. Tento kód v následujícím kroku použije `idleEvent` a `syncEvent` k určení, zda pracovní postup čeká další uhádnout nebo dokončení.

    > [!NOTE]
    >  V tomto příkladu hostitelská aplikace používá automatické obnovení události v <xref:System.Activities.WorkflowApplication.Completed%2A> a <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny pro synchronizaci hostitelská aplikace se průběh pracovního postupu. Není nutné a blokovat čekání pracovního postupu na nečinnost před obnovením záložku, ale v tomto příkladu jsou požadované události synchronizace, tak hostitele pozná, zda dokončení pracovního postupu nebo určuje, zda je čekání na další vstupu uživatele s použitím <xref:System.Activities.Bookmark>. Další informace najdete v tématu [záložky](bookmarks.md).

3. Odeberte volání `WaitOne`a nahraďte kód, shromažďovat vstup od uživatele a pokračovat <xref:System.Activities.Bookmark>.

     Odeberte následující řádek kódu.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     V následujícím příkladu nahraďte ho.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> Sestavení a spuštění aplikace

1. Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a vyberte **nastavit jako spouštěný projekt**.

2. Stisknutím kláves CTRL + F5 sestavte a spusťte aplikaci. Došlo k pokusu o uhodnutí číslo na oplátku co nejrychleji.

     Pokud chcete vyzkoušet aplikace s jedním z jiné styly pracovního postupu, nahraďte `Workflow1` v kódu, který vytvoří <xref:System.Activities.WorkflowApplication> s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`, v závislosti na styl pracovního postupu, který očekáváte.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Pokyny ohledně toho, jak přidat do aplikace pracovního postupu, trvalosti najdete v dalším tématu s názvem [jak: Vytvoření a spuštění dlouhodobého spuštění pracovního postupu](how-to-create-and-run-a-long-running-workflow.md).

## <a name="example"></a>Příklad
 V následujícím příkladu je kompletní kód pro výpis `Main` metody.

> [!NOTE]
>  Nahraďte prosím `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup můžete dokončit v předchozím [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md) kroku. Pokud jste nenahrazují `Workflow1` pak při akci a vytvářet nebo spouštět pracovní postup bude docházet k chybám sestavení.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Programování Windows Workflow Foundation](programming.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření pracovního postupu](how-to-create-a-workflow.md)
- [Postupy: Vytvoření a spuštění dlouhodobého spuštění pracovního postupu](how-to-create-and-run-a-long-running-workflow.md)
- [Čekání na zadání v pracovním postupu](waiting-for-input-in-a-workflow.md)
- [Hostování pracovních postupů](hosting-workflows.md)