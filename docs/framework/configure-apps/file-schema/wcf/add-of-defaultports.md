---
title: "&lt;add&gt; – &lt;defaultPorts&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2aa63c7a5e730b2fb45f614cb2fe5f88444cee4a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="f8b3b-102">&lt;add&gt; – &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="f8b3b-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="f8b3b-103">Koncový bod výchozí komunikace, která klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="f8b3b-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="f8b3b-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8b3b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-105">\<behaviors></span></span>  
<span data-ttu-id="f8b3b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f8b3b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-107">\<behavior></span></span>  
<span data-ttu-id="f8b3b-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="f8b3b-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-109">\<defaultPorts></span></span>  
<span data-ttu-id="f8b3b-110">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b3b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8b3b-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8b3b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8b3b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f8b3b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f8b3b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8b3b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8b3b-114">Attributes</span></span>  
  
|<span data-ttu-id="f8b3b-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f8b3b-115">Attribute</span></span>|<span data-ttu-id="f8b3b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f8b3b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8b3b-117">port</span><span class="sxs-lookup"><span data-stu-id="f8b3b-117">port</span></span>|<span data-ttu-id="f8b3b-118">Celé číslo, které určuje výchozí číslo portu komunikace</span><span class="sxs-lookup"><span data-stu-id="f8b3b-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="f8b3b-119">scheme</span><span class="sxs-lookup"><span data-stu-id="f8b3b-119">scheme</span></span>|<span data-ttu-id="f8b3b-120">Řetězec, který určuje skupinu nastavení protokolu přidružený k portu komunikace.</span><span class="sxs-lookup"><span data-stu-id="f8b3b-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8b3b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b3b-121">Child Elements</span></span>  
 <span data-ttu-id="f8b3b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="f8b3b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8b3b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b3b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f8b3b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8b3b-124">Element</span></span>|<span data-ttu-id="f8b3b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f8b3b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8b3b-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="f8b3b-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="f8b3b-127">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="f8b3b-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8b3b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8b3b-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
