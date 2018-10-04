---
title: Chování zrušení modelování v pracovních postupech
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 72bed8da8ed67121340a55afb9bbe768fbd631e6
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580898"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Chování zrušení modelování v pracovních postupech
Aktivity může být zrušen v pracovním postupu, například podle <xref:System.Activities.Statements.Parallel> aktivity zrušení neúplné větví při jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> vyhodnotí jako `true`, nebo z mimo pracovní postup, pokud hostitel volá <xref:System.Activities.WorkflowApplication.Cancel%2A>. K poskytování zrušení zpracování, můžete použít autoři pracovního postupu <xref:System.Activities.Statements.CancellationScope> aktivity, <xref:System.Activities.Statements.CompensableActivity> aktivity, nebo vytvořte vlastní aktivity, které poskytují logiku zrušení. Toto téma obsahuje základní informace o zrušení v pracovních postupech.  
  
## <a name="cancellation-compensation-and-transactions"></a>Zrušení, odškodnění a transakce  
 Transakce vaší aplikaci poskytuje schopnost zrušit všechny změny, provede v rámci transakce, pokud dojde k nějaké chybě během jakékoli části procesu transakce (vrácení zpět). Ne všechny práce, která může být nutné zrušit nebo vrátit zpět je však vhodné pro transakce, jako je například dlouhotrvající nebo práce, který nezahrnuje transakční prostředky. Pokud dojde k následující chybě v pracovním postupu kompenzace poskytuje model pro vrácení předchozí Dokončená práce není transakční. Zrušení poskytuje model pro pracovní postup a autoři aktivity pro zpracování není transakční práce, které se nedokončila. Pokud aktivita nebyla dokončena její spuštění a bude zrušen, bude vyvolána vlastní logiku zrušení, pokud je k dispozici.  
  
