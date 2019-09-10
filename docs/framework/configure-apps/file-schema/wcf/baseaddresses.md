---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850204"
---
# <a name="baseaddresses"></a><span data-ttu-id="3a092-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="3a092-101">\<baseAddresses></span></span>
<span data-ttu-id="3a092-102">Představuje kolekci `baseAddress` prvků, které jsou základními adresami hostitele služby v prostředí s místním hostováním.</span><span class="sxs-lookup"><span data-stu-id="3a092-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="3a092-103">Pokud je k dispozici základní adresa, lze koncovým bodům nakonfigurovat adresy relativní vzhledem k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="3a092-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
<span data-ttu-id="3a092-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a092-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a092-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3a092-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3a092-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)</span><span class="sxs-lookup"><span data-stu-id="3a092-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="3a092-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)</span><span class="sxs-lookup"><span data-stu-id="3a092-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="3a092-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hostitele**](host.md)</span><span class="sxs-lookup"><span data-stu-id="3a092-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="3a092-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adres BaseAddresses >**</span><span class="sxs-lookup"><span data-stu-id="3a092-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a092-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a092-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="3a092-111">type</span><span class="sxs-lookup"><span data-stu-id="3a092-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a092-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3a092-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3a092-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3a092-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a092-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="3a092-114">Attributes</span></span>  
 <span data-ttu-id="3a092-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="3a092-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a092-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3a092-116">Child Elements</span></span>  
  
|<span data-ttu-id="3a092-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="3a092-117">Element</span></span>|<span data-ttu-id="3a092-118">Popis</span><span class="sxs-lookup"><span data-stu-id="3a092-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a092-119">\<add></span><span class="sxs-lookup"><span data-stu-id="3a092-119">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="3a092-120">Prvek konfigurace, který určuje základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="3a092-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a092-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3a092-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3a092-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="3a092-122">Element</span></span>|<span data-ttu-id="3a092-123">Popis</span><span class="sxs-lookup"><span data-stu-id="3a092-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a092-124">\<host></span><span class="sxs-lookup"><span data-stu-id="3a092-124">\<host></span></span>](host.md)|<span data-ttu-id="3a092-125">Prvek konfigurace, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="3a092-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a092-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a092-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="3a092-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="3a092-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
