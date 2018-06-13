---
title: '&lt;add&gt; – &lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 28ddc98bd66c1f74f857448aa710d3998ddbd3dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748747"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="cd183-102">&lt;add&gt; – &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="cd183-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="cd183-103">Koncový bod výchozí komunikace, která klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="cd183-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="cd183-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cd183-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd183-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cd183-105">\<behaviors></span></span>  
<span data-ttu-id="cd183-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cd183-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cd183-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cd183-107">\<behavior></span></span>  
<span data-ttu-id="cd183-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="cd183-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="cd183-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="cd183-109">\<defaultPorts></span></span>  
<span data-ttu-id="cd183-110">\<add></span><span class="sxs-lookup"><span data-stu-id="cd183-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd183-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd183-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd183-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd183-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cd183-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd183-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd183-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd183-114">Attributes</span></span>  
  
|<span data-ttu-id="cd183-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="cd183-115">Attribute</span></span>|<span data-ttu-id="cd183-116">Popis</span><span class="sxs-lookup"><span data-stu-id="cd183-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd183-117">port</span><span class="sxs-lookup"><span data-stu-id="cd183-117">port</span></span>|<span data-ttu-id="cd183-118">Celé číslo, které určuje výchozí číslo portu komunikace</span><span class="sxs-lookup"><span data-stu-id="cd183-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="cd183-119">scheme</span><span class="sxs-lookup"><span data-stu-id="cd183-119">scheme</span></span>|<span data-ttu-id="cd183-120">Řetězec, který určuje skupinu nastavení protokolu přidružený k portu komunikace.</span><span class="sxs-lookup"><span data-stu-id="cd183-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd183-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd183-121">Child Elements</span></span>  
 <span data-ttu-id="cd183-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd183-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd183-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd183-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cd183-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd183-124">Element</span></span>|<span data-ttu-id="cd183-125">Popis</span><span class="sxs-lookup"><span data-stu-id="cd183-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd183-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="cd183-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="cd183-127">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="cd183-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd183-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd183-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
