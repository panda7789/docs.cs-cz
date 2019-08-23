---
title: <add> z <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926710"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="e660e-102">\<Přidat > \<> defaultPorts</span><span class="sxs-lookup"><span data-stu-id="e660e-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="e660e-103">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="e660e-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="e660e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e660e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e660e-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e660e-105">\<behaviors></span></span>  
<span data-ttu-id="e660e-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e660e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e660e-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e660e-107">\<behavior></span></span>  
<span data-ttu-id="e660e-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="e660e-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="e660e-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="e660e-109">\<defaultPorts></span></span>  
<span data-ttu-id="e660e-110">\<add></span><span class="sxs-lookup"><span data-stu-id="e660e-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e660e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e660e-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e660e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e660e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e660e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e660e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e660e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="e660e-114">Attributes</span></span>  
  
|<span data-ttu-id="e660e-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="e660e-115">Attribute</span></span>|<span data-ttu-id="e660e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e660e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e660e-117">port</span><span class="sxs-lookup"><span data-stu-id="e660e-117">port</span></span>|<span data-ttu-id="e660e-118">Celé číslo, které určuje výchozí číslo komunikačního portu</span><span class="sxs-lookup"><span data-stu-id="e660e-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="e660e-119">scheme</span><span class="sxs-lookup"><span data-stu-id="e660e-119">scheme</span></span>|<span data-ttu-id="e660e-120">Řetězec, který určuje skupinu nastavení protokolu, která je přidružena k komunikačnímu portu.</span><span class="sxs-lookup"><span data-stu-id="e660e-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e660e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e660e-121">Child Elements</span></span>  
 <span data-ttu-id="e660e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="e660e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e660e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e660e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e660e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e660e-124">Element</span></span>|<span data-ttu-id="e660e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e660e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e660e-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="e660e-126">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="e660e-127">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="e660e-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e660e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e660e-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
