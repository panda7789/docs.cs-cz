---
title: Instance
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118986"
---
# <a name="instances"></a><span data-ttu-id="9033a-102">Instance</span><span class="sxs-lookup"><span data-stu-id="9033a-102">Instances</span></span>
<span data-ttu-id="9033a-103">Název čítače: instance.</span><span class="sxs-lookup"><span data-stu-id="9033a-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9033a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9033a-104">Description</span></span>  
 <span data-ttu-id="9033a-105">Počet kontextů instance, které službu nyní obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9033a-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="9033a-106">Ve většině případů, počet kontextů instance je stejný jako počet instancí.</span><span class="sxs-lookup"><span data-stu-id="9033a-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="9033a-107">Následující scénáře jsou však výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="9033a-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="9033a-108">Volá metody služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda explicitně.</span><span class="sxs-lookup"><span data-stu-id="9033a-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="9033a-109">A <xref:System.ServiceModel.ReleaseInstanceMode> platí pro <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span><span class="sxs-lookup"><span data-stu-id="9033a-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9033a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9033a-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
