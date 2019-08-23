---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926414"
---
# <a name="baseaddresses"></a><span data-ttu-id="f3ffc-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="f3ffc-101">\<baseAddresses></span></span>
<span data-ttu-id="f3ffc-102">Představuje kolekci `baseAddress` prvků, které jsou základními adresami hostitele služby v prostředí s místním hostováním.</span><span class="sxs-lookup"><span data-stu-id="f3ffc-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="f3ffc-103">Pokud je k dispozici základní adresa, lze koncovým bodům nakonfigurovat adresy relativní vzhledem k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="f3ffc-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="f3ffc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f3ffc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3ffc-105">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="f3ffc-105">\<client></span></span>  
<span data-ttu-id="f3ffc-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="f3ffc-106">\<endpoint></span></span>  
<span data-ttu-id="f3ffc-107">\<host></span><span class="sxs-lookup"><span data-stu-id="f3ffc-107">\<host></span></span>  
<span data-ttu-id="f3ffc-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="f3ffc-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ffc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3ffc-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="f3ffc-110">type</span><span class="sxs-lookup"><span data-stu-id="f3ffc-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3ffc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3ffc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f3ffc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3ffc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3ffc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3ffc-113">Attributes</span></span>  
 <span data-ttu-id="f3ffc-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3ffc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3ffc-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3ffc-115">Child Elements</span></span>  
  
|<span data-ttu-id="f3ffc-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3ffc-116">Element</span></span>|<span data-ttu-id="f3ffc-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f3ffc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3ffc-118">\<add></span><span class="sxs-lookup"><span data-stu-id="f3ffc-118">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="f3ffc-119">Prvek konfigurace, který určuje základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="f3ffc-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3ffc-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3ffc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f3ffc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3ffc-121">Element</span></span>|<span data-ttu-id="f3ffc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f3ffc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3ffc-123">\<host></span><span class="sxs-lookup"><span data-stu-id="f3ffc-123">\<host></span></span>](host.md)|<span data-ttu-id="f3ffc-124">Prvek konfigurace, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="f3ffc-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3ffc-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3ffc-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="f3ffc-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="f3ffc-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
