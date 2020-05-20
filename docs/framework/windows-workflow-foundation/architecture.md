---
title: Architektura Windows Workflow
description: Programovací model Windows Workflow Foundation zapouzdřují jednotky práce jako aktivity, které běží v prostředí s řízením toku, zpracováním výjimek a dalšími funkcemi.
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 22ebeb7d95342ad6843e0721da8b213ed4a4d9b6
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420133"
---
# <a name="windows-workflow-architecture"></a>Architektura Windows Workflow
Programovací model Windows Workflow Foundation (WF) vyvolává úroveň abstrakce pro vývoj interaktivních dlouhotrvajících aplikací. Pracovní jednotky se zapouzdřují jako aktivity. Aktivity běží v prostředí, které poskytuje vybavení pro řízení toku, zpracování výjimek, šíření chyb, stálost stavových dat, načítání a uvolňování probíhajících pracovních postupů z paměti, sledování a toku transakcí.  
  
## <a name="activity-architecture"></a>Architektura aktivity  
 Aktivity jsou vyvíjeny jako typy CLR, které jsou odvozeny z <xref:System.Activities.Activity> , <xref:System.Activities.CodeActivity> , <xref:System.Activities.AsyncCodeActivity> nebo <xref:System.Activities.NativeActivity> , nebo jejich varianty, které vracejí hodnotu, <xref:System.Activities.Activity%601> ,, <xref:System.Activities.CodeActivity%601> <xref:System.Activities.AsyncCodeActivity%601> nebo <xref:System.Activities.NativeActivity%601> . Vývoj aktivit, které jsou odvozeny od <xref:System.Activities.Activity> , umožňuje uživateli sestavovat již existující aktivity a rychle tak vytvářet jednotky práce, které jsou spouštěny v prostředí pracovního postupu. <xref:System.Activities.CodeActivity>na druhé straně umožňuje logiku spouštění vytvořit ve spravovaném kódu pomocí <xref:System.Activities.CodeActivityContext> primárně pro přístup k argumentům aktivity. <xref:System.Activities.AsyncCodeActivity>je podobný s <xref:System.Activities.CodeActivity> tím rozdílem, že lze použít k implementaci asynchronních úloh. Vývoj aktivit, které jsou odvozeny od <xref:System.Activities.NativeActivity> , umožňuje uživatelům přistupovat k modulu runtime prostřednictvím <xref:System.Activities.NativeActivityContext> funkce pro funkci, jako je plánování podřízených objektů, vytváření záložek, vyvolání asynchronní práce, registrace transakcí a další.  
  
 Vytváření aktivit, které jsou odvozeny z <xref:System.Activities.Activity> , je deklarativní a tyto aktivity lze vytvořit v jazyce XAML. V následujícím příkladu je aktivita s názvem `Prompt` vytvořena pomocí jiných aktivit pro tělo provádění.  
  
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
 <xref:System.Activities.ActivityContext>Je rozhraní autora aktivity pro modul runtime pracovního postupu a poskytuje přístup k spoustě funkcí běhového prostředí. V následujícím příkladu je definována aktivita, která používá kontext spuštění k vytvoření záložky (mechanismus, který umožňuje aktivity registrovat bod pokračování ve svém spuštění, který může být obnoven hostitelem předávání dat do aktivity).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>Životní cyklus aktivity  
 Instance aktivity začíná ve <xref:System.Activities.ActivityInstanceState.Executing> stavu. Pokud nedošlo k výjimkám, zůstane v tomto stavu, dokud nebudou dokončeny všechny podřízené aktivity a dokud nejsou dokončeny všechny další dokončené práce ( <xref:System.Activities.Bookmark> objekty, například), a to tak, aby se přechod do <xref:System.Activities.ActivityInstanceState.Closed> stavu dokončil. Nadřazená instance aktivity může požádat o zrušení podřízeného objektu. Pokud je podřízený objekt schopný zrušit jeho dokončení ve <xref:System.Activities.ActivityInstanceState.Canceled> stavu. Pokud je vyvolána výjimka během provádění, modul runtime vloží aktivitu do <xref:System.Activities.ActivityInstanceState.Faulted> stavu a rozšíří výjimku do nadřazeného řetězce aktivit. Níže jsou uvedené tři stavy dokončování aktivity:
  
- **Uzavřeno:** Aktivita dokončila svoji práci a ukončila ji.  
  
- **Zrušeno:** Aktivita byla řádně opuštěna a ukončena. Práce není explicitně vrácena zpět, pokud je tento stav zadán.  
  
- **Došlo k chybě:** V aktivitě došlo k chybě a byla ukončena bez dokončení práce.  
  
 Aktivity zůstanou ve <xref:System.Activities.ActivityInstanceState.Executing> stavu, kdy jsou trvalé nebo Nenačtené.
