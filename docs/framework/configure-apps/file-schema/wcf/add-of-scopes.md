---
title: '&lt;add&gt; – &lt;scopes&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 961fb3e388e3ae756bd7511ea6c65df6dd2a1486
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705570"
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="ef717-102">&lt;add&gt; – &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="ef717-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="ef717-103">Přidá vlastní rozsahy identifikátoru Uri, který můžete použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="ef717-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="ef717-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef717-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef717-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ef717-105">\<behaviors></span></span>  
<span data-ttu-id="ef717-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ef717-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ef717-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ef717-107">\<behavior></span></span>  
<span data-ttu-id="ef717-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="ef717-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="ef717-109">\<obory ></span><span class="sxs-lookup"><span data-stu-id="ef717-109">\<scopes></span></span>  
<span data-ttu-id="ef717-110">\<add></span><span class="sxs-lookup"><span data-stu-id="ef717-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef717-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef717-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef717-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ef717-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ef717-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ef717-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef717-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ef717-114">Attributes</span></span>  
  
|<span data-ttu-id="ef717-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="ef717-115">Attribute</span></span>|<span data-ttu-id="ef717-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ef717-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef717-117">rozsah</span><span class="sxs-lookup"><span data-stu-id="ef717-117">scope</span></span>|<span data-ttu-id="ef717-118">Identifikátor URI, který obsahuje informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="ef717-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef717-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ef717-119">Child Elements</span></span>  
 <span data-ttu-id="ef717-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="ef717-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef717-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ef717-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ef717-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef717-122">Element</span></span>|<span data-ttu-id="ef717-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ef717-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef717-124">\<scopes></span><span class="sxs-lookup"><span data-stu-id="ef717-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="ef717-125">Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="ef717-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef717-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef717-126">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
