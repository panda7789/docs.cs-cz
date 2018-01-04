---
title: '&lt;obory&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0a2309bb19b30f6927d5e9cd3047950936dff08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="4c41e-102">&lt;obory&gt;</span><span class="sxs-lookup"><span data-stu-id="4c41e-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="4c41e-103">Obsahuje kolekci elementů konfigurace, které určují obor vlastní identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="4c41e-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="4c41e-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4c41e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4c41e-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4c41e-105">\<behaviors></span></span>  
<span data-ttu-id="4c41e-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4c41e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4c41e-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4c41e-107">\<behavior></span></span>  
<span data-ttu-id="4c41e-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="4c41e-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="4c41e-109">\<obory ></span><span class="sxs-lookup"><span data-stu-id="4c41e-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c41e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c41e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c41e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c41e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4c41e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c41e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c41e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c41e-113">Attributes</span></span>  
 <span data-ttu-id="4c41e-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c41e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c41e-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c41e-115">Child Elements</span></span>  
  
|<span data-ttu-id="4c41e-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="4c41e-116">Attribute</span></span>|<span data-ttu-id="4c41e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="4c41e-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4c41e-118">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="4c41e-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="4c41e-119">Přidá informace o oboru pro koncový bod, který lze použít v odpovídající kritériím pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="4c41e-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c41e-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c41e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4c41e-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c41e-121">Element</span></span>|<span data-ttu-id="4c41e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4c41e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c41e-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="4c41e-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="4c41e-124">Určuje různé zjišťování nastavení pro koncový bod, například jeho možnosti rozpoznání, obory a vlastní rozšíření jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="4c41e-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c41e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c41e-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
