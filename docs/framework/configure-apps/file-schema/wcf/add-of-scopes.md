---
title: "&lt;add&gt; – &lt;scopes&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 012d86297f75874b57231d7c347c7412ad04aa1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="c4126-102">&lt;add&gt; – &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="c4126-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="c4126-103">Přidá obor vlastní identifikátor Uri, který můžete použít k filtrování koncové body služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="c4126-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="c4126-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c4126-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4126-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c4126-105">\<behaviors></span></span>  
<span data-ttu-id="c4126-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c4126-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c4126-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c4126-107">\<behavior></span></span>  
<span data-ttu-id="c4126-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c4126-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="c4126-109">\<obory ></span><span class="sxs-lookup"><span data-stu-id="c4126-109">\<scopes></span></span>  
<span data-ttu-id="c4126-110">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="c4126-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4126-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4126-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4126-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4126-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c4126-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4126-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4126-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4126-114">Attributes</span></span>  
  
|<span data-ttu-id="c4126-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="c4126-115">Attribute</span></span>|<span data-ttu-id="c4126-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c4126-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4126-117">rozsah</span><span class="sxs-lookup"><span data-stu-id="c4126-117">scope</span></span>|<span data-ttu-id="c4126-118">Identifikátor URI, který obsahuje informace o oboru koncového bodu, který lze použít v odpovídající kritériím pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="c4126-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4126-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4126-119">Child Elements</span></span>  
 <span data-ttu-id="c4126-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="c4126-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4126-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4126-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c4126-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4126-122">Element</span></span>|<span data-ttu-id="c4126-123">Popis</span><span class="sxs-lookup"><span data-stu-id="c4126-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4126-124">\<obory ></span><span class="sxs-lookup"><span data-stu-id="c4126-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="c4126-125">Obsahuje kolekci elementů konfigurace, které určují obor vlastní identifikátory URI, které mohou být použity k filtrování koncové body služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="c4126-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4126-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4126-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
