---
title: Přehled Windows Workflow
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: ada5ec75d130c9c518c5129db6c12b61c3acbf45
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802528"
---
# <a name="windows-workflow-overview"></a>Přehled Windows Workflow
Pracovní postup je sada jednotek prvků s názvem *aktivity* , které se ukládají jako model, který popisuje reálný proces. Pracovní postupy představují způsob, jak popsat pořadí spouštění a závislé vztahy mezi částmi krátkodobé nebo dlouhodobé práce. Tato práce prochází modelem od začátku do konce a aktivity můžou provádět lidé nebo funkce systému.  
  
## <a name="workflow-run-time-engine"></a>Běhový modul workflowu  
 Každá spuštěná instance pracovního postupu je vytvořena a udržována modulem runtime spouštěným v procesu, který komunikuje s hostitelským procesem pomocí jedné z následujících možností:  
  
- <xref:System.Activities.WorkflowInvoker>, který vyvolá pracovní postup, jako je metoda.  
  
- <xref:System.Activities.WorkflowApplication> pro explicitní kontrolu nad prováděním jedné instance pracovního postupu.  
  
- <xref:System.ServiceModel.WorkflowServiceHost> pro interakce založené na zprávách ve scénářích s více instancemi.  
  
 Každá z těchto tříd balí modul runtime základní aktivity reprezentovaný jako <xref:System.Activities.ActivityInstance> zodpovědný za spuštění aktivity. V doméně aplikace může běžet několik <xref:System.Activities.ActivityInstance> objektů současně.  
  
 Každý z předchozích tří objektů interakce hostitele je vytvořen ze stromové struktury aktivit, které jsou označovány jako program pracovního postupu. Pomocí těchto typů nebo vlastního hostitele, který zabalí <xref:System.Activities.ActivityInstance>, lze pracovní postupy spustit v jakémkoli procesu systému Windows, včetně konzolových aplikací, aplikací založených na formulářích, služeb systému Windows, webů ASP.NET a služeb Windows Communication Foundation (WCF).  
  
 ![Komponenty pracovního postupu v hostitelském procesu](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Komponenty pracovního postupu v hostitelském procesu  
  
## <a name="interaction-between-workflow-components"></a>Interakce mezi komponentami pracovního postupu  
 Následující diagram znázorňuje, jak komponenty pracovního postupu vzájemně komunikují.  
  
 ![Diagram, který ukazuje, jak komponenty pracovního postupu pracují.](./media/overview/workflow-component-interatction.gif)  
  
 V předchozím diagramu je metoda <xref:System.Activities.WorkflowInvoker.Invoke%2A> <xref:System.Activities.WorkflowInvoker> třídy použita k vyvolání několika instancí pracovního postupu. <xref:System.Activities.WorkflowInvoker> se používá pro zjednodušené pracovní postupy, které nepotřebují správu od hostitele. pracovní postupy, které vyžadují správu od hostitele (například <xref:System.Activities.Bookmark> obnovení), je třeba spustit pomocí <xref:System.Activities.WorkflowApplication.Run%2A>. Před vyvoláním jiného není nutné čekat na dokončení jedné instance pracovního postupu. Běhový modul podporuje souběžné spouštění více instancí pracovního postupu.  Vyvolané pracovní postupy jsou následující:  
  
- <xref:System.Activities.Statements.Sequence> aktivita obsahující <xref:System.Activities.Statements.WriteLine> podřízenou aktivitu. <xref:System.Activities.Variable> nadřazené aktivity je vázán na <xref:System.Activities.InArgument> podřízené aktivity. Další informace o proměnných, argumentech a vazbách naleznete v tématu [Variables a Arguments](variables-and-arguments.md).  
  
- Vlastní aktivita s názvem `ReadLine`. Volajícímu <xref:System.Activities.WorkflowInvoker.Invoke%2A> metodu vrátí <xref:System.Activities.OutArgument> `ReadLine` aktivity.  
  
- Vlastní aktivita odvozená z <xref:System.Activities.CodeActivity> abstraktní třídy. <xref:System.Activities.CodeActivity> může přistupovat k funkcím modulu runtime (například ke sledování a vlastnostem) pomocí <xref:System.Activities.CodeActivityContext>, který je k dispozici jako parametr metody <xref:System.Activities.CodeActivity.Execute%2A>. Další informace o těchto funkcích runtime najdete v tématu [sledování pracovních postupů a trasování](workflow-tracking-and-tracing.md) a [Vlastnosti spuštění pracovního postupu](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Viz také:

- [BizTalk Server 2006 nebo WF? Výběr správného nástroje pro pracovní postup pro váš projekt](https://docs.microsoft.com/previous-versions/dotnet/articles/cc303238(v=msdn.10))
