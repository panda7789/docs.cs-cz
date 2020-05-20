---
title: Vytváření asynchronních aktivit v WF
description: Naučte se vytvářet vlastní asynchronní aktivity pomocí funkce AsyncCodeActivity, která umožňuje odvozeným aktivitám implementovat logiku asynchronního spuštění.
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: f7ce0c0157791b34723feff185aed24bb56a4b3f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421524"
---
# <a name="creating-asynchronous-activities-in-wf"></a>Vytváření asynchronních aktivit v WF
<xref:System.Activities.AsyncCodeActivity>poskytuje tvůrcům aktivity základní třídu pro použití, která umožňuje odvozeným aktivitám implementovat logiku asynchronního spuštění. To je užitečné pro vlastní aktivity, které musí provádět asynchronní práci bez podržení vlákna plánovače pracovních postupů a blokování všech aktivit, které mohou být schopny běžet paralelně. Toto téma poskytuje přehled o tom, jak vytvořit vlastní asynchronní aktivity pomocí nástroje <xref:System.Activities.AsyncCodeActivity> .  
  
## <a name="using-asynccodeactivity"></a>Použití funkce AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType>poskytuje vlastní autory aktivity s různými základními třídami pro různé požadavky na vytváření aktivit. Každá z nich má konkrétní sémantiku a poskytuje pracovní postup autora (a modulu runtime aktivit) odpovídající kontrakt. <xref:System.Activities.AsyncCodeActivity>Aktivita založená na aktivitě je aktivita, která provádí asynchronní práci vzhledem ke vláknu Scheduleru a jehož logika provádění je vyjádřena ve spravovaném kódu. V důsledku asynchronního řízení <xref:System.Activities.AsyncCodeActivity> může způsobit nečinný bod během provádění. Z důvodu nestálé povahy asynchronní práce <xref:System.Activities.AsyncCodeActivity> vždy vytvoří blok bez trvalého blokování po dobu trvání provádění aktivity. To zabrání modulu runtime pracovního postupu v zachování instance pracovního postupu uprostřed asynchronní práce a zároveň zabrání instanci pracovního postupu v uvolnění při provádění asynchronního kódu.  
  
### <a name="asynccodeactivity-methods"></a>Metody funkce AsyncCodeActivity  
 Aktivity, které jsou odvozeny z <xref:System.Activities.AsyncCodeActivity> , mohou vytvořit logiku asynchronního spuštění přepsáním <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metod a pomocí vlastního kódu. Při volání do modulu runtime jsou tyto metody předány <xref:System.Activities.AsyncCodeActivityContext> . <xref:System.Activities.AsyncCodeActivityContext>umožňuje autorovi aktivity poskytovat sdílený stav napříč <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> v rámci vlastnosti daného kontextu <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> . V následujícím příkladu `GenerateRandom` aktivita generuje náhodné číslo asynchronně.  
  
 [!code-csharp[CFX_ActivityExample#8](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Předchozí ukázková aktivita je odvozena z <xref:System.Activities.AsyncCodeActivity%601> a má pojmenovanou zvýšenou úroveň `OutArgument<int>` `Result` . Hodnota vrácená `GetRandom` metodou je extrahována a vrácena <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> přepsáním a tato hodnota je nastavena jako `Result` hodnota. Asynchronní aktivity, které nevracejí výsledek, by měly být odvozeny z <xref:System.Activities.AsyncCodeActivity> . V následujícím příkladu `DisplayRandom` je definována aktivita, která je odvozena z <xref:System.Activities.AsyncCodeActivity> . Tato aktivita se podobá `GetRandom` aktivitě, ale místo vrácení výsledku se zobrazí zpráva do konzoly.  
  
 [!code-csharp[CFX_ActivityExample#11](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Všimněte si, že vzhledem k tomu, že není k dispozici žádná návratová hodnota, `DisplayRandom` používá <xref:System.Action> namísto <xref:System.Func%602> vyvolání delegáta a delegát nevrací žádnou hodnotu.  
  
 <xref:System.Activities.AsyncCodeActivity>také poskytuje <xref:System.Activities.AsyncCodeActivity.Cancel%2A> přepsání. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>I když <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> jsou vyžadované přepsání, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> je volitelné a lze je přepsat, aby aktivita vyčistila svůj nezpracovaný asynchronní stav při jeho zrušení nebo přerušení. Pokud je to možné `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` `true` , musí aktivita zavolat <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> . Jakékoli výjimky vyvolané z této metody jsou pro instanci pracovního postupu závažné.  
  
 [!code-csharp[CFX_ActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Vyvolání asynchronních metod pro třídu  
 Mnoho tříd v .NET Framework poskytuje asynchronní funkce a tuto funkci lze asynchronně vyvolávat pomocí <xref:System.Activities.AsyncCodeActivity> aktivity založené na. V následujícím příkladu je vytvořena aktivita, která asynchronně vytvoří soubor pomocí <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[CFX_ActivityExample#12](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Stav sdílení mezi metodami BeginExecute a EndExecute  
 V předchozím příkladu <xref:System.IO.FileStream> byl objekt, který byl vytvořen v, <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> použit v <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . To je možné, protože `file` Proměnná byla předána do <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> vlastnosti v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> . Toto je správná metoda pro stav sdílení mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . Je nesprávné použít členskou proměnnou v odvozené třídě ( `FileWriter` v tomto případě) ke sdílení stavu mezi <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> vzhledem k tomu, že na objekt aktivity může odkazovat více instancí aktivity. Pokus o použití členské proměnné ke sdílení stavu může mít za následek hodnoty z jednoho <xref:System.Activities.ActivityInstance> přepsání nebo využívání hodnot z jiného <xref:System.Activities.ActivityInstance> .  
  
### <a name="accessing-argument-values"></a>Přístup k hodnotám argumentů  
 Prostředí <xref:System.Activities.AsyncCodeActivity> se skládá z argumentů definovaných v aktivitě. K těmto argumentům lze z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání použít <xref:System.Activities.AsyncCodeActivityContext> parametr. K argumentům není v delegátu možné přistupovat, ale hodnoty argumentů nebo jiná požadovaná data lze předat delegátovi pomocí jeho parametrů. V následujícím příkladu je definována náhodná aktivita generování čísel, která získá celkovou horní mez od svého `Max` argumentu. Hodnota argumentu je předána do asynchronního kódu, když je vyvolán delegát.  
  
 [!code-csharp[CFX_ActivityExample#9](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Plánování akcí nebo podřízených aktivit pomocí funkce AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>odvozené vlastní aktivity poskytují metodu pro asynchronní práci s ohledem na vlákno pracovního postupu, ale neposkytují možnost plánovat podřízené aktivity nebo akce. Asynchronní chování se ale dá začlenit s plánováním podřízených aktivit prostřednictvím složení. Lze vytvořit asynchronní aktivitu a následně složenou s <xref:System.Activities.Activity> nebo <xref:System.Activities.NativeActivity> odvozenou aktivitou, která poskytuje asynchronní chování a plánování podřízených aktivit nebo akcí. Například může být vytvořena aktivita, která je odvozena z <xref:System.Activities.Activity> a má jako její implementaci a <xref:System.Activities.Statements.Sequence> obsahující asynchronní aktivity, i další aktivity, které implementují logiku aktivity. Další příklady sestavování aktivit pomocí <xref:System.Activities.Activity> a <xref:System.Activities.NativeActivity> naleznete v tématu [How to: Create a Activity](how-to-create-an-activity.md) a [Authoring Options](activity-authoring-options-in-wf.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Action>
- <xref:System.Func%602>
