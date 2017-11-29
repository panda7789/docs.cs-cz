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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cdc85c23202154728610ab4721bf830004928c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="11b99-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="11b99-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="11b99-103">Určuje identifikátor URI, pro který by měl být vytvořen kanál přenosu.</span><span class="sxs-lookup"><span data-stu-id="11b99-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="11b99-104">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="11b99-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="11b99-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="11b99-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="11b99-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="11b99-106">\<behaviors></span></span>  
<span data-ttu-id="11b99-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="11b99-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="11b99-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="11b99-108">\<behavior></span></span>  
<span data-ttu-id="11b99-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="11b99-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b99-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b99-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b99-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11b99-111">Attributes and Elements</span></span>  
 <span data-ttu-id="11b99-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11b99-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b99-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="11b99-113">Attributes</span></span>  
  
|<span data-ttu-id="11b99-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="11b99-114">Attribute</span></span>|<span data-ttu-id="11b99-115">Popis</span><span class="sxs-lookup"><span data-stu-id="11b99-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="11b99-116">Řetězec, který určuje identifikátor URI, který označuje trasy, která by měly přijmout zprávu.</span><span class="sxs-lookup"><span data-stu-id="11b99-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b99-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11b99-117">Child Elements</span></span>  
 <span data-ttu-id="11b99-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="11b99-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11b99-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11b99-119">Parent Elements</span></span>  
  
|<span data-ttu-id="11b99-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="11b99-120">Element</span></span>|<span data-ttu-id="11b99-121">Popis</span><span class="sxs-lookup"><span data-stu-id="11b99-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11b99-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="11b99-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="11b99-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="11b99-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11b99-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="11b99-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
