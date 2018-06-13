---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6218bb3f205f2825eb3f10fabf834cfd0396ac87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754129"
---
# <a name="ltclientviagt"></a><span data-ttu-id="344dd-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="344dd-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="344dd-103">Určuje identifikátor URI, pro který by měl být vytvořen kanál přenosu.</span><span class="sxs-lookup"><span data-stu-id="344dd-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="344dd-104">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="344dd-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="344dd-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="344dd-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="344dd-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="344dd-106">\<behaviors></span></span>  
<span data-ttu-id="344dd-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="344dd-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="344dd-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="344dd-108">\<behavior></span></span>  
<span data-ttu-id="344dd-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="344dd-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344dd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="344dd-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="344dd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="344dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="344dd-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="344dd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="344dd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="344dd-113">Attributes</span></span>  
  
|<span data-ttu-id="344dd-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="344dd-114">Attribute</span></span>|<span data-ttu-id="344dd-115">Popis</span><span class="sxs-lookup"><span data-stu-id="344dd-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="344dd-116">Řetězec, který určuje identifikátor URI, který označuje trasy, která by měly přijmout zprávu.</span><span class="sxs-lookup"><span data-stu-id="344dd-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="344dd-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="344dd-117">Child Elements</span></span>  
 <span data-ttu-id="344dd-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="344dd-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="344dd-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="344dd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="344dd-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="344dd-120">Element</span></span>|<span data-ttu-id="344dd-121">Popis</span><span class="sxs-lookup"><span data-stu-id="344dd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="344dd-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="344dd-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="344dd-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="344dd-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="344dd-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="344dd-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>
