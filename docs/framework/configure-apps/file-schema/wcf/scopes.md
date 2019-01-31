---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: eee6382c578648866045fd9b283454d9e0e76fcb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275021"
---
# <a name="scopes"></a><span data-ttu-id="4a85b-101">\<obory ></span><span class="sxs-lookup"><span data-stu-id="4a85b-101">\<scopes></span></span>
<span data-ttu-id="4a85b-102">Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="4a85b-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="4a85b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a85b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a85b-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4a85b-104">\<behaviors></span></span>  
<span data-ttu-id="4a85b-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4a85b-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="4a85b-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4a85b-106">\<behavior></span></span>  
<span data-ttu-id="4a85b-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="4a85b-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="4a85b-108">\<obory ></span><span class="sxs-lookup"><span data-stu-id="4a85b-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a85b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a85b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a85b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a85b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4a85b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a85b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a85b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a85b-112">Attributes</span></span>  
 <span data-ttu-id="4a85b-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a85b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a85b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a85b-114">Child Elements</span></span>  
  
|<span data-ttu-id="4a85b-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a85b-115">Attribute</span></span>|<span data-ttu-id="4a85b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4a85b-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4a85b-117">\<add></span><span class="sxs-lookup"><span data-stu-id="4a85b-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="4a85b-118">Přidá informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="4a85b-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a85b-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a85b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4a85b-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a85b-120">Element</span></span>|<span data-ttu-id="4a85b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4a85b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a85b-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="4a85b-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="4a85b-123">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="4a85b-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a85b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a85b-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
