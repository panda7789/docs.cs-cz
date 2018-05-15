---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2f7de066a1b91e9fa22fbe0213e221c6f4bbe617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="a31b9-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="a31b9-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="a31b9-103">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="a31b9-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="a31b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a31b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a31b9-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a31b9-105">\<behaviors></span></span>  
<span data-ttu-id="a31b9-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a31b9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a31b9-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a31b9-107">\<behavior></span></span>  
<span data-ttu-id="a31b9-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="a31b9-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="a31b9-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="a31b9-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31b9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a31b9-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a31b9-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a31b9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a31b9-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a31b9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a31b9-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a31b9-113">Attributes</span></span>  
 <span data-ttu-id="a31b9-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="a31b9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a31b9-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a31b9-115">Child Elements</span></span>  
  
|<span data-ttu-id="a31b9-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a31b9-116">Element</span></span>|<span data-ttu-id="a31b9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a31b9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a31b9-118">\<Přidat > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="a31b9-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="a31b9-119">Koncový bod výchozí komunikace, která klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="a31b9-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a31b9-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a31b9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a31b9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a31b9-121">Element</span></span>|<span data-ttu-id="a31b9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a31b9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a31b9-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="a31b9-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="a31b9-124">Seznam výchozích portů.</span><span class="sxs-lookup"><span data-stu-id="a31b9-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a31b9-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a31b9-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
