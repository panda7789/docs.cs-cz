---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 3d1f7774f61060880a5c3b0327bdd6c2cc4dd74e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102996"
---
# <a name="host"></a><span data-ttu-id="de67e-101">\<host></span><span class="sxs-lookup"><span data-stu-id="de67e-101">\<host></span></span>
<span data-ttu-id="de67e-102">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="de67e-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="de67e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de67e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="de67e-104">\<services></span><span class="sxs-lookup"><span data-stu-id="de67e-104">\<services></span></span>  
<span data-ttu-id="de67e-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="de67e-105">\<service></span></span>  
<span data-ttu-id="de67e-106">\<host></span><span class="sxs-lookup"><span data-stu-id="de67e-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de67e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de67e-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="de67e-108">Type</span><span class="sxs-lookup"><span data-stu-id="de67e-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de67e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de67e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de67e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de67e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de67e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="de67e-111">Attributes</span></span>  
 <span data-ttu-id="de67e-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="de67e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de67e-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de67e-113">Child Elements</span></span>  
  
|<span data-ttu-id="de67e-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="de67e-114">Element</span></span>|<span data-ttu-id="de67e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="de67e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de67e-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="de67e-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="de67e-117">Kolekce `baseAddress` prvky, které určuje základní adresy použité hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="de67e-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="de67e-118">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="de67e-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="de67e-119">Konfigurace element, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="de67e-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de67e-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de67e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="de67e-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="de67e-121">Element</span></span>|<span data-ttu-id="de67e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="de67e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de67e-123">\<služby ></span><span class="sxs-lookup"><span data-stu-id="de67e-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="de67e-124">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="de67e-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de67e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de67e-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="de67e-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="de67e-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
