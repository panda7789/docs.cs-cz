---
title: "Architektura pracovního postupu systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed13d7885cb8abd760aed6bd5812cb8b7c75bc02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-architecture"></a>Architektura pracovního postupu systému Windows
[!INCLUDE[wf](../../../includes/wf-md.md)]zvýší úroveň abstrakce pro vývoj aplikací interaktivní časově náročné. Pracovní jednotky se zapouzdřené jako aktivity. Aktivity spustit v prostředí, které poskytuje možnosti pro řízení toku, výjimek, chyb šíření, trvalosti dat o stavu, načítání a uvolňování probíhající pracovních postupů z paměti, sledování a toku transakcí.  
  
## <a name="activity-architecture"></a>Architektura aktivity  
 Aktivity jsou vyvinutý jako typy CLR, které jsou odvozeny od buď <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>, nebo jejich varianty, které vrací hodnotu, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, nebo <xref:System.Activities.NativeActivity%601>. Vývoj aktivit, které jsou odvozeny od <xref:System.Activities.Activity> umožňuje uživateli sestavte existující aktivity rychle vytvořit pracovní jednotky, které jsou spuštěny v prostředí pracovního postupu. <xref:System.Activities.CodeActivity>, na druhé straně umožňuje logiky provádění vytvářet spravovaného kódu pomocí <xref:System.Activities.CodeActivityContext> především pro přístup k argumenty aktivity. <xref:System.Activities.AsyncCodeActivity>je podobná <xref:System.Activities.CodeActivity> s tím rozdílem, že ho můžete použít k implementaci asynchronních úloh. Vývoj aktivit, které jsou odvozeny od <xref:System.Activities.NativeActivity> umožňuje uživatelům přistupovat k běhu programu prostřednictvím <xref:System.Activities.NativeActivityContext> pro fungování jako podřízené objekty, vytváření záložek, plánování vyvolání asynchronní pracovní, registraci transakce a další.  
  
 Vytváření aktivit, které jsou odvozeny od <xref:System.Activities.Activity> je deklarativní a tyto aktivity mohou být vytvořené v jazyce XAML. V následujícím příkladu aktivity volá `Prompt` je vytvořený pomocí jiné aktivity pro spuštění textu.  
  
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
 <xref:System.Activities.ActivityContext> Je rozhraní Autor aktivita pro modul runtime pracovního postupu a poskytuje přístup k modulu runtime zadávané funkcí. V následujícím příkladu je definován aktivitu využívající kontext provádění na vytvoření záložky (mechanismus, který umožňuje aktivitu registrace bodu pokračování v jeho spuštění, který může být obnoven, hostitel předávání dat do aktivity).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Životní cyklus aktivity  
 Instance aktivity spustí v <xref:System.Activities.ActivityInstanceState.Executing> stavu. Pokud nedojde k výjimky, zůstane v tomto stavu, dokud všechny podřízené aktivity dokončení provádění a všemi ostatními čekající na vyřízení pracovní (<xref:System.Activities.Bookmark> objekty, například) bylo dokončeno, v okamžiku ho přechodů k <xref:System.Activities.ActivityInstanceState.Closed> stavu. Nadřazená aktivita instance může požádat o podřízené zrušit; je-li dítě moct zrušit dokončí za <xref:System.Activities.ActivityInstanceState.Canceled> stavu. Pokud během provádění je vyvolána výjimka, modul runtime vloží do aktivity <xref:System.Activities.ActivityInstanceState.Faulted> stavu a rozšíří výjimka řetězem nadřazené aktivit. Toto jsou tři dokončení stav aktivity:  
  
-   **Ukončit:** aktivity dokončil svou práci a byl ukončen.  
  
-   **Došlo ke zrušení:** řádně aktivity opuštění svou práci a byl ukončen. Pracovní není explicitně vrácena zpět, když se zadá tento stav.  
  
-   **Došlo k chybě:** aktivity došlo k chybě a byl ukončen bez dokončení svou práci.  
  
 Aktivity zůstat v <xref:System.Activities.ActivityInstanceState.Executing> stav, když jsou nastavené jako trvalé nebo odpojeno.
