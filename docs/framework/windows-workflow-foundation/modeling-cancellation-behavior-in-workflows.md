---
title: Modelování chování zrušení v pracovních postupech
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: ec0cf810693e2eda01a4c489b6eb938538719228
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965940"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Modelování chování zrušení v pracovních postupech
Aktivity lze zrušit v rámci pracovního postupu, <xref:System.Activities.Statements.Parallel> například aktivitou zrušení nedokončených větví <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> při vyhodnocování `true`nebo mimo pracovní postup, pokud hostitel volá <xref:System.Activities.WorkflowApplication.Cancel%2A>. Aby bylo možné zajišťovat zrušení, autoři pracovního postupu <xref:System.Activities.Statements.CancellationScope> mohou aktivitu aktivity <xref:System.Activities.Statements.CompensableActivity> , aktivity nebo vytvářet vlastní aktivity, které poskytují logiku zrušení. V tomto tématu najdete přehled zrušení v pracovních postupech.  
  
## <a name="cancellation-compensation-and-transactions"></a>Zrušení, kompenzace a transakce  
 Transakce poskytují vaší aplikaci možnost přerušení (vrácení zpět) všech změn provedených v rámci transakce, pokud dojde k chybám během jakékoli části procesu transakce. Ne všechny práce, které mohou být nutné zrušit nebo zrušit, jsou však vhodné pro transakce, například dlouhotrvající práci nebo práce, které nezahrnují transakční prostředky. Kompenzace poskytuje model pro vrácení dříve dokončené netransakční práce v případě, že v pracovním postupu dojde k následnému selhání. Zrušení poskytuje model pro pracovní postupy a autory aktivity, které zpracovávají netransakční práci, která nebyla dokončena. Pokud aktivita nedokončila své provedení a je zrušena, bude její logika zrušení vyvolána, pokud je k dispozici.  
  
> [!NOTE]
> Další informace o transakcích a kompenzacích najdete v tématu [transakce](workflow-transactions.md) a [kompenzace](compensation.md).  
  
## <a name="using-cancellationscope"></a>Použití CancellationScope  
 Aktivita má dva oddíly, které mohou obsahovat podřízené aktivity: <xref:System.Activities.Statements.CancellationScope.Body%2A> a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. <xref:System.Activities.Statements.CancellationScope> Je místo, kde jsou umístěny aktivity, které tvoří logiku aktivity, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> a je místo, kde jsou umístěny aktivity, které poskytují logiku pro zrušení aktivity. <xref:System.Activities.Statements.CancellationScope.Body%2A> Aktivitu lze zrušit pouze v případě, že nebyla dokončena. V případě <xref:System.Activities.Statements.CancellationScope> aktivity se dokončování odkazuje na dokončení aktivit <xref:System.Activities.Statements.CancellationScope.Body%2A>v. Pokud je <xref:System.Activities.Statements.CancellationScope.Body%2A> naplánována žádost o zrušení a aktivity v nástroji již nejsou dokončeny, <xref:System.Activities.Statements.CancellationScope> bude označena jako <xref:System.Activities.ActivityInstanceState.Canceled> a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktivity budou provedeny.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Zrušení pracovního postupu z hostitele  
 Hostitel může zrušit pracovní postup voláním <xref:System.Activities.WorkflowApplication.Cancel%2A> metody <xref:System.Activities.WorkflowApplication> instance, která je hostitelem pracovního postupu. V následujícím příkladu je vytvořen pracovní postup, který má <xref:System.Activities.Statements.CancellationScope>. Je vyvolán pracovní postup a hostitel pak provede volání <xref:System.Activities.WorkflowApplication.Cancel%2A>. Hlavní spuštění pracovního postupu se zastaví, <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> <xref:System.Activities.Statements.CancellationScope> vyvolá se a potom se pracovní postup <xref:System.Activities.ActivityInstanceState.Canceled>dokončí se stavem.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **Spouští se pracovní postup.**  
