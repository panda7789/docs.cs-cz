---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855339"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="ea7c7-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="ea7c7-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="ea7c7-102">Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="ea7c7-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="ea7c7-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea7c7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea7c7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ea7c7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ea7c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="ea7c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="ea7c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dynamicEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="ea7c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7c7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea7c7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea7c7-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ea7c7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea7c7-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ea7c7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea7c7-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ea7c7-110">Attributes</span></span>  
 <span data-ttu-id="ea7c7-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="ea7c7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea7c7-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ea7c7-112">Child Elements</span></span>  
  
|<span data-ttu-id="ea7c7-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea7c7-113">Element</span></span>|<span data-ttu-id="ea7c7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ea7c7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea7c7-115">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="ea7c7-115">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="ea7c7-116">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="ea7c7-116">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea7c7-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ea7c7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ea7c7-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea7c7-118">Element</span></span>|<span data-ttu-id="ea7c7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ea7c7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea7c7-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ea7c7-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ea7c7-121">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="ea7c7-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea7c7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea7c7-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
