---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142807"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Překladač záložek pro WorkflowHostingEndpoint
Tato ukázka ukazuje, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak <xref:System.ServiceModel.Activities.WorkflowServiceHost> lze použít s k vytvoření instancí pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> používá k vytvoření instancí pracovního postupu hostovaných pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>aplikace . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který lze použít v následujících scénářích:  
  
- Vytváření nových instancí pracovního postupu.  
  
- Obnovení záložek v instanci pracovního postupu hostované v aplikaci <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Ukázkový koncový bod, který je součástí zpřístupňuje smlouvu, která poskytuje operace k vytvoření pracovního postupu a vrátí ID instance nebo vytvoří instanci s určitým ID. Ukázková konzolová <xref:System.ServiceModel.Activities.WorkflowServiceHost> aplikace vytvoří instanci `CreationEndpoint` s definicí pracovního postupu a přidá a k hostiteli. Potom volá `Create` operaci v koncovém bodě k vytvoření nové instance pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. Konzola `CreationEndpoint` zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu. Zpráva "Hello World!" je vytištěna instancí pracovního postupu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
