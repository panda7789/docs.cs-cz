---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 7e661570f8b94b979595a615b3f6819d41ed5e35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766696"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="ff774-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="ff774-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="ff774-103">Umožňuje načítání informací o adresu metadat ze záhlaví zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="ff774-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="ff774-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ff774-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff774-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ff774-105">\<behaviors></span></span>  
<span data-ttu-id="ff774-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff774-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ff774-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ff774-107">\<behavior></span></span>  
<span data-ttu-id="ff774-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="ff774-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff774-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff774-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff774-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ff774-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff774-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ff774-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff774-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ff774-112">Attributes</span></span>  
 <span data-ttu-id="ff774-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="ff774-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff774-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ff774-114">Child Elements</span></span>  
  
|<span data-ttu-id="ff774-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff774-115">Element</span></span>|<span data-ttu-id="ff774-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ff774-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff774-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ff774-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="ff774-118">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="ff774-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff774-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ff774-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ff774-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff774-120">Element</span></span>|<span data-ttu-id="ff774-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ff774-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff774-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ff774-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff774-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="ff774-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff774-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff774-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
