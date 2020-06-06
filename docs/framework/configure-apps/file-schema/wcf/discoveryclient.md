---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739031"
---
# \<discoveryClient>
<span data-ttu-id="2386d-101">Konfigurační prvek pro vytvoření vlastní vazby, která umožňuje klientské aplikaci automaticky vyhledat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="2386d-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="2386d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2386d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2386d-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2386d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2386d-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2386d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2386d-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="2386d-105">Attributes</span></span>  
  
|<span data-ttu-id="2386d-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="2386d-106">Attribute</span></span>|<span data-ttu-id="2386d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2386d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2386d-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="2386d-108">discoveryEndpoint</span></span>|<span data-ttu-id="2386d-109">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="2386d-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2386d-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2386d-110">Child Elements</span></span>  
  
|<span data-ttu-id="2386d-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="2386d-111">Element</span></span>|<span data-ttu-id="2386d-112">Description</span><span class="sxs-lookup"><span data-stu-id="2386d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="2386d-113">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="2386d-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="2386d-114">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="2386d-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2386d-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2386d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2386d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="2386d-116">Element</span></span>|<span data-ttu-id="2386d-117">Description</span><span class="sxs-lookup"><span data-stu-id="2386d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="2386d-118">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2386d-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2386d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2386d-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
