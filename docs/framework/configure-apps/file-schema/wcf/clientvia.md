---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3782eb9cbe793fef450c8b1c58456a1d4f7b0b94
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="a4ba1-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="a4ba1-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="a4ba1-103">Určuje identifikátor URI, pro který by měl být vytvořen kanál přenosu.</span><span class="sxs-lookup"><span data-stu-id="a4ba1-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="a4ba1-104">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a4ba1-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="a4ba1-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a4ba1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4ba1-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a4ba1-106">\<behaviors></span></span>  
<span data-ttu-id="a4ba1-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a4ba1-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a4ba1-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a4ba1-108">\<behavior></span></span>  
<span data-ttu-id="a4ba1-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="a4ba1-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ba1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4ba1-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4ba1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a4ba1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a4ba1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a4ba1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4ba1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a4ba1-113">Attributes</span></span>  
  
|<span data-ttu-id="a4ba1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a4ba1-114">Attribute</span></span>|<span data-ttu-id="a4ba1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a4ba1-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="a4ba1-116">Řetězec, který určuje identifikátor URI, který označuje trasy, která by měly přijmout zprávu.</span><span class="sxs-lookup"><span data-stu-id="a4ba1-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4ba1-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a4ba1-117">Child Elements</span></span>  
 <span data-ttu-id="a4ba1-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a4ba1-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4ba1-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4ba1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a4ba1-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a4ba1-120">Element</span></span>|<span data-ttu-id="a4ba1-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a4ba1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4ba1-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a4ba1-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a4ba1-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a4ba1-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4ba1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4ba1-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
