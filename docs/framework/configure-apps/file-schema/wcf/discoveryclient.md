---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5e586437e3b269d361c254744e820ee8e8c0ca0a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400400"
---
# <a name="discoveryclient"></a><span data-ttu-id="5d676-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="5d676-101">\<discoveryClient></span></span>
<span data-ttu-id="5d676-102">Konfigurační prvek pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="5d676-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="5d676-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d676-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d676-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5d676-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5d676-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5d676-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5d676-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5d676-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5d676-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="5d676-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5d676-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Objektem DiscoveryClient zahozena >**</span><span class="sxs-lookup"><span data-stu-id="5d676-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d676-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d676-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d676-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5d676-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5d676-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5d676-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d676-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5d676-112">Attributes</span></span>  
  
|<span data-ttu-id="5d676-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5d676-113">Attribute</span></span>|<span data-ttu-id="5d676-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5d676-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d676-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="5d676-115">discoveryEndpoint</span></span>|<span data-ttu-id="5d676-116">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="5d676-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d676-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5d676-117">Child Elements</span></span>  
  
|<span data-ttu-id="5d676-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d676-118">Element</span></span>|<span data-ttu-id="5d676-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5d676-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d676-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5d676-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="5d676-121">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5d676-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="5d676-122">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="5d676-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d676-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5d676-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5d676-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d676-124">Element</span></span>|<span data-ttu-id="5d676-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5d676-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d676-126">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5d676-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5d676-127">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="5d676-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d676-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d676-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
