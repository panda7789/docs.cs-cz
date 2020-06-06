---
title: <services> z <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 219a05b1-f573-45c9-849b-e86bc373b62f
ms.openlocfilehash: 1106a9c62f4b57a2a695343c26879b2adf0934de
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "61758168"
---
# <a name="services-of-workflowruntime"></a><span data-ttu-id="d20fb-102">\<services> z \<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="d20fb-102">\<services> of \<workflowRuntime></span></span>
<span data-ttu-id="d20fb-103">Představuje kolekci služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="d20fb-103">Represents a collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="d20fb-104">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="d20fb-104">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="d20fb-105">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při <xref:System.Workflow.Runtime.WorkflowRuntime> volání příslušného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d20fb-105">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d20fb-106">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d20fb-106">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d20fb-107">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d20fb-107">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20fb-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d20fb-108">See also</span></span>

- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="d20fb-109">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d20fb-109">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
