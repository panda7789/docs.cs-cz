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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e941b63e42af9237388df6be8223acbad8db745
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="ccb10-102">&lt;add&gt; – &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="ccb10-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="ccb10-103">Představuje konfiguraci element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="ccb10-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="ccb10-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ccb10-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccb10-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="ccb10-105">\<client></span></span>  
<span data-ttu-id="ccb10-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="ccb10-106">\<endpoint></span></span>  
<span data-ttu-id="ccb10-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="ccb10-107">\<host></span></span>  
<span data-ttu-id="ccb10-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="ccb10-108">\<baseAddresses></span></span>  
<span data-ttu-id="ccb10-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="ccb10-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb10-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccb10-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="ccb10-111">Typ</span><span class="sxs-lookup"><span data-stu-id="ccb10-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccb10-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ccb10-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ccb10-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ccb10-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccb10-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ccb10-114">Attributes</span></span>  
  
|<span data-ttu-id="ccb10-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="ccb10-115">Attribute</span></span>|<span data-ttu-id="ccb10-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ccb10-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="ccb10-117">Řetězec, který určuje základní adresu použitou touto hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="ccb10-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccb10-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ccb10-118">Child Elements</span></span>  
 <span data-ttu-id="ccb10-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="ccb10-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccb10-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ccb10-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ccb10-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="ccb10-121">Element</span></span>|<span data-ttu-id="ccb10-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ccb10-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccb10-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="ccb10-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="ccb10-124">Kolekce `baseAddress` elementy.</span><span class="sxs-lookup"><span data-stu-id="ccb10-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccb10-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccb10-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="ccb10-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="ccb10-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
