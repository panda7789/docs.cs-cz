---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398074"
---
# \<defaultPorts>
<span data-ttu-id="fad0a-101">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="fad0a-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="fad0a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fad0a-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fad0a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fad0a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fad0a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fad0a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fad0a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="fad0a-105">Attributes</span></span>  
 <span data-ttu-id="fad0a-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="fad0a-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fad0a-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fad0a-107">Child Elements</span></span>  
  
|<span data-ttu-id="fad0a-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="fad0a-108">Element</span></span>|<span data-ttu-id="fad0a-109">Description</span><span class="sxs-lookup"><span data-stu-id="fad0a-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fad0a-110">\<add>tohoto\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="fad0a-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="fad0a-111">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="fad0a-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fad0a-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fad0a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fad0a-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="fad0a-113">Element</span></span>|<span data-ttu-id="fad0a-114">Description</span><span class="sxs-lookup"><span data-stu-id="fad0a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="fad0a-115">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="fad0a-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fad0a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fad0a-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
