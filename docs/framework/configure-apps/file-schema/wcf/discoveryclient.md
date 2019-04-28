---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704021"
---
# <a name="discoveryclient"></a><span data-ttu-id="690c0-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="690c0-101">\<discoveryClient></span></span>
<span data-ttu-id="690c0-102">Prvek konfigurace pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="690c0-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="690c0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="690c0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="690c0-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="690c0-104">\<bindings></span></span>  
<span data-ttu-id="690c0-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="690c0-105">\<customBinding></span></span>  
<span data-ttu-id="690c0-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="690c0-106">\<binding></span></span>  
<span data-ttu-id="690c0-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="690c0-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690c0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="690c0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="690c0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="690c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="690c0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="690c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="690c0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="690c0-111">Attributes</span></span>  
  
|<span data-ttu-id="690c0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="690c0-112">Attribute</span></span>|<span data-ttu-id="690c0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="690c0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="690c0-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="690c0-114">discoveryEndpoint</span></span>|<span data-ttu-id="690c0-115">Řetězec, který obsahuje název koncového bodu zjišťování, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="690c0-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="690c0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="690c0-116">Child Elements</span></span>  
  
|<span data-ttu-id="690c0-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="690c0-117">Element</span></span>|<span data-ttu-id="690c0-118">Popis</span><span class="sxs-lookup"><span data-stu-id="690c0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="690c0-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="690c0-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="690c0-120">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="690c0-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="690c0-121">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="690c0-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="690c0-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="690c0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="690c0-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="690c0-123">Element</span></span>|<span data-ttu-id="690c0-124">Popis</span><span class="sxs-lookup"><span data-stu-id="690c0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="690c0-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="690c0-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="690c0-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="690c0-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="690c0-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="690c0-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
