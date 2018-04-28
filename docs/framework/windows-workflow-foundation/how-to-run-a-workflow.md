---
title: 'Postupy: spuštění pracovního postupu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88c8adc74b707891a93e34aa135db82715da968e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-run-a-workflow"></a>Postupy: spuštění pracovního postupu
Toto téma je pokračování kurzu Windows Workflow Foundation Začínáme a popisuje, jak vytvořit hostitele pracovního postupu a spuštění pracovního postupu definované v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tématu.  
  
> [!NOTE]
>  Každého tématu v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) a [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
> [!NOTE]
>  Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>Vytvoření projektu hostitele pracovního postupu  
  
1.  Otevřete řešení z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu pomocí [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Klikněte pravým tlačítkem myši **WF45GettingStartedTutorial** řešení v **Průzkumníku řešení** a vyberte **přidat**, **nový projekt**.  
  
    > [!TIP]
    >  Pokud **Průzkumníku řešení** se nezobrazí okno, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
3.  V **nainstalovaná** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**).  
  
    > [!NOTE]
    >  V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalovaná** uzlu.  
  
     Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework. Vyberte **pracovního postupu konzolové aplikace** z **pracovního postupu** seznamu. Typ `NumberGuessWorkflowHost` do **název** pole a klikněte na tlačítko **OK**. Tím se vytvoří aplikace starter pracovního postupu s základní pracovní postup, který je hostitelem podporu. Tento základní hostování kód je upravit a použít ke spuštění aplikace pracovního postupu.  
  
4.  Klikněte pravým tlačítkem na nově přidaný **NumberGuessWorkflowHost** projektu v **Průzkumníku řešení** a vyberte **přidat odkaz na**. Vyberte **řešení** z **přidat odkaz na** seznamu, zaškrtněte políčko vedle položky **NumberGuessWorkflowActivities**a potom klikněte na **OK** .  
  
5.  Klikněte pravým tlačítkem na **Workflow1.xaml** v **Průzkumníku řešení** a zvolte **odstranit**. Klikněte na tlačítko **OK** k potvrzení.  
  
### <a name="to-modify-the-workflow-hosting-code"></a>Upravit pracovní postup hostování kódu  
  
1.  Klikněte dvakrát na **Program.cs** nebo **Module1.vb** v **Průzkumníku řešení** zobrazíte kód.  
  
    > [!TIP]
    >  Pokud **Průzkumníku řešení** se nezobrazí okno, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
     Protože tento projekt bylo vytvořeno pomocí **pracovního postupu konzolové aplikace** šablony, **Program.cs** nebo **Module1.vb** obsahuje následující hostování základní pracovní postup kód.  
  
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
  
     Tato vygenerována hostování kód používá <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> poskytuje jednoduchý způsob pro vyvolání pracovního postupu, jako by byly volání metody a lze použít pouze pro pracovní postupy, které nepoužívají trvalost. <xref:System.Activities.WorkflowApplication> poskytuje bohatší model pro spouštění pracovních postupů, které obsahuje oznámení o události životního cyklu, řízení provádění, obnovení záložku a trvalost. Tento příklad používá záložky a <xref:System.Activities.WorkflowApplication> se používá k hostování pracovní postup. Přidejte následující `using` nebo **importy** příkaz v horní části **Program.cs** nebo **Module1.vb** pod existující **pomocí** nebo **importy** příkazy.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     Nahraďte řádky kódu, které používají <xref:System.Activities.WorkflowInvoker> s následující basic <xref:System.Activities.WorkflowApplication> hostování kódu. Tato ukázka hostování kód ukazuje základní kroky pro hostování a vyvolání pracovní postup, ale ještě neobsahuje funkce k úspěšnému spuštění pracovního postupu z tohoto tématu. V následujících krocích je-li změnit tento základní kód a další funkce se přidají, dokud se nedokončí aplikace.  
  
    > [!NOTE]
    >  Nahraďte `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup dokončit v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) krok. Pokud jste nenahrazují `Workflow1` pak při akci a sestavení nebo spusťte pracovní postup bude docházet k chybám sestavení.  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     Tento kód vytvoří <xref:System.Activities.WorkflowApplication>, jako odběratel u tři události životního cyklu pracovního postupu, spustí pracovní postup pomocí volání <xref:System.Activities.WorkflowApplication.Run%2A>a potom čeká na dokončení pracovního postupu. Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> je sada a hostitele dokončení aplikace.  
  
### <a name="to-set-input-arguments-of-a-workflow"></a>Chcete-li nastavit vstupní argumenty pracovního postupu  
  
1.  Přidejte následující příkaz v horní části **Program.cs** nebo **Module1.vb** pod existující `using` nebo `Imports` příkazy.  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  Nahraďte řádek kódu, který vytvoří nový <xref:System.Activities.WorkflowApplication> s následujícím kódem, který vytvoří a předává slovník parametrů do pracovního postupu při jeho vytvoření.  
  
    > [!NOTE]
    >  Nahraďte `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup dokončit v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) krok. Pokud jste nenahrazují `Workflow1` pak při akci a sestavení nebo spusťte pracovní postup bude docházet k chybám sestavení.  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     Tento slovník obsahuje jeden element s klíčem `MaxNumber`. Klíče ve slovníku vstupní odpovídají vstupní argumenty na kořenové aktivity pracovního postupu. `MaxNumber` v tomto pracovním postupu se používá k určení horní mez pro náhodně generovaným číslem.  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Načíst výstup argumenty pracovního postupu  
  
