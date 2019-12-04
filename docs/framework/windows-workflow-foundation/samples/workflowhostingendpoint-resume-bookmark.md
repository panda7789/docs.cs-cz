---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3b3c7d40a70e797960837c82e2f5a08b2814e17f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710964"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Záložka pro obnovení WorkflowHostingEndpoint
Tato ukázka předvádí, jak lze <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytváření instancí pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint><xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Účely  
 Tato ukázka používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostovaného pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> je bod rozšíření pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>, který se dá použít v těchto scénářích:  
  
- Vytváření nových instancí pracovního postupu.  
  
- Obnovování záložek v instanci pracovního postupu hostované ve <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrácení ID instance nebo vytvoření instance s určitým ID. Ukázková Konzolová aplikace vytvoří instanci <xref:System.ServiceModel.Activities.WorkflowServiceHost> se základní definicí pracovního postupu a přidá `CreationEndpoint` k hostiteli. Pak na koncovém bodu zavolá operaci `Create` a vytvoří novou instanci pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. Konzola `CreationEndpoint` zobrazuje zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu. Zpráva "Hello World!" je vytištěn pracovním postupem po úspěšném obnovení záložky.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
