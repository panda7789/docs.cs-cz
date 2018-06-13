---
title: '&lt;add&gt; – &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 3f1b7e8f1f4ab8542270d459ce5020ce4320eea9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754142"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="35d36-102">&lt;add&gt; – &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="35d36-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="35d36-103">Představuje konfiguraci element, který určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="35d36-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="35d36-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35d36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="35d36-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="35d36-105">\<client></span></span>  
<span data-ttu-id="35d36-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="35d36-106">\<endpoint></span></span>  
<span data-ttu-id="35d36-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="35d36-107">\<host></span></span>  
<span data-ttu-id="35d36-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="35d36-108">\<baseAddresses></span></span>  
<span data-ttu-id="35d36-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="35d36-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35d36-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35d36-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="35d36-111">Typ</span><span class="sxs-lookup"><span data-stu-id="35d36-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35d36-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="35d36-112">Attributes and Elements</span></span>  
 <span data-ttu-id="35d36-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="35d36-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35d36-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="35d36-114">Attributes</span></span>  
  
|<span data-ttu-id="35d36-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="35d36-115">Attribute</span></span>|<span data-ttu-id="35d36-116">Popis</span><span class="sxs-lookup"><span data-stu-id="35d36-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="35d36-117">Řetězec, který určuje základní adresu použitou touto hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="35d36-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35d36-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="35d36-118">Child Elements</span></span>  
 <span data-ttu-id="35d36-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="35d36-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35d36-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="35d36-120">Parent Elements</span></span>  
  
|<span data-ttu-id="35d36-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="35d36-121">Element</span></span>|<span data-ttu-id="35d36-122">Popis</span><span class="sxs-lookup"><span data-stu-id="35d36-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35d36-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="35d36-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="35d36-124">Kolekce `baseAddress` elementy.</span><span class="sxs-lookup"><span data-stu-id="35d36-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35d36-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="35d36-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="35d36-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="35d36-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