**CancellationHandler vyvoláno.**    
**B30ebb30-df46-4d90-A211-e31c38d8db3c pracovního postupu se zrušil.**    
> [!NOTE]
> Pokud je <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> aktivita zrušena a vyvolána, je jejímu autorovi pracovní postup, který určuje, jak se zrušila zrušená aktivita před zrušením, aby bylo možné poskytnout příslušnou logiku zrušení. <xref:System.Activities.Statements.CancellationScope> <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Neposkytuje žádné informace o průběhu zrušené aktivity.  
  
 Pracovní postup lze také zrušit z hostitele, pokud bubliny s neošetřenou výjimkou provedou za kořenem pracovního postupu a <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> obslužná rutina vrátí. <xref:System.Activities.UnhandledExceptionAction.Cancel> V tomto příkladu se spustí pracovní postup a potom vyvolá <xref:System.ApplicationException>. Tato výjimka není ošetřena pracovním postupem, a proto <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> je vyvolána obslužná rutina. Obslužná rutina instruuje modul runtime, aby zrušil pracovní postup a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> vyvolala se <xref:System.Activities.Statements.CancellationScope> aktuálně spuštěná aktivita.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **Spouští se pracovní postup.**  
**6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 v pracovním postupu**   
**Byla vyvolána výjimka ApplicationException.**    
**CancellationHandler vyvoláno.**    
**6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 pracovního postupu se zrušil.**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Zrušení aktivity v rámci pracovního postupu  
 Aktivitu lze také zrušit její nadřazenou položku. Například pokud <xref:System.Activities.Statements.Parallel> má aktivita více spuštěných větví <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> a vyhodnotí se `true` jako pak nedokončené větve se zruší. V tomto příkladu <xref:System.Activities.Statements.Parallel> se vytvoří aktivita, která má dvě větve. Je nastavená tak ,<xref:System.Activities.Statements.Parallel> aby byla dokončena, jakmile se dokončí kterákoli z jejích větví. `true` <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> V tomto příkladu se větev 2 dokončí, takže se větev 1 zruší.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **Spouští se větev 1.**  
**Větev 2 byla dokončena.**    
**Větev 1 byla zrušena.**    
**E0685e24-18ef-4A47-acf3-5c638732f3be pracovního postupu se dokončil.**  Aktivity jsou zrušeny i v případě, že se v rámci aktivity zobrazí bublinová výjimka po kořenu aktivity, ale zpracovává se v pracovním postupu na vyšší úrovni. V tomto příkladu se hlavní logika pracovního postupu skládá z <xref:System.Activities.Statements.Sequence> aktivity. Je zadán <xref:System.Activities.Statements.TryCatch> jako <xref:System.Activities.Statements.CancellationScope.Body%2A> aktivitaaktivity,kterájeobsažena<xref:System.Activities.Statements.CancellationScope>vaktivitě. <xref:System.Activities.Statements.Sequence> Výjimka je vyvolána z těla <xref:System.Activities.Statements.Sequence>, je zpracována nadřazenou <xref:System.Activities.Statements.TryCatch> aktivitou a <xref:System.Activities.Statements.Sequence> je zrušena.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **Spouští se sekvence.**  
**Sekvence byla zrušena.**    
**Byla zachycena výjimka.**    
**E3c18939-121e-4c43-af1c-ba1ce977ce55 pracovního postupu se dokončil.**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Vyvolání výjimek z CancellationHandler  
 Jakékoli výjimky vyvolané z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> a <xref:System.Activities.Statements.CancellationScope> jsou pro pracovní postup velmi závažné. Pokud existuje možnost výjimek z <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>a, <xref:System.Activities.Statements.TryCatch> použijte v <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> k zachycení a zpracování těchto výjimek.  
  
