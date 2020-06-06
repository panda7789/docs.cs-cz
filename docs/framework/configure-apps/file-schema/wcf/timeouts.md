---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854974"
---
# \<timeOuts>
<span data-ttu-id="0023b-101">Představuje prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="0023b-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="0023b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0023b-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0023b-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0023b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0023b-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0023b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0023b-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="0023b-105">Attributes</span></span>  
  
|<span data-ttu-id="0023b-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="0023b-106">Attribute</span></span>|<span data-ttu-id="0023b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0023b-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0023b-108"><xref:System.TimeSpan>Hodnota, která určuje časový interval, po který může hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="0023b-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="0023b-109"><xref:System.TimeSpan>Hodnota, která určuje časový interval, po který může hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="0023b-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0023b-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0023b-110">Child Elements</span></span>  
 <span data-ttu-id="0023b-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="0023b-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0023b-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0023b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0023b-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="0023b-113">Element</span></span>|<span data-ttu-id="0023b-114">Description</span><span class="sxs-lookup"><span data-stu-id="0023b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="0023b-115">Prvek konfigurace, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="0023b-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0023b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0023b-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="0023b-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="0023b-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
