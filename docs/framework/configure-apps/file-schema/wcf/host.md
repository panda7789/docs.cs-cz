---
title: '&lt;Hostitel&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: afa9d65223ab3a7730a55bc41ed98458707b32db
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145221"
---
# <a name="lthostgt"></a><span data-ttu-id="0dd9a-102">&lt;Hostitel&gt;</span><span class="sxs-lookup"><span data-stu-id="0dd9a-102">&lt;host&gt;</span></span>
<span data-ttu-id="0dd9a-103">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="0dd9a-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="0dd9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0dd9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0dd9a-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="0dd9a-105">\<services></span></span>  
<span data-ttu-id="0dd9a-106">\<služby ></span><span class="sxs-lookup"><span data-stu-id="0dd9a-106">\<service></span></span>  
<span data-ttu-id="0dd9a-107">\<Hostitel ></span><span class="sxs-lookup"><span data-stu-id="0dd9a-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd9a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dd9a-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="0dd9a-109">Typ</span><span class="sxs-lookup"><span data-stu-id="0dd9a-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dd9a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0dd9a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0dd9a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0dd9a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dd9a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0dd9a-112">Attributes</span></span>  
 <span data-ttu-id="0dd9a-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="0dd9a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0dd9a-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0dd9a-114">Child Elements</span></span>  
  
|<span data-ttu-id="0dd9a-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="0dd9a-115">Element</span></span>|<span data-ttu-id="0dd9a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="0dd9a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dd9a-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="0dd9a-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="0dd9a-118">Kolekce `baseAddress` prvky, které určuje základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="0dd9a-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="0dd9a-119">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="0dd9a-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="0dd9a-120">Konfigurace element, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="0dd9a-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0dd9a-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0dd9a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0dd9a-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="0dd9a-122">Element</span></span>|<span data-ttu-id="0dd9a-123">Popis</span><span class="sxs-lookup"><span data-stu-id="0dd9a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dd9a-124">\<service></span><span class="sxs-lookup"><span data-stu-id="0dd9a-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="0dd9a-125">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0dd9a-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dd9a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0dd9a-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="0dd9a-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="0dd9a-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
