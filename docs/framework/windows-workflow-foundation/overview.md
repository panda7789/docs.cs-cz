---
title: Přehled Windows Workflow
description: Tento článek popisuje pracovní postupy modelu Workflow Foundation, které jsou modely, které popisují reálné procesy.
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: ec1a00b37abe2cb842735fb98e1c113a97943758
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421472"
---
# <a name="windows-workflow-overview"></a>Přehled Windows Workflow
Pracovní postup je sada jednotek prvků s názvem *aktivity* , které se ukládají jako model, který popisuje reálný proces. Pracovní postupy představují způsob, jak popsat pořadí spouštění a závislé vztahy mezi částmi krátkodobé nebo dlouhodobé práce. Tato práce prochází modelem od začátku do konce a aktivity můžou provádět lidé nebo funkce systému.  
  
## <a name="workflow-run-time-engine"></a>Běhový modul workflowu  
 Každá spuštěná instance pracovního postupu je vytvořena a udržována modulem runtime spouštěným v procesu, který komunikuje s hostitelským procesem pomocí jedné z následujících možností:  
  
- A <xref:System.Activities.WorkflowInvoker> , který vyvolá pracovní postup, jako je metoda.  
  
- <xref:System.Activities.WorkflowApplication>Pro explicitní kontrolu nad prováděním jedné instance pracovního postupu.  
  
- <xref:System.ServiceModel.WorkflowServiceHost>Pro interakce založené na zprávách ve scénářích s více instancemi.  
  
 Každá z těchto tříd balí modul runtime základní aktivity představovaný jako <xref:System.Activities.ActivityInstance> zodpovědný za spuštění aktivity. <xref:System.Activities.ActivityInstance>V doméně aplikace může běžet několik objektů současně.  
  
 Každý z předchozích tří objektů interakce hostitele je vytvořen ze stromové struktury aktivit, které jsou označovány jako program pracovního postupu. Pomocí těchto typů nebo vlastního hostitele, který zabalíte <xref:System.Activities.ActivityInstance> , můžete pracovní postupy spustit v jakémkoli procesu systému Windows, včetně konzolových aplikací, aplikací založených na formulářích, služeb systému Windows, webů ASP.NET a služeb Windows Communication Foundation (WCF).  
  
 ![Komponenty pracovního postupu v hostitelském procesu](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Komponenty pracovního postupu v hostitelském procesu  
  
## <a name="interaction-between-workflow-components"></a>Interakce mezi komponentami pracovního postupu  
 Následující diagram znázorňuje, jak komponenty pracovního postupu vzájemně komunikují.  
  
 ![Diagram, který ukazuje, jak komponenty pracovního postupu pracují.](./media/overview/workflow-component-interatction.gif)  
  
 V předchozím diagramu <xref:System.Activities.WorkflowInvoker.Invoke%2A> <xref:System.Activities.WorkflowInvoker> je metoda třídy použita k vyvolání několika instancí pracovního postupu. <xref:System.Activities.WorkflowInvoker>se používá pro zjednodušené pracovní postupy, které nepotřebují správu od hostitele. pracovní postupy, které vyžadují správu od hostitele (například obnovení <xref:System.Activities.Bookmark> ), musí být spuštěny pomocí <xref:System.Activities.WorkflowApplication.Run%2A> místo toho. Před vyvoláním jiného není nutné čekat na dokončení jedné instance pracovního postupu. Běhový modul podporuje souběžné spouštění více instancí pracovního postupu.  Vyvolané pracovní postupy jsou následující:  
  
- <xref:System.Activities.Statements.Sequence>Aktivita, která obsahuje <xref:System.Activities.Statements.WriteLine> podřízenou aktivitu. <xref:System.Activities.Variable>Nadřazená aktivita je svázána s <xref:System.Activities.InArgument> podřízenou aktivitou. Další informace o proměnných, argumentech a vazbách naleznete v tématu [Variables a Arguments](variables-and-arguments.md).  
  
- Vlastní aktivita se nazývá `ReadLine` . <xref:System.Activities.OutArgument> `ReadLine` Aktivita se vrátí volající <xref:System.Activities.WorkflowInvoker.Invoke%2A> metodě.  
  
- Vlastní aktivita, která je odvozena z <xref:System.Activities.CodeActivity> abstraktní třídy. <xref:System.Activities.CodeActivity>Může přistupovat k funkcím modulu runtime (například ke sledování a vlastnostem) pomocí <xref:System.Activities.CodeActivityContext> , který je k dispozici jako parametr <xref:System.Activities.CodeActivity.Execute%2A> metody. Další informace o těchto funkcích runtime najdete v tématu [sledování pracovních postupů a trasování](workflow-tracking-and-tracing.md) a [Vlastnosti spuštění pracovního postupu](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Viz také

- [BizTalk Server 2006 nebo WF? Výběr správného nástroje pro pracovní postup pro váš projekt](https://docs.microsoft.com/previous-versions/dotnet/articles/cc303238(v=msdn.10))
