---
title: Korelace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc1608cc4e746af56e7d89237f0c1f5e6cc3bc7e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="correlation"></a><span data-ttu-id="afcc3-102">Korelace</span><span class="sxs-lookup"><span data-stu-id="afcc3-102">Correlation</span></span>
<span data-ttu-id="afcc3-103">Když aplikace služby pracovního postupu komunikovat s jinými službami, je důležité, aby zpráv mezi nimi jsou odesílány do instance příslušné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="afcc3-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="afcc3-104">Korelace poskytuje mechanismus pro tento.</span><span class="sxs-lookup"><span data-stu-id="afcc3-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="afcc3-105">Témata v této části poskytují přehled korelace a způsobu jeho použití v různých pracovních postupech služby.</span><span class="sxs-lookup"><span data-stu-id="afcc3-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afcc3-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="afcc3-106">In This Section</span></span>  
 [<span data-ttu-id="afcc3-107">Korelace – přehled</span><span class="sxs-lookup"><span data-stu-id="afcc3-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="afcc3-108">Poskytuje přehled typů korelace, které jsou k dispozici v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afcc3-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="afcc3-109">Kontextová výměna</span><span class="sxs-lookup"><span data-stu-id="afcc3-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="afcc3-110">Popisuje korelace kontextové výměny.</span><span class="sxs-lookup"><span data-stu-id="afcc3-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="afcc3-111">Trvanlivý duplexní přenos</span><span class="sxs-lookup"><span data-stu-id="afcc3-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="afcc3-112">Popisuje korelace trvanlivého duplexního přenosu.</span><span class="sxs-lookup"><span data-stu-id="afcc3-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="afcc3-113">Na základě obsahu</span><span class="sxs-lookup"><span data-stu-id="afcc3-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="afcc3-114">Popisuje korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="afcc3-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="afcc3-115">Požadavek odpověď</span><span class="sxs-lookup"><span data-stu-id="afcc3-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="afcc3-116">Popisuje korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="afcc3-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="afcc3-117">Řešení potíží – korelace</span><span class="sxs-lookup"><span data-stu-id="afcc3-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="afcc3-118">Poskytuje metody pro řešení potíží – korelace.</span><span class="sxs-lookup"><span data-stu-id="afcc3-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afcc3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="afcc3-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="afcc3-120">Korelace na základě obsahu</span><span class="sxs-lookup"><span data-stu-id="afcc3-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="afcc3-121">Korelační kalkulačky</span><span class="sxs-lookup"><span data-stu-id="afcc3-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
