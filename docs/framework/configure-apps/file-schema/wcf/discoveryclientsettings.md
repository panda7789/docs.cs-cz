---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 5b60c7281b92a487ba3ee275f7405cb82bd6cd87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282240"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="470f5-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="470f5-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="470f5-102">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="470f5-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="470f5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="470f5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="470f5-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="470f5-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="470f5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="470f5-105">Syntax</span></span>  
  
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
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="470f5-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="470f5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="470f5-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="470f5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="470f5-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="470f5-108">Attributes</span></span>  
  
|<span data-ttu-id="470f5-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="470f5-109">Attribute</span></span>|<span data-ttu-id="470f5-110">Popis</span><span class="sxs-lookup"><span data-stu-id="470f5-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="470f5-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="470f5-111">discoveryEndpoint</span></span>|<span data-ttu-id="470f5-112">Řetězec, který obsahuje název koncového bodu zjišťování, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="470f5-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="470f5-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="470f5-113">Child Elements</span></span>  
  
|<span data-ttu-id="470f5-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="470f5-114">Element</span></span>|<span data-ttu-id="470f5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="470f5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="470f5-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="470f5-116">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="470f5-117">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="470f5-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="470f5-118">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="470f5-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="470f5-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="470f5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="470f5-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="470f5-120">Element</span></span>|<span data-ttu-id="470f5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="470f5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="470f5-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="470f5-122">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="470f5-123">Definuje standardní koncový bod, který obsahuje informace, které umožní, aby aplikace fungovala jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="470f5-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="470f5-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="470f5-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
