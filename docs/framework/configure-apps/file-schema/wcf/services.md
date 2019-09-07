---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 1f9cb6c95fa14a5b8a55cc561699e2a07e1dc80c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399587"
---
# <a name="services"></a><span data-ttu-id="40eb5-101">\<> služeb</span><span class="sxs-lookup"><span data-stu-id="40eb5-101">\<services></span></span>
<span data-ttu-id="40eb5-102">Služby jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="40eb5-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="40eb5-103">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="40eb5-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="40eb5-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40eb5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40eb5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="40eb5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="40eb5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> služeb**</span><span class="sxs-lookup"><span data-stu-id="40eb5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
## <a name="syntax"></a><span data-ttu-id="40eb5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40eb5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40eb5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40eb5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="40eb5-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40eb5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40eb5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="40eb5-110">Attributes</span></span>  
 <span data-ttu-id="40eb5-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="40eb5-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40eb5-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40eb5-112">Child Elements</span></span>  
  
|<span data-ttu-id="40eb5-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="40eb5-113">Element</span></span>|<span data-ttu-id="40eb5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="40eb5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40eb5-115">\<service></span><span class="sxs-lookup"><span data-stu-id="40eb5-115">\<service></span></span>](service.md)|<span data-ttu-id="40eb5-116">Zadejte kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="40eb5-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40eb5-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40eb5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="40eb5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="40eb5-118">Element</span></span>|<span data-ttu-id="40eb5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="40eb5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40eb5-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="40eb5-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="40eb5-121">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="40eb5-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40eb5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40eb5-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
