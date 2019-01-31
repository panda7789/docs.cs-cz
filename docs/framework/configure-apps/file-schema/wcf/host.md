---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 8a8f9db96281d8d775ff5c2923018228b3a9c1e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269026"
---
# <a name="host"></a><span data-ttu-id="73e55-101">\<host></span><span class="sxs-lookup"><span data-stu-id="73e55-101">\<host></span></span>
<span data-ttu-id="73e55-102">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="73e55-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="73e55-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73e55-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="73e55-104">\<services></span><span class="sxs-lookup"><span data-stu-id="73e55-104">\<services></span></span>  
<span data-ttu-id="73e55-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="73e55-105">\<service></span></span>  
<span data-ttu-id="73e55-106">\<host></span><span class="sxs-lookup"><span data-stu-id="73e55-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e55-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73e55-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="73e55-108">Typ</span><span class="sxs-lookup"><span data-stu-id="73e55-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73e55-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="73e55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73e55-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="73e55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73e55-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="73e55-111">Attributes</span></span>  
 <span data-ttu-id="73e55-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="73e55-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73e55-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="73e55-113">Child Elements</span></span>  
  
|<span data-ttu-id="73e55-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="73e55-114">Element</span></span>|<span data-ttu-id="73e55-115">Popis</span><span class="sxs-lookup"><span data-stu-id="73e55-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73e55-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="73e55-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="73e55-117">Kolekce `baseAddress` prvky, které určuje základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="73e55-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="73e55-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="73e55-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="73e55-119">Konfigurace element, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="73e55-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73e55-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="73e55-120">Parent Elements</span></span>  
  
|<span data-ttu-id="73e55-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="73e55-121">Element</span></span>|<span data-ttu-id="73e55-122">Popis</span><span class="sxs-lookup"><span data-stu-id="73e55-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73e55-123">\<service></span><span class="sxs-lookup"><span data-stu-id="73e55-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="73e55-124">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="73e55-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73e55-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73e55-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="73e55-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="73e55-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
