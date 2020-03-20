---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182746"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Záložka pro obnovení WorkflowHostingEndpoint
Tato ukázka ukazuje, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak <xref:System.ServiceModel.Activities.WorkflowServiceHost> lze použít s k vytvoření instancí pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> používá k vytvoření instance <xref:System.ServiceModel.Activities.WorkflowServiceHost>pracovního postupu hostované pomocí . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který lze použít v následujících scénářích:  
  
- Vytváření nových instancí pracovního postupu.  
  
- Obnovení záložek na instanci pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost>postupu hostované v aplikaci .  
  
 Ukázkový koncový bod, který je součástí zpřístupňuje smlouvu, která poskytuje operace k vytvoření pracovního postupu a vrácení ID instance nebo k vytvoření instance s určitým ID. Ukázková konzolová <xref:System.ServiceModel.Activities.WorkflowServiceHost> aplikace vytvoří instanci se `CreationEndpoint` základní definicí pracovního postupu a přidá k hostiteli. Potom volá `Create` operaci v koncovém bodě k vytvoření nové instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. Konzola `CreationEndpoint` zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu. Zpráva "Hello World!" je vytištěn pracovním postupem při úspěšném obnovení záložky.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
