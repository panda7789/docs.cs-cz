---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6491411d8cfe5c7a5a944f3b1cd728c9f0a4b852
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641210"
---
# <a name="ltclientviagt"></a><span data-ttu-id="ae0ad-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="ae0ad-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="ae0ad-103">Určuje identifikátor URI, pro který by měl být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="ae0ad-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ae0ad-104">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ae0ad-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="ae0ad-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ae0ad-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae0ad-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ae0ad-106">\<behaviors></span></span>  
<span data-ttu-id="ae0ad-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ae0ad-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ae0ad-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ae0ad-108">\<behavior></span></span>  
<span data-ttu-id="ae0ad-109">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="ae0ad-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0ad-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae0ad-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae0ad-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae0ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ae0ad-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae0ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae0ad-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae0ad-113">Attributes</span></span>  
  
|<span data-ttu-id="ae0ad-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae0ad-114">Attribute</span></span>|<span data-ttu-id="ae0ad-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0ad-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ae0ad-116">Řetězec určující identifikátor URI, který označuje cestu zpráva měla použít.</span><span class="sxs-lookup"><span data-stu-id="ae0ad-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae0ad-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae0ad-117">Child Elements</span></span>  
 <span data-ttu-id="ae0ad-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="ae0ad-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae0ad-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae0ad-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ae0ad-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae0ad-120">Element</span></span>|<span data-ttu-id="ae0ad-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0ad-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae0ad-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ae0ad-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ae0ad-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ae0ad-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae0ad-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae0ad-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
