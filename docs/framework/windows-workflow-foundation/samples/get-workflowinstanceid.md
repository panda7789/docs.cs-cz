---
title: Získání WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204318"
---
# <a name="get-workflowinstanceid"></a>Získání WorkflowInstanceId
Tato ukázka předvádí, jak používat vlastní aktivitu, `GetWorkflowInstanceId` vrátit identifikátor instance pracovního postupu  
  
## <a name="demonstrates"></a>Demonstruje  
 Vývoj vlastních aktivit, jak získat přístup k instanci pracovního postupu.  
  
## <a name="discussion"></a>Diskuse  
 ID instance s běžícím workflowem potřeba psát kód. Pokud chcete k vytvoření plně deklarativního pracovního postupu, musíte aktivitu, která vrací ID instance pracovního postupu tak, aby aktivita může být odkazováno v pracovním postupu poskytnout plně deklarativního prostředí pro tvorbu pracovního postupu. Mnoho scénářů vyžadují přístup k instance ID: několik příkladů jsou pro protokolování nebo auditování nebo zadáním instance ID zpátky do klienta pro budoucí přidružení plnit korelace úrovni aplikace (například pomocí tato aktivita uvnitř Aktivitu odeslání odpovědi SendReply).  
  
 `GetWorkflowInstanceId` je implementován jako <xref:System.Activities.CodeActivity%601> vzhledem k tomu, že musí vracet hodnotu typu <xref:System.Guid>, a musí mít přístup k <xref:System.Activities.CodeActivityContext> pro získání pracovního postupu instance ID. Jeho implementace je poměrně základní.  
  
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
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
