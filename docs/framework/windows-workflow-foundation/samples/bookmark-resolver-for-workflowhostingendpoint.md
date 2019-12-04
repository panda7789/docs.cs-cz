---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 99371cc64ca2790bec383b4ab5dca280d4bb9659
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716755"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Překladač záložek pro WorkflowHostingEndpoint
Tato ukázka předvádí, jak lze <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytváření instancí pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint><xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Účely  
 V této ukázce se používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytváření instancí pracovních postupů hostovaných pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> je bod rozšíření pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>, který se dá použít v těchto scénářích:  
  
- Vytváření nových instancí pracovního postupu.  
  
- Obnovování záložek v instanci pracovního postupu hostované ve <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrátí ID instance nebo vytvoří instanci s určitým ID. Ukázková Konzolová aplikace vytvoří instanci <xref:System.ServiceModel.Activities.WorkflowServiceHost> s definicí pracovního postupu a přidá `CreationEndpoint` k hostiteli. Pak na koncovém bodu zavolá operaci `Create` a vytvoří novou instanci pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. Konzola `CreationEndpoint` zobrazuje zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu. Zpráva "Hello World!" je vytištěna instancí pracovního postupu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
