---
title: "Vytváření asynchronních aktivit v WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2fd247348050b8335f4f6354c88664d497dbbf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-asynchronous-activities-in-wf"></a>Vytváření asynchronních aktivit v WF
<xref:System.Activities.AsyncCodeActivity>poskytuje základní třídu používat, že umožňuje odvozené aktivity pro implementaci asynchronního spuštění logiku autoři aktivity. To je užitečné pro vlastní aktivity, které musíte provést asynchronní pracovní bez podržte podprocesu plánovače pracovního postupu a blokuje veškeré aktivity, které pravděpodobně bude moci spustit souběžně. Toto téma obsahuje přehled o tom, jak vytvořit vlastní asynchronní aktivity pomocí <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>Pomocí AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType>vlastní aktivity autoři poskytuje různé základní třídy pro požadavky na autorizaci jiné aktivitě. Každé z nich představuje konkrétní sémantického a poskytuje Autor pracovního postupu (a aktivity runtime) odpovídající kontrakt. <xref:System.Activities.AsyncCodeActivity> Na základě aktivity je aktivitou, která provede práci asynchronně relativně k plánovač vláken a jehož logiky provádění vyjádřeného v spravovaný kód. V důsledku asynchronní, přejdete <xref:System.Activities.AsyncCodeActivity> může vyvolávat bod nečinnosti během provádění. Vzhledem k povaze volatile asynchronní práce <xref:System.Activities.AsyncCodeActivity> vždy vytvoří blok žádné zachovat po dobu trvání provádění aktivity. To zabrání modulu runtime pracovního postupu uložením k instanci pracovního postupu uprostřed asynchronní pracovní a rovněž zamezí k instanci pracovního postupu z uvolnění chvíli kód asynchronní provádění.  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity metody  
 Aktivity, které jsou odvozeny od <xref:System.Activities.AsyncCodeActivity> můžete vytvořit logiku asynchronního spuštění přepsáním <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody s vlastní kód. Při volání modulem runtime, se předávají tyto metody <xref:System.Activities.AsyncCodeActivityContext>. <xref:System.Activities.AsyncCodeActivityContext>umožňuje autorovi aktivity poskytnutí sdílené mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> v daném kontextu <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> vlastnost. V následujícím příkladu `GenerateRandom` aktivity asynchronně generuje náhodné číslo.  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Předchozí příklad aktivita je odvozena z <xref:System.Activities.AsyncCodeActivity%601>, a má se zvýšenými oprávněními `OutArgument<int>` s názvem `Result`. Hodnoty vrácené `GetRandom` metoda je extrahována a vrácené <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> override a tato hodnota je nastavena jako `Result` hodnotu. Asynchronní aktivity, které nevracejí výsledek by měl být odvozen z <xref:System.Activities.AsyncCodeActivity>. V následujícím příkladu `DisplayRandom` aktivity je definován, která je odvozena z <xref:System.Activities.AsyncCodeActivity>. Tato aktivita je stejná jako `GetRandom` aktivity, ale místo vrácením výsledku zobrazí zprávu do konzoly.  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Všimněte si, že vzhledem k tomu, že je žádnou návratovou hodnotu `DisplayRandom` používá <xref:System.Action> místo <xref:System.Func%602> k vyvolání jeho delegáta a delegát nevrací žádnou hodnotu.  
  
 <xref:System.Activities.AsyncCodeActivity>také poskytuje <xref:System.Activities.AsyncCodeActivity.Cancel%2A> přepsat. Při <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> jsou požadované přepisy <xref:System.Activities.AsyncCodeActivity.Cancel%2A> je volitelný a může být přepsána tak aktivity můžete vyčistit stav nezpracovaných asynchronní při jeho zrušena nebo přerušena. Pokud vyčištění je možné, a `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` je `true`, by měly volat aktivity <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Jakékoli výjimky vyvolány z této metody jsou závažné k instanci pracovního postupu.  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Volání asynchronních metod třídy  
 Mnoho tříd v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronní nakonfigurovánu a tato funkce umožňuje asynchronně volání pomocí <xref:System.Activities.AsyncCodeActivity> na základě aktivity. V následujícím příkladu z [pomocí AsyncOperationContext v aktivitě](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md), aktivita je vytvořen, který asynchronně vytvoří soubor pomocí <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Sdílení stavu mezi BeginExecute a EndExecute metody  
 V předchozím příkladu <xref:System.IO.FileStream> objekt, který byl vytvořen v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> v přístupu <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. To je možné, protože `file` proměnná byla předána <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> vlastnost v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Toto je správný způsob pro sdílení stavu mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Je nesprávný pro použití v odvozené třídě členské proměnné (`FileWriter` v tomto případě) ke sdílení stavu mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> vzhledem k tomu, že objekt aktivity může být odkazován více instancemi aktivity. Pokus o použití členské proměnné sdílet stavu může mít za následek hodnoty z jednoho <xref:System.Activities.ActivityInstance> přepsání nebo využívání hodnoty z jiné <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Přístup k argumentu hodnoty  
 Prostředí <xref:System.Activities.AsyncCodeActivity> se skládá z argumentů definované na aktivity. Tyto argumenty je přístupná z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání pomocí <xref:System.Activities.AsyncCodeActivityContext> parametr. Argumenty, které nejsou přístupné v delegáta, ale argument hodnoty nebo jiné požadovaným datům lze předat v delegáta pomocí jeho parametry. V následujícím příkladu je definován náhodné generování číslo aktivity který získá včetně horní mez z jeho `Max` argument. Hodnota argumentu je předané do asynchronní kód při vyvolání delegáta.  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Plánování akce nebo podřízené aktivity pomocí AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>odvozené vlastních aktivit poskytují metodu pro provádění pracovní asynchronně s ohledem na vlákno pracovního postupu, ale neposkytuje možnost plánování podřízené aktivity nebo akce. Asynchronní chování však lze začlenit s plánování aktivit podřízené prostřednictvím složení. Asynchronní aktivitu vytvořili a pak se skládá <xref:System.Activities.Activity> nebo <xref:System.Activities.NativeActivity> odvozené aktivity zajistit asynchronní chování a plánování podřízené aktivity nebo akce. Například aktivita by bylo možné vytvořit odvozenou od <xref:System.Activities.Activity>a jako jeho implementace <xref:System.Activities.Statements.Sequence> obsahující asynchronní aktivitu jako i další aktivity, které implementují logiku aktivity. Další příklady skládání aktivity pomocí <xref:System.Activities.Activity> a <xref:System.Activities.NativeActivity>, najdete v části [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md), [možnosti vytváření aktivity](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)a [složené](../../../docs/framework/windows-workflow-foundation/samples/composite.md) ukázky aktivity.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Action>  
 <xref:System.Func%602>  
 [Pomocí AsyncOperationContext v aktivitě](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)
