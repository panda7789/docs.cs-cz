---
title: Získání WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 37dc0cac9c6ac69b9e430677a9c8cf3f47b200eb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716023"
---
# <a name="get-workflowinstanceid"></a>Získání WorkflowInstanceId
Tato ukázka předvádí, jak použít vlastní aktivitu `GetWorkflowInstanceId` k vrácení ID instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vývoj vlastních aktivit, jak získat přístup k instanci pracovního postupu.  
  
## <a name="discussion"></a>Účely  
 Získání ID instance spuštěného pracovního postupu vyžaduje zápis kódu. Chcete-li napsat plně deklarativní pracovní postup, budete potřebovat aktivitu, která může vrátit ID instance pracovního postupu, aby mohla být na aktivitu odkazována v pracovním postupu, aby poskytovala plně deklarativní prostředí pro vytváření pracovních postupů. Řada scénářů vyžaduje přístup k ID instance: několik příkladů je pro účely protokolování nebo auditování nebo pro korelaci na úrovni aplikace poskytnutím ID instance back klientovi pro budoucí přidružení (například pomocí této aktivity uvnitř Aktivita SendReply).  
  
 `GetWorkflowInstanceId` je implementován jako <xref:System.Activities.CodeActivity%601>, protože musí vracet hodnotu typu <xref:System.Guid>a musí mít přístup k <xref:System.Activities.CodeActivityContext> pro získání ID instance pracovního postupu. Jeho implementace je poměrně základní.  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
