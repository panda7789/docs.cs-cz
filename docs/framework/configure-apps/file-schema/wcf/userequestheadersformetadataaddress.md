---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121183"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="15585-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="15585-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="15585-102">Umožňuje načítání informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="15585-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="15585-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="15585-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="15585-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="15585-104">\<behaviors></span></span>  
<span data-ttu-id="15585-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="15585-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="15585-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="15585-106">\<behavior></span></span>  
<span data-ttu-id="15585-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="15585-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15585-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15585-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15585-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="15585-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15585-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="15585-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15585-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="15585-111">Attributes</span></span>  
 <span data-ttu-id="15585-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="15585-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15585-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="15585-113">Child Elements</span></span>  
  
|<span data-ttu-id="15585-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="15585-114">Element</span></span>|<span data-ttu-id="15585-115">Popis</span><span class="sxs-lookup"><span data-stu-id="15585-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15585-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="15585-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="15585-117">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="15585-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15585-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="15585-118">Parent Elements</span></span>  
  
|<span data-ttu-id="15585-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="15585-119">Element</span></span>|<span data-ttu-id="15585-120">Popis</span><span class="sxs-lookup"><span data-stu-id="15585-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15585-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="15585-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="15585-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="15585-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15585-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15585-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
