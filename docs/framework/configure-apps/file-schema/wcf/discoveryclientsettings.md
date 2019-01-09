---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: bb443334e0713464e64ec9297bbab4ad11eda723
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145052"
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="a66cc-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="a66cc-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="a66cc-103">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="a66cc-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="a66cc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a66cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a66cc-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a66cc-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66cc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a66cc-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a66cc-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a66cc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a66cc-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a66cc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a66cc-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a66cc-109">Attributes</span></span>  
  
|<span data-ttu-id="a66cc-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="a66cc-110">Attribute</span></span>|<span data-ttu-id="a66cc-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a66cc-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a66cc-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="a66cc-112">discoveryEndpoint</span></span>|<span data-ttu-id="a66cc-113">Řetězec, který obsahuje název koncového bodu zjišťování, která umožňuje klientské aplikaci automaticky vyhledávat zjistitelné služby a najít adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="a66cc-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a66cc-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a66cc-114">Child Elements</span></span>  
  
|<span data-ttu-id="a66cc-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="a66cc-115">Element</span></span>|<span data-ttu-id="a66cc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a66cc-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a66cc-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a66cc-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="a66cc-118">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="a66cc-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="a66cc-119">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="a66cc-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a66cc-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a66cc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a66cc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a66cc-121">Element</span></span>|<span data-ttu-id="a66cc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a66cc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a66cc-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a66cc-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="a66cc-124">Definuje standardní koncový bod, který obsahuje informace, které umožní, aby aplikace fungovala jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="a66cc-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a66cc-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a66cc-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
