---
title: Chování zrušení modelování v pracovních postupech
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 8738afa838f1d0ca36b7fd6def00f0794bcf47ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143041"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Chování zrušení modelování v pracovních postupech
Aktivity lze zrušit v rámci pracovního <xref:System.Activities.Statements.Parallel> postupu, například aktivitou, která `true`zruší neúplné větve, když <xref:System.Activities.WorkflowApplication.Cancel%2A>je vyhodnocována <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> do aplikace , nebo mimo pracovní postup, pokud hostitel volá . Chcete-li poskytnout zpracování zrušení, <xref:System.Activities.Statements.CancellationScope> autoři <xref:System.Activities.Statements.CompensableActivity> pracovního postupu můžete použít aktivitu, aktivitu nebo vytvořit vlastní aktivity, které poskytují logiku zrušení. Toto téma obsahuje přehled zrušení v pracovních postupech.  
  
## <a name="cancellation-compensation-and-transactions"></a>Zrušení, kompenzace a transakce  
 Transakce poskytují aplikaci možnost přerušit (vrátit zpět) všechny změny provedené v rámci transakce, pokud dojde k chybám během jakékoli části procesu transakce. Však ne všechny práce, které mohou být nutné zrušit nebo vrátit zpět je vhodné pro transakce, jako je například dlouhotrvající práce nebo práce, která nezahrnuje transakční prostředky. Kompenzace poskytuje model pro vrácení dříve dokončené netransakční práce, pokud dojde k následné chybě v pracovním postupu. Zrušení poskytuje model pro autory pracovního postupu a aktivity pro zpracování netransakční práce, která nebyla dokončena. Pokud aktivita nedokončila své spuštění a je zrušena, její logika zrušení bude vyvolána, pokud je k dispozici.  
  
> [!NOTE]
> Další informace o transakcích a kompenzacích naleznete v [tématu Transakce](workflow-transactions.md) a [kompenzace](compensation.md).  
  
## <a name="using-cancellationscope"></a>Použití CancellationScope  
 Aktivita <xref:System.Activities.Statements.CancellationScope> má dvě části, které <xref:System.Activities.Statements.CancellationScope.Body%2A> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>mohou obsahovat podřízené aktivity: a . Je, <xref:System.Activities.Statements.CancellationScope.Body%2A> kde jsou umístěny aktivity, které tvoří <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> logiku aktivity a je, kde jsou umístěny aktivity, které poskytují logiku zrušení pro aktivitu. Aktivitu lze zrušit pouze v případě, že nebyla dokončena. V případě <xref:System.Activities.Statements.CancellationScope> činnosti se dokončením rozumí dokončení činností v <xref:System.Activities.Statements.CancellationScope.Body%2A>oblasti . Pokud je naplánována žádost o zrušení <xref:System.Activities.Statements.CancellationScope.Body%2A> a aktivity <xref:System.Activities.Statements.CancellationScope> v aplikaci <xref:System.Activities.ActivityInstanceState.Canceled> nebyly <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> dokončeny, budou označeny jako a aktivity budou provedeny.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Zrušení pracovního postupu z hostitele  
 Hostitel může zrušit pracovní postup <xref:System.Activities.WorkflowApplication.Cancel%2A> voláním <xref:System.Activities.WorkflowApplication> metody instance, která je hostitelem pracovního postupu. V následujícím příkladu je vytvořen <xref:System.Activities.Statements.CancellationScope>pracovní postup, který má . Pracovní postup je vyvolán a hostitel provede <xref:System.Activities.WorkflowApplication.Cancel%2A>volání . Hlavní spuštění pracovního postupu je <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> zastaveno, <xref:System.Activities.Statements.CancellationScope> je vyvoláno a pracovní postup <xref:System.Activities.ActivityInstanceState.Canceled>se dokončí se stavem .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Při vyvolání tohoto pracovního postupu se konzoli zobrazí následující výstup.  
  
 **Spuštění pracovního postupu.**  
**CancellationHandler vyvolána.** 
 **Pracovní postup b30ebb30-df46-4d90-a211-e31c38d8db3c Zrušeno.**
