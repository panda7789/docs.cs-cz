---
title: '&lt;hostitele&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 9c48fff7473449192887bfd8cc201dd87cb4e7f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lthostgt"></a><span data-ttu-id="90b6e-102">&lt;hostitele&gt;</span><span class="sxs-lookup"><span data-stu-id="90b6e-102">&lt;host&gt;</span></span>
<span data-ttu-id="90b6e-103">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="90b6e-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="90b6e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90b6e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="90b6e-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="90b6e-105">\<services></span></span>  
<span data-ttu-id="90b6e-106">\<služby ></span><span class="sxs-lookup"><span data-stu-id="90b6e-106">\<service></span></span>  
<span data-ttu-id="90b6e-107">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="90b6e-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b6e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90b6e-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="90b6e-109">Typ</span><span class="sxs-lookup"><span data-stu-id="90b6e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90b6e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90b6e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90b6e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90b6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90b6e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="90b6e-112">Attributes</span></span>  
 <span data-ttu-id="90b6e-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="90b6e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90b6e-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90b6e-114">Child Elements</span></span>  
  
|<span data-ttu-id="90b6e-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="90b6e-115">Element</span></span>|<span data-ttu-id="90b6e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="90b6e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90b6e-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="90b6e-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="90b6e-118">Kolekce `baseAddress` prvky, které určuje základní adresy používané hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="90b6e-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="90b6e-119">\<časové limity ></span><span class="sxs-lookup"><span data-stu-id="90b6e-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="90b6e-120">Konfigurace element, který určuje dobu dobu povolenou pro hostitele služby otevřete nebo zavřete.</span><span class="sxs-lookup"><span data-stu-id="90b6e-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90b6e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90b6e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="90b6e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="90b6e-122">Element</span></span>|<span data-ttu-id="90b6e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="90b6e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90b6e-124">\<service></span><span class="sxs-lookup"><span data-stu-id="90b6e-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="90b6e-125">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="90b6e-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90b6e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="90b6e-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="90b6e-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="90b6e-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
