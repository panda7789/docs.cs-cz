---
title: "Kontrolní koncový bod pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5894a8b5d4d0873a231927498a8d1e2c4e18afd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-control-endpoint"></a>Kontrolní koncový bod pracovního postupu
Kontrolní koncový bod pracovního postupu umožňuje vývojářům volat operace ovládacího prvku vzdálené řízení instancí pracovních postupů, které jsou hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Tato funkce slouží k prostřednictvím kódu programu provádění operací řízení jako pozastavení, obnovení a ukončení.  
  
> [!WARNING]
>  Pokud pomocí kontrolní koncový bod pracovního postupu v rámci transakce a pracovní postup se řídí obsahuje <xref:System.Activities.Statements.Persist> aktivity, instance pracovního postupu se zablokuje, dokud transakce časového limitu.  
  
## <a name="workflow-instance-management"></a>Správa instancí pracovního postupu  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Definuje novou smlouvu názvem <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Tento kontrakt definuje řady řízení operace, které vám umožňují vzdáleně ovládat instancí pracovních postupů, které jsou hostované <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>je standardní koncový bod, který představuje implementaci objektu <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontrakt. <xref:System.ServiceModel.Activities.WorkflowControlClient>je třída, která se používá k odeslání operace ovládacího prvku na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Instance pracovního postupu může být v jednom z následujících stavů:  
  
 Aktivní  
 Stav instance pracovního postupu před dosažením stavu dokončení, a pokud není v pozastaveném stavu. V tomto stavu instance pracovního postupu spustí a zpracuje zprávy o aplikaci.  
  
 Dočasně blokován.  
 V tomto stavu instance pracovního postupu nejde spustit i v případě, že existují aktivity, které nebyly spuštění nebo částečně spustili.  
  
 Byla dokončena  
 Poslední stav instance pracovního postupu. Instance pracovního postupu nelze spustit po dosažení stavu dokončení.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Rozhraní definuje sadu s verzemi synchronní a asynchronní operace u ovládacího prvku. Zpracované verze vyžadují použití deklaracemi transakce vazby. Následující tabulka uvádí operace ovládacího prvku podporována.  
  
|Operace ovládací prvek|Popis|  
|-----------------------|-----------------|  
|Přerušení|Vynuceně zastaví provádění k instanci pracovního postupu.|  
|Zrušit|Přechází do stavu dokončení instanci pracovního postupu z aktivní nebo pozastaveném stavu.|  
|Spustit|Poskytuje možnost spustit instanci pracovního postupu.|  
|Pozastavit|Přejde do režimu spánku instanci pracovního postupu z aktivním stavu.|  
|Ukončení|Přechází do stavu dokončení instanci pracovního postupu z aktivní nebo pozastaveném stavu.|  
|Zrušit pozastavení účtu|Přechází instance pracovního postupu z režimu spánku aktivním stavu.|  
|TransactedCancel|Provede operace zrušení v transakci (v plynoucích z klienta nebo vytvoří místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být k instanci pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedRun|Provede operaci spustit v transakci (v plynoucích z klienta nebo vytvoří místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být k instanci pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedSuspend|Provede operaci pozastavit v transakci (v plynoucích z klienta nebo vytvoří místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být k instanci pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedTerminate|Provede operace ukončení v transakci (v plynoucích z klienta nebo vytvoří místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být k instanci pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedUnsuspend|Provede operaci Unsuspend v rámci transakce (v plynoucích z klienta nebo vytvoří místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být k instanci pracovního postupu jako trvalý, během provádění této operace.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Kontrakt neposkytuje prostředky k vytvoření nové instance pracovního postupu, pouze ke správě existující instance pracovního postupu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vzdáleně vytvoření nové instance pracovního postupu, najdete v části [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>je standardní koncový bod s pevnou kontraktu, <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Když je přidán do <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance, to může koncový bod, pak se používá k odeslání příkazu operace na všechny instance pracovního postupu, který je hostitelem instance hostitele. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Standardní koncové body, najdete v části [standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient>je třída, která umožňuje odesílání zpráv řízení <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> na <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Obsahuje metody pro každou operací podporované <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontrakt s výjimkou zpracovaných operací. <xref:System.ServiceModel.Activities.WorkflowControlClient>vedlejším transakce se používá k určení, zda má být použita zpracovaných operaci.
