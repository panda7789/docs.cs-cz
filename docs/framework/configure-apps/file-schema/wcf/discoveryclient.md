---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739031"
---
# <a name="discoveryclient"></a><span data-ttu-id="7c71c-101">\<objektem DiscoveryClient zahozena ></span><span class="sxs-lookup"><span data-stu-id="7c71c-101">\<discoveryClient></span></span>
<span data-ttu-id="7c71c-102">Konfigurační prvek pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="7c71c-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="7c71c-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7c71c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c71c-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7c71c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7c71c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7c71c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7c71c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7c71c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7c71c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="7c71c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7c71c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<objektem discoveryclient zahozena >**</span><span class="sxs-lookup"><span data-stu-id="7c71c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c71c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c71c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c71c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c71c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c71c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c71c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c71c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c71c-112">Attributes</span></span>  
  
|<span data-ttu-id="7c71c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7c71c-113">Attribute</span></span>|<span data-ttu-id="7c71c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7c71c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c71c-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="7c71c-115">discoveryEndpoint</span></span>|<span data-ttu-id="7c71c-116">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="7c71c-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c71c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c71c-117">Child Elements</span></span>  
  
|<span data-ttu-id="7c71c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c71c-118">Element</span></span>|<span data-ttu-id="7c71c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7c71c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c71c-120">\<oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7c71c-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="7c71c-121">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="7c71c-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="7c71c-122">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="7c71c-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c71c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c71c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7c71c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c71c-124">Element</span></span>|<span data-ttu-id="7c71c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7c71c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c71c-126">vazba \<</span><span class="sxs-lookup"><span data-stu-id="7c71c-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="7c71c-127">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7c71c-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c71c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c71c-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
