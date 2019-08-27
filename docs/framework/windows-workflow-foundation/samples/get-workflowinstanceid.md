---
title: Získání WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 73fee4376b1abe29620bfae05bbd96fccf7b17c4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038150"
---
# <a name="get-workflowinstanceid"></a>Získání WorkflowInstanceId
Tato ukázka předvádí, `GetWorkflowInstanceId` jak použít vlastní aktivitu k vrácení ID instance pracovního postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vývoj vlastních aktivit, jak získat přístup k instanci pracovního postupu.  
  
## <a name="discussion"></a>Účely  
 Získání ID instance spuštěného pracovního postupu vyžaduje zápis kódu. Chcete-li napsat plně deklarativní pracovní postup, budete potřebovat aktivitu, která může vrátit ID instance pracovního postupu, aby mohla být na aktivitu odkazována v pracovním postupu, aby poskytovala plně deklarativní prostředí pro vytváření pracovních postupů. Řada scénářů vyžaduje přístup k ID instance: několik příkladů je pro účely protokolování nebo auditování nebo pro korelaci na úrovni aplikace poskytnutím ID instance back klientovi pro budoucí přidružení (například pomocí této aktivity uvnitř Aktivita SendReply).  
  
 `GetWorkflowInstanceId`je implementována jako <xref:System.Activities.CodeActivity%601> , protože musí vracet hodnotu typu <xref:System.Guid>a <xref:System.Activities.CodeActivityContext> musí mít přístup k pro získání ID instance pracovního postupu. Jeho implementace je poměrně základní.  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
