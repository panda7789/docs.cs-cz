---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399205"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="e65b2-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="e65b2-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="e65b2-102">Umožňuje načtení informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="e65b2-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="e65b2-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e65b2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e65b2-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e65b2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e65b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e65b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e65b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e65b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="e65b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e65b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="e65b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useRequestHeadersForMetadataAddress >**</span><span class="sxs-lookup"><span data-stu-id="e65b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65b2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e65b2-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e65b2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e65b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e65b2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e65b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e65b2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e65b2-112">Attributes</span></span>  
 <span data-ttu-id="e65b2-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="e65b2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e65b2-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e65b2-114">Child Elements</span></span>  
  
|<span data-ttu-id="e65b2-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="e65b2-115">Element</span></span>|<span data-ttu-id="e65b2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e65b2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e65b2-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="e65b2-117">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="e65b2-118">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="e65b2-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e65b2-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e65b2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e65b2-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="e65b2-120">Element</span></span>|<span data-ttu-id="e65b2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e65b2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e65b2-122">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e65b2-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e65b2-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e65b2-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e65b2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e65b2-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
