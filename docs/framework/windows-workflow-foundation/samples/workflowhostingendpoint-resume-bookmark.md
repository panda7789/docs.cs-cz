---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 5c3c996a73d8f88e925d459fae3eb785996eada4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340539"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Záložka pro obnovení WorkflowHostingEndpoint
Tato ukázka předvádí, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jde použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>,  <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> představuje rozšíření bod pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> , který lze použít v následujících scénářích:  
  
-   Vytvoření nové instance pracovního postupu.  
  
-   Obnovení záložky pro instanci pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Ukázka koncového bodu, který je součástí zpřístupňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vracet ID instance, nebo vytvořit instanci s konkrétním ID. Vytvoří ukázkovou aplikaci konzoly <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance s definicí základní pracovní postup a přidá `CreationEndpoint` k hostiteli. Poté zavolá `Create` operace na koncový bod pro vytvoření nové instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. `CreationEndpoint` Konzoly zobrazuje zprávu, která obsahuje instance ID, když je vytvořena instance pracovního postupu. Zprávu "Hello World!" je vytištěna v pracovním postupu na úspěšné obnovení záložky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
