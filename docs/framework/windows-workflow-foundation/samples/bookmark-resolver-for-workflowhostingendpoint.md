---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 4676b3c624a7ba1539a7a12ed38c286f688dcf9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344289"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Překladač záložek pro WorkflowHostingEndpoint
Tato ukázka předvádí, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jde použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> vytvořit hostované pomocí instancí pracovních postupů <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> představuje rozšíření bod pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> , který lze použít v následujících scénářích:  
  
-   Vytvoření nové instance pracovního postupu.  
  
-   Obnovení záložky pro instanci pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Ukázka koncového bodu, který je součástí zpřístupňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrátí instance ID nebo vytvoří instanci s konkrétním ID. Vytvoří ukázkovou aplikaci konzoly <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance s definicí pracovního postupu a přidá `CreationEndpoint` k hostiteli. Poté zavolá `Create` operace na koncový bod pro vytvoření nové instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. `CreationEndpoint` Konzoly zobrazuje zprávu, která obsahuje instance ID, když je vytvořena instance pracovního postupu. Zprávu "Hello World!" tištěné instance pracovního postupu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
