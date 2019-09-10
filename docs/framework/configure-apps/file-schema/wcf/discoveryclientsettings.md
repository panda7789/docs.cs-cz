---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855409"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="242c1-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="242c1-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="242c1-102">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="242c1-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="242c1-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="242c1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="242c1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="242c1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="242c1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="242c1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="242c1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="242c1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="242c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Standardendpoint definovanému >** </span><span class="sxs-lookup"><span data-stu-id="242c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="242c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClientSettings >**</span><span class="sxs-lookup"><span data-stu-id="242c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="242c1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="242c1-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="242c1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="242c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="242c1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="242c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="242c1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="242c1-112">Attributes</span></span>  
  
|<span data-ttu-id="242c1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="242c1-113">Attribute</span></span>|<span data-ttu-id="242c1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="242c1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="242c1-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="242c1-115">discoveryEndpoint</span></span>|<span data-ttu-id="242c1-116">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="242c1-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="242c1-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="242c1-117">Child Elements</span></span>  
  
|<span data-ttu-id="242c1-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="242c1-118">Element</span></span>|<span data-ttu-id="242c1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="242c1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="242c1-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="242c1-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="242c1-121">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="242c1-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="242c1-122">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="242c1-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="242c1-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="242c1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="242c1-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="242c1-124">Element</span></span>|<span data-ttu-id="242c1-125">Popis</span><span class="sxs-lookup"><span data-stu-id="242c1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="242c1-126">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="242c1-126">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="242c1-127">Definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="242c1-127">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="242c1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="242c1-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
