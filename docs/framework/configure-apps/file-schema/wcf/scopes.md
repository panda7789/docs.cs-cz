---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399941"
---
# \<scopes>
<span data-ttu-id="e9c9d-101">Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="e9c9d-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="e9c9d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9c9d-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9c9d-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9c9d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e9c9d-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9c9d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9c9d-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9c9d-105">Attributes</span></span>  
 <span data-ttu-id="e9c9d-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="e9c9d-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9c9d-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9c9d-107">Child Elements</span></span>  
  
|<span data-ttu-id="e9c9d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="e9c9d-108">Attribute</span></span>|<span data-ttu-id="e9c9d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e9c9d-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="e9c9d-110">Přidá informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="e9c9d-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9c9d-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9c9d-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e9c9d-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9c9d-112">Element</span></span>|<span data-ttu-id="e9c9d-113">Description</span><span class="sxs-lookup"><span data-stu-id="e9c9d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="e9c9d-114">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="e9c9d-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9c9d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9c9d-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
