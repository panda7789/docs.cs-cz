---
title: Instance
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473039"
---
# <a name="instances"></a><span data-ttu-id="31d57-102">Instance</span><span class="sxs-lookup"><span data-stu-id="31d57-102">Instances</span></span>
<span data-ttu-id="31d57-103">Název čítače: instance.</span><span class="sxs-lookup"><span data-stu-id="31d57-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="31d57-104">Popis</span><span class="sxs-lookup"><span data-stu-id="31d57-104">Description</span></span>  
 <span data-ttu-id="31d57-105">Počet kontexty instance, které nyní obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="31d57-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="31d57-106">Ve většině případů, počet kontexty instance je stejný jako počet instancí.</span><span class="sxs-lookup"><span data-stu-id="31d57-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="31d57-107">Následující scénáře jsou však výjimkou tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="31d57-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="31d57-108">Volání metody služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda explicitně.</span><span class="sxs-lookup"><span data-stu-id="31d57-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="31d57-109">A <xref:System.ServiceModel.ReleaseInstanceMode> se použije pro <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span><span class="sxs-lookup"><span data-stu-id="31d57-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d57-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="31d57-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
