---
title: '&lt;DynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 215bc9d8540b2d782a0c63f2f5be96f6fcde6812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746758"
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="925f6-102">&lt;DynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="925f6-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="925f6-103">Tento element konfigurace definuje standardní koncový bod, který obsahuje informace o povolení aplikace fungovat jako klient programu, můžete najít adresa koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="925f6-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="925f6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="925f6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="925f6-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="925f6-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925f6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="925f6-106">Syntax</span></span>  
  
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
            <add name="String" namespace="String" />
          <contractTypeNames>
          <extensions />
          <scopes>
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="925f6-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="925f6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="925f6-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="925f6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="925f6-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="925f6-109">Attributes</span></span>  
 <span data-ttu-id="925f6-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="925f6-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="925f6-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="925f6-111">Child Elements</span></span>  
  
|<span data-ttu-id="925f6-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="925f6-112">Element</span></span>|<span data-ttu-id="925f6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="925f6-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="925f6-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="925f6-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="925f6-115">Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="925f6-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="925f6-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="925f6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="925f6-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="925f6-117">Element</span></span>|<span data-ttu-id="925f6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="925f6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="925f6-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="925f6-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="925f6-120">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="925f6-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="925f6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="925f6-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
