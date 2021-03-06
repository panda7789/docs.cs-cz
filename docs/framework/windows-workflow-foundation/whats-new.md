---
title: Novinky ve Windows Workflow Foundation
description: Přečtěte si o programovací model Windows Workflow Foundation změnách v .NET Framework 4. Pracovní postupy je snazší vytvářet, spouštět a udržovat.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: b25b71a61f8a96d59c79e780d9fe5cd03abfa299
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419340"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Novinky ve Windows Workflow Foundation

Programovací model Windows Workflow Foundation (WF) v .NET Framework 4 mění několik paradigmat vývoje z předchozích verzí. Pracovní postupy teď usnadňují vytváření, spouštění a údržbu a implementaci hostitele nových funkcí. Další informace o migraci aplikací pro pracovní postup .NET 3,0 a .NET 3,5 na používání nejnovější verze najdete v tématu [pokyny k migraci](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Model aktivity pracovního postupu  
 Tato aktivita je nyní základní jednotkou vytváření pracovního postupu namísto použití <xref:System.Workflow.Activities.SequentialWorkflowActivity> <xref:System.Workflow.Activities.StateMachineWorkflowActivity> tříd nebo. <xref:System.Activities.Activity>Třída poskytuje základní abstrakci chování pracovního postupu. Autoři aktivit pak můžou implementovat buď <xref:System.Activities.CodeActivity> pro základní funkce vlastní aktivity, nebo <xref:System.Activities.NativeActivity> pro funkce vlastní aktivity, které používají šířky modulu runtime. <xref:System.Activities.Activity>je třída používaná autory aktivity k vyjádření nového chování deklarativně v závislosti na jiných <xref:System.Activities.NativeActivity> , <xref:System.Activities.CodeActivity> , <xref:System.Activities.AsyncCodeActivity> nebo <xref:System.Activities.DynamicActivity> objektech, ať už jsou vlastní nebo zahrnuté do [předdefinované knihovny aktivit](net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Rozšířené možnosti složené aktivity  
 <xref:System.Activities.Statements.Flowchart>je výkonná nová aktivita toku řízení, která umožňuje autorům modelování libovolných smyček a podmíněných větví. <xref:System.Activities.Statements.Flowchart>poskytuje programovací model řízený událostmi, který byl dřív možné implementovat pouze pomocí <xref:System.Workflow.Activities.StateMachineWorkflowActivity> . Procesní pracovní postupy využívají nové aktivity řízení toku, které modelují tradiční struktury řízení toku, jako jsou <xref:System.Activities.Statements.TryCatch> a <xref:System.Activities.Statements.Switch%601> .  
  
## <a name="expanded-built-in-activity-library"></a>Rozšířená integrovaná knihovna aktivit  
 Mezi nové funkce knihovny aktivit patří:  
  
- Nové aktivity řízení toku, například,, <xref:System.Activities.Statements.DoWhile> , <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.TryCatch> , <xref:System.Activities.Statements.ForEach%601> , a <xref:System.Activities.Statements.Switch%601> <xref:System.Activities.Statements.ParallelForEach%601> .  
  
- Aktivity pro manipulaci s členskými daty, jako jsou například <xref:System.Activities.Statements.Assign> aktivity a shromažďování dat <xref:System.Activities.Statements.AddToCollection%601> .  
  
- Aktivity pro řízení transakcí, například <xref:System.Activities.Statements.TransactionScope> a <xref:System.Activities.Statements.Compensate> .  
  
- Nové aktivity zasílání zpráv, jako jsou <xref:System.ServiceModel.Activities.SendContent> a <xref:System.ServiceModel.Activities.ReceiveReply> .  
  
## <a name="explicit-activity-data-model"></a>Datový model explicitní aktivity  
 .NET Framework 4 obsahuje nové možnosti ukládání a přesouvání dat. Data je možné ukládat do aktivity pomocí <xref:System.Activities.Variable> . Při přesunu dat do aktivity a mimo ni se používají specializované typy argumentů k určení, která směrová data se pohybují. Tyto typy jsou <xref:System.Activities.InArgument> , <xref:System.Activities.InOutArgument> a <xref:System.Activities.OutArgument> . Další informace najdete v tématu [programovací model Windows Workflow Foundation datový model](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Rozšířené možnosti hostování, trvalosti a sledování  
 .NET Framework 4 obsahuje vylepšení trvalosti, například následující:  
  
- K dispozici je více možností pro spouštění pracovních postupů, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost> , <xref:System.Activities.WorkflowApplication> a <xref:System.Activities.WorkflowInvoker> .  
  
- Data stavu pracovního postupu lze explicitně trvale uchovat pomocí <xref:System.Activities.Statements.Persist> aktivity.  
  
- Hostitel může zachovat <xref:System.Activities.ActivityInstance> bez jeho uvolnění.  
  
- Pracovní postup může při práci s daty, která nesmí být trvalá, určit zóny bez trvalého uložení, aby se trvala odložená, dokud nedojde k ukončení zóny bez trvalého uložení.  
  
- Transakce se dají přesměrovat do pracovního postupu pomocí <xref:System.Activities.Statements.TransactionScope> .  
  
- Sledování je snazší pomocí <xref:System.Activities.Tracking.TrackingParticipant> .  
  
- Sledování do protokolu událostí systému je k dispozici pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant> .  
  
- Obnovení pracovního postupu, který čeká na vyřízení, se teď spravuje pomocí <xref:System.Activities.Bookmark> objektu.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Snadnější možnost rozšiřování prostředí Návrháře WF  
 Nový Návrhář WF je postaven na Windows Presentation Foundation (WPF) a poskytuje jednodušší model pro použití při rehostování Návrháře WF mimo Visual Studio a poskytuje také snadnější mechanismy pro vytváření vlastních návrhářů aktivit. Další informace najdete v tématu [přizpůsobení prostředí pro návrh pracovního postupu](customizing-the-workflow-design-experience.md).