1.  Změnit <xref:System.Activities.WorkflowApplication.Completed%2A> obslužná rutina načtení a zobrazuje počet oplátku používá pracovní postup.  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a>Chcete-li obnovit záložky  
  
1.  Přidejte následující kód v horní části `Main` metoda bezprostředně za existující <xref:System.Threading.AutoResetEvent> deklarace.  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  Přidejte následující <xref:System.Activities.WorkflowApplication.Idle%2A> obslužných rutin pod existující tři pracovní postup životního cyklu obslužných rutin v `Main`.  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     Pokaždé, když pracovní postup bude nečinnosti čekání na další odhad, se nazývá této obslužné rutiny a `idleAction` <xref:System.Threading.AutoResetEvent> nastavena. Kód v následujícím kroku používá `idleEvent` a `syncEvent` k určení, zda pracovní postup se čeká na další odhad nebo dokončení.  
  
    > [!NOTE]
    >  V tomto příkladu používá hostitelskou aplikaci automatickým vynulováním události v <xref:System.Activities.WorkflowApplication.Completed%2A> a <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny pro synchronizaci hostitelskou aplikaci s průběh pracovního postupu. Není nutné blokovat a počkejte, pracovní postup na nečinnost před obnovením záložku, ale v tomto příkladu události synchronizace jsou vyžaduje, aby hostitel věděli, jestli dokončení pracovního postupu nebo jestli je čekání na další vstup uživatele pomocí <xref:System.Activities.Bookmark>. Další informace najdete v tématu [záložky](../../../docs/framework/windows-workflow-foundation/bookmarks.md).  
  
3.  Odeberte volání `WaitOne`a nahraďte ji metodou kód shromažďovat vstup od uživatele a obnovit <xref:System.Activities.Bookmark>.  
  
     Odeberte následující řádek kódu.  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     Nahraďte ji následujícím příkladu.  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a> Sestavení a spuštění aplikace  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníku řešení** a vyberte **nastavit jako spouštěný projekt**.  
  
2.  Stisknutím klávesy CTRL + F5 sestavení a spuštění aplikace. Zkuste tak snadno uhodnout číslo na nejmenším oplátku míře.  
  
     Pokud chcete vyzkoušet aplikace s jedním z dalších styly pracovního postupu, nahraďte `Workflow1` v kódu, který vytvoří <xref:System.Activities.WorkflowApplication> s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`, v závislosti na styl pracovního postupu, který požadavky.  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     Pokyny o tom, jak přidat trvalost do aplikace pracovního postupu, naleznete v dalším tématu [postupy: vytvoření a spuštění dlouhém pracovním postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je úplný výpis pro kódu `Main` metoda.  
  
> [!NOTE]
>  Nahraďte `Workflow1` v těchto příkladech s `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, nebo `StateMachineNumberGuessWorkflow`podle toho, které pracovní postup dokončit v předchozím [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) krok. Pokud jste nenahrazují `Workflow1` pak při akci a sestavení nebo spusťte pracovní postup bude docházet k chybám sestavení.  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [Programování Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Postupy: Vytvoření a spuštění dlouhodobého pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [Čekání na zadání v pracovním postupu](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [Hostování pracovních postupů](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)
