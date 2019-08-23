---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918710"
---
# <a name="host"></a><span data-ttu-id="f8b76-101">\<host></span><span class="sxs-lookup"><span data-stu-id="f8b76-101">\<host></span></span>
<span data-ttu-id="f8b76-102">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="f8b76-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="f8b76-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f8b76-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8b76-104">\<> služeb</span><span class="sxs-lookup"><span data-stu-id="f8b76-104">\<services></span></span>  
<span data-ttu-id="f8b76-105">\<> služby</span><span class="sxs-lookup"><span data-stu-id="f8b76-105">\<service></span></span>  
<span data-ttu-id="f8b76-106">\<host></span><span class="sxs-lookup"><span data-stu-id="f8b76-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b76-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8b76-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="f8b76-108">type</span><span class="sxs-lookup"><span data-stu-id="f8b76-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8b76-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8b76-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f8b76-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f8b76-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8b76-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8b76-111">Attributes</span></span>  
 <span data-ttu-id="f8b76-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="f8b76-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f8b76-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b76-113">Child Elements</span></span>  
  
|<span data-ttu-id="f8b76-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8b76-114">Element</span></span>|<span data-ttu-id="f8b76-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f8b76-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8b76-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="f8b76-116">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="f8b76-117">Kolekce `baseAddress` prvků, které určují základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="f8b76-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="f8b76-118">\<Časové limity ></span><span class="sxs-lookup"><span data-stu-id="f8b76-118">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="f8b76-119">Prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="f8b76-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8b76-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b76-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f8b76-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8b76-121">Element</span></span>|<span data-ttu-id="f8b76-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f8b76-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8b76-123">\<service></span><span class="sxs-lookup"><span data-stu-id="f8b76-123">\<service></span></span>](service.md)|<span data-ttu-id="f8b76-124">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8b76-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8b76-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8b76-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="f8b76-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="f8b76-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
