---
title: '&lt;Služby&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 789fc52f628174ef61a9c7169cb0cae0f1ba8e31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749228"
---
# <a name="ltservicesgt"></a><span data-ttu-id="d9876-102">&lt;Služby&gt;</span><span class="sxs-lookup"><span data-stu-id="d9876-102">&lt;services&gt;</span></span>
<span data-ttu-id="d9876-103">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d9876-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="d9876-104">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="d9876-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="d9876-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d9876-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9876-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9876-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9876-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d9876-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d9876-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9876-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9876-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9876-109">Attributes</span></span>  
 <span data-ttu-id="d9876-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="d9876-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9876-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d9876-111">Child Elements</span></span>  
  
|<span data-ttu-id="d9876-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9876-112">Element</span></span>|<span data-ttu-id="d9876-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d9876-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9876-114">\<service></span><span class="sxs-lookup"><span data-stu-id="d9876-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="d9876-115">Definujte kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="d9876-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9876-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d9876-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d9876-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9876-117">Element</span></span>|<span data-ttu-id="d9876-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d9876-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9876-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d9876-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="d9876-120">Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d9876-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9876-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9876-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
