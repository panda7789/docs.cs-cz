---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 7d0afd638e9a311b69ff47b6789d5fde093945ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212099"
---
# <a name="baseaddresses"></a><span data-ttu-id="98767-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="98767-101">\<baseAddresses></span></span>
<span data-ttu-id="98767-102">Představuje kolekci `baseAddress` elementy, které jsou základními adresami hostitele služby v prostředí Self-Hosted.</span><span class="sxs-lookup"><span data-stu-id="98767-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="98767-103">Pokud základní adresa je k dispozici, můžete být koncové body nakonfigurované adresy relativní k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="98767-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="98767-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="98767-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="98767-105">\<client></span><span class="sxs-lookup"><span data-stu-id="98767-105">\<client></span></span>  
<span data-ttu-id="98767-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="98767-106">\<endpoint></span></span>  
<span data-ttu-id="98767-107">\<host></span><span class="sxs-lookup"><span data-stu-id="98767-107">\<host></span></span>  
<span data-ttu-id="98767-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="98767-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98767-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98767-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="98767-110">Type</span><span class="sxs-lookup"><span data-stu-id="98767-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98767-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="98767-111">Attributes and Elements</span></span>  
 <span data-ttu-id="98767-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="98767-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98767-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="98767-113">Attributes</span></span>  
 <span data-ttu-id="98767-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="98767-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="98767-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="98767-115">Child Elements</span></span>  
  
|<span data-ttu-id="98767-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="98767-116">Element</span></span>|<span data-ttu-id="98767-117">Popis</span><span class="sxs-lookup"><span data-stu-id="98767-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98767-118">\<add></span><span class="sxs-lookup"><span data-stu-id="98767-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="98767-119">Konfigurační element určující základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="98767-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98767-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="98767-120">Parent Elements</span></span>  
  
|<span data-ttu-id="98767-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="98767-121">Element</span></span>|<span data-ttu-id="98767-122">Popis</span><span class="sxs-lookup"><span data-stu-id="98767-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98767-123">\<host></span><span class="sxs-lookup"><span data-stu-id="98767-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="98767-124">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="98767-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98767-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98767-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="98767-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="98767-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
