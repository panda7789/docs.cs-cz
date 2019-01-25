---
title: '&lt;add&gt; – &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 31edf570a7374a4b4fe31760d35ec196ecfcb3c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553565"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="8cff6-102">&lt;add&gt; – &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="8cff6-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="8cff6-103">Představuje konfigurační element určující základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="8cff6-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="8cff6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8cff6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cff6-105">\<client></span><span class="sxs-lookup"><span data-stu-id="8cff6-105">\<client></span></span>  
<span data-ttu-id="8cff6-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="8cff6-106">\<endpoint></span></span>  
<span data-ttu-id="8cff6-107">\<host></span><span class="sxs-lookup"><span data-stu-id="8cff6-107">\<host></span></span>  
<span data-ttu-id="8cff6-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="8cff6-108">\<baseAddresses></span></span>  
<span data-ttu-id="8cff6-109">\<Vlastnost baseAddress ></span><span class="sxs-lookup"><span data-stu-id="8cff6-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cff6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cff6-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="8cff6-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8cff6-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cff6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8cff6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8cff6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8cff6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cff6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="8cff6-114">Attributes</span></span>  
  
|<span data-ttu-id="8cff6-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="8cff6-115">Attribute</span></span>|<span data-ttu-id="8cff6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8cff6-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="8cff6-117">Řetězec, který určuje základní adresu použitou hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="8cff6-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cff6-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8cff6-118">Child Elements</span></span>  
 <span data-ttu-id="8cff6-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="8cff6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cff6-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8cff6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8cff6-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="8cff6-121">Element</span></span>|<span data-ttu-id="8cff6-122">Popis</span><span class="sxs-lookup"><span data-stu-id="8cff6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cff6-123">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="8cff6-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="8cff6-124">Kolekce `baseAddress` elementy.</span><span class="sxs-lookup"><span data-stu-id="8cff6-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cff6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cff6-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="8cff6-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="8cff6-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
