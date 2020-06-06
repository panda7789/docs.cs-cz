---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855409"
---
# \<discoveryClientSettings>
<span data-ttu-id="48f38-101">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="48f38-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="48f38-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48f38-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48f38-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="48f38-103">Attributes and Elements</span></span>  
 <span data-ttu-id="48f38-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="48f38-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48f38-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="48f38-105">Attributes</span></span>  
  
|<span data-ttu-id="48f38-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="48f38-106">Attribute</span></span>|<span data-ttu-id="48f38-107">Popis</span><span class="sxs-lookup"><span data-stu-id="48f38-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48f38-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="48f38-108">discoveryEndpoint</span></span>|<span data-ttu-id="48f38-109">Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientské aplikaci automaticky vyhledávat zjistitelnou službu a najít její adresu za běhu.</span><span class="sxs-lookup"><span data-stu-id="48f38-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48f38-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="48f38-110">Child Elements</span></span>  
  
|<span data-ttu-id="48f38-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="48f38-111">Element</span></span>|<span data-ttu-id="48f38-112">Description</span><span class="sxs-lookup"><span data-stu-id="48f38-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="48f38-113">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="48f38-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="48f38-114">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="48f38-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48f38-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="48f38-115">Parent Elements</span></span>  
  
|<span data-ttu-id="48f38-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="48f38-116">Element</span></span>|<span data-ttu-id="48f38-117">Description</span><span class="sxs-lookup"><span data-stu-id="48f38-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="48f38-118">Definuje standardní koncový bod, který obsahuje informace, které umožní aplikaci fungovat jako klientský program, který může najít adresu koncového bodu dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="48f38-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48f38-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="48f38-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
