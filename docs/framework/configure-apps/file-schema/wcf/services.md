---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 4dc425fa97eaf99664f0d9bbbbc851c462cbf373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274960"
---
# <a name="services"></a><span data-ttu-id="e1788-101">\<services></span><span class="sxs-lookup"><span data-stu-id="e1788-101">\<services></span></span>
<span data-ttu-id="e1788-102">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e1788-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e1788-103">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="e1788-103">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="e1788-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e1788-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1788-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1788-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1788-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e1788-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e1788-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e1788-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1788-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e1788-108">Attributes</span></span>  
 <span data-ttu-id="e1788-109">Žádná</span><span class="sxs-lookup"><span data-stu-id="e1788-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1788-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e1788-110">Child Elements</span></span>  
  
|<span data-ttu-id="e1788-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1788-111">Element</span></span>|<span data-ttu-id="e1788-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e1788-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1788-113">\<service></span><span class="sxs-lookup"><span data-stu-id="e1788-113">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="e1788-114">Definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="e1788-114">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1788-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e1788-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e1788-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1788-116">Element</span></span>|<span data-ttu-id="e1788-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e1788-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1788-118">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e1788-118">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e1788-119">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e1788-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1788-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1788-120">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServicesSection>
