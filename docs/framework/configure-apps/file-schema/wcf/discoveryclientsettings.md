---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 2783796166d56be3d4983ab09a60d62491699fe3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925866"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="4fbf4-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="4fbf4-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="4fbf4-102">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="4fbf4-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="4fbf4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4fbf4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4fbf4-104">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="4fbf4-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fbf4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fbf4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fbf4-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4fbf4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4fbf4-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4fbf4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fbf4-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fbf4-108">Attributes</span></span>  
  
|<span data-ttu-id="4fbf4-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="4fbf4-109">Attribute</span></span>|<span data-ttu-id="4fbf4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4fbf4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fbf4-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="4fbf4-111">discoveryEndpoint</span></span>|<span data-ttu-id="4fbf4-112">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="4fbf4-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fbf4-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4fbf4-113">Child Elements</span></span>  
  
|<span data-ttu-id="4fbf4-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fbf4-114">Element</span></span>|<span data-ttu-id="4fbf4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4fbf4-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fbf4-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4fbf4-116">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="4fbf4-117">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4fbf4-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="4fbf4-118">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="4fbf4-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fbf4-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4fbf4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4fbf4-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fbf4-120">Element</span></span>|<span data-ttu-id="4fbf4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4fbf4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fbf4-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4fbf4-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="4fbf4-123">Definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="4fbf4-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fbf4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fbf4-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
