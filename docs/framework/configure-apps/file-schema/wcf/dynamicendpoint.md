---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: e1a53869faa1997d2e79c3d2869a15001ee29626
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187743"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="1b146-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="1b146-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="1b146-102">Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní, aby aplikace fungovala jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="1b146-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="1b146-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1b146-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b146-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1b146-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b146-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b146-105">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b146-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1b146-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1b146-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1b146-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b146-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="1b146-108">Attributes</span></span>  
 <span data-ttu-id="1b146-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="1b146-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b146-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1b146-110">Child Elements</span></span>  
  
|<span data-ttu-id="1b146-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b146-111">Element</span></span>|<span data-ttu-id="1b146-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1b146-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b146-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="1b146-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="1b146-114">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="1b146-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b146-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1b146-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1b146-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b146-116">Element</span></span>|<span data-ttu-id="1b146-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1b146-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b146-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1b146-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1b146-119">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="1b146-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b146-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b146-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
