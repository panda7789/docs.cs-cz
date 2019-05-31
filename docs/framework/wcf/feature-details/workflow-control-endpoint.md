---
title: Kontrolní koncový bod pracovního postupu
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 781a7cefaeeb8cd9cd21298471c59de2e7815244
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424017"
---
# <a name="workflow-control-endpoint"></a>Kontrolní koncový bod pracovního postupu
Kontrolní koncový bod pracovního postupu umožňuje vývojářům volat operace řízení vzdálené řízení hostované pomocí instancí pracovních postupů <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Tato funkce slouží k provádění operací správy, jako je pozastavení, obnovení a ukončit prostřednictvím kódu programu.  
  
> [!WARNING]
>  Pokud koncový bod pracovního postupu ovládací prvek v rámci transakce a pracovní postup je řízen pomocí obsahuje <xref:System.Activities.Statements.Persist> aktivity, instance pracovního postupu bude blokovat, dokud transakce vyprší časový limit.  
  
## <a name="workflow-instance-management"></a>Správa instancí pracovního postupu  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Definuje novou smlouvu volá <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Tento kontrakt definuje řadu ovládacího prvku operace, které vám umožní vzdálené řízení instancí pracovních postupů, které jsou hostovány <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> je standardní koncový bod, který poskytuje implementaci <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu. <xref:System.ServiceModel.Activities.WorkflowControlClient> je třída, která se používá k odeslání operace ovládacího prvku, které se <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Instance pracovního postupu může být v jednom z následujících stavů:  
  
 Aktivní  
 Stav instance pracovního postupu předtím, než dosáhne stavu dokončení a když to není v pozastaveném stavu. V tomto stavu instance pracovního postupu spuštěn a zpracovává zprávy aplikace.  
  
 Dočasně blokován.  
 V tomto stavu instance pracovního postupu nejde spustit i v případě, že existují aktivity, které nebyly spuštěny, spuštění nebo částečně spuštěny.  
  
 Byla dokončena  
 Konečný stav instance pracovního postupu. Po dosažení dokončeného stavu nelze spustit instanci pracovního postupu.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Rozhraní definuje sadu operací řízení verzí synchronní a asynchronní. Počet zrušených zpracovaných verze vyžadují použití s ohledem na transakce vazby. Následující tabulka uvádí podporované operace ovládacího prvku.  
  
|Operace správy|Popis|  
|-----------------------|-----------------|  
|Přerušení|Vynuceně zastaví spuštění instance pracovního postupu.|  
|Zrušit|Přejde do dokončeného stavu instance pracovního postupu ze stavu aktivní nebo se pozastavuje.|  
|Spustit|Představuje příležitost ke spuštění instance pracovního postupu.|  
|Pozastavit|Převede instanci pracovního postupu ze stavu Aktivní do pozastaveného stavu.|  
|ukončit|Přejde do dokončeného stavu instance pracovního postupu ze stavu aktivní nebo se pozastavuje.|  
|Zrušit pozastavení účtu uživatele|Přechází do stavu aktivní instance pracovního postupu v pozastaveném stavu.|  
|TransactedCancel|Provede operaci zrušit v rámci transakce (byla převedena z klienta nebo vytváření místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být instance pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedRun|Provede operaci spustit v rámci transakce (byla převedena z klienta nebo vytváření místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být instance pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedSuspend|Provede operaci pozastavení v rámci transakce (byla převedena z klienta nebo vytváření místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být instance pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedTerminate|Provádí operace ukončení v rámci transakce (byla převedena z klienta nebo vytváření místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být instance pracovního postupu jako trvalý, během provádění této operace.|  
|TransactedUnsuspend|Provede operaci zrušit pozastavení v rámci transakce (byla převedena z klienta nebo vytváření místně). Pokud systém udržuje trvalého stavu instance pracovního postupu, musí být instance pracovního postupu jako trvalý, během provádění této operace.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Smlouvy neposkytuje prostředek pro vytvoření nové instance pracovního postupu, jenom ke správě existující instance pracovního postupu. Další informace o vzdálené vytvoření nové instance pracovního postupu najdete v tématu [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> je standardní koncový bod s pevnou smlouvy <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Když se přidá <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance tohoto koncového bodu může pak použije k odesílání příkazu operace do jakékoli instance pracovního postupu, který je hostitelem instance hostitele. Další informace o standardních koncových bodů najdete v tématu [standardních koncových bodů](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> je třída, která umožňuje odesílání ovládacího prvku <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> na <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Obsahuje metody pro každou operací podporované <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu s výjimkou počet zrušených zpracovaných operací. <xref:System.ServiceModel.Activities.WorkflowControlClient> okolí transakce používá k určení, zda by měl být použit počet zrušených zpracovaných operací.
