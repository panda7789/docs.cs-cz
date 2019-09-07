---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398074"
---
# <a name="defaultports"></a><span data-ttu-id="cd76d-101">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="cd76d-101">\<defaultPorts></span></span>
<span data-ttu-id="cd76d-102">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="cd76d-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="cd76d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd76d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd76d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cd76d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cd76d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cd76d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="cd76d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cd76d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="cd76d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cd76d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="cd76d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="cd76d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="cd76d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultPorts >**</span><span class="sxs-lookup"><span data-stu-id="cd76d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd76d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd76d-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd76d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd76d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cd76d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd76d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd76d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd76d-113">Attributes</span></span>  
 <span data-ttu-id="cd76d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd76d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd76d-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd76d-115">Child Elements</span></span>  
  
|<span data-ttu-id="cd76d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd76d-116">Element</span></span>|<span data-ttu-id="cd76d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="cd76d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd76d-118">\<Přidat > \<> defaultPorts</span><span class="sxs-lookup"><span data-stu-id="cd76d-118">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="cd76d-119">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="cd76d-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd76d-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd76d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cd76d-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd76d-121">Element</span></span>|<span data-ttu-id="cd76d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="cd76d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd76d-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="cd76d-123">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="cd76d-124">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="cd76d-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd76d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd76d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
