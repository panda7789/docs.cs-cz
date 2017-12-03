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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e780e1975aecc80ea458ec6a86fca61e4ad22448
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="2bd02-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2bd02-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="2bd02-103">Tento element konfigurace definuje standardní koncový bod, který obsahuje informace o povolení aplikace fungovat jako klient programu, můžete najít adresa koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="2bd02-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="2bd02-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2bd02-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2bd02-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2bd02-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd02-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bd02-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bd02-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2bd02-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2bd02-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2bd02-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bd02-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="2bd02-109">Attributes</span></span>  
 <span data-ttu-id="2bd02-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="2bd02-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2bd02-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2bd02-111">Child Elements</span></span>  
  
|<span data-ttu-id="2bd02-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bd02-112">Element</span></span>|<span data-ttu-id="2bd02-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2bd02-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bd02-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="2bd02-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="2bd02-115">Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="2bd02-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bd02-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2bd02-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2bd02-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bd02-117">Element</span></span>|<span data-ttu-id="2bd02-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2bd02-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bd02-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2bd02-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2bd02-120">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="2bd02-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bd02-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bd02-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
