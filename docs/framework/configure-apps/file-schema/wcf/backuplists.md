---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850268"
---
# \<backupLists>
<span data-ttu-id="723a9-101">Představuje konfigurační oddíl pro definování sady záložních služeb použitých při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="723a9-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="723a9-102">Každý podřízený element je seznam zálohování, který vytvoří výčet sady koncových bodů, které chcete, aby služba Směrování použila v případě, že není dostupný primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="723a9-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="723a9-103">Pokud je první koncový bod v seznamu mimo provoz, směrovací služba se v seznamu automaticky převezme na další.</span><span class="sxs-lookup"><span data-stu-id="723a9-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="723a9-104">Díky tomu můžete rychle přidat do své aplikace spolehlivost, aniž byste museli poučit klientské aplikace o tom, jak zpracovávat složité vzory nebo kde jsou nasazené všechny služby.</span><span class="sxs-lookup"><span data-stu-id="723a9-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="723a9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="723a9-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="723a9-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="723a9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="723a9-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="723a9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="723a9-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="723a9-108">Attributes</span></span>  
 <span data-ttu-id="723a9-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="723a9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="723a9-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="723a9-110">Child Elements</span></span>  
  
|<span data-ttu-id="723a9-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="723a9-111">Element</span></span>|<span data-ttu-id="723a9-112">Description</span><span class="sxs-lookup"><span data-stu-id="723a9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="723a9-113">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="723a9-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="723a9-114">.</span><span class="sxs-lookup"><span data-stu-id="723a9-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="723a9-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="723a9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="723a9-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="723a9-116">Element</span></span>|<span data-ttu-id="723a9-117">Description</span><span class="sxs-lookup"><span data-stu-id="723a9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="723a9-118">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF), který se <xref:System.ServiceModel.Dispatcher.MessageFilter> má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky definující cílové koncové body, na které se odesílají zprávy, když se filtr shoduje.</span><span class="sxs-lookup"><span data-stu-id="723a9-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="723a9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="723a9-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
