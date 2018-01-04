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
ms.workload: dotnet
ms.openlocfilehash: 1efe61bf5f4276836c65e9c81d316dc0664f3de2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="5ea79-102">&lt;add&gt; – &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="5ea79-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="5ea79-103">Koncový bod výchozí komunikace, která klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="5ea79-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="5ea79-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5ea79-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ea79-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5ea79-105">\<behaviors></span></span>  
<span data-ttu-id="5ea79-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5ea79-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5ea79-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5ea79-107">\<behavior></span></span>  
<span data-ttu-id="5ea79-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="5ea79-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="5ea79-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="5ea79-109">\<defaultPorts></span></span>  
<span data-ttu-id="5ea79-110">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="5ea79-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea79-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ea79-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea79-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ea79-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ea79-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ea79-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea79-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ea79-114">Attributes</span></span>  
  
|<span data-ttu-id="5ea79-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5ea79-115">Attribute</span></span>|<span data-ttu-id="5ea79-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea79-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ea79-117">port</span><span class="sxs-lookup"><span data-stu-id="5ea79-117">port</span></span>|<span data-ttu-id="5ea79-118">Celé číslo, které určuje výchozí číslo portu komunikace</span><span class="sxs-lookup"><span data-stu-id="5ea79-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="5ea79-119">scheme</span><span class="sxs-lookup"><span data-stu-id="5ea79-119">scheme</span></span>|<span data-ttu-id="5ea79-120">Řetězec, který určuje skupinu nastavení protokolu přidružený k portu komunikace.</span><span class="sxs-lookup"><span data-stu-id="5ea79-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea79-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ea79-121">Child Elements</span></span>  
 <span data-ttu-id="5ea79-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ea79-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea79-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ea79-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea79-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ea79-124">Element</span></span>|<span data-ttu-id="5ea79-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea79-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ea79-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="5ea79-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="5ea79-127">Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="5ea79-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ea79-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ea79-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
