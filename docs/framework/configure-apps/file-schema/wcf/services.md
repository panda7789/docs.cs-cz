---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 2db168d48e3959a7d80a10ca27134f58e3fcb2de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168074"
---
# <a name="services"></a><span data-ttu-id="329f0-101">\<services></span><span class="sxs-lookup"><span data-stu-id="329f0-101">\<services></span></span>
<span data-ttu-id="329f0-102">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="329f0-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="329f0-103">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="329f0-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="329f0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="329f0-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329f0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="329f0-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="329f0-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="329f0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="329f0-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="329f0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="329f0-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="329f0-108">Attributes</span></span>  
 <span data-ttu-id="329f0-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="329f0-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="329f0-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="329f0-110">Child Elements</span></span>  
  
|<span data-ttu-id="329f0-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="329f0-111">Element</span></span>|<span data-ttu-id="329f0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="329f0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="329f0-113">\<služby ></span><span class="sxs-lookup"><span data-stu-id="329f0-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="329f0-114">Definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="329f0-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="329f0-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="329f0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="329f0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="329f0-116">Element</span></span>|<span data-ttu-id="329f0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="329f0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="329f0-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="329f0-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="329f0-119">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="329f0-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="329f0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="329f0-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
