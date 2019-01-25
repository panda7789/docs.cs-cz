---
title: '&lt;Obory&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 1235b483f63ab71405803c16f2d3c9926b15cfad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642984"
---
# <a name="ltscopesgt"></a><span data-ttu-id="32539-102">&lt;Obory&gt;</span><span class="sxs-lookup"><span data-stu-id="32539-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="32539-103">Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="32539-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="32539-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32539-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32539-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="32539-105">\<behaviors></span></span>  
<span data-ttu-id="32539-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="32539-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="32539-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="32539-107">\<behavior></span></span>  
<span data-ttu-id="32539-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="32539-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="32539-109">\<obory ></span><span class="sxs-lookup"><span data-stu-id="32539-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32539-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32539-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32539-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32539-111">Attributes and Elements</span></span>  
 <span data-ttu-id="32539-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32539-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32539-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="32539-113">Attributes</span></span>  
 <span data-ttu-id="32539-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="32539-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32539-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32539-115">Child Elements</span></span>  
  
|<span data-ttu-id="32539-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="32539-116">Attribute</span></span>|<span data-ttu-id="32539-117">Popis</span><span class="sxs-lookup"><span data-stu-id="32539-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="32539-118">\<add></span><span class="sxs-lookup"><span data-stu-id="32539-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="32539-119">Přidá informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="32539-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32539-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32539-120">Parent Elements</span></span>  
  
|<span data-ttu-id="32539-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="32539-121">Element</span></span>|<span data-ttu-id="32539-122">Popis</span><span class="sxs-lookup"><span data-stu-id="32539-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32539-123">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="32539-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="32539-124">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="32539-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32539-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32539-125">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
