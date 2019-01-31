---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: dc4b31e729f9037da101bdf3e6cde28e91b1a070
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277014"
---
# <a name="baseaddresses"></a><span data-ttu-id="80bf9-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="80bf9-101">\<baseAddresses></span></span>
<span data-ttu-id="80bf9-102">Představuje kolekci `baseAddress` elementy, které jsou základními adresami hostitele služby v prostředí Self-Hosted.</span><span class="sxs-lookup"><span data-stu-id="80bf9-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="80bf9-103">Pokud základní adresa je k dispozici, můžete být koncové body nakonfigurované adresy relativní k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="80bf9-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="80bf9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80bf9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80bf9-105">\<client></span><span class="sxs-lookup"><span data-stu-id="80bf9-105">\<client></span></span>  
<span data-ttu-id="80bf9-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="80bf9-106">\<endpoint></span></span>  
<span data-ttu-id="80bf9-107">\<host></span><span class="sxs-lookup"><span data-stu-id="80bf9-107">\<host></span></span>  
<span data-ttu-id="80bf9-108">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="80bf9-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80bf9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80bf9-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="80bf9-110">Typ</span><span class="sxs-lookup"><span data-stu-id="80bf9-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80bf9-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80bf9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="80bf9-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80bf9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80bf9-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="80bf9-113">Attributes</span></span>  
 <span data-ttu-id="80bf9-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="80bf9-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80bf9-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80bf9-115">Child Elements</span></span>  
  
|<span data-ttu-id="80bf9-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="80bf9-116">Element</span></span>|<span data-ttu-id="80bf9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="80bf9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80bf9-118">\<add></span><span class="sxs-lookup"><span data-stu-id="80bf9-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="80bf9-119">Konfigurační element určující základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="80bf9-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80bf9-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80bf9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="80bf9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="80bf9-121">Element</span></span>|<span data-ttu-id="80bf9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="80bf9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80bf9-123">\<host></span><span class="sxs-lookup"><span data-stu-id="80bf9-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="80bf9-124">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="80bf9-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80bf9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80bf9-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="80bf9-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="80bf9-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
