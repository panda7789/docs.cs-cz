---
title: Získání WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142729"
---
# <a name="get-workflowinstanceid"></a>Získání WorkflowInstanceId
Tato ukázka ukazuje, jak použít `GetWorkflowInstanceId` vlastní aktivitu, chcete-li vrátit ID instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vlastní vývoj aktivit, jak získat přístup k instanci pracovního postupu.  
  
## <a name="discussion"></a>Diskuse  
 Získání ID instance spuštěného pracovního postupu vyžaduje psaní kódu. Pokud chcete napsat plně deklarativní pracovní postup, potřebujete aktivitu, která může vrátit ID instance pracovního postupu, aby na aktivitu bylo možné odkazovat v pracovním postupu a poskytnout tak plně deklarativní prostředí pro vytváření pracovního postupu. Mnoho scénářů vyžaduje přístup k ID instance: několik příkladů je pro účely protokolování nebo auditování nebo pro korelaci na úrovni aplikace poskytnutím ID instance zpět klientovi pro budoucí přidružení (například pomocí této aktivity uvnitř SendReply).  
  
 `GetWorkflowInstanceId`je implementována jako, <xref:System.Activities.CodeActivity%601> protože musí <xref:System.Guid>vrátit hodnotu typu <xref:System.Activities.CodeActivityContext> a musí mít přístup k získání ID instance pracovního postupu. Jeho realizace je poměrně základní.  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
