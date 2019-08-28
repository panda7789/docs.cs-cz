---
title: 'Postupy: Spuštění pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 07f0e5dc232411633626add460ffc29cc7a79d81
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044356"
---
# <a name="how-to-run-a-workflow"></a>Postupy: Spuštění pracovního postupu
Toto téma je pokračováním v kurzu programovací model Windows Workflow Foundation Začínáme a popisuje, jak vytvořit hostitele pracovního postupu a spustit pracovní postup definovaný v předchozím [postupu: Vytvořte téma pracovního](how-to-create-a-workflow.md) postupu.

> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li dokončit toto téma, je [nutné nejprve provést následující kroky: Vytvoření aktivity](how-to-create-an-activity.md) a [postup: Vytvořte pracovní postup](how-to-create-a-workflow.md).

> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Vytvoření projektu hostitele pracovního postupu  
  
1. Otevřete řešení z předchozího [postupu: Vytvoření tématu aktivity](how-to-create-an-activity.md) pomocí sady Visual Studio 2012.  
  
2. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení **WF45GettingStartedTutorial** a vyberte **Přidat**, **Nový projekt**.  
  
    > [!TIP]
    > Pokud se okno **Průzkumník řešení** nezobrazí, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .

3. V **nainstalovaném** uzlu vyberte možnost **Visual C#** , **Workflow** (nebo **Visual Basic**, **pracovní postup**).

    > [!NOTE]
    > V závislosti na tom, který programovací jazyk je nakonfigurován jako primární jazyk v aplikaci Visual Studio, může být uzel **vizuálu C#**  nebo **Visual Basic** pod uzlem **ostatní jazyky** v **nainstalovaném** uzlu.

     V rozevíracím seznamu .NET Framework verze se ujistěte, že je vybraná možnost **.NET Framework 4,5** . V seznamu **pracovních postupů** vyberte **Konzolová aplikace pracovního postupu** . Do `NumberGuessWorkflowHost` pole **název** zadejte a klikněte na **OK**. Tím se vytvoří aplikace pracovního postupu Starter se základní podporou hostování pracovního postupu. Tento základní kód pro hostování se upraví a použije ke spuštění aplikace pracovního postupu.

4. Klikněte pravým tlačítkem na nově přidaný projekt **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat odkaz**. V seznamu **Přidat odkaz** vyberte **řešení** , zaškrtněte políčko vedle **NumberGuessWorkflowActivities**a potom klikněte na tlačítko **OK**.

5. V **Průzkumník řešení** klikněte pravým tlačítkem na **Workflow1. XAML** a vyberte **Odstranit**. Potvrďte kliknutím na tlačítko **OK** .

### <a name="to-modify-the-workflow-hosting-code"></a>Úprava kódu hostování pracovního postupu

1. Poklikejte na **program.cs** nebo **Module1. vb** v **Průzkumník řešení** pro zobrazení kódu.

    > [!TIP]
    > Pokud se okno **Průzkumník řešení** nezobrazí, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .

     Vzhledem k tomu, že tento projekt byl vytvořen pomocí šablony **konzolové aplikace pracovního postupu** , **program.cs** nebo **Module1. vb** obsahuje následující základní kód pro hostování pracovního postupu.

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     Tento generovaný kód pro hostování <xref:System.Activities.WorkflowInvoker>používá. <xref:System.Activities.WorkflowInvoker>poskytuje jednoduchý způsob, jak vyvolat pracovní postup, jako by šlo o volání metody a dá se použít jenom pro pracovní postupy, které nepoužívají trvalost. <xref:System.Activities.WorkflowApplication>poskytuje bohatší model pro spouštění pracovních postupů, které obsahují oznámení o událostech životního cyklu, řízení spouštění, opětovném obnovení záložek a persistenci. V tomto příkladu se používají <xref:System.Activities.WorkflowApplication> záložky a slouží k hostování pracovního postupu. Přidejte `using` následující příkaz nebo **importy** na začátek **program.cs** nebo **Module1. vb** pod existující příkazy **using** nebo Imports .

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Nahraďte řádky kódu, které jsou <xref:System.Activities.WorkflowInvoker> používány, pomocí následujícího <xref:System.Activities.WorkflowApplication> základního hostujícího kódu. Tento ukázkový hostující kód znázorňuje základní kroky pro hostování a vyvolání pracovního postupu, ale ještě neobsahuje funkce pro úspěšné spuštění pracovního postupu z tohoto tématu. V následujících krocích se tento základní kód upraví a přidají se další funkce, dokud se aplikace nedokončí.

    > [!NOTE]
    > Nahraďte `Workflow1` je v těchto příkladech `SequentialNumberGuessWorkflow`pomocí `FlowchartNumberGuessWorkflow`, `StateMachineNumberGuessWorkflow`nebo v závislosti na tom, který pracovní postup jste dokončili v předchozím [postupu: Vytvořte krok pracovního](how-to-create-a-workflow.md) postupu. Pokud se nenahradíte `Workflow1` , zobrazí se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Tento kód vytvoří <xref:System.Activities.WorkflowApplication>přihlášení k odběru tří událostí životního cyklu pracovního postupu, spustí pracovní postup s <xref:System.Activities.WorkflowApplication.Run%2A>voláním a potom počká, až se pracovní postup dokončí. Po dokončení <xref:System.Threading.AutoResetEvent> pracovního postupu se nastaví a hostitelská aplikace se dokončí.

