---
title: Architektura Windows Workflow
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: e2effc0f53153057b8a9034e4dc80cb19bbe7685
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834866"
---
# <a name="windows-workflow-architecture"></a>Architektura Windows Workflow
Programovací model Windows Workflow Foundation (WF) vyvolává úroveň abstrakce pro vývoj interaktivních dlouhotrvajících aplikací. Pracovní jednotky se zapouzdřují jako aktivity. Aktivity běží v prostředí, které poskytuje vybavení pro řízení toku, zpracování výjimek, šíření chyb, stálost stavových dat, načítání a uvolňování probíhajících pracovních postupů z paměti, sledování a toku transakcí.  
  
## <a name="activity-architecture"></a>Architektura aktivity  
 Aktivity jsou vyvíjeny jako typy CLR, které jsou odvozeny od <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> nebo <xref:System.Activities.NativeActivity> nebo jejich varianty, které vracejí hodnotu, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601> nebo <xref:System.Activities.NativeActivity%601>. Vývoj aktivit odvozený od <xref:System.Activities.Activity> umožňuje uživateli sestavovat již existující aktivity a rychle tak vytvářet jednotky práce, které se spouštějí v prostředí pracovního postupu. <xref:System.Activities.CodeActivity> na druhé straně umožňuje logiku provádění vytvořit ve spravovaném kódu pomocí <xref:System.Activities.CodeActivityContext> primárně pro přístup k argumentům aktivity. <xref:System.Activities.AsyncCodeActivity> se podobá <xref:System.Activities.CodeActivity> s tím rozdílem, že lze použít k implementaci asynchronních úloh. Vývoj aktivit odvozený od <xref:System.Activities.NativeActivity> umožňuje uživatelům přistupovat k modulu runtime prostřednictvím <xref:System.Activities.NativeActivityContext> pro funkce, jako je plánování podřízených objektů, vytváření záložek, vyvolání asynchronní práce, registrace transakcí a další.  
  
 Aktivity vytváření, které jsou odvozeny od <xref:System.Activities.Activity> jsou deklarativní a tyto aktivity lze vytvořit v jazyce XAML. V následujícím příkladu se aktivita s názvem `Prompt` vytvoří pomocí jiných aktivit pro tělo provádění.  
  
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
 @No__t-0 je rozhraní autora aktivity pro modul runtime pracovního postupu a poskytuje přístup k spoustě funkcí běhového prostředí. V následujícím příkladu je definována aktivita, která používá kontext spuštění k vytvoření záložky (mechanismus, který umožňuje aktivity registrovat bod pokračování ve svém spuštění, který může být obnoven hostitelem předávání dat do aktivity).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Životní cyklus aktivity  
 Instance aktivity začíná ve stavu <xref:System.Activities.ActivityInstanceState.Executing>. Pokud nedošlo k výjimkám, zůstane v tomto stavu, dokud nebudou dokončeny všechny podřízené aktivity a dokud nejsou dokončeny všechny ostatní objekty, které čekají na vyřízení (<xref:System.Activities.Bookmark> objektů), a v takovém případě přejdete do stavu <xref:System.Activities.ActivityInstanceState.Closed>. Nadřazená instance aktivity může požádat o zrušení podřízeného objektu. Pokud je možné podřízenou položku zrušit, dokončí se ve stavu <xref:System.Activities.ActivityInstanceState.Canceled>. Pokud je vyvolána výjimka během provádění, modul runtime vloží aktivitu do stavu @no__t 0 a rozšíří výjimku do nadřazeného řetězce aktivit. Níže jsou uvedené tři stavy dokončování aktivity:
  
- **Uzavřeno:** Aktivita dokončila svoji práci a ukončila ji.  
  
- **Zrušeno:** Aktivita byla řádně opuštěna a ukončena. Práce není explicitně vrácena zpět, pokud je tento stav zadán.  
  
- **Došlo k chybě:** V aktivitě došlo k chybě a byla ukončena bez dokončení práce.  
  
 Aktivity zůstávají ve stavu <xref:System.Activities.ActivityInstanceState.Executing>, pokud jsou trvalé nebo Nenačtené.
