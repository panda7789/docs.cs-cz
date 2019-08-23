---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 462a06e5a773310b6364838ae2ebc14da0a2ee1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925892"
---
# <a name="defaultports"></a><span data-ttu-id="adbe2-101">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="adbe2-101">\<defaultPorts></span></span>
<span data-ttu-id="adbe2-102">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="adbe2-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="adbe2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="adbe2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="adbe2-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="adbe2-104">\<behaviors></span></span>  
<span data-ttu-id="adbe2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="adbe2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="adbe2-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="adbe2-106">\<behavior></span></span>  
<span data-ttu-id="adbe2-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="adbe2-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="adbe2-108">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="adbe2-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adbe2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adbe2-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adbe2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="adbe2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="adbe2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="adbe2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adbe2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="adbe2-112">Attributes</span></span>  
 <span data-ttu-id="adbe2-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="adbe2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="adbe2-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="adbe2-114">Child Elements</span></span>  
  
|<span data-ttu-id="adbe2-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="adbe2-115">Element</span></span>|<span data-ttu-id="adbe2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="adbe2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adbe2-117">\<Přidat > \<> defaultPorts</span><span class="sxs-lookup"><span data-stu-id="adbe2-117">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="adbe2-118">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="adbe2-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adbe2-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="adbe2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="adbe2-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="adbe2-120">Element</span></span>|<span data-ttu-id="adbe2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="adbe2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adbe2-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="adbe2-122">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="adbe2-123">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="adbe2-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adbe2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adbe2-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
