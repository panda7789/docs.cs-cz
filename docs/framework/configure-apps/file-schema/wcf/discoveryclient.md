---
title: '&lt;objekty discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0b7161c9e4564367348d1c94d469d6fa4a4b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="44b49-102">&lt;objekty discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="44b49-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="44b49-103">Element konfigurace pro vytvoření vlastní vazby, která umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.</span><span class="sxs-lookup"><span data-stu-id="44b49-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="44b49-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="44b49-104">\<system.serviceModel></span></span>  
<span data-ttu-id="44b49-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="44b49-105">\<bindings></span></span>  
<span data-ttu-id="44b49-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="44b49-106">\<customBinding></span></span>  
<span data-ttu-id="44b49-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="44b49-107">\<binding></span></span>  
<span data-ttu-id="44b49-108">\<objekty discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="44b49-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b49-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44b49-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44b49-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44b49-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44b49-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44b49-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44b49-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="44b49-112">Attributes</span></span>  
  
|<span data-ttu-id="44b49-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="44b49-113">Attribute</span></span>|<span data-ttu-id="44b49-114">Popis</span><span class="sxs-lookup"><span data-stu-id="44b49-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44b49-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="44b49-115">discoveryEndpoint</span></span>|<span data-ttu-id="44b49-116">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.</span><span class="sxs-lookup"><span data-stu-id="44b49-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44b49-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44b49-117">Child Elements</span></span>  
  
|<span data-ttu-id="44b49-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="44b49-118">Element</span></span>|<span data-ttu-id="44b49-119">Popis</span><span class="sxs-lookup"><span data-stu-id="44b49-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44b49-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="44b49-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="44b49-121">Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="44b49-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="44b49-122">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).</span><span class="sxs-lookup"><span data-stu-id="44b49-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44b49-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44b49-123">Parent Elements</span></span>  
  
|<span data-ttu-id="44b49-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="44b49-124">Element</span></span>|<span data-ttu-id="44b49-125">Popis</span><span class="sxs-lookup"><span data-stu-id="44b49-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44b49-126">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="44b49-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="44b49-127">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="44b49-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44b49-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="44b49-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
