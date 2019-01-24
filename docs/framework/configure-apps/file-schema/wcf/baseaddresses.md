---
title: '&lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 34d400e74b24e9eb4140d1b43597b0217b23d80c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730123"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="511ef-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="511ef-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="511ef-103">Představuje kolekci `baseAddress` elementy, které jsou základními adresami hostitele služby v prostředí Self-Hosted.</span><span class="sxs-lookup"><span data-stu-id="511ef-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="511ef-104">Pokud základní adresa je k dispozici, můžete být koncové body nakonfigurované adresy relativní k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="511ef-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="511ef-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="511ef-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="511ef-106">\<client></span><span class="sxs-lookup"><span data-stu-id="511ef-106">\<client></span></span>  
<span data-ttu-id="511ef-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="511ef-107">\<endpoint></span></span>  
<span data-ttu-id="511ef-108">\<host></span><span class="sxs-lookup"><span data-stu-id="511ef-108">\<host></span></span>  
<span data-ttu-id="511ef-109">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="511ef-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511ef-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="511ef-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="511ef-111">Typ</span><span class="sxs-lookup"><span data-stu-id="511ef-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="511ef-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="511ef-112">Attributes and Elements</span></span>  
 <span data-ttu-id="511ef-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="511ef-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="511ef-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="511ef-114">Attributes</span></span>  
 <span data-ttu-id="511ef-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="511ef-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="511ef-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="511ef-116">Child Elements</span></span>  
  
|<span data-ttu-id="511ef-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="511ef-117">Element</span></span>|<span data-ttu-id="511ef-118">Popis</span><span class="sxs-lookup"><span data-stu-id="511ef-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="511ef-119">\<add></span><span class="sxs-lookup"><span data-stu-id="511ef-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="511ef-120">Konfigurační element určující základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="511ef-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="511ef-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="511ef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="511ef-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="511ef-122">Element</span></span>|<span data-ttu-id="511ef-123">Popis</span><span class="sxs-lookup"><span data-stu-id="511ef-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="511ef-124">\<host></span><span class="sxs-lookup"><span data-stu-id="511ef-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="511ef-125">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="511ef-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="511ef-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="511ef-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="511ef-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="511ef-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
