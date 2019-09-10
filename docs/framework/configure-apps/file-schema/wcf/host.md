---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855210"
---
# <a name="host"></a><span data-ttu-id="78fe0-101">\<host></span><span class="sxs-lookup"><span data-stu-id="78fe0-101">\<host></span></span>
<span data-ttu-id="78fe0-102">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="78fe0-102">Specifies settings for a service host.</span></span>  
  
<span data-ttu-id="78fe0-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="78fe0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="78fe0-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="78fe0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="78fe0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)</span><span class="sxs-lookup"><span data-stu-id="78fe0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="78fe0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)</span><span class="sxs-lookup"><span data-stu-id="78fe0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="78fe0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> hostitele**</span><span class="sxs-lookup"><span data-stu-id="78fe0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fe0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78fe0-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="78fe0-109">type</span><span class="sxs-lookup"><span data-stu-id="78fe0-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78fe0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78fe0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78fe0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78fe0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78fe0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="78fe0-112">Attributes</span></span>  
 <span data-ttu-id="78fe0-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="78fe0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78fe0-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78fe0-114">Child Elements</span></span>  
  
|<span data-ttu-id="78fe0-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="78fe0-115">Element</span></span>|<span data-ttu-id="78fe0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="78fe0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78fe0-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="78fe0-117">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="78fe0-118">Kolekce `baseAddress` prvků, které určují základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="78fe0-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="78fe0-119">\<Časové limity ></span><span class="sxs-lookup"><span data-stu-id="78fe0-119">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="78fe0-120">Prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="78fe0-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78fe0-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78fe0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="78fe0-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="78fe0-122">Element</span></span>|<span data-ttu-id="78fe0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="78fe0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78fe0-124">\<service></span><span class="sxs-lookup"><span data-stu-id="78fe0-124">\<service></span></span>](service.md)|<span data-ttu-id="78fe0-125">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="78fe0-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78fe0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78fe0-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="78fe0-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="78fe0-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