> [!NOTE]
>  Další informace o transakce a kompenzace najdete v tématu [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) a [kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="using-cancellationscope"></a>Použití CancellationScope  
 <xref:System.Activities.Statements.CancellationScope> Aktivita má dvě části, které mohou obsahovat podřízené aktivity: <xref:System.Activities.Statements.CancellationScope.Body%2A> a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope.Body%2A> Je, kde jsou umístěny aktivity, které tvoří logiku aktivity a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> je, kde jsou umístěny aktivity, které poskytují logiku zrušení aktivity. Aktivita se dá zrušit jenom v případě, že nebyla dokončena. V případě třídy <xref:System.Activities.Statements.CancellationScope> aktivity, dokončení odkazuje na dokončení aktivity ve <xref:System.Activities.Statements.CancellationScope.Body%2A>. Pokud je naplánováno na žádost o zrušení a aktivity ve službě <xref:System.Activities.Statements.CancellationScope.Body%2A> nebyla dokončena, pak bude <xref:System.Activities.Statements.CancellationScope> se označí jako <xref:System.Activities.ActivityInstanceState.Canceled> a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktivity se spustí.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Zrušení pracovního postupu z hostitele  
 Hostitele můžete zrušit pracovního postupu pomocí volání <xref:System.Activities.WorkflowApplication.Cancel%2A> metodu <xref:System.Activities.WorkflowApplication> instanci, která je hostitelem pracovního postupu. V následujícím příkladu se vytvoří pracovní postup, který má <xref:System.Activities.Statements.CancellationScope>. Pracovní postup je vyvolána, a potom hostitele provede volání <xref:System.Activities.WorkflowApplication.Cancel%2A>. Hlavní provádění pracovního postupu je zastavena, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> je vyvolána, a pak se stavem dokončení pracovního postupu <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **Spuštění pracovního postupu.**  
**CancellationHandler vyvolána.**   
**B30ebb30-df46-4d90-a211-e31c38d8db3c pracovního postupu bylo zrušeno.**    
> [!NOTE]
>  Když <xref:System.Activities.Statements.CancellationScope> aktivity se zruší a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> vyvolala, zodpovídá za autora pracovního postupu a určit pokrok, zrušené aktivity provedené před ní byla zrušena negace logiku odpovídající zrušení. <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Neposkytuje žádné informace o průběhu zrušené aktivity.  
  
 Pracovní postup lze také zrušit z hostitele k neošetřené výjimce bubliny až po kořenového pracovního postupu a <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužná rutina vrátí <xref:System.Activities.UnhandledExceptionAction.Cancel>. V tomto příkladu pracovní postup spustí a následně vyvolává <xref:System.ApplicationException>. Tato výjimka je ošetřena pracovního postupu a proto <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je vyvolána obslužná rutina. Obslužná rutina dá pokyn modulu runtime pracovního postupu, zrušit a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktuálně provedení <xref:System.Activities.Statements.CancellationScope> vyvolání aktivity.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **Spuštění pracovního postupu.**  
**OnUnhandledException v 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 pracovního postupu**   
**Byla vyvolána ApplicationException.**   
**CancellationHandler vyvolána.**   
**6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 pracovního postupu bylo zrušeno.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Ruší se aktivity z uvnitř pracovního postupu  
 Aktivita se dá zrušit také podle svého nadřazeného objektu. Například pokud <xref:System.Activities.Statements.Parallel> aktivity je provádění několika větví a jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> vyhodnotí jako `true` pak zruší jeho neúplné větví. V tomto příkladu <xref:System.Activities.Statements.Parallel> aktivity se vytvoří, která má dvě větve. Jeho <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> je nastavena na `true` proto <xref:System.Activities.Statements.Parallel> se dokončí po dokončení jedné z jeho větví. V tomto příkladu větev 2 dokončí, a proto zrušena větev 1.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **Nepodmíněný skok od 1.**  
**Větev 2 dokončení.**   
**Větev 1 bylo zrušeno.**   
**Dokončení e0685e24-18ef-4a47-acf3-5c638732f3be pracovního postupu.**  Aktivity se zruší také, pokud výjimka bubliny až po kořenové aktivity, ale je zpracována na vyšší úrovni v pracovním postupu. V tomto příkladu tvořen Hlavní logika pracovního postupu <xref:System.Activities.Statements.Sequence> aktivity. <xref:System.Activities.Statements.Sequence> Je zadán jako <xref:System.Activities.Statements.CancellationScope.Body%2A> z <xref:System.Activities.Statements.CancellationScope> aktivitu, která je obsažena ve <xref:System.Activities.Statements.TryCatch> aktivity. Výjimka je vyvolána z textu <xref:System.Activities.Statements.Sequence>, zařizuje služba nadřazené <xref:System.Activities.Statements.TryCatch> aktivitu a <xref:System.Activities.Statements.Sequence> se zruší.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **Pořadí spouštění.**  
**Pořadí bylo zrušeno.**   
**Byla zachycena výjimka.**   
**Dokončení e3c18939-121e-4c43-af1c-ba1ce977ce55 pracovního postupu.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Generování výjimek ve CancellationHandler  
 Výjimky vyvolané z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> z <xref:System.Activities.Statements.CancellationScope> jsou závažná do pracovního postupu. Pokud je možnost uvozovací znaky z výjimek <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, používat <xref:System.Activities.Statements.TryCatch> v <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> k zachycení a zpracování těchto výjimek.  
  
### <a name="cancellation-using-compensableactivity"></a>Aktivita CompensableActivity pomocí zrušení  
 Podobně jako <xref:System.Activities.Statements.CancellationScope> aktivity, <xref:System.Activities.Statements.CompensableActivity> má <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Pokud <xref:System.Activities.Statements.CompensableActivity> dojde ke zrušení, všechny aktivity v jeho <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jsou vyvolány. To může být užitečné pro vrácení zpět částečně dokončené kompenzovatelná práce. Informace o tom, jak používat <xref:System.Activities.Statements.CompensableActivity> kompenzaci a zrušení naleznete v tématu [kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Zrušení použití vlastní aktivity  
 Vlastní aktivita autoři můžete implementovat logiku zrušení do jejich vlastních aktivit v několika různými způsoby. Vlastní aktivity, které jsou odvozeny z <xref:System.Activities.Activity> můžete implementovat logiku zrušení tak, že <xref:System.Activities.Statements.CancellationScope> nebo jiné vlastní aktivitu, která obsahuje logiku zrušení v těle aktivity. <xref:System.Activities.AsyncCodeActivity> a <xref:System.Activities.NativeActivity> odvozený od aktivit můžete přepsat jejich <xref:System.Activities.NativeActivity.Cancel%2A> metoda a poskytnout logiku zrušení existuje. <xref:System.Activities.CodeActivity> odvozený od aktivit neposkytují žádné zřídit pro zrušení, protože veškerou práci provádí jeden zřízeno provádění modul runtime volá <xref:System.Activities.CodeActivity.Execute%2A> metody. Pokud nebyla dosud zavolána metoda execute a <xref:System.Activities.CodeActivity> na základě aktivity se zruší, zavře aktivitu se stavem <xref:System.Activities.ActivityInstanceState.Canceled> a <xref:System.Activities.CodeActivity.Execute%2A> metoda není volána.  
  
### <a name="cancellation-using-nativeactivity"></a>Zrušení pomocí NativeActivity  
 <xref:System.Activities.NativeActivity> odvozený od aktivit můžete přepsat <xref:System.Activities.NativeActivity.Cancel%2A> metodu k dispozici vlastní zrušení logiku. Pokud není tato metoda potlačena, se použije výchozí logiku zrušení pracovního postupu. Výchozí zrušení je proces, ke které dochází pro <xref:System.Activities.NativeActivity> , nepřepisuje <xref:System.Activities.NativeActivity.Cancel%2A> metody nebo jejichž <xref:System.Activities.NativeActivity.Cancel%2A> metoda volá základní <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> metoda. Při zrušení aktivitu, modul runtime příznaky aktivity pro zrušení a automaticky zpracovává určité vyčištění. Pokud aktivita pouze obsahuje nevyřízené záložky, záložky se odeberou a aktivity se označí jako <xref:System.Activities.ActivityInstanceState.Canceled>. Všechny zbývající podřízené aktivity zrušené aktivity se pak zruší. Jakékoli pokusy o naplánovat další podřízené aktivity, způsobí pokus bude ignorována a aktivity se označí jako <xref:System.Activities.ActivityInstanceState.Canceled>. Pokud všechny zbývající podřízená aktivita dokončí za <xref:System.Activities.ActivityInstanceState.Canceled> nebo <xref:System.Activities.ActivityInstanceState.Faulted> stavu, a aktivitu označí jako <xref:System.Activities.ActivityInstanceState.Canceled>. Všimněte si, že žádost o zrušení můžete ignorovat. Pokud aktivita nemá žádné nevyřízené záložky nebo spuštěné podřízené aktivity a všechny další pracovní položky není naplánovat po opatření příznakem pro zrušení, bude dokončena úspěšně. Zrušení této výchozí přípony pro řadu scénářů, ale v případě potřeby další zrušení logiky pak integrované zrušení aktivity nebo vlastní aktivity lze použít.  
  
 V následujícím příkladu <xref:System.Activities.NativeActivity.Cancel%2A> přepsání <xref:System.Activities.NativeActivity> na základě vlastní `ParallelForEach` aktivity je definován. Když dojde ke zrušení aktivity, toto přepsání zpracovává zrušení logiku pro aktivitu. V tomto příkladu je součástí [neobecné ParallelForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md) vzorku.  
  
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
  
 <xref:System.Activities.NativeActivity> odvozený od aktivit můžete určit, pokud bylo vyžádáno zrušení zkontrolováním <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> vlastnost a sami označit jako zrušenou voláním <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> metody. Volání <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> okamžitě neskončí aktivita. Modul runtime jako obvykle dokončí činnost, nemá žádné další zbývající práce, ale pokud <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> nazývá poslední stav <xref:System.Activities.ActivityInstanceState.Canceled> místo <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Zrušení pomocí AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity> na základě aktivity můžete také zadat vlastní zrušení logiky tak, že přepíšete <xref:System.Activities.AsyncCodeActivity.Cancel%2A> metody. Pokud není tato metoda potlačena, se neprovádí žádné zrušení zpracování, pokud se zruší aktivity. V následujícím příkladu <xref:System.Activities.AsyncCodeActivity.Cancel%2A> přepsání <xref:System.Activities.AsyncCodeActivity> na základě vlastní `ExecutePowerShell` aktivity je definována. Při zrušení aktivita provádí zrušení požadované chování.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> odvozený od aktivit můžete určit, pokud bylo vyžádáno zrušení zkontrolováním <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> vlastnost a sami označit jako zrušenou voláním <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> metody.