> [!NOTE]
> Pokud <xref:System.Activities.Statements.CancellationScope> je aktivita zrušena <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> a vyvolána, je odpovědností autora pracovního postupu určit průběh, který byla zrušena před zrušením, aby byla poskytnuta příslušná logika zrušení. Neposkytuje <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> žádné informace o průběhu zrušené aktivity.  
  
 Pracovní postup lze také zrušit z hostitele, pokud neošetřená výjimka bubliny <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> až <xref:System.Activities.UnhandledExceptionAction.Cancel>za kořen pracovního postupu a obslužná rutina vrátí . V tomto příkladu se spustí <xref:System.ApplicationException>pracovní postup a potom vyvolá . Tato výjimka není zpracována pracovním <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> postupem a proto je obslužná rutina vyvolána. Obslužná rutina instruuje <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> modul runtime ke <xref:System.Activities.Statements.CancellationScope> zrušení pracovního postupu a je vyvolána aktuálně spuštěná aktivita.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Při vyvolání tohoto pracovního postupu se konzoli zobrazí následující výstup.  
  
 **Spuštění pracovního postupu.**  
**OnUnhandledException v pracovním postupu 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**
**Byla vyvolána výjimka z aplikace.** 
 **CancellationHandler vyvolána.** 
 **Pracovní postup 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 Zrušeno.**
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Zrušení aktivity z pracovního postupu  
 Aktivitu může zrušit také nadřazená aktivita. Například pokud <xref:System.Activities.Statements.Parallel> aktivita má více vykonávajících <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> větví `true` a její vyhodnocuje se pak její neúplné větve budou zrušeny. V tomto <xref:System.Activities.Statements.Parallel> příkladu je vytvořena aktivita, která má dvě větve. Jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> je `true` nastavena <xref:System.Activities.Statements.Parallel> tak, aby dokončí, jakmile některý z jeho poboček je dokončena. V tomto příkladu bude dokončena větev 2, a proto je pobočka 1 zrušena.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Při vyvolání tohoto pracovního postupu se konzoli zobrazí následující výstup.  
  
 **Větev 1 začíná.**  
**Pobočka 2 dokončena.** 
 **Pobočka 1 zrušena.** 
 **Pracovní postup e0685e24-18ef-4a47-acf3-5c638732f3be dokončen.**  Aktivity jsou také zrušeny, pokud výjimka bubliny za kořen aktivity, ale je zpracována na vyšší úrovni v pracovním postupu. V tomto příkladu se hlavní logika <xref:System.Activities.Statements.Sequence> pracovního postupu skládá z aktivity. Je <xref:System.Activities.Statements.Sequence> určen jako <xref:System.Activities.Statements.CancellationScope.Body%2A> aktivita, <xref:System.Activities.Statements.CancellationScope> která je <xref:System.Activities.Statements.TryCatch> obsažena aktivity. Výjimka je vyvolána z <xref:System.Activities.Statements.Sequence>těla , je <xref:System.Activities.Statements.TryCatch> zpracována <xref:System.Activities.Statements.Sequence> nadřazenou aktivitou a je zrušena.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Při vyvolání tohoto pracovního postupu se konzoli zobrazí následující výstup.  
  
 **Sekvence začíná.**  
**Sekvence byla zrušena.** 
 **Výjimka byla zachycena.** 
 **Pracovní postup e3c18939-121e-4c43-af1c-ba1ce977ce55 Dokončeno.**
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Vyvolání výjimek z operátoru CancellationHandler  
 Všechny výjimky vyvoláné <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> a jsou závažné pracovního postupu. Pokud existuje možnost výjimky uvození <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>z <xref:System.Activities.Statements.TryCatch> , <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> použijte v catch a zpracování těchto výjimek.  
  
