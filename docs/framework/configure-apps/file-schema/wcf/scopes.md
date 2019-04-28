---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670622"
---
# <a name="scopes"></a><span data-ttu-id="c0c32-101">\<obory ></span><span class="sxs-lookup"><span data-stu-id="c0c32-101">\<scopes></span></span>
<span data-ttu-id="c0c32-102">Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="c0c32-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="c0c32-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c0c32-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0c32-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c0c32-104">\<behaviors></span></span>  
<span data-ttu-id="c0c32-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c0c32-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="c0c32-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c0c32-106">\<behavior></span></span>  
<span data-ttu-id="c0c32-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="c0c32-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="c0c32-108">\<obory ></span><span class="sxs-lookup"><span data-stu-id="c0c32-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c32-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0c32-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0c32-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0c32-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0c32-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0c32-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0c32-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0c32-112">Attributes</span></span>  
 <span data-ttu-id="c0c32-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0c32-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0c32-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0c32-114">Child Elements</span></span>  
  
|<span data-ttu-id="c0c32-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0c32-115">Attribute</span></span>|<span data-ttu-id="c0c32-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c32-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c0c32-117">\<add></span><span class="sxs-lookup"><span data-stu-id="c0c32-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="c0c32-118">Přidá informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="c0c32-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0c32-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0c32-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c0c32-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0c32-120">Element</span></span>|<span data-ttu-id="c0c32-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c32-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0c32-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="c0c32-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="c0c32-123">Určuje různá nastavení zjišťování pro koncový bod, například jeho rozpoznatelnost, rozsahy a všechny vlastní rozšíření jeho metadat.</span><span class="sxs-lookup"><span data-stu-id="c0c32-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0c32-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0c32-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
