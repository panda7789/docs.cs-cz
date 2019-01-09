---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 0af5dee41c6adf560c90874e6e9a44b62c5decc6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147345"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="6d5d1-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="6d5d1-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="6d5d1-103">Představuje kolekci `baseAddress` elementy, které jsou základními adresami hostitele služby v prostředí Self-Hosted.</span><span class="sxs-lookup"><span data-stu-id="6d5d1-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="6d5d1-104">Pokud základní adresa je k dispozici, můžete být koncové body nakonfigurované adresy relativní k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="6d5d1-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="6d5d1-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6d5d1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6d5d1-106">\<klient ></span><span class="sxs-lookup"><span data-stu-id="6d5d1-106">\<client></span></span>  
<span data-ttu-id="6d5d1-107">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="6d5d1-107">\<endpoint></span></span>  
<span data-ttu-id="6d5d1-108">\<Hostitel ></span><span class="sxs-lookup"><span data-stu-id="6d5d1-108">\<host></span></span>  
<span data-ttu-id="6d5d1-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="6d5d1-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d5d1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d5d1-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="6d5d1-111">Typ</span><span class="sxs-lookup"><span data-stu-id="6d5d1-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d5d1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d5d1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6d5d1-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d5d1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d5d1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d5d1-114">Attributes</span></span>  
 <span data-ttu-id="6d5d1-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d5d1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6d5d1-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d5d1-116">Child Elements</span></span>  
  
|<span data-ttu-id="6d5d1-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d5d1-117">Element</span></span>|<span data-ttu-id="6d5d1-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6d5d1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d5d1-119">\<add></span><span class="sxs-lookup"><span data-stu-id="6d5d1-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="6d5d1-120">Konfigurační element určující základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="6d5d1-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d5d1-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d5d1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6d5d1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d5d1-122">Element</span></span>|<span data-ttu-id="6d5d1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6d5d1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d5d1-124">\<Hostitel ></span><span class="sxs-lookup"><span data-stu-id="6d5d1-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="6d5d1-125">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="6d5d1-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d5d1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d5d1-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="6d5d1-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="6d5d1-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
