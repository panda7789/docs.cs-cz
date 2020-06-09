---
title: Kontrolní koncový bod pracovního postupu
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 91923129235a596e4fa19a8e5982845a25db9712
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594917"
---
# <a name="workflow-control-endpoint"></a>Kontrolní koncový bod pracovního postupu
Koncový bod řízení pracovního postupu umožňuje vývojářům volat operace řízení pro vzdálené řízení instancí pracovních postupů hostovaných pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Tato funkce se dá použít k programovému provádění operací řízení, jako je pozastavení, obnovení a ukončení.  
  
> [!WARNING]
> Pokud používáte řídicí koncový bod pracovního postupu v rámci transakce a řízený pracovní postup obsahuje <xref:System.Activities.Statements.Persist> aktivitu, instance pracovního postupu se zablokuje, dokud nevyprší časový limit transakce.  
  
## <a name="workflow-instance-management"></a>Správa instancí pracovního postupu  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Definuje novou kontrakt s názvem <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> . Tato Smlouva definuje řadu operací řízení, které umožňují vzdáleně řídit instance pracovních postupů, které hostuje <xref:System.ServiceModel.Activities.WorkflowServiceHost> . <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>je standardní koncový bod, který poskytuje implementaci <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> kontraktu. <xref:System.ServiceModel.Activities.WorkflowControlClient>je třída, která slouží k odeslání operací ovládacího prvku do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> .  
  
 Instance pracovního postupu můžou být v jednom z následujících stavů:  
  
 Aktivní  
 Stav instance pracovního postupu před tím, než dosáhne stavu dokončeno, a když není v pozastaveném stavu. V tomto stavu instance pracovního postupu spouští a zpracovává zprávy aplikací.  
  
 Dočasně blokován.  
 V tomto stavu se instance pracovního postupu nespustí ani v případě, že dojde k aktivitám, které nezačaly běžet nebo byly částečně spuštěny.  
  
 Dokončeno  
 Konečný stav instance pracovního postupu. Po dosažení stavu dokončení nelze instanci pracovního postupu spustit.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>Rozhraní definuje sadu operací řízení s synchronními a asynchronními verzemi. Verze v transakčním systému vyžadují použití vazby zohledňující transakci. V následující tabulce jsou uvedeny podporované operace ovládacího prvku.  
  
|Operace řízení|Popis|  
|-----------------------|-----------------|  
|Přerušení|Vynuceně zastaví provádění instance pracovního postupu.|  
|Zrušit|Přepřechoduje instanci pracovního postupu z aktivního nebo pozastaveného stavu do stavu dokončeno.|  
|Spustit|Poskytuje instanci pracovního postupu, kterou je možné provést.|  
|Suspend|Převede instanci pracovního postupu z aktivního stavu do pozastaveného stavu.|  
|Terminate|Přepřechoduje instanci pracovního postupu z aktivního nebo pozastaveného stavu do stavu dokončeno.|  
|Zrušit pozastavení účtu|Převede instanci pracovního postupu z pozastaveného stavu do stavu aktivní.|  
|TransactedCancel|Provede operaci zrušení v rámci transakce (v toku z klienta nebo v místním prostředí). Pokud systém udržuje trvalý stav instance pracovního postupu, během provádění této operace musí být instance pracovního postupu trvalá.|  
|TransactedRun|Provede operaci spuštění v rámci transakce (Flow z klienta nebo vytvořená místně). Pokud systém udržuje trvalý stav instance pracovního postupu, během provádění této operace musí být instance pracovního postupu trvalá.|  
|TransactedSuspend|Provede operaci pozastavit v rámci transakce (v toku z klienta nebo vytvořená místně). Pokud systém udržuje trvalý stav instance pracovního postupu, během provádění této operace musí být instance pracovního postupu trvalá.|  
|TransactedTerminate|Provede operaci ukončení v rámci transakce (v toku z klienta nebo v místním prostředí). Pokud systém udržuje trvalý stav instance pracovního postupu, během provádění této operace musí být instance pracovního postupu trvalá.|  
|TransactedUnsuspend|Provede operaci zrušení pozastavení v rámci transakce (v toku z klienta nebo v místním prostředí). Pokud systém udržuje trvalý stav instance pracovního postupu, během provádění této operace musí být instance pracovního postupu trvalá.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>Kontrakt neposkytuje způsob, jak vytvořit novou instanci pracovního postupu, a to pouze za účelem správy existujících instancí pracovního postupu. Další informace o vzdáleném vytvoření nové instance pracovního postupu najdete v tématu [rozšiřitelnost hostitele služby pracovního postupu](workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>je standardní koncový bod s pevným kontraktem <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> . Po přidání do <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance je možné tento koncový bod použít k odeslání operací příkazů do jakékoli instance pracovního postupu hostované instancí hostitele. Další informace o standardních koncových bodech naleznete v tématu [Standardní koncové body](standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient>je třída, která umožňuje odeslat řídicí zprávy do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> v <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Obsahuje metodu pro každou operaci podporovanou <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> smlouvou s výjimkou operací s podporou transakcí. <xref:System.ServiceModel.Activities.WorkflowControlClient>Používá ambientní transakci k určení, zda by měla být použita transakční operace.
