---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 6c03057fca23b037702c702b9a574045ebb302b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656623"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="b68b2-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="b68b2-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="b68b2-103">Umožňuje načítání informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="b68b2-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="b68b2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b68b2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b68b2-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b68b2-105">\<behaviors></span></span>  
<span data-ttu-id="b68b2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b68b2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b68b2-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b68b2-107">\<behavior></span></span>  
<span data-ttu-id="b68b2-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="b68b2-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68b2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b68b2-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b68b2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b68b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b68b2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b68b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b68b2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b68b2-112">Attributes</span></span>  
 <span data-ttu-id="b68b2-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="b68b2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b68b2-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b68b2-114">Child Elements</span></span>  
  
|<span data-ttu-id="b68b2-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="b68b2-115">Element</span></span>|<span data-ttu-id="b68b2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b68b2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b68b2-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="b68b2-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="b68b2-118">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="b68b2-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b68b2-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b68b2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b68b2-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b68b2-120">Element</span></span>|<span data-ttu-id="b68b2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b68b2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b68b2-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b68b2-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b68b2-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="b68b2-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b68b2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b68b2-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
