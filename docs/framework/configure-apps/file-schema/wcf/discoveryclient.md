---
title: '&lt;discoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5046d3342372960211942128372e9f62d98a2952
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573082"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="f906e-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="f906e-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="f906e-103">Prvek konfigurace pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="f906e-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="f906e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f906e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f906e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f906e-105">\<bindings></span></span>  
<span data-ttu-id="f906e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f906e-106">\<customBinding></span></span>  
<span data-ttu-id="f906e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f906e-107">\<binding></span></span>  
<span data-ttu-id="f906e-108">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="f906e-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f906e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f906e-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f906e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f906e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f906e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f906e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f906e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f906e-112">Attributes</span></span>  
  
|<span data-ttu-id="f906e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f906e-113">Attribute</span></span>|<span data-ttu-id="f906e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f906e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f906e-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="f906e-115">discoveryEndpoint</span></span>|<span data-ttu-id="f906e-116">Řetězec, který obsahuje název koncového bodu zjišťování, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="f906e-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f906e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f906e-117">Child Elements</span></span>  
  
|<span data-ttu-id="f906e-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f906e-118">Element</span></span>|<span data-ttu-id="f906e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f906e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f906e-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="f906e-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f906e-121">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="f906e-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f906e-122">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="f906e-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f906e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f906e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f906e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f906e-124">Element</span></span>|<span data-ttu-id="f906e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f906e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f906e-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="f906e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f906e-127">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="f906e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f906e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f906e-128">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
