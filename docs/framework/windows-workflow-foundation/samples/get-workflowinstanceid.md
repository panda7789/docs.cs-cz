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
# <a name="get-workflowinstanceid"></a><span data-ttu-id="d75e5-102">Získání WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d75e5-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="d75e5-103">Tato ukázka ukazuje, jak použít `GetWorkflowInstanceId` vlastní aktivitu, chcete-li vrátit ID instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d75e5-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d75e5-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="d75e5-104">Demonstrates</span></span>  
 <span data-ttu-id="d75e5-105">Vlastní vývoj aktivit, jak získat přístup k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d75e5-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d75e5-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="d75e5-106">Discussion</span></span>  
 <span data-ttu-id="d75e5-107">Získání ID instance spuštěného pracovního postupu vyžaduje psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="d75e5-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="d75e5-108">Pokud chcete napsat plně deklarativní pracovní postup, potřebujete aktivitu, která může vrátit ID instance pracovního postupu, aby na aktivitu bylo možné odkazovat v pracovním postupu a poskytnout tak plně deklarativní prostředí pro vytváření pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d75e5-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="d75e5-109">Mnoho scénářů vyžaduje přístup k ID instance: několik příkladů je pro účely protokolování nebo auditování nebo pro korelaci na úrovni aplikace poskytnutím ID instance zpět klientovi pro budoucí přidružení (například pomocí této aktivity uvnitř SendReply).</span><span class="sxs-lookup"><span data-stu-id="d75e5-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="d75e5-110">`GetWorkflowInstanceId`je implementována jako, <xref:System.Activities.CodeActivity%601> protože musí <xref:System.Guid>vrátit hodnotu typu <xref:System.Activities.CodeActivityContext> a musí mít přístup k získání ID instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d75e5-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="d75e5-111">Jeho realizace je poměrně základní.</span><span class="sxs-lookup"><span data-stu-id="d75e5-111">Its implementation is fairly basic.</span></span>  
  
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
> <span data-ttu-id="d75e5-112">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d75e5-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d75e5-113">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d75e5-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d75e5-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d75e5-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d75e5-115">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d75e5-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
