---
title: Vytváření asynchronních aktivit v WF
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: 1b7fe1c5c998660f054d2ca060c108c758e36db7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650925"
---
# <a name="creating-asynchronous-activities-in-wf"></a>Vytváření asynchronních aktivit v WF
<xref:System.Activities.AsyncCodeActivity> poskytuje základní třídu použít, že umožňuje odvozené aktivity implementovat logiku spouštění asynchronní autoři aktivity. To je užitečné pro vlastní aktivity, které musíte provést asynchronní práce bez podržení Plánovač vlákna pracovního postupu a blokuje veškeré aktivity, které může být možné spouštět paralelně. Toto téma obsahuje přehled o tom, jak vytvořit vlastní asynchronních aktivit pomocí <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>Pomocí AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType> vlastní aktivita autoři poskytuje různé základní třídy pro požadavky na autorizaci jiné aktivitě. Každé z nich představuje konkrétní sémantické a poskytuje Autor pracovního postupu (a modul runtime aktivit) odpovídající kontraktu. <xref:System.Activities.AsyncCodeActivity> Závislosti aktivit je aktivitou, která provádí asynchronně vzhledem k plánovači vlákna a logiku jejichž spouštění je vyjádřen v spravovaného kódu. V důsledku asynchronní, přejděte <xref:System.Activities.AsyncCodeActivity> může vyvolávat nečinnosti bod během provádění. Vzhledem k volatile povaze asynchronní práce <xref:System.Activities.AsyncCodeActivity> dočasného bloku vytvoří vždy po dobu trvání provádění aktivity. To zabraňuje modulu runtime pracovního postupu v trvalém ukládání instance pracovního postupu uprostřed asynchronní práce a tím také ochrana instance pracovního postupu z uvolňování chvíli provádí asynchronní kód.  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity metody  
 Aktivity, které jsou odvozeny z <xref:System.Activities.AsyncCodeActivity> asynchronnímu spouštění logiky můžete vytvořit tak, že přepíšete <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody s vlastním kódem. Když se zavolá pomocí modulu runtime, tyto metody jsou předány <xref:System.Activities.AsyncCodeActivityContext>. <xref:System.Activities.AsyncCodeActivityContext> umožňuje autorovi aktivit poskytují sdílený stav napříč <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> v kontextu <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> vlastnost. V následujícím příkladu `GenerateRandom` aktivity asynchronně generuje náhodné číslo.  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Předchozí příklad aktivity je odvozena z <xref:System.Activities.AsyncCodeActivity%601>, a má zvýšenými `OutArgument<int>` s názvem `Result`. Hodnota vrácená `GetRandom` metody se extrahují a vrácené <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> přepsání a tato hodnota je nastavena jako `Result` hodnotu. Asynchronní aktivity, která nevrátí výsledek by měl být odvozen z <xref:System.Activities.AsyncCodeActivity>. V následujícím příkladu `DisplayRandom` aktivity je definován, která je odvozena z <xref:System.Activities.AsyncCodeActivity>. Tato aktivita je podobná `GetRandom` aktivitu, ale místo vrácení výsledku zobrazí zprávu do konzoly.  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Upozorňujeme, že neexistuje žádná návratová hodnota `DisplayRandom` používá <xref:System.Action> místo <xref:System.Func%602> k vyvolání jeho delegáta a delegáta nevrací žádnou hodnotu.  
  
 <xref:System.Activities.AsyncCodeActivity> poskytuje také <xref:System.Activities.AsyncCodeActivity.Cancel%2A> přepsat. Zatímco <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> jsou požadované přepisy <xref:System.Activities.AsyncCodeActivity.Cancel%2A> je volitelné a můžete přepsat tak aktivity můžete vyčistit stavu nevyřízených asynchronních při jeho zrušena nebo přerušena. Pokud vyčištění je možné a `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` je `true`, by měly volat aktivitu <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Výjimky vyvolané z této metody jsou závažná instance pracovního postupu.  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Volání asynchronní metody ve třídě  
 Mnoho ze tříd v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poskytuje asynchronní funkce a tato funkce může být vyvolána asynchronně pomocí <xref:System.Activities.AsyncCodeActivity> podle aktivity. V následujícím příkladu se vytvoří aktivita, která asynchronně vytvoří soubor s použitím <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Sdílení stavu mezi BeginExecute a EndExecute metody  
 V předchozím příkladu <xref:System.IO.FileStream> objekt, který byl vytvořen v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> se použila v <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. To je možné, protože `file` byla předána proměnná <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> vlastnost v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Toto je správný způsob sdílení stavu mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Je nesprávná můžete členské proměnné v odvozené třídě (`FileWriter` v tomto případě) ke sdílení stavu mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> vzhledem k tomu, že objekt aktivity může odkazovat více instancí aktivity. Pokus o použití členskou proměnnou ke sdílení stavu může vést k hodnoty z jednoho <xref:System.Activities.ActivityInstance> přepsání nebo používání hodnoty z jiného <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Přístup k hodnoty argumentů  
 Prostředí, které <xref:System.Activities.AsyncCodeActivity> se skládá z argumentů definované v aktivitě. Tyto argumenty je přístupný z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepíše pomocí <xref:System.Activities.AsyncCodeActivityContext> parametru. Argumenty není přístupná na delegáta, ale hodnoty argumentů nebo jiných požadovaných dat lze předat v delegátovi pomocí jeho parametry. V následujícím příkladu je definován náhodné číslo generování aktivity, který získá inkluzivní dolní mez z jeho `Max` argument. Hodnota argumentu předaný k asynchronnímu kódu při vyvolání delegáta.  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Plánování akce nebo podřízené aktivity pomocí AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity> odvozené vlastních aktivit poskytují způsob provedení práce asynchronně s ohledem na vlákna pracovního postupu, ale neposkytuje možnosti plánovat podřízené aktivity nebo akce. Asynchronní chování však být použity s plánováním podřízených aktivit prostřednictvím složení. Asynchronní aktivita vytvořili a potom utvořený za použití <xref:System.Activities.Activity> nebo <xref:System.Activities.NativeActivity> odvozené aktivity k poskytování asynchronní chování a plánováním podřízených aktivit nebo akce. Například aktivita může vytvořit, která je odvozena z <xref:System.Activities.Activity>a jako jeho implementace <xref:System.Activities.Statements.Sequence> obsahující asynchronní aktivitu jako také další činnosti, které implementují logiku aktivity. Další příklady vytváření aktivit pomocí <xref:System.Activities.Activity> a <xref:System.Activities.NativeActivity>, naleznete v tématu [jak: Vytvořit aktivitu](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) a [aktivity vytváření možnosti](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Action>
- <xref:System.Func%602>
