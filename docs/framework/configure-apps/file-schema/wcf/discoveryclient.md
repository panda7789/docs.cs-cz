---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919276"
---
# <a name="discoveryclient"></a><span data-ttu-id="85e5a-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="85e5a-101">\<discoveryClient></span></span>
<span data-ttu-id="85e5a-102">Konfigurační prvek pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="85e5a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="85e5a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="85e5a-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="85e5a-104">\<bindings></span></span>  
<span data-ttu-id="85e5a-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="85e5a-105">\<customBinding></span></span>  
<span data-ttu-id="85e5a-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="85e5a-106">\<binding></span></span>  
<span data-ttu-id="85e5a-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="85e5a-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e5a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85e5a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85e5a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="85e5a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="85e5a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="85e5a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85e5a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="85e5a-111">Attributes</span></span>  
  
|<span data-ttu-id="85e5a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="85e5a-112">Attribute</span></span>|<span data-ttu-id="85e5a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="85e5a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85e5a-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="85e5a-114">discoveryEndpoint</span></span>|<span data-ttu-id="85e5a-115">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85e5a-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="85e5a-116">Child Elements</span></span>  
  
|<span data-ttu-id="85e5a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="85e5a-117">Element</span></span>|<span data-ttu-id="85e5a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="85e5a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85e5a-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="85e5a-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="85e5a-120">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="85e5a-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="85e5a-121">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="85e5a-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85e5a-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="85e5a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="85e5a-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="85e5a-123">Element</span></span>|<span data-ttu-id="85e5a-124">Popis</span><span class="sxs-lookup"><span data-stu-id="85e5a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85e5a-125">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="85e5a-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="85e5a-126">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="85e5a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85e5a-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85e5a-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
