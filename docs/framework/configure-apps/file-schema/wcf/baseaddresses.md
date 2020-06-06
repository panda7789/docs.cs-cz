---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850204"
---
# \<baseAddresses>
<span data-ttu-id="ec504-101">Představuje kolekci `baseAddress` prvků, které jsou základními adresami hostitele služby v prostředí s místním hostováním.</span><span class="sxs-lookup"><span data-stu-id="ec504-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="ec504-102">Pokud je k dispozici základní adresa, lze koncovým bodům nakonfigurovat adresy relativní vzhledem k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="ec504-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="ec504-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec504-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="ec504-104">Typ</span><span class="sxs-lookup"><span data-stu-id="ec504-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec504-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec504-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ec504-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec504-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec504-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec504-107">Attributes</span></span>  
 <span data-ttu-id="ec504-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec504-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec504-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec504-109">Child Elements</span></span>  
  
|<span data-ttu-id="ec504-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec504-110">Element</span></span>|<span data-ttu-id="ec504-111">Description</span><span class="sxs-lookup"><span data-stu-id="ec504-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="ec504-112">Prvek konfigurace, který určuje základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="ec504-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec504-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec504-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ec504-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec504-114">Element</span></span>|<span data-ttu-id="ec504-115">Description</span><span class="sxs-lookup"><span data-stu-id="ec504-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="ec504-116">Prvek konfigurace, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="ec504-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec504-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec504-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="ec504-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="ec504-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
