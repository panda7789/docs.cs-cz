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
ms.workload: dotnet
ms.openlocfilehash: 7a1870a8c331aae16ab14da62c64d6fb15ecd3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="346e3-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="346e3-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="346e3-103">Určuje identifikátor URI, pro který by měl být vytvořen kanál přenosu.</span><span class="sxs-lookup"><span data-stu-id="346e3-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="346e3-104">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="346e3-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="346e3-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="346e3-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="346e3-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="346e3-106">\<behaviors></span></span>  
<span data-ttu-id="346e3-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="346e3-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="346e3-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="346e3-108">\<behavior></span></span>  
<span data-ttu-id="346e3-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="346e3-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346e3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="346e3-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="346e3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="346e3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="346e3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="346e3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="346e3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="346e3-113">Attributes</span></span>  
  
|<span data-ttu-id="346e3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="346e3-114">Attribute</span></span>|<span data-ttu-id="346e3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="346e3-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="346e3-116">Řetězec, který určuje identifikátor URI, který označuje trasy, která by měly přijmout zprávu.</span><span class="sxs-lookup"><span data-stu-id="346e3-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="346e3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="346e3-117">Child Elements</span></span>  
 <span data-ttu-id="346e3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="346e3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="346e3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="346e3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="346e3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="346e3-120">Element</span></span>|<span data-ttu-id="346e3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="346e3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="346e3-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="346e3-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="346e3-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="346e3-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="346e3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="346e3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
