---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399205"
---
# \<useRequestHeadersForMetadataAddress>
<span data-ttu-id="41201-101">Umožňuje načtení informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="41201-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="41201-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41201-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41201-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="41201-103">Attributes and Elements</span></span>  
 <span data-ttu-id="41201-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="41201-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41201-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="41201-105">Attributes</span></span>  
 <span data-ttu-id="41201-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="41201-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41201-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="41201-107">Child Elements</span></span>  
  
|<span data-ttu-id="41201-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="41201-108">Element</span></span>|<span data-ttu-id="41201-109">Description</span><span class="sxs-lookup"><span data-stu-id="41201-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="41201-110">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="41201-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41201-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="41201-111">Parent Elements</span></span>  
  
|<span data-ttu-id="41201-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="41201-112">Element</span></span>|<span data-ttu-id="41201-113">Description</span><span class="sxs-lookup"><span data-stu-id="41201-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="41201-114">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="41201-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41201-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="41201-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
