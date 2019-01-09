---
title: '&lt;add&gt; – &lt;scopes&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: e2bf649259d6ccb0e55428ab3619fe561d051ff7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146225"
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="32422-102">&lt;add&gt; – &lt;scopes&gt;</span><span class="sxs-lookup"><span data-stu-id="32422-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="32422-103">Přidá vlastní rozsahy identifikátoru Uri, který můžete použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="32422-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="32422-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32422-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32422-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="32422-105">\<behaviors></span></span>  
<span data-ttu-id="32422-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="32422-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="32422-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="32422-107">\<behavior></span></span>  
<span data-ttu-id="32422-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="32422-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="32422-109">\<obory ></span><span class="sxs-lookup"><span data-stu-id="32422-109">\<scopes></span></span>  
<span data-ttu-id="32422-110">\<add></span><span class="sxs-lookup"><span data-stu-id="32422-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32422-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32422-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32422-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32422-112">Attributes and Elements</span></span>  
 <span data-ttu-id="32422-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32422-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32422-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="32422-114">Attributes</span></span>  
  
|<span data-ttu-id="32422-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="32422-115">Attribute</span></span>|<span data-ttu-id="32422-116">Popis</span><span class="sxs-lookup"><span data-stu-id="32422-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32422-117">rozsah</span><span class="sxs-lookup"><span data-stu-id="32422-117">scope</span></span>|<span data-ttu-id="32422-118">Identifikátor URI, který obsahuje informace o rozsahu koncového bodu, který lze použít v kritériích přiřazování pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="32422-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32422-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32422-119">Child Elements</span></span>  
 <span data-ttu-id="32422-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="32422-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32422-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32422-121">Parent Elements</span></span>  
  
|<span data-ttu-id="32422-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="32422-122">Element</span></span>|<span data-ttu-id="32422-123">Popis</span><span class="sxs-lookup"><span data-stu-id="32422-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32422-124">\<obory ></span><span class="sxs-lookup"><span data-stu-id="32422-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="32422-125">Obsahuje kolekci prvků konfigurace, které určují vlastní rozsahy identifikátoru URI, který lze použít k fitrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="32422-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32422-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="32422-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
