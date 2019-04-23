---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213074"
---
# <a name="scopes"></a><span data-ttu-id="fe485-101">\<obory ></span><span class="sxs-lookup"><span data-stu-id="fe485-101">\<scopes></span></span>
<span data-ttu-id="fe485-102">Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="fe485-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="fe485-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fe485-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fe485-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fe485-104">\<behaviors></span></span>  
<span data-ttu-id="fe485-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="fe485-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="fe485-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fe485-106">\<behavior></span></span>  
<span data-ttu-id="fe485-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="fe485-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="fe485-108">\<obory ></span><span class="sxs-lookup"><span data-stu-id="fe485-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe485-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe485-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe485-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe485-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe485-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe485-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe485-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe485-112">Attributes</span></span>  
 <span data-ttu-id="fe485-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe485-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe485-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe485-114">Child Elements</span></span>  
  
|<span data-ttu-id="fe485-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe485-115">Attribute</span></span>|<span data-ttu-id="fe485-116">Popis</span><span class="sxs-lookup"><span data-stu-id="fe485-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fe485-117">\<add></span><span class="sxs-lookup"><span data-stu-id="fe485-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="fe485-118">Přidá informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="fe485-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe485-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe485-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fe485-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe485-120">Element</span></span>|<span data-ttu-id="fe485-121">Popis</span><span class="sxs-lookup"><span data-stu-id="fe485-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe485-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="fe485-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="fe485-123">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="fe485-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe485-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe485-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
