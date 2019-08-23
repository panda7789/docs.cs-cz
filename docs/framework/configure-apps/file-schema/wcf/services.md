---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: c00d5fe3e8b2ba05843e09aca6aaa79386541bad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937191"
---
# <a name="services"></a><span data-ttu-id="2b207-101">\<> služeb</span><span class="sxs-lookup"><span data-stu-id="2b207-101">\<services></span></span>
<span data-ttu-id="2b207-102">Služby jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="2b207-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="2b207-103">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="2b207-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="2b207-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2b207-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b207-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b207-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b207-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b207-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2b207-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b207-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b207-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b207-108">Attributes</span></span>  
 <span data-ttu-id="2b207-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="2b207-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b207-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b207-110">Child Elements</span></span>  
  
|<span data-ttu-id="2b207-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b207-111">Element</span></span>|<span data-ttu-id="2b207-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2b207-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b207-113">\<service></span><span class="sxs-lookup"><span data-stu-id="2b207-113">\<service></span></span>](service.md)|<span data-ttu-id="2b207-114">Zadejte kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="2b207-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b207-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b207-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2b207-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b207-116">Element</span></span>|<span data-ttu-id="2b207-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2b207-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b207-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2b207-118">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="2b207-119">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2b207-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b207-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b207-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
