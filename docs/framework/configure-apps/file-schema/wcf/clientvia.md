---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 48e56b79f47e84122ddd4d7f55d50044510bfa66
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149050"
---
# <a name="ltclientviagt"></a><span data-ttu-id="dc4d3-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="dc4d3-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="dc4d3-103">Určuje identifikátor URI, pro který by měl být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="dc4d3-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="dc4d3-104">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="dc4d3-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="dc4d3-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dc4d3-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc4d3-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-106">\<behaviors></span></span>  
<span data-ttu-id="dc4d3-107">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="dc4d3-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-108">\<behavior></span></span>  
<span data-ttu-id="dc4d3-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4d3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc4d3-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc4d3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc4d3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dc4d3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc4d3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc4d3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc4d3-113">Attributes</span></span>  
  
|<span data-ttu-id="dc4d3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="dc4d3-114">Attribute</span></span>|<span data-ttu-id="dc4d3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="dc4d3-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="dc4d3-116">Řetězec určující identifikátor URI, který označuje cestu zpráva měla použít.</span><span class="sxs-lookup"><span data-stu-id="dc4d3-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc4d3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc4d3-117">Child Elements</span></span>  
 <span data-ttu-id="dc4d3-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="dc4d3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc4d3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc4d3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc4d3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc4d3-120">Element</span></span>|<span data-ttu-id="dc4d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="dc4d3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc4d3-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc4d3-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="dc4d3-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="dc4d3-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc4d3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc4d3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
