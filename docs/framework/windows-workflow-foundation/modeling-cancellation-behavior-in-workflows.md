---
title: "Chování zrušení modelování v pracovních postupech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94a3cb69e2e897e992a05a19325630ca9bb1ae3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Chování zrušení modelování v pracovních postupech
Aktivity může být zrušen uvnitř pracovního postupu, například při <xref:System.Activities.Statements.Parallel> aktivity zrušení neúplné větví při jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> vyhodnotí jako `true`, nebo z mimo pracovní postup, pokud hostitel volá <xref:System.Activities.WorkflowApplication.Cancel%2A>. Zajistit zpracování zrušení, můžete použít autoři pracovního postupu <xref:System.Activities.Statements.CancellationScope> aktivitu <xref:System.Activities.Statements.CompensableActivity> aktivity, nebo vytvořit vlastní aktivity, které poskytují logiku zrušení. Toto téma poskytuje přehled o zrušení v pracovních postupech.  
  
## <a name="cancellation-compensation-and-transactions"></a>Zrušení, kompenzace a transakce  
 Transakce poskytují aplikace možnost přerušit všechny změny provést v rámci transakce, pokud všechny chyby, ke kterým došlo během libovolná součást procesu transakce (vrátit zpět změny). Ne všechny práci, kterou může třeba zrušena nebo odvolat je však vhodné pro transakce, jako je například dlouho běžící nebo práce, který nezahrnuje transakční prostředky. Kompenzace poskytuje model pro rušení dříve dokončená netransakční práce, pokud dojde k následující chybě v pracovním postupu. Zrušení poskytuje model pro pracovní postup a aktivity autorům zpracování netransakční fungovat, která nebyla dokončena. Pokud aktivita nebyl dokončen jeho spuštění a je zrušená, bude vyvolána svou logikou zrušení, pokud je k dispozici.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]transakce a kompenzace, najdete v části [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) a [kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="using-cancellationscope"></a>Pomocí CancellationScope  
 <xref:System.Activities.Statements.CancellationScope> Aktivita má dvě části, které mohou obsahovat podřízené aktivity: <xref:System.Activities.Statements.CancellationScope.Body%2A> a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope.Body%2A> Je, kde jsou umístěny aktivity, které tvoří logiku aktivity a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> je, kde jsou umístěny aktivity, které poskytují logiku zrušení aktivity. Aktivita zrušit lze pouze v případě, že nebyla dokončena. U <xref:System.Activities.Statements.CancellationScope> dokončení aktivity, odkazuje na dokončení aktivity v <xref:System.Activities.Statements.CancellationScope.Body%2A>. Pokud je naplánováno na žádost o zrušení a aktivity v <xref:System.Activities.Statements.CancellationScope.Body%2A> dosud nebyly dokončeny, pak se <xref:System.Activities.Statements.CancellationScope> budou označeny jako <xref:System.Activities.ActivityInstanceState.Canceled> a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktivity bude proveden.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Zrušení pracovního postupu z hostitele  
 Hostitel, můžete zrušit pracovní postup volání <xref:System.Activities.WorkflowApplication.Cancel%2A> metodu <xref:System.Activities.WorkflowApplication> instance, který je hostitelem pracovního postupu. V následujícím příkladu se vytvoří pracovní postup, který má <xref:System.Activities.Statements.CancellationScope>. Pracovní postup je voláno, a pak hostitele zavolá <xref:System.Activities.WorkflowApplication.Cancel%2A>. Hlavní spuštění pracovního postupu je zastavena, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> je vyvolána, a pak dokončení pracovního postupu se stavem <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly.  
  
 **Spouštění pracovního postupu.**  
**CancellationHandler vyvolat.**   
**Pracovní postup b30ebb30-df46-4d90-a211-e31c38d8db3c zrušena.**    
> [!NOTE]
>  Když <xref:System.Activities.Statements.CancellationScope> aktivity se zruší a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> vyvolána, má na starosti Autor pracovního postupu k určení průběh, aby bylo možné poskytnout příslušné zrušení logiku byla zrušena zrušené aktivity provedené před ním. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Neposkytuje žádné informace o průběhu zrušené aktivity.  
  
 Pracovní postup lze také zrušit z hostitele k neošetřené výjimce bubliny až po kořenu pracovního postupu a <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužná rutina vrátí <xref:System.Activities.UnhandledExceptionAction.Cancel>. V tomto příkladu spustí pracovní postup a potom vyvolá <xref:System.ApplicationException>. Tato výjimka se neošetřená v tomto pracovním postupu a proto <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je volána obslužná rutina. Obslužná rutina dá pokyn modulu runtime pracovního postupu, zrušit a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z aktuálně spuštěných <xref:System.Activities.Statements.CancellationScope> aktivity vyvolání.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly.  
  
 **Spouštění pracovního postupu.**  
**OnUnhandledException v 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 pracovního postupu**   
**ApplicationException – byla vyvolána.**   
**CancellationHandler vyvolat.**   
**Pracovní postup 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 zrušena.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Probíhá zrušení aktivity z uvnitř pracovního postupu  
 Aktivitu můžete také zrušeno jeho nadřazený objekt. Například pokud <xref:System.Activities.Statements.Parallel> aktivita má více větví provádění a jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> vyhodnocuje `true` a jeho nedokončené větve, budou zrušeny. V tomto příkladu <xref:System.Activities.Statements.Parallel> je vytvořena aktivita, která má dvě pobočky. Jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> je nastaven na `true` proto <xref:System.Activities.Statements.Parallel> dokončí při dokončení některého z jeho větve. V tomto příkladu větve 2 dokončí, a proto zrušena větve 1.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly.  
  
 **Větev, od 1.**  
**Větev 2 dokončení.**   
**Větev 1 zrušena.**   
**Pracovní postup e0685e24-18ef-4a47-acf3-5c638732f3be byla dokončena.**  Aktivity jsou také zruší, pokud se výjimka bubliny až po kořenu aktivity, ale je zpracováván na vyšší úrovni v pracovním postupu. V tomto příkladu Hlavní logika pracovního postupu se skládá z <xref:System.Activities.Statements.Sequence> aktivity. <xref:System.Activities.Statements.Sequence> Je zadán jako <xref:System.Activities.Statements.CancellationScope.Body%2A> z <xref:System.Activities.Statements.CancellationScope> aktivity, který je obsažený v <xref:System.Activities.Statements.TryCatch> aktivity. Z textu je vyvolána výjimka <xref:System.Activities.Statements.Sequence>, zpracovává nadřízený objekt <xref:System.Activities.Statements.TryCatch> aktivitu a <xref:System.Activities.Statements.Sequence> je zrušená.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly.  
  
 **Pořadí spouštění.**  
**Pořadí zrušena.**   
**Byla zjištěna výjimka.**   
**Pracovní postup e3c18939-121e-4c43-af1c-ba1ce977ce55 byla dokončena.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Vyvolání výjimek z CancellationHandler  
 Jakékoli výjimky vyvolány z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> jsou závažné do pracovního postupu. Pokud je možné, výjimek uvozovací znaky z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, používat <xref:System.Activities.Statements.TryCatch> v <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> zachytit a zpracování těchto výjimek.  
  
### <a name="cancellation-using-compensableactivity"></a>Zrušení pomocí CompensableActivity  
 Podobně jako <xref:System.Activities.Statements.CancellationScope> aktivity, <xref:System.Activities.Statements.CompensableActivity> má <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Pokud <xref:System.Activities.Statements.CompensableActivity> zrušení žádné aktivity v jeho <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jsou vyvolány. To může být užitečné pro rušení částečně dokončená compensable práce. Informace o tom, jak používat <xref:System.Activities.Statements.CompensableActivity> kompenzace a zrušení najdete v tématu [kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Zrušení pomocí vlastních aktivit  
 Autoři vlastní aktivitu můžete implementovat logiku zrušení do svých vlastních aktivit v několika různými způsoby. Vlastní aktivity, které jsou odvozeny od <xref:System.Activities.Activity> můžete implementovat logiku zrušení umístěním <xref:System.Activities.Statements.CancellationScope> nebo další vlastní aktivita, která obsahuje logiku zrušení v těle aktivity. <xref:System.Activities.AsyncCodeActivity>a <xref:System.Activities.NativeActivity> odvozené aktivit můžete přepsat jejich odpovídajících <xref:System.Activities.NativeActivity.Cancel%2A> metoda a poskytují logiku zrušení existuje. <xref:System.Activities.CodeActivity>odvozené aktivity neposkytují žádné zřídit pro zrušení, protože všechny práci se provádí v jednom shluku provádění při volání modulu runtime <xref:System.Activities.CodeActivity.Execute%2A> metoda. Pokud ještě nebyla byla volána metoda execute a <xref:System.Activities.CodeActivity> na základě aktivity se zruší, zavře aktivitu se stavem <xref:System.Activities.ActivityInstanceState.Canceled> a <xref:System.Activities.CodeActivity.Execute%2A> metoda není volána.  
  
### <a name="cancellation-using-nativeactivity"></a>Zrušení pomocí NativeActivity  
 <xref:System.Activities.NativeActivity>odvozené aktivit můžete přepsat <xref:System.Activities.NativeActivity.Cancel%2A> metody můžete zajistit vlastní zrušení logiku. Pokud není tato metoda potlačena, je použita výchozí logiku zrušení pracovního postupu. Zrušení výchozí je proces, který dochází <xref:System.Activities.NativeActivity> , nemůže přepsat <xref:System.Activities.NativeActivity.Cancel%2A> metoda nebo jehož <xref:System.Activities.NativeActivity.Cancel%2A> metoda volá základní <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> metoda. Při zrušení aktivitu modul runtime flags aktivity pro zrušení a automaticky zpracovává určité čištění. Pokud aktivita má jenom zbývající záložky, záložky se odeberou a aktivity budou označeny jako <xref:System.Activities.ActivityInstanceState.Canceled>. Žádné nevyřízené podřízené aktivity zrušené aktivity budou naopak zrušeny. Pokusy o naplánovat další podřízené aktivity bude mít za následek pokus bude ignorována a aktivity budou označeny jako <xref:System.Activities.ActivityInstanceState.Canceled>. Pokud dokončení všech zbývajících podřízené aktivity v <xref:System.Activities.ActivityInstanceState.Canceled> nebo <xref:System.Activities.ActivityInstanceState.Faulted> stavu, pak aktivity budou označeny jako <xref:System.Activities.ActivityInstanceState.Canceled>. Všimněte si, že žádost o zrušení můžete ignorovat. Pokud aktivita nemá žádné nevyřízené záložky nebo provádění podřízené aktivity a naplánovat není žádné další pracovní položky po opatření příznakem pro zrušení, bude úspěšně dokončena. Tento výchozí zrušení přípony pro mnoho scénářů, ale je potřeba další zrušení logiku, pak předdefinované zrušení aktivity nebo vlastní aktivity lze nastavit.  
  
 V následujícím příkladu <xref:System.Activities.NativeActivity.Cancel%2A> přepsat z <xref:System.Activities.NativeActivity> na základě vlastní `ParallelForEach` aktivity je definována. Při zrušení aktivity toto přepsání zpracovává zrušení logiku pro aktivitu. Tato ukázka je součástí [ParallelForEach Non-Obecné](../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md) ukázka.  
  
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
  
 <xref:System.Activities.NativeActivity>odvozené aktivity můžete určit, pokud zrušení požaduje zkontrolováním <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> vlastnost a sami označit jako zrušená voláním <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> metoda. Volání metody <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> okamžitě nedokončí aktivity. Modul runtime jako obvykle dokončí aktivity, když nemá žádné další zbývající práce, ale pokud <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> se označuje jako konečné stavu bude <xref:System.Activities.ActivityInstanceState.Canceled> místo <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Zrušení pomocí AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>na základě aktivity můžete taky zadat vlastní zrušení logiku přepsáním <xref:System.Activities.AsyncCodeActivity.Cancel%2A> metoda. Pokud není tato metoda potlačena, se provádí žádné zpracování zrušení, pokud došlo ke zrušení aktivity. V následujícím příkladu <xref:System.Activities.AsyncCodeActivity.Cancel%2A> přepsat z <xref:System.Activities.AsyncCodeActivity> na základě vlastní `ExecutePowerShell` aktivity je definována. Po zrušení aktivity provede požadované zrušení chování. Tato ukázka je součástí [pomocí aktivity InvokePowerShell](../../../docs/framework/windows-workflow-foundation/samples/using-the-invokepowershell-activity.md) ukázka.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>odvozené aktivity můžete určit, pokud zrušení požaduje zkontrolováním <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> vlastnost a sami označit jako zrušená voláním <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> metoda.
