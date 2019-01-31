---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 786a70e8c686497e91492938a4d0796db4f6dd91
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269793"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="bf612-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="bf612-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="bf612-102">Tento prvek konfigurace definuje standardní koncový bod, který obsahuje informace, které umožní, aby aplikace fungovala jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="bf612-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="bf612-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf612-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf612-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="bf612-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf612-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf612-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf612-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf612-106">Attributes and Elements</span></span>  
 <span data-ttu-id="bf612-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf612-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf612-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf612-108">Attributes</span></span>  
 <span data-ttu-id="bf612-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf612-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf612-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf612-110">Child Elements</span></span>  
  
|<span data-ttu-id="bf612-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf612-111">Element</span></span>|<span data-ttu-id="bf612-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bf612-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf612-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="bf612-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="bf612-114">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="bf612-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf612-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf612-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bf612-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf612-116">Element</span></span>|<span data-ttu-id="bf612-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bf612-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf612-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="bf612-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="bf612-119">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="bf612-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf612-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf612-120">See also</span></span>
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
