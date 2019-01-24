---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2c742f98315c0e497ac4117953424bae913cb5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614494"
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="7fdeb-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="7fdeb-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="7fdeb-103">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fdeb-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="7fdeb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7fdeb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7fdeb-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7fdeb-105">\<behaviors></span></span>  
<span data-ttu-id="7fdeb-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7fdeb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7fdeb-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7fdeb-107">\<behavior></span></span>  
<span data-ttu-id="7fdeb-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="7fdeb-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="7fdeb-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="7fdeb-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdeb-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fdeb-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fdeb-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7fdeb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7fdeb-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7fdeb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fdeb-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7fdeb-113">Attributes</span></span>  
 <span data-ttu-id="7fdeb-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="7fdeb-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7fdeb-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7fdeb-115">Child Elements</span></span>  
  
|<span data-ttu-id="7fdeb-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="7fdeb-116">Element</span></span>|<span data-ttu-id="7fdeb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7fdeb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fdeb-118">\<Přidat > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="7fdeb-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="7fdeb-119">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fdeb-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fdeb-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7fdeb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7fdeb-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="7fdeb-121">Element</span></span>|<span data-ttu-id="7fdeb-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7fdeb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fdeb-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="7fdeb-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="7fdeb-124">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="7fdeb-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fdeb-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fdeb-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
