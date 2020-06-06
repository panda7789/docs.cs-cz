---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854975"
---
# \<services>
<span data-ttu-id="f1c4c-101">Služby jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f1c4c-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="f1c4c-102">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="f1c4c-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="f1c4c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1c4c-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1c4c-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1c4c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f1c4c-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1c4c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1c4c-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1c4c-106">Attributes</span></span>  
 <span data-ttu-id="f1c4c-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1c4c-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1c4c-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1c4c-108">Child Elements</span></span>  
  
|<span data-ttu-id="f1c4c-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1c4c-109">Element</span></span>|<span data-ttu-id="f1c4c-110">Description</span><span class="sxs-lookup"><span data-stu-id="f1c4c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="f1c4c-111">Zadejte kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="f1c4c-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1c4c-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1c4c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f1c4c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1c4c-113">Element</span></span>|<span data-ttu-id="f1c4c-114">Description</span><span class="sxs-lookup"><span data-stu-id="f1c4c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="f1c4c-115">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f1c4c-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1c4c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1c4c-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
