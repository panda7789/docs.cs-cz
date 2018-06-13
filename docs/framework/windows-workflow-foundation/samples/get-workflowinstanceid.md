---
title: Získat WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: fbfaf52931345571e5125200fe467dcc098b9dc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513903"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="64838-102">Získat WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="64838-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="64838-103">Tento příklad ukazuje, jak použít vlastní aktivity, `GetWorkflowInstanceId` vrátit ID instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="64838-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="64838-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="64838-104">Demonstrates</span></span>  
 <span data-ttu-id="64838-105">Vývoj vlastní aktivity, jak získat přístup k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="64838-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="64838-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="64838-106">Discussion</span></span>  
 <span data-ttu-id="64838-107">Získávání ID instance s běžícím workflowem vyžaduje psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="64838-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="64838-108">Pokud chcete vytvoření plně deklarativního pracovního postupu, musíte aktivitu, která můžete vrátit zpět ID instance pracovního postupu, může být odkazováno aktivity v pracovním postupu zajistit plně deklarativního pracovního postupu pro tvorbu prostředí.</span><span class="sxs-lookup"><span data-stu-id="64838-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="64838-109">Mnoho scénářů vyžadují přístup k instance ID: několik příkladů pro protokolování nebo auditování účely nebo pro provádění korelace úrovni aplikace poskytnutím instance ID zpět do klienta pro budoucí přidružení (například pomocí této aktivity uvnitř Aktivita SendReply).</span><span class="sxs-lookup"><span data-stu-id="64838-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="64838-110">`GetWorkflowInstanceId` je implementovaný jako <xref:System.Activities.CodeActivity%601> protože musí vracet hodnoty typu <xref:System.Guid>, a musí mít přístup k <xref:System.Activities.CodeActivityContext> pro získání pracovního postupu instance ID.</span><span class="sxs-lookup"><span data-stu-id="64838-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="64838-111">Jeho implementace je vcelku jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="64838-111">Its implementation is fairly basic.</span></span>  
  
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
>  <span data-ttu-id="64838-112">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="64838-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="64838-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="64838-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="64838-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="64838-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="64838-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="64838-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
