---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b8864760c1700cd785922b922346204d194f56cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176810"
---
# <a name="clientvia"></a><span data-ttu-id="7bf0f-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="7bf0f-101">\<clientVia></span></span>
<span data-ttu-id="7bf0f-102">Určuje identifikátor URI, pro který by měl být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="7bf0f-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="7bf0f-103">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7bf0f-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="7bf0f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7bf0f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bf0f-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7bf0f-105">\<behaviors></span></span>  
<span data-ttu-id="7bf0f-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7bf0f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7bf0f-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7bf0f-107">\<behavior></span></span>  
<span data-ttu-id="7bf0f-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="7bf0f-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf0f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bf0f-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bf0f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7bf0f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7bf0f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7bf0f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bf0f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7bf0f-112">Attributes</span></span>  
  
|<span data-ttu-id="7bf0f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7bf0f-113">Attribute</span></span>|<span data-ttu-id="7bf0f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7bf0f-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="7bf0f-115">Řetězec určující identifikátor URI, který označuje cestu zpráva měla použít.</span><span class="sxs-lookup"><span data-stu-id="7bf0f-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bf0f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7bf0f-116">Child Elements</span></span>  
 <span data-ttu-id="7bf0f-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="7bf0f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bf0f-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7bf0f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7bf0f-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="7bf0f-119">Element</span></span>|<span data-ttu-id="7bf0f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7bf0f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bf0f-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7bf0f-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7bf0f-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7bf0f-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bf0f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bf0f-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
