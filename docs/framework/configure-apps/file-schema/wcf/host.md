---
title: '&lt;hostitele&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a><span data-ttu-id="b4373-102">&lt;hostitele&gt;</span><span class="sxs-lookup"><span data-stu-id="b4373-102">&lt;host&gt;</span></span>
<span data-ttu-id="b4373-103">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="b4373-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="b4373-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b4373-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b4373-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="b4373-105">\<services></span></span>  
<span data-ttu-id="b4373-106">\<služby ></span><span class="sxs-lookup"><span data-stu-id="b4373-106">\<service></span></span>  
<span data-ttu-id="b4373-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="b4373-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4373-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4373-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="b4373-109">Typ</span><span class="sxs-lookup"><span data-stu-id="b4373-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4373-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b4373-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b4373-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b4373-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4373-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b4373-112">Attributes</span></span>  
 <span data-ttu-id="b4373-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="b4373-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4373-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b4373-114">Child Elements</span></span>  
  
|<span data-ttu-id="b4373-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="b4373-115">Element</span></span>|<span data-ttu-id="b4373-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b4373-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4373-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="b4373-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="b4373-118">Kolekce `baseAddress` prvky, které určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="b4373-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="b4373-119">\<časové limity ></span><span class="sxs-lookup"><span data-stu-id="b4373-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="b4373-120">Konfigurace element, který určuje dobu dobu povolenou pro hostitele služby otevřete nebo zavřete.</span><span class="sxs-lookup"><span data-stu-id="b4373-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4373-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b4373-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b4373-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="b4373-122">Element</span></span>|<span data-ttu-id="b4373-123">Popis</span><span class="sxs-lookup"><span data-stu-id="b4373-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4373-124">\<služby ></span><span class="sxs-lookup"><span data-stu-id="b4373-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="b4373-125">Určuje nastavení pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="b4373-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4373-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4373-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="b4373-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="b4373-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
