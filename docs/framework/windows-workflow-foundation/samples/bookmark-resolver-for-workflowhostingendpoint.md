---
title: Překladač záložek pro WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: e5a8adc73ba08007802eeb3b66de27098c688d84
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044331"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Překladač záložek pro WorkflowHostingEndpoint
Tato ukázka předvádí, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instancí pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Účely  
 Tato ukázka používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instancí pracovního postupu hostovaných <xref:System.ServiceModel.Activities.WorkflowServiceHost>pomocí. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který může být použit v následujících situacích:  
  
- Vytváření nových instancí pracovního postupu.  
  
- Obnovování záložek v instanci pracovního postupu hostované <xref:System.ServiceModel.Activities.WorkflowServiceHost>v.  
  
 Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrátí ID instance nebo vytvoří instanci s určitým ID. Ukázková Konzolová aplikace vytvoří <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci s definicí pracovního postupu a `CreationEndpoint` přidá ji do hostitele. Pak zavolá `Create` operaci na koncovém bodu a vytvoří novou instanci pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. `CreationEndpoint` Konzola zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu. Zpráva "Hello World!" je vytištěna instancí pracovního postupu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
