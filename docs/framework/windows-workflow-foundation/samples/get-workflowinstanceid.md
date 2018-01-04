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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8fc0edc1e128e03a18c512fc0be03a02537ba71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="e6b39-102">Získat WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e6b39-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="e6b39-103">Tento příklad ukazuje, jak použít vlastní aktivity, `GetWorkflowInstanceId` vrátit ID instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e6b39-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e6b39-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="e6b39-104">Demonstrates</span></span>  
 <span data-ttu-id="e6b39-105">Vývoj vlastní aktivity, jak získat přístup k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e6b39-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e6b39-106">Diskusní</span><span class="sxs-lookup"><span data-stu-id="e6b39-106">Discussion</span></span>  
 <span data-ttu-id="e6b39-107">Získávání ID instance s běžícím workflowem vyžaduje psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="e6b39-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="e6b39-108">Pokud chcete vytvoření plně deklarativního pracovního postupu, musíte aktivitu, která můžete vrátit zpět ID instance pracovního postupu, může být odkazováno aktivity v pracovním postupu zajistit plně deklarativního pracovního postupu pro tvorbu prostředí.</span><span class="sxs-lookup"><span data-stu-id="e6b39-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="e6b39-109">Mnoho scénářů vyžadují přístup k instance ID: několik příkladů pro protokolování nebo auditování účely nebo pro provádění korelace úrovni aplikace poskytnutím instance ID zpět do klienta pro budoucí přidružení (například pomocí této aktivity uvnitř Aktivita SendReply).</span><span class="sxs-lookup"><span data-stu-id="e6b39-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="e6b39-110">`GetWorkflowInstanceId`je implementovaný jako <xref:System.Activities.CodeActivity%601> protože musí vracet hodnoty typu <xref:System.Guid>, a musí mít přístup k <xref:System.Activities.CodeActivityContext> pro získání pracovního postupu instance ID.</span><span class="sxs-lookup"><span data-stu-id="e6b39-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="e6b39-111">Jeho implementace je vcelku jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="e6b39-111">Its implementation is fairly basic.</span></span>  
  
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
>  <span data-ttu-id="e6b39-112">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="e6b39-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6b39-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e6b39-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e6b39-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e6b39-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6b39-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e6b39-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