### <a name="cancellation-using-compensableactivity"></a>Zrušení pomocí CompensableActivity  
 Stejně <xref:System.Activities.Statements.CancellationScope> jako <xref:System.Activities.Statements.CompensableActivity> činnost, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>má . Pokud <xref:System.Activities.Statements.CompensableActivity> je zrušena, všechny aktivity v jeho <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jsou vyvolány. To může být užitečné pro zrušení částečně dokončené kompenzační práce. Informace o tom, <xref:System.Activities.Statements.CompensableActivity> jak použít pro kompenzaci a zrušení, naleznete [v tématu Kompenzace](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Zrušení pomocí vlastních aktivit  
 Vlastní autoři aktivit mohou implementovat logiku zrušení do svých vlastních aktivit několika různými způsoby. Vlastní aktivity, <xref:System.Activities.Activity> které jsou odvozeny <xref:System.Activities.Statements.CancellationScope> z můžete implementovat logiku zrušení umístěním nebo jiné vlastní aktivity, která obsahuje logiku zrušení v těle aktivity. <xref:System.Activities.AsyncCodeActivity>a <xref:System.Activities.NativeActivity> odvozené aktivity můžete <xref:System.Activities.NativeActivity.Cancel%2A> přepsat jejich příslušné metody a poskytnout logiku zrušení tam. <xref:System.Activities.CodeActivity>odvozené aktivity neposkytují žádné ustanovení o zrušení, protože všechny jejich práce se <xref:System.Activities.CodeActivity.Execute%2A> provádí v jednom spuštění při runtime volá metodu. Pokud metoda spuštění ještě nebyla <xref:System.Activities.CodeActivity> volána a je zrušena aktivita založená, aktivita se zavře se stavem <xref:System.Activities.ActivityInstanceState.Canceled> a <xref:System.Activities.CodeActivity.Execute%2A> metoda není volána.  
  
### <a name="cancellation-using-nativeactivity"></a>Zrušení pomocí NativeActivity  
 <xref:System.Activities.NativeActivity>odvozené aktivity můžete <xref:System.Activities.NativeActivity.Cancel%2A> přepsat metodu poskytnout vlastní zrušení logiky. Pokud tato metoda není přepsána, použije se výchozí logika zrušení pracovního postupu. Výchozí zrušení je proces, který <xref:System.Activities.NativeActivity> probíhá pro <xref:System.Activities.NativeActivity.Cancel%2A> který nepřepíše metodu nebo jehož <xref:System.Activities.NativeActivity.Cancel%2A> metoda volá základní <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> metodu. Když je aktivita zrušena, runtime označí aktivitu pro zrušení a automaticky zpracovává určité vyčištění. Pokud má aktivita pouze nevyřízené záložky, budou záložky odstraněny <xref:System.Activities.ActivityInstanceState.Canceled>a aktivita bude označena jako . Všechny nevyřízené podřízené aktivity zrušené aktivity budou zrušeny. Jakýkoli pokus o naplánování dalších podřízených aktivit bude mít <xref:System.Activities.ActivityInstanceState.Canceled>za následek ignorování pokusu a aktivita bude označena jako . Pokud se v or <xref:System.Activities.ActivityInstanceState.Canceled> <xref:System.Activities.ActivityInstanceState.Faulted> stavu dokončí jakákoli nevyřízená podřízená aktivita, bude aktivita označena jako <xref:System.Activities.ActivityInstanceState.Canceled>. Všimněte si, že požadavek na zrušení lze ignorovat. Pokud aktivita nemá žádné nevyřízené záložky nebo provádění podřízených aktivit a neplánuje žádné další pracovní položky po označení pro zrušení, bude úspěšně dokončena. Toto výchozí zrušení stačí pro mnoho scénářů, ale pokud je potřeba další logiku zrušení, pak integrované aktivity zrušení nebo vlastní aktivity lze použít.  
  
 V následujícím příkladu <xref:System.Activities.NativeActivity.Cancel%2A> je definováno přepsání <xref:System.Activities.NativeActivity> vlastní `ParallelForEach` aktivity na základě. Když je aktivita zrušena, toto přepsání zpracovává logiku zrušení aktivity. Tento příklad je součástí [neobecné ParallelForEach](./samples/non-generic-parallelforeach.md) vzorku.  
  
```csharp  
protected override void Cancel(NativeActivityContext context)  
{  
    // If we do not have a completion condition then we can just  
    // use default logic.  
    if (this.CompletionCondition == null)  
    {  
        base.Cancel(context);  
    }  
    else  
    {  
        context.CancelChildren();  
    }  
}  
```  
  
 <xref:System.Activities.NativeActivity>odvozené aktivity můžete určit, pokud zrušení <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> byla požadována kontrolou vlastnosti <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> a označit se jako zrušené voláním metody. Volání <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> okamžitě nedokončí aktivitu. Jako obvykle, runtime dokončí aktivitu, když nemá žádné <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> další vynikající práce, <xref:System.Activities.ActivityInstanceState.Canceled> ale <xref:System.Activities.ActivityInstanceState.Closed>pokud se nazývá konečný stav bude místo .  
  
### <a name="cancellation-using-asynccodeactivity"></a>Zrušení pomocí AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>založené aktivity mohou také poskytnout vlastní <xref:System.Activities.AsyncCodeActivity.Cancel%2A> logiku zrušení přepsáním metody. Pokud tato metoda není přepsána, pak žádné zpracování zrušení se provádí, pokud je aktivita zrušena. V následujícím příkladu <xref:System.Activities.AsyncCodeActivity.Cancel%2A> je definováno přepsání <xref:System.Activities.AsyncCodeActivity> vlastní `ExecutePowerShell` aktivity na základě. Když je aktivita zrušena, provede požadované chování zrušení.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>odvozené aktivity můžete určit, pokud zrušení <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> byla požadována kontrolou vlastnosti <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> a označit se jako zrušené voláním metody.
