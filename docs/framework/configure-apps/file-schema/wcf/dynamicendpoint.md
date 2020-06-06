---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855339"
---
# \<dynamicEndpoint>
<span data-ttu-id="32c90-101">Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="32c90-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="32c90-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32c90-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c90-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32c90-103">Attributes and Elements</span></span>  
 <span data-ttu-id="32c90-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32c90-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c90-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="32c90-105">Attributes</span></span>  
 <span data-ttu-id="32c90-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="32c90-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32c90-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32c90-107">Child Elements</span></span>  
  
|<span data-ttu-id="32c90-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="32c90-108">Element</span></span>|<span data-ttu-id="32c90-109">Description</span><span class="sxs-lookup"><span data-stu-id="32c90-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="32c90-110">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="32c90-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32c90-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32c90-111">Parent Elements</span></span>  
  
|<span data-ttu-id="32c90-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="32c90-112">Element</span></span>|<span data-ttu-id="32c90-113">Description</span><span class="sxs-lookup"><span data-stu-id="32c90-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="32c90-114">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="32c90-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32c90-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="32c90-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
