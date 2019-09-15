---
title: Získání WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: f8bd3205f5b7a4b3bae5203dc90a3c393cedcbdd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989373"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="9d0e2-102">Získání WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9d0e2-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="9d0e2-103">Tato ukázka předvádí, `GetWorkflowInstanceId` jak použít vlastní aktivitu k vrácení ID instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9d0e2-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="9d0e2-104">Demonstrates</span></span>  
 <span data-ttu-id="9d0e2-105">Vývoj vlastních aktivit, jak získat přístup k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9d0e2-106">Účely</span><span class="sxs-lookup"><span data-stu-id="9d0e2-106">Discussion</span></span>  
 <span data-ttu-id="9d0e2-107">Získání ID instance spuštěného pracovního postupu vyžaduje zápis kódu.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="9d0e2-108">Chcete-li napsat plně deklarativní pracovní postup, budete potřebovat aktivitu, která může vrátit ID instance pracovního postupu, aby mohla být na aktivitu odkazována v pracovním postupu, aby poskytovala plně deklarativní prostředí pro vytváření pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="9d0e2-109">Řada scénářů vyžaduje přístup k ID instance: několik příkladů je pro účely protokolování nebo auditování nebo pro korelaci na úrovni aplikace poskytnutím ID instance back klientovi pro budoucí přidružení (například pomocí této aktivity uvnitř Aktivita SendReply).</span><span class="sxs-lookup"><span data-stu-id="9d0e2-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="9d0e2-110">`GetWorkflowInstanceId`je implementována jako <xref:System.Activities.CodeActivity%601> , protože musí vracet hodnotu typu <xref:System.Guid>a <xref:System.Activities.CodeActivityContext> musí mít přístup k pro získání ID instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="9d0e2-111">Jeho implementace je poměrně základní.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="9d0e2-112">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d0e2-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9d0e2-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d0e2-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9d0e2-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
