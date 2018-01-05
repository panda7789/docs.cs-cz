---
title: "&lt;služby&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a><span data-ttu-id="0583e-102">&lt;služby&gt;</span><span class="sxs-lookup"><span data-stu-id="0583e-102">&lt;services&gt;</span></span>
<span data-ttu-id="0583e-103">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0583e-103">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="0583e-104">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="0583e-104">Each service has its own `service` configuration section.</span></span>  
  
 <span data-ttu-id="0583e-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0583e-105">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0583e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0583e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0583e-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0583e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0583e-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0583e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0583e-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="0583e-109">Attributes</span></span>  
 <span data-ttu-id="0583e-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="0583e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0583e-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0583e-111">Child Elements</span></span>  
  
|<span data-ttu-id="0583e-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="0583e-112">Element</span></span>|<span data-ttu-id="0583e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0583e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0583e-114">\<služby ></span><span class="sxs-lookup"><span data-stu-id="0583e-114">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="0583e-115">Definujte kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="0583e-115">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0583e-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0583e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0583e-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="0583e-117">Element</span></span>|<span data-ttu-id="0583e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0583e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0583e-119">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0583e-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="0583e-120">Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0583e-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0583e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0583e-121">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServicesSection>
