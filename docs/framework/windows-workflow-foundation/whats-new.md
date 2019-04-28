---
title: Novinky ve Windows Workflow Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: 5ab1419a29dd77ac276681bb49dc529fc05d5b15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669533"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Novinky ve Windows Workflow Foundation
Windows Workflow Foundation (WF) v [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] více paradigmat vývoj se změní z předchozí verze. Pracovní postupy se teď snadněji vytvářet, spouštět a udržovat a implementovat celou řadu nových funkcí. Další informace o migraci .NET 3.0 a 3.5 rozhraní .NET aplikace pracovního postupu chcete používat nejnovější verzi najdete v tématu [pokyny k migraci](migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Model aktivity pracovního postupu  
 Aktivita je nyní základní jednotky vytvoření pracovního postupu, spíš než <xref:System.Workflow.Activities.SequentialWorkflowActivity> nebo <xref:System.Workflow.Activities.StateMachineWorkflowActivity> třídy. <xref:System.Activities.Activity> Třída poskytuje základní abstrakce chování pracovního postupu. Autoři aktivitu poté můžete implementovat buď <xref:System.Activities.CodeActivity> pro vlastní aktivity základní funkce, nebo <xref:System.Activities.NativeActivity> pro vlastní aktivity funkci, která používá kontejnerových nástrojů modulu runtime. <xref:System.Activities.Activity> je třída používaná autory aktivity vyjádřit nové chování deklarativně z hlediska jiné <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.DynamicActivity> objektů, ať už jsou vlastní nebo součástí [předdefinovanou aktivitu Knihovna](net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Složené bohaté možnosti aktivity  
 <xref:System.Activities.Statements.Flowchart> je výkonný novou aktivitu toku řízení, která umožňuje autorům model libovolného smyček a podmíněného větvení. <xref:System.Activities.Statements.Flowchart> poskytuje založený na událostech programovací model, který byl dříve pouze moct pomocí provádí <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Procedurální pracovní postupy těžit z nových aktivit řízení toku, které modelují tradiční řízení toku na struktury, jako například <xref:System.Activities.Statements.TryCatch> a <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Rozbalit knihovna předdefinovaných aktivit  
 Mezi nové funkce knihovny aktivit patří:  
  
- Nový tok řízení činností, jako jsou například <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, a <xref:System.Activities.Statements.ParallelForEach%601>.  
  
- Aktivity pro manipulaci s členská data, jako například <xref:System.Activities.Statements.Assign> a kolekce aktivity, jako <xref:System.Activities.Statements.AddToCollection%601>.  
  
- Aktivity řízení transakce, jako například <xref:System.Activities.Statements.TransactionScope> a <xref:System.Activities.Statements.Compensate>.  
  
- Nové aktivity zasílání zpráv, jako <xref:System.ServiceModel.Activities.SendContent> a <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Datový Model explicitní aktivity  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] obsahuje nové možnosti pro ukládání nebo při přenosech dat. Data mohou být uložena v aktivity pomocí <xref:System.Activities.Variable>. Při přesouvání dat do a z aktivity, typy argumentů specializované slouží k určení, která data směr pohybuje. Tyto typy jsou <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, a <xref:System.Activities.OutArgument>. Další informace najdete v tématu [Windows Workflow Foundation Data Model](data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Rozšířená hostování, stálost a možnosti sledování  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] obsahuje vylepšení trvalost, jako je následující:  
  
- Více možností pro spouštění pracovních postupů, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, a <xref:System.Activities.WorkflowInvoker>.  
  
- Data o stavu pracovního postupu můžete nastavit explicitně jako trvalý, pomocí <xref:System.Activities.Statements.Persist> aktivity.  
  
- Dá se zachovat hostitele <xref:System.Activities.ActivityInstance> bez uvolnění ho.  
  
- Můžete zadat pracovního postupu bez zachování zóny při práci s daty, která nelze nastavit jako trvalý, takže trvalosti je odložit, dokud zóně no-persist ukončí.  
  
- Transakce mohou být předávány do pracovního postupu pomocí <xref:System.Activities.Statements.TransactionScope>.  
  
- Sledování se snadno provádí pomocí <xref:System.Activities.Tracking.TrackingParticipant>.  
  
- Sledování do protokolu událostí systému je prováděno pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
- Obnovení čekající pracovního postupu je teď spravovaná pomocí <xref:System.Activities.Bookmark> objektu.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Snazší možnost rozšíření prostředí Návrháře pracovního postupu  
 Nové Návrháře pracovního postupu je založená na Windows Presentation Foundation (WPF) nabízí jednodušší model pro použití při změna hostování návrháře pracovního postupu mimo sadu Visual Studio a poskytuje také snazší mechanismy pro vytvoření vlastní návrháři aktivit. Další informace najdete v tématu [Kustomizace možností návrhu pracovního postupu](customizing-the-workflow-design-experience.md).
