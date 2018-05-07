---
title: BOOKMARK překladač pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: f8afb804525ecf36127e32441c92f43af70f5099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>BOOKMARK překladač pro WorkflowHostingEndpoint
Tento příklad ukazuje, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskusní  
 V tomto příkladu <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovních postupů, které jsou hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> je bod rozšiřitelnosti pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> které lze použít v následujících scénářích:  
  
-   Vytvoření nové instance pracovního postupu.  
  
-   Záložky na instanci pracovního postupu obnovení hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Ukázka koncového bodu, který je součástí zpřístupní kontrakt, který obsahuje operace vytvoření pracovního postupu a vrátí instance ID nebo vytvoří instanci s konkrétním ID. Vytvoří ukázkovou aplikaci konzoly <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci s definicí pracovního postupu a přidá `CreationEndpoint` na hostitele. Potom zavolá `Create` operace na koncový bod pro vytvoření nové instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení.  
  
2.  Spusťte aplikaci. `CreationEndpoint` Konzola zobrazí zprávu, která zahrnuje instance ID při vytvoření instance pracovního postupu. Zpráva "Hello, World!" je tištěné k instanci pracovního postupu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
