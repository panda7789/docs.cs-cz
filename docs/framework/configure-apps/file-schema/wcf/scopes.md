---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399941"
---
# <a name="scopes"></a><span data-ttu-id="14b20-101">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="14b20-101">\<scopes></span></span>
<span data-ttu-id="14b20-102">Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="14b20-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="14b20-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="14b20-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14b20-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="14b20-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="14b20-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="14b20-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="14b20-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="14b20-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="14b20-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="14b20-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="14b20-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="14b20-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="14b20-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> oborů**</span><span class="sxs-lookup"><span data-stu-id="14b20-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b20-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14b20-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14b20-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14b20-111">Attributes and Elements</span></span>  
 <span data-ttu-id="14b20-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14b20-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14b20-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="14b20-113">Attributes</span></span>  
 <span data-ttu-id="14b20-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="14b20-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14b20-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14b20-115">Child Elements</span></span>  
  
|<span data-ttu-id="14b20-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="14b20-116">Attribute</span></span>|<span data-ttu-id="14b20-117">Popis</span><span class="sxs-lookup"><span data-stu-id="14b20-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="14b20-118">\<add></span><span class="sxs-lookup"><span data-stu-id="14b20-118">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="14b20-119">Přidá informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="14b20-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14b20-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14b20-120">Parent Elements</span></span>  
  
|<span data-ttu-id="14b20-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="14b20-121">Element</span></span>|<span data-ttu-id="14b20-122">Popis</span><span class="sxs-lookup"><span data-stu-id="14b20-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14b20-123">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="14b20-123">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="14b20-124">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="14b20-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14b20-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14b20-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
