---
title: Záložka pro obnovení WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 83065a0034303dcbc83f846ba455f71e954fdb54
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037769"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Záložka pro obnovení WorkflowHostingEndpoint
Tato ukázka předvádí, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak lze použít s <xref:System.ServiceModel.Activities.WorkflowServiceHost> k vytvoření instancí pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Účely  
 Tato ukázka používá <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k vytvoření instance pracovního postupu hostovaného pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>je bod <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozšiřitelnosti, který může být použit v následujících situacích:  
  
- Vytváření nových instancí pracovního postupu.  
  
- Obnovování záložek v instanci pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Vzorový koncový bod, který je součástí, zveřejňuje kontrakt, který poskytuje operace pro vytvoření pracovního postupu a vrácení ID instance nebo vytvoření instance s určitým ID. Ukázková Konzolová aplikace vytvoří <xref:System.ServiceModel.Activities.WorkflowServiceHost> instanci se základní definicí pracovního postupu a `CreationEndpoint` přidá do hostitele. Pak zavolá `Create` operaci na koncovém bodu a vytvoří novou instanci pracovního postupu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte řešení.  
  
2. Spusťte aplikaci. `CreationEndpoint` Konzola zobrazí zprávu, která obsahuje ID instance při vytvoření instance pracovního postupu. Zpráva "Hello World!" je vytištěn pracovním postupem po úspěšném obnovení záložky.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
