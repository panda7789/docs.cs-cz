---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855210"
---
# \<host>
<span data-ttu-id="092d4-101">Určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="092d4-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="092d4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="092d4-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="092d4-103">Typ</span><span class="sxs-lookup"><span data-stu-id="092d4-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="092d4-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="092d4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="092d4-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="092d4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="092d4-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="092d4-106">Attributes</span></span>  
 <span data-ttu-id="092d4-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="092d4-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="092d4-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="092d4-108">Child Elements</span></span>  
  
|<span data-ttu-id="092d4-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="092d4-109">Element</span></span>|<span data-ttu-id="092d4-110">Description</span><span class="sxs-lookup"><span data-stu-id="092d4-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="092d4-111">Kolekce `baseAddress` prvků, které určují základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="092d4-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="092d4-112">Prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="092d4-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="092d4-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="092d4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="092d4-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="092d4-114">Element</span></span>|<span data-ttu-id="092d4-115">Description</span><span class="sxs-lookup"><span data-stu-id="092d4-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="092d4-116">Určuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="092d4-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="092d4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="092d4-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="092d4-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="092d4-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
