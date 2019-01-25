---
title: '&lt;dynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: dcb52143c874b14c9241940f9b326a07b3fa6a82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540247"
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="a3123-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="a3123-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="a3123-103">Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní, aby aplikace fungovala jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="a3123-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="a3123-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a3123-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3123-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="a3123-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3123-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3123-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3123-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3123-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a3123-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3123-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3123-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3123-109">Attributes</span></span>  
 <span data-ttu-id="a3123-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="a3123-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3123-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3123-111">Child Elements</span></span>  
  
|<span data-ttu-id="a3123-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3123-112">Element</span></span>|<span data-ttu-id="a3123-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a3123-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3123-114">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="a3123-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="a3123-115">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="a3123-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3123-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3123-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a3123-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3123-117">Element</span></span>|<span data-ttu-id="a3123-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a3123-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3123-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="a3123-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="a3123-120">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="a3123-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3123-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3123-121">See also</span></span>
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
