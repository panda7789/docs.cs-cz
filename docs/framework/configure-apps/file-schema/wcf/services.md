---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854975"
---
# <a name="services"></a><span data-ttu-id="3ca47-101">\<> služeb</span><span class="sxs-lookup"><span data-stu-id="3ca47-101">\<services></span></span>
<span data-ttu-id="3ca47-102">Služby jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3ca47-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3ca47-103">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="3ca47-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="3ca47-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3ca47-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3ca47-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3ca47-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3ca47-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> služeb**</span><span class="sxs-lookup"><span data-stu-id="3ca47-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca47-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ca47-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ca47-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ca47-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3ca47-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ca47-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ca47-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ca47-110">Attributes</span></span>  
 <span data-ttu-id="3ca47-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ca47-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ca47-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ca47-112">Child Elements</span></span>  
  
|<span data-ttu-id="3ca47-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ca47-113">Element</span></span>|<span data-ttu-id="3ca47-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ca47-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ca47-115">\<service></span><span class="sxs-lookup"><span data-stu-id="3ca47-115">\<service></span></span>](service.md)|<span data-ttu-id="3ca47-116">Zadejte kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="3ca47-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ca47-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ca47-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3ca47-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ca47-118">Element</span></span>|<span data-ttu-id="3ca47-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3ca47-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ca47-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ca47-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="3ca47-121">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ca47-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ca47-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ca47-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
