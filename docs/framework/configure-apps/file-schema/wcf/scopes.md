---
title: '&lt;Obory&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7e2dda0d0def4d1f90bf1b4dbf54f18983355222
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltscopesgt"></a><span data-ttu-id="28e47-102">&lt;Obory&gt;</span><span class="sxs-lookup"><span data-stu-id="28e47-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="28e47-103">Obsahuje kolekci elementů konfigurace, které určují obor vlastní identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="28e47-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="28e47-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28e47-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28e47-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="28e47-105">\<behaviors></span></span>  
<span data-ttu-id="28e47-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28e47-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="28e47-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="28e47-107">\<behavior></span></span>  
<span data-ttu-id="28e47-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="28e47-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="28e47-109">\<obory ></span><span class="sxs-lookup"><span data-stu-id="28e47-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e47-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28e47-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28e47-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28e47-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28e47-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28e47-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28e47-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="28e47-113">Attributes</span></span>  
 <span data-ttu-id="28e47-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="28e47-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28e47-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28e47-115">Child Elements</span></span>  
  
|<span data-ttu-id="28e47-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="28e47-116">Attribute</span></span>|<span data-ttu-id="28e47-117">Popis</span><span class="sxs-lookup"><span data-stu-id="28e47-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="28e47-118">\<add></span><span class="sxs-lookup"><span data-stu-id="28e47-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="28e47-119">Přidá informace o oboru pro koncový bod, který lze použít v odpovídající kritériím pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="28e47-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28e47-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28e47-120">Parent Elements</span></span>  
  
|<span data-ttu-id="28e47-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="28e47-121">Element</span></span>|<span data-ttu-id="28e47-122">Popis</span><span class="sxs-lookup"><span data-stu-id="28e47-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28e47-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="28e47-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="28e47-124">Určuje různé zjišťování nastavení pro koncový bod, například jeho možnosti rozpoznání, obory a vlastní rozšíření jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="28e47-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28e47-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="28e47-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
