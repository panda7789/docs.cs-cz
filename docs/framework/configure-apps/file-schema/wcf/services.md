---
title: '&lt;Služby&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 7b26224f1217e7f73a529c082c2c9272ec189a5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573254"
---
# <a name="ltservicesgt"></a><span data-ttu-id="e6c59-102">&lt;Služby&gt;</span><span class="sxs-lookup"><span data-stu-id="e6c59-102">&lt;services&gt;</span></span>
<span data-ttu-id="e6c59-103">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e6c59-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e6c59-104">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="e6c59-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="e6c59-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6c59-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c59-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6c59-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6c59-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e6c59-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e6c59-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e6c59-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6c59-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="e6c59-109">Attributes</span></span>  
 <span data-ttu-id="e6c59-110">Žádná</span><span class="sxs-lookup"><span data-stu-id="e6c59-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6c59-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e6c59-111">Child Elements</span></span>  
  
|<span data-ttu-id="e6c59-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6c59-112">Element</span></span>|<span data-ttu-id="e6c59-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e6c59-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6c59-114">\<service></span><span class="sxs-lookup"><span data-stu-id="e6c59-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="e6c59-115">Definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="e6c59-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6c59-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e6c59-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e6c59-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6c59-117">Element</span></span>|<span data-ttu-id="e6c59-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e6c59-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6c59-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e6c59-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e6c59-120">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e6c59-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6c59-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6c59-121">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServicesSection>
