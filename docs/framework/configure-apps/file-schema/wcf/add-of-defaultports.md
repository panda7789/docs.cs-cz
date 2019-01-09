---
title: '&lt;add&gt; – &lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 0932ef9afacb6278c4857dcfd6ba545595ff8f9d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147717"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="938fc-102">&lt;add&gt; – &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="938fc-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="938fc-103">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="938fc-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="938fc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="938fc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="938fc-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="938fc-105">\<behaviors></span></span>  
<span data-ttu-id="938fc-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="938fc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="938fc-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="938fc-107">\<behavior></span></span>  
<span data-ttu-id="938fc-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="938fc-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="938fc-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="938fc-109">\<defaultPorts></span></span>  
<span data-ttu-id="938fc-110">\<add></span><span class="sxs-lookup"><span data-stu-id="938fc-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938fc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="938fc-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="938fc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="938fc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="938fc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="938fc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="938fc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="938fc-114">Attributes</span></span>  
  
|<span data-ttu-id="938fc-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="938fc-115">Attribute</span></span>|<span data-ttu-id="938fc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="938fc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="938fc-117">port</span><span class="sxs-lookup"><span data-stu-id="938fc-117">port</span></span>|<span data-ttu-id="938fc-118">Celé číslo, které určuje výchozí číslo komunikačního portu</span><span class="sxs-lookup"><span data-stu-id="938fc-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="938fc-119">scheme</span><span class="sxs-lookup"><span data-stu-id="938fc-119">scheme</span></span>|<span data-ttu-id="938fc-120">Řetězec, který určuje skupinu nastavení protokolu přidružené komunikaci portu.</span><span class="sxs-lookup"><span data-stu-id="938fc-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="938fc-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="938fc-121">Child Elements</span></span>  
 <span data-ttu-id="938fc-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="938fc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="938fc-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="938fc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="938fc-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="938fc-124">Element</span></span>|<span data-ttu-id="938fc-125">Popis</span><span class="sxs-lookup"><span data-stu-id="938fc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="938fc-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="938fc-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="938fc-127">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="938fc-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="938fc-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="938fc-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
