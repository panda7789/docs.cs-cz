---
title: Získání WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43778655"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="8cdfb-102">Získání WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="8cdfb-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="8cdfb-103">Tato ukázka předvádí, jak používat vlastní aktivitu, `GetWorkflowInstanceId` vrátit identifikátor instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8cdfb-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8cdfb-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="8cdfb-104">Demonstrates</span></span>  
 <span data-ttu-id="8cdfb-105">Vývoj vlastních aktivit, jak získat přístup k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8cdfb-106">Diskuse</span><span class="sxs-lookup"><span data-stu-id="8cdfb-106">Discussion</span></span>  
 <span data-ttu-id="8cdfb-107">ID instance s běžícím workflowem potřeba psát kód.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="8cdfb-108">Pokud chcete k vytvoření plně deklarativního pracovního postupu, musíte aktivitu, která vrací ID instance pracovního postupu tak, aby aktivita může být odkazováno v pracovním postupu poskytnout plně deklarativního prostředí pro tvorbu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="8cdfb-109">Mnoho scénářů vyžadují přístup k instance ID: několik příkladů jsou pro protokolování nebo auditování nebo zadáním instance ID zpátky do klienta pro budoucí přidružení plnit korelace úrovni aplikace (například pomocí tato aktivita uvnitř Aktivitu odeslání odpovědi SendReply).</span><span class="sxs-lookup"><span data-stu-id="8cdfb-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="8cdfb-110">`GetWorkflowInstanceId` je implementován jako <xref:System.Activities.CodeActivity%601> vzhledem k tomu, že musí vracet hodnotu typu <xref:System.Guid>, a musí mít přístup k <xref:System.Activities.CodeActivityContext> pro získání pracovního postupu instance ID.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="8cdfb-111">Jeho implementace je poměrně základní.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-111">Its implementation is fairly basic.</span></span>  
  
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
>  <span data-ttu-id="8cdfb-112">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8cdfb-113">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8cdfb-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8cdfb-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8cdfb-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8cdfb-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
