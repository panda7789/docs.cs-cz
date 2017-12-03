---
title: "&lt;add&gt; – &lt;baseAddresses&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf417653652c2a0f28fe5c6491a7da9949678140
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="4f3b4-102">&lt;add&gt; – &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="4f3b4-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="4f3b4-103">Představuje konfiguraci element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="4f3b4-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="4f3b4-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f3b4-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-105">\<client></span></span>  
<span data-ttu-id="4f3b4-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-106">\<endpoint></span></span>  
<span data-ttu-id="4f3b4-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-107">\<host></span></span>  
<span data-ttu-id="4f3b4-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-108">\<baseAddresses></span></span>  
<span data-ttu-id="4f3b4-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f3b4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f3b4-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="4f3b4-111">Typ</span><span class="sxs-lookup"><span data-stu-id="4f3b4-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f3b4-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4f3b4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f3b4-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4f3b4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f3b4-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4f3b4-114">Attributes</span></span>  
  
|<span data-ttu-id="4f3b4-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4f3b4-115">Attribute</span></span>|<span data-ttu-id="4f3b4-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4f3b4-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="4f3b4-117">Řetězec, který určuje základní adresu použitou touto hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="4f3b4-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f3b4-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4f3b4-118">Child Elements</span></span>  
 <span data-ttu-id="4f3b4-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="4f3b4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f3b4-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4f3b4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4f3b4-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f3b4-121">Element</span></span>|<span data-ttu-id="4f3b4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4f3b4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f3b4-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="4f3b4-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="4f3b4-124">Kolekce `baseAddress` elementy.</span><span class="sxs-lookup"><span data-stu-id="4f3b4-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f3b4-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f3b4-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="4f3b4-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="4f3b4-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
