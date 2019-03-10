---
title: Architektura Windows Workflow
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 5d6e1ead9184bfb61eb466389671ca2e74264ae3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723736"
---
# <a name="windows-workflow-architecture"></a>Architektura Windows Workflow
Windows Workflow Foundation (WF) zvýší úroveň abstrakce pro vývoj interaktivní dlouho běžící aplikace. Pracovní jednotky jsou zapouzdřeny jako aktivity. Aktivity spuštění v prostředí, které poskytuje funkce pro řízení toku, zpracování výjimek, šíření chyb, trvalosti dat o stavu, načítání a uvolňování probíhajících pracovních postupů z paměti, sledování a tok transakcí.  
  
## <a name="activity-architecture"></a>Architektura aktivity  
 Aktivity jsou vyvíjeny jako typy CLR, které jsou odvozeny z buď <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>, nebo jejich variant, které vrací hodnotu, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, nebo <xref:System.Activities.NativeActivity%601>. Vývoj aktivit, které jsou odvozeny z <xref:System.Activities.Activity> mu umožní Poskládejte si můžete rychle vytvořit jednotky práce, které jsou spuštěny v prostředí pracovního postupu již existujících aktivit. <xref:System.Activities.CodeActivity>, na druhé straně, umožňuje spouštění logiky nebylo vytvořeno ve spravovaném kódu použitím <xref:System.Activities.CodeActivityContext> především pro přístup k argumenty aktivity. <xref:System.Activities.AsyncCodeActivity> je podobný <xref:System.Activities.CodeActivity> s tím rozdílem, že je možné provádět asynchronní úlohy. Vývoj aktivit, které jsou odvozeny z <xref:System.Activities.NativeActivity> umožňuje uživatelům přístup k modulu runtime prostřednictvím <xref:System.Activities.NativeActivityContext> pro funkce, jako je plánování podřízené položky, vytváření záložek, volání asynchronní práce, zápisu transakce a další.  
  
 Vytváření aktivit, které jsou odvozeny z <xref:System.Activities.Activity> je deklarativní a dají se vytvářet tyto aktivity v XAML. V následujícím příkladu volá aktivita `Prompt` je vytvořený pomocí další aktivity pro zpracování textu.  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a>Kontext aktivity  
 <xref:System.Activities.ActivityContext> Je autorem aktivity rozhraní pro modul runtime pracovního postupu a poskytuje přístup k modulu runtime řadu funkcí. V následujícím příkladu je definován aktivity, které používá kontext spuštění pro vytvoření záložky (mechanismus, který umožňuje aktivita registrace bodu pokračování v provádění, který šlo obnovit hostitele předávání dat o aktivitě).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Životní cyklus aktivity  
 Instance aktivity na začátku <xref:System.Activities.ActivityInstanceState.Executing> stavu. Pokud nedojde k výjimky, zůstane v tomto stavu, dokud všechny podřízené aktivity jsou dokončené, provádění a jakékoli jiné probíhající práce (<xref:System.Activities.Bookmark> objekty, například) je dokončeno, na které bod přechody <xref:System.Activities.ActivityInstanceState.Closed> stavu. Nadřazená instance aktivity požádat o zrušení; podřízené Pokud podřízená je možné zrušit dokončí za <xref:System.Activities.ActivityInstanceState.Canceled> stavu. Pokud během provádění dojde k výjimce, modul runtime umístí aktivitu <xref:System.Activities.ActivityInstanceState.Faulted> stavu a rozšíří výjimku řetězem nadřazené aktivity. Stavy tři dokončení aktivity jsou následující:  
  
-   **Zavřít:** Aktivita dokončil svou práci a byl ukončen.  
  
-   **Zrušeno:** Aktivita má řádně opuštěných svou práci a byl ukončen. Pracovní není explicitně vrácena zpět, když se zadá tento stav.  
  
-   **Došlo k chybě:** Aktivita došlo k chybě a byl ukončen bez dokončení práce.  
  
 Aktivity zůstanou v <xref:System.Activities.ActivityInstanceState.Executing> stav, když jsou trvalé nebo byla uvolněna.
