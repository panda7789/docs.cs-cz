---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: bcbf1c633e0796c6056759dfbb55014838e0e293
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151407"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="e49ff-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="e49ff-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="e49ff-103">Umožňuje načítání informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="e49ff-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="e49ff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e49ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e49ff-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e49ff-105">\<behaviors></span></span>  
<span data-ttu-id="e49ff-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e49ff-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e49ff-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e49ff-107">\<behavior></span></span>  
<span data-ttu-id="e49ff-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="e49ff-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49ff-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e49ff-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e49ff-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e49ff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e49ff-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e49ff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e49ff-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e49ff-112">Attributes</span></span>  
 <span data-ttu-id="e49ff-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="e49ff-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e49ff-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e49ff-114">Child Elements</span></span>  
  
|<span data-ttu-id="e49ff-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="e49ff-115">Element</span></span>|<span data-ttu-id="e49ff-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e49ff-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e49ff-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="e49ff-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="e49ff-118">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="e49ff-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e49ff-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e49ff-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e49ff-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="e49ff-120">Element</span></span>|<span data-ttu-id="e49ff-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e49ff-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e49ff-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e49ff-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e49ff-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e49ff-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e49ff-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e49ff-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
