---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 512a91bf25180606213eb9eb3b4f7c6a0cb4cbbf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284802"
---
# <a name="discoveryclient"></a><span data-ttu-id="557a7-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="557a7-101">\<discoveryClient></span></span>
<span data-ttu-id="557a7-102">Prvek konfigurace pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="557a7-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="557a7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="557a7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="557a7-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="557a7-104">\<bindings></span></span>  
<span data-ttu-id="557a7-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="557a7-105">\<customBinding></span></span>  
<span data-ttu-id="557a7-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="557a7-106">\<binding></span></span>  
<span data-ttu-id="557a7-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="557a7-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="557a7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="557a7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="557a7-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="557a7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="557a7-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="557a7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="557a7-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="557a7-111">Attributes</span></span>  
  
|<span data-ttu-id="557a7-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="557a7-112">Attribute</span></span>|<span data-ttu-id="557a7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="557a7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="557a7-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="557a7-114">discoveryEndpoint</span></span>|<span data-ttu-id="557a7-115">Řetězec, který obsahuje název koncového bodu zjišťování, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="557a7-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="557a7-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="557a7-116">Child Elements</span></span>  
  
|<span data-ttu-id="557a7-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="557a7-117">Element</span></span>|<span data-ttu-id="557a7-118">Popis</span><span class="sxs-lookup"><span data-stu-id="557a7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="557a7-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="557a7-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="557a7-120">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="557a7-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="557a7-121">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="557a7-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="557a7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="557a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="557a7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="557a7-123">Element</span></span>|<span data-ttu-id="557a7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="557a7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="557a7-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="557a7-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="557a7-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="557a7-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="557a7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="557a7-127">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
