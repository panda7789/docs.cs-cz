---
title: '&lt;discoveryClientSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd2e9f3fd6d2cd0b99c6b63bc8ad0eefc9ff3e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="13c46-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="13c46-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="13c46-103">Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="13c46-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="13c46-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="13c46-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="13c46-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="13c46-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c46-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13c46-106">Syntax</span></span>  
  
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
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13c46-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13c46-107">Attributes and Elements</span></span>  
 <span data-ttu-id="13c46-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="13c46-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13c46-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="13c46-109">Attributes</span></span>  
  
|<span data-ttu-id="13c46-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="13c46-110">Attribute</span></span>|<span data-ttu-id="13c46-111">Popis</span><span class="sxs-lookup"><span data-stu-id="13c46-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13c46-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="13c46-112">discoveryEndpoint</span></span>|<span data-ttu-id="13c46-113">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.</span><span class="sxs-lookup"><span data-stu-id="13c46-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13c46-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13c46-114">Child Elements</span></span>  
  
|<span data-ttu-id="13c46-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="13c46-115">Element</span></span>|<span data-ttu-id="13c46-116">Popis</span><span class="sxs-lookup"><span data-stu-id="13c46-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13c46-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="13c46-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="13c46-118">Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="13c46-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="13c46-119">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).</span><span class="sxs-lookup"><span data-stu-id="13c46-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13c46-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13c46-120">Parent Elements</span></span>  
  
|<span data-ttu-id="13c46-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="13c46-121">Element</span></span>|<span data-ttu-id="13c46-122">Popis</span><span class="sxs-lookup"><span data-stu-id="13c46-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13c46-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="13c46-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="13c46-124">Definuje standardní koncový bod, který obsahuje informace o povolení aplikace fungovat jako klient programu, můžete najít adresa koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="13c46-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13c46-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="13c46-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
