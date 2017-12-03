---
title: "Obnovit WorkflowHostingEndpoint záložek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1179d09d68d8730847776cf98e3996e3e6817753
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Obnovit WorkflowHostingEndpoint záložek
Tento příklad ukazuje, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskusní  
 V tomto příkladu <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod rozšiřitelnosti pro <xref:System.ServiceModel.Activities.WorkflowServiceHost> které lze použít v následujících scénářích:  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
