---
title: '&lt;host&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 1fb35058d407d0fbae78092bb4ccd45b0aaa40e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702025"
---
# <a name="lthostgt"></a><span data-ttu-id="623fe-102">&lt;host&gt;</span><span class="sxs-lookup"><span data-stu-id="623fe-102">&lt;host&gt;</span></span>
<span data-ttu-id="623fe-103">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="623fe-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="623fe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="623fe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="623fe-105">\<services></span><span class="sxs-lookup"><span data-stu-id="623fe-105">\<services></span></span>  
<span data-ttu-id="623fe-106">\<služby ></span><span class="sxs-lookup"><span data-stu-id="623fe-106">\<service></span></span>  
<span data-ttu-id="623fe-107">\<host></span><span class="sxs-lookup"><span data-stu-id="623fe-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="623fe-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="623fe-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="623fe-109">Typ</span><span class="sxs-lookup"><span data-stu-id="623fe-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="623fe-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="623fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="623fe-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="623fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="623fe-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="623fe-112">Attributes</span></span>  
 <span data-ttu-id="623fe-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="623fe-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="623fe-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="623fe-114">Child Elements</span></span>  
  
|<span data-ttu-id="623fe-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="623fe-115">Element</span></span>|<span data-ttu-id="623fe-116">Popis</span><span class="sxs-lookup"><span data-stu-id="623fe-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="623fe-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="623fe-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="623fe-118">Kolekce `baseAddress` prvky, které určuje základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="623fe-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="623fe-119">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="623fe-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="623fe-120">Konfigurace element, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="623fe-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="623fe-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="623fe-121">Parent Elements</span></span>  
  
|<span data-ttu-id="623fe-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="623fe-122">Element</span></span>|<span data-ttu-id="623fe-123">Popis</span><span class="sxs-lookup"><span data-stu-id="623fe-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="623fe-124">\<service></span><span class="sxs-lookup"><span data-stu-id="623fe-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="623fe-125">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="623fe-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="623fe-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="623fe-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="623fe-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="623fe-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