### <a name="to-set-input-arguments-of-a-workflow"></a>Nastavení vstupních argumentů pracovního postupu

1. Přidejte následující příkaz na začátek **program.cs** nebo **Module1. vb** pod existující `using` příkazy nebo `Imports` .

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Nahraďte řádek kódu, který vytvoří nový <xref:System.Activities.WorkflowApplication> , pomocí následujícího kódu, který vytvoří a předá do pracovního postupu slovník parametrů při jeho vytvoření.

    > [!NOTE]
    > Nahraďte `Workflow1` je v těchto příkladech `SequentialNumberGuessWorkflow`pomocí `FlowchartNumberGuessWorkflow`, `StateMachineNumberGuessWorkflow`nebo v závislosti na tom, který pracovní postup jste dokončili v předchozím [postupu: Vytvořte krok pracovního](how-to-create-a-workflow.md) postupu. Pokud se nenahradíte `Workflow1` , zobrazí se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Tento slovník obsahuje jeden element s klíčem `MaxNumber`. Klíče ve vstupním slovníku odpovídají vstupním argumentům pro kořenovou aktivitu pracovního postupu. `MaxNumber`používá pracovní postup k určení horní meze pro náhodně generované číslo.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Načtení výstupních argumentů pracovního postupu

1. <xref:System.Activities.WorkflowApplication.Completed%2A> Upravte obslužnou rutinu tak, aby načetla a zobrazila počet zapínání pomocí pracovního postupu.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Obnovení záložky

1. Do vrcholu `Main` metody přidejte následující kód hned po existující <xref:System.Threading.AutoResetEvent> deklaraci.

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužnou rutinu hned pod stávající tři obslužné rutiny životního cyklu `Main`pracovního postupu v.

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Pokaždé, když se pracovní postup nečinný čeká na další odhad, je tato obslužná rutina volána a `idleAction` <xref:System.Threading.AutoResetEvent> je nastavena. Kód v následujícím kroku používá `idleEvent` a `syncEvent` k určení, zda pracovní postup čeká na další odhad nebo je dokončen.

    > [!NOTE]
    > V tomto příkladu hostitelská aplikace používá události automatického resetu v <xref:System.Activities.WorkflowApplication.Completed%2A> obslužných rutinách a <xref:System.Activities.WorkflowApplication.Idle%2A> k synchronizaci hostitelské aplikace s průběhem pracovního postupu. Není nutné a blokovat čekání pracovního postupu na nečinnost před obnovením záložku, ale v tomto příkladu jsou požadované události synchronizace, tak hostitele pozná, zda dokončení pracovního postupu nebo určuje, zda je čekání na další vstupu uživatele s použitím <xref:System.Activities.Bookmark>. Další informace najdete v tématu [záložky](bookmarks.md).

3. Odeberte volání `WaitOne`a nahraďte ho kódem pro shromáždění vstupu od uživatele a pokračování v <xref:System.Activities.Bookmark>.

     Odeberte následující řádek kódu.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Nahraďte následujícím příkladem.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a>Sestavení a spuštění aplikace

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **nastavit jako spouštěný projekt**.

2. Stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte aplikaci. Zkuste číslo uhodnout v co nejkratší míře.

     Chcete-li aplikaci vyzkoušet s jedním z dalších stylů pracovního postupu, nahraďte `Workflow1` v kódu, který <xref:System.Activities.WorkflowApplication> vytváří s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`nebo `StateMachineNumberGuessWorkflow`, podle toho, který styl pracovního postupu si přejete.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Pokyny, jak přidat trvalost do aplikace pracovního postupu, najdete v dalším tématu [postup: Vytvořte a spusťte dlouhodobě běžící pracovní](how-to-create-and-run-a-long-running-workflow.md)postup.

## <a name="example"></a>Příklad
 Následující příklad je úplný výpis kódu pro `Main` metodu.

> [!NOTE]
> Nahraďte `Workflow1` je v těchto příkladech `SequentialNumberGuessWorkflow`pomocí `FlowchartNumberGuessWorkflow`, `StateMachineNumberGuessWorkflow`nebo v závislosti na tom, který pracovní postup jste dokončili v předchozím [postupu: Vytvořte krok pracovního](how-to-create-a-workflow.md) postupu. Pokud se nenahradíte `Workflow1` , zobrazí se při pokusu o vytvoření nebo spuštění pracovního postupu chyby sestavení.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Programování Windows Workflow Foundation](programming.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvořit pracovní postup](how-to-create-a-workflow.md)
- [Postupy: Vytvoření a spuštění dlouhého běžícího pracovního postupu](how-to-create-and-run-a-long-running-workflow.md)
- [Čekání na zadání v pracovním postupu](waiting-for-input-in-a-workflow.md)
- [Hostování pracovních postupů](hosting-workflows.md)
