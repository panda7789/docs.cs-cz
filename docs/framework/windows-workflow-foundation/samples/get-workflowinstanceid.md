---
title: "Získat WorkflowInstanceId"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f1eb6a1d9cd875d0332bb1d59933f75c807f74e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="get-workflowinstanceid"></a>Získat WorkflowInstanceId
Tento příklad ukazuje, jak použít vlastní aktivity, `GetWorkflowInstanceId` vrátit ID instance pracovního postupu  
  
## <a name="demonstrates"></a>Demonstruje  
 Vývoj vlastní aktivity, jak získat přístup k instanci pracovního postupu.  
  
## <a name="discussion"></a>Diskusní  
 Získávání ID instance s běžícím workflowem vyžaduje psaní kódu. Pokud chcete vytvoření plně deklarativního pracovního postupu, musíte aktivitu, která můžete vrátit zpět ID instance pracovního postupu, může být odkazováno aktivity v pracovním postupu zajistit plně deklarativního pracovního postupu pro tvorbu prostředí. Mnoho scénářů vyžadují přístup k instance ID: několik příkladů pro protokolování nebo auditování účely nebo pro provádění korelace úrovni aplikace poskytnutím instance ID zpět do klienta pro budoucí přidružení (například pomocí této aktivity uvnitř Aktivita SendReply).  
  
 `GetWorkflowInstanceId`je implementovaný jako <xref:System.Activities.CodeActivity%601> protože musí vracet hodnoty typu <xref:System.Guid>, a musí mít přístup k <xref:System.Activities.CodeActivityContext> pro získání pracovního postupu instance ID. Jeho implementace je vcelku jednoduchá.  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
