---
title: '&lt;Služby&gt;'
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: a48bd0ac30c1a85602122b2fd9213c2aa5159e91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148094"
---
# <a name="ltservicesgt"></a><span data-ttu-id="39135-102">&lt;Služby&gt;</span><span class="sxs-lookup"><span data-stu-id="39135-102">&lt;services&gt;</span></span>
<span data-ttu-id="39135-103">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="39135-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="39135-104">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="39135-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="39135-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39135-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39135-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39135-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39135-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39135-107">Attributes and Elements</span></span>  
 <span data-ttu-id="39135-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39135-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39135-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="39135-109">Attributes</span></span>  
 <span data-ttu-id="39135-110">Žádná</span><span class="sxs-lookup"><span data-stu-id="39135-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39135-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39135-111">Child Elements</span></span>  
  
|<span data-ttu-id="39135-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="39135-112">Element</span></span>|<span data-ttu-id="39135-113">Popis</span><span class="sxs-lookup"><span data-stu-id="39135-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39135-114">\<service></span><span class="sxs-lookup"><span data-stu-id="39135-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="39135-115">Definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="39135-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39135-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39135-116">Parent Elements</span></span>  
  
|<span data-ttu-id="39135-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="39135-117">Element</span></span>|<span data-ttu-id="39135-118">Popis</span><span class="sxs-lookup"><span data-stu-id="39135-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39135-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="39135-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="39135-120">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="39135-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39135-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="39135-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
