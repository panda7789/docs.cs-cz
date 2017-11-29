---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e24d340364f126d9cf33295d6d36d1b686065a76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="5501f-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="5501f-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="5501f-103">Tento element konfigurace definuje standardní koncový bod, který obsahuje informace o povolení aplikace fungovat jako klient programu, můžete najít adresa koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="5501f-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="5501f-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5501f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5501f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5501f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5501f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5501f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5501f-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5501f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5501f-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5501f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5501f-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="5501f-109">Attributes</span></span>  
 <span data-ttu-id="5501f-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="5501f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5501f-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5501f-111">Child Elements</span></span>  
  
|<span data-ttu-id="5501f-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="5501f-112">Element</span></span>|<span data-ttu-id="5501f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5501f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5501f-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="5501f-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="5501f-115">Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="5501f-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5501f-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5501f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5501f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="5501f-117">Element</span></span>|<span data-ttu-id="5501f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5501f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5501f-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5501f-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5501f-120">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="5501f-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5501f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5501f-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
