---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 3dc7fb19c5c7729620a5d9f3df1111b2dbdacf78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925839"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="53cfb-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="53cfb-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="53cfb-102">Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="53cfb-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="53cfb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="53cfb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="53cfb-104">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="53cfb-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53cfb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53cfb-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53cfb-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53cfb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="53cfb-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53cfb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53cfb-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="53cfb-108">Attributes</span></span>  
 <span data-ttu-id="53cfb-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="53cfb-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="53cfb-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53cfb-110">Child Elements</span></span>  
  
|<span data-ttu-id="53cfb-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="53cfb-111">Element</span></span>|<span data-ttu-id="53cfb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="53cfb-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53cfb-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="53cfb-113">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="53cfb-114">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="53cfb-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53cfb-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53cfb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="53cfb-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="53cfb-116">Element</span></span>|<span data-ttu-id="53cfb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="53cfb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53cfb-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="53cfb-118">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="53cfb-119">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="53cfb-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53cfb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53cfb-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
