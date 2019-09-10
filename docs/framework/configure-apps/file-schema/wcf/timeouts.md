---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854974"
---
# <a name="timeouts"></a><span data-ttu-id="2942a-101">\<Časové limity ></span><span class="sxs-lookup"><span data-stu-id="2942a-101">\<timeOuts></span></span>
<span data-ttu-id="2942a-102">Představuje prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="2942a-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
<span data-ttu-id="2942a-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2942a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2942a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2942a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2942a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)</span><span class="sxs-lookup"><span data-stu-id="2942a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="2942a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)</span><span class="sxs-lookup"><span data-stu-id="2942a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="2942a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hostitele**](host.md)</span><span class="sxs-lookup"><span data-stu-id="2942a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="2942a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Časové limity >**</span><span class="sxs-lookup"><span data-stu-id="2942a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2942a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2942a-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2942a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2942a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2942a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2942a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2942a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2942a-112">Attributes</span></span>  
  
|<span data-ttu-id="2942a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2942a-113">Attribute</span></span>|<span data-ttu-id="2942a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2942a-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2942a-115"><xref:System.TimeSpan> Hodnota, která určuje časový interval, po který může hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="2942a-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="2942a-116"><xref:System.TimeSpan> Hodnota, která určuje časový interval, po který může hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="2942a-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2942a-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2942a-117">Child Elements</span></span>  
 <span data-ttu-id="2942a-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="2942a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2942a-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2942a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2942a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="2942a-120">Element</span></span>|<span data-ttu-id="2942a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2942a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2942a-122">\<host></span><span class="sxs-lookup"><span data-stu-id="2942a-122">\<host></span></span>](host.md)|<span data-ttu-id="2942a-123">Prvek konfigurace, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="2942a-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2942a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2942a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="2942a-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="2942a-125">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
