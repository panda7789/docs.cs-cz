---
title: Obnovit WorkflowHostingEndpoint záložek
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3af31af17e0c362beb8ba4b9b0479de59cab8ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Obnovit WorkflowHostingEndpoint záložek
Tento příklad ukazuje, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskusní  
 V tomto příkladu <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> je bod rozšiřitelnosti pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> které lze použít v následujících scénářích:  
  
-   Vytvoření nové instance pracovního postupu.  
  
-   Záložky na instanci pracovního postupu obnovení hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Ukázka koncového bodu, který je součástí zpřístupní kontrakt, který obsahuje operace vytvoření pracovního postupu a vrátíte se ID instance nebo pro vytvoření instance s konkrétním ID. Vytvoří ukázkovou aplikaci konzoly <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci s definicí základní pracovní postup a přidá `CreationEndpoint` na hostitele. Potom zavolá `Create` operace na koncový bod pro vytvoření nové instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení.  
  
2.  Spusťte aplikaci. `CreationEndpoint` Konzola zobrazí zprávu, která zahrnuje instance ID při vytvoření instance pracovního postupu. Zpráva "Hello, World!" je vytištěna v tomto pracovním postupu na úspěšné obnovení záložky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
