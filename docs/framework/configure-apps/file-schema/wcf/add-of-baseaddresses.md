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
ms.workload: dotnet
ms.openlocfilehash: 516c615248c95ef3107664b996f457fb80b46373
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="d64f9-102">&lt;add&gt; – &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="d64f9-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="d64f9-103">Představuje konfiguraci element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="d64f9-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="d64f9-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d64f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d64f9-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="d64f9-105">\<client></span></span>  
<span data-ttu-id="d64f9-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="d64f9-106">\<endpoint></span></span>  
<span data-ttu-id="d64f9-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="d64f9-107">\<host></span></span>  
<span data-ttu-id="d64f9-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d64f9-108">\<baseAddresses></span></span>  
<span data-ttu-id="d64f9-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="d64f9-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d64f9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d64f9-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="d64f9-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d64f9-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d64f9-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d64f9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d64f9-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d64f9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d64f9-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d64f9-114">Attributes</span></span>  
  
|<span data-ttu-id="d64f9-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d64f9-115">Attribute</span></span>|<span data-ttu-id="d64f9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d64f9-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="d64f9-117">Řetězec, který určuje základní adresu použitou touto hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="d64f9-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d64f9-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d64f9-118">Child Elements</span></span>  
 <span data-ttu-id="d64f9-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="d64f9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d64f9-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d64f9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d64f9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d64f9-121">Element</span></span>|<span data-ttu-id="d64f9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d64f9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d64f9-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d64f9-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="d64f9-124">Kolekce `baseAddress` elementy.</span><span class="sxs-lookup"><span data-stu-id="d64f9-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d64f9-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d64f9-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="d64f9-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="d64f9-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
