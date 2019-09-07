---
title: <add> z <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398310"
---
# <a name="add-of-scopes"></a><span data-ttu-id="5a53c-102">\<Přidat > \<oborů ></span><span class="sxs-lookup"><span data-stu-id="5a53c-102">\<add> of \<scopes></span></span>
<span data-ttu-id="5a53c-103">Přidá identifikátor URI vlastního rozsahu, který lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="5a53c-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="5a53c-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a53c-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a53c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5a53c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5a53c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5a53c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="5a53c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> oborů**](scopes.md)</span><span class="sxs-lookup"><span data-stu-id="5a53c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)</span></span>\
<span data-ttu-id="5a53c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="5a53c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a53c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a53c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a53c-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a53c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5a53c-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a53c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a53c-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a53c-115">Attributes</span></span>  
  
|<span data-ttu-id="5a53c-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a53c-116">Attribute</span></span>|<span data-ttu-id="5a53c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5a53c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a53c-118">rozsah</span><span class="sxs-lookup"><span data-stu-id="5a53c-118">scope</span></span>|<span data-ttu-id="5a53c-119">Identifikátor URI, který obsahuje informace o oboru pro koncový bod, který lze použít v porovnání kritérií pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="5a53c-119">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a53c-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a53c-120">Child Elements</span></span>  
 <span data-ttu-id="5a53c-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a53c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a53c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a53c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5a53c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a53c-123">Element</span></span>|<span data-ttu-id="5a53c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="5a53c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a53c-125">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="5a53c-125">\<scopes></span></span>](scopes.md)|<span data-ttu-id="5a53c-126">Obsahuje kolekci prvků konfigurace, které určují identifikátory URI vlastního oboru, které lze použít k filtrování koncových bodů služby během dotazu.</span><span class="sxs-lookup"><span data-stu-id="5a53c-126">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a53c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a53c-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