### <a name="cancellation-using-compensableactivity"></a>Zrušení pomocí aktivita CompensableActivity  
 Podobně jako <xref:System.Activities.Statements.CancellationScope> u aktivity <xref:System.Activities.Statements.CompensableActivity> má <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Pokud je zrušena, všechny aktivity ve svých <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> vyvoláních. <xref:System.Activities.Statements.CompensableActivity> To může být užitečné pro zrušení částečně dokončené kompenzovatelná práce. Informace o tom, jak používat <xref:System.Activities.Statements.CompensableActivity> k kompenzaci a zrušení, najdete v tématu [kompenzace](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Zrušení pomocí vlastních aktivit  
 Autoři vlastní aktivity mohou implementovat logiku zrušení do jejich vlastních aktivit několika různými způsoby. Vlastní aktivity, které jsou <xref:System.Activities.Activity> odvozeny z, mohou implementovat logiku <xref:System.Activities.Statements.CancellationScope> zrušení umístěním nebo jiné vlastní aktivity, která obsahuje logiku zrušení v těle aktivity. <xref:System.Activities.AsyncCodeActivity>a <xref:System.Activities.NativeActivity> odvozené aktivity mohou přepsat jejich příslušnou <xref:System.Activities.NativeActivity.Cancel%2A> metodu a poskytnout logiku zrušení. <xref:System.Activities.CodeActivity>odvozené aktivity neposkytují žádné ustanovení pro zrušení, protože veškerá jejich práce se provádí v rámci jediného nárůstu provádění, když modul runtime <xref:System.Activities.CodeActivity.Execute%2A> volá metodu. Pokud metoda Execute ještě nebyla volána a <xref:System.Activities.CodeActivity> aktivita na základě je zrušena, aktivita se ukončí se <xref:System.Activities.ActivityInstanceState.Canceled> stavem a <xref:System.Activities.CodeActivity.Execute%2A> metoda není volána.  
  
### <a name="cancellation-using-nativeactivity"></a>Zrušení pomocí NativeActivity  
 <xref:System.Activities.NativeActivity>odvozené aktivity mohou přepsat <xref:System.Activities.NativeActivity.Cancel%2A> metodu pro poskytnutí vlastní logiky zrušení. Pokud tato metoda není přepsána, použije se výchozí logika zrušení pracovního postupu. Výchozí zrušení je proces <xref:System.Activities.NativeActivity> , který nastane pro, který <xref:System.Activities.NativeActivity.Cancel%2A> nepřepisuje metodu, nebo jejíž <xref:System.Activities.NativeActivity.Cancel%2A> metoda volá základní <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> metodu. Při zrušení aktivity modul runtime označí aktivitu pro zrušení a automaticky zpracuje určité vyčištění. Pokud má aktivita pouze nedokončené záložky, záložky budou odebrány a aktivita bude označena jako <xref:System.Activities.ActivityInstanceState.Canceled>. Všechny nedokončené podřízené aktivity zrušené aktivity se zase zruší. Pokus o naplánování dalších podřízených aktivit bude mít za následek ignorování pokusu a aktivita bude označena jako <xref:System.Activities.ActivityInstanceState.Canceled>. Pokud se kterákoli nedokončená podřízená <xref:System.Activities.ActivityInstanceState.Canceled> aktivita <xref:System.Activities.ActivityInstanceState.Faulted> dokončí ve stavu nebo, bude se tato <xref:System.Activities.ActivityInstanceState.Canceled>aktivita označit jako. Všimněte si, že žádost o zrušení může být ignorována. Pokud aktivita neobsahuje žádné nedokončené záložky nebo spouští podřízené aktivity a neplánuje žádné další pracovní položky po označení pro zrušení, bude úspěšně dokončena. Toto výchozí zrušení postačuje pro mnoho scénářů, ale pokud je potřeba další logiku zrušení, pak můžete použít předdefinované aktivity zrušení nebo vlastní aktivity.  
  
 V následujícím příkladu <xref:System.Activities.NativeActivity.Cancel%2A> je definováno přepsání <xref:System.Activities.NativeActivity> vlastní `ParallelForEach` aktivity založené na. Při zrušení aktivity toto přepsání zpracovává logiku zrušení aktivity. Tento příklad je součástí ParallelForEach vzorku, [který není obecný](./samples/non-generic-parallelforeach.md) .  
  
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
  
 <xref:System.Activities.NativeActivity>odvozené aktivity mohou určit, zda bylo zrušení vyžádáno <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> , kontrolou vlastnosti a označit samy sebe jako zrušené <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> voláním metody. Volání <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> neprovede aktivitu okamžitě. V obvyklých případech modul runtime aktivitu dokončí, pokud nemá další nevyřízenou práci, ale <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> Pokud je volána jako konečný stav, <xref:System.Activities.ActivityInstanceState.Canceled> bude místo <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Zrušení pomocí funkce AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>Aktivity založené na základě mohou také poskytovat vlastní logiku zrušení přepsáním <xref:System.Activities.AsyncCodeActivity.Cancel%2A> metody. Pokud tato metoda není přepsána, neprovádí se při zrušení aktivity žádné zpracování zrušení. V následujícím příkladu <xref:System.Activities.AsyncCodeActivity.Cancel%2A> je definováno přepsání <xref:System.Activities.AsyncCodeActivity> vlastní `ExecutePowerShell` aktivity založené na. Po zrušení aktivity se provede požadované chování zrušení.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity>odvozené aktivity mohou určit, zda bylo zrušení vyžádáno <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> , kontrolou vlastnosti a označit samy sebe jako zrušené <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> voláním metody.
