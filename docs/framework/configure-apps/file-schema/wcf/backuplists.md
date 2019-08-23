---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926438"
---
# <a name="backuplists"></a><span data-ttu-id="9968a-101">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="9968a-101">\<backupLists></span></span>
<span data-ttu-id="9968a-102">Představuje konfigurační oddíl pro definování sady záložních služeb použitých při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="9968a-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="9968a-103">Každý podřízený element je seznam zálohování, který vytvoří výčet sady koncových bodů, které chcete, aby služba Směrování použila v případě, že není dostupný primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9968a-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="9968a-104">Pokud je první koncový bod v seznamu mimo provoz, směrovací služba se v seznamu automaticky převezme na další.</span><span class="sxs-lookup"><span data-stu-id="9968a-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="9968a-105">Díky tomu můžete rychle přidat do své aplikace spolehlivost, aniž byste museli poučit klientské aplikace o tom, jak zpracovávat složité vzory nebo kde jsou nasazené všechny služby.</span><span class="sxs-lookup"><span data-stu-id="9968a-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="9968a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9968a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9968a-107">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="9968a-107">\<routing></span></span>  
<span data-ttu-id="9968a-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="9968a-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9968a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9968a-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9968a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9968a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9968a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9968a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9968a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9968a-112">Attributes</span></span>  
 <span data-ttu-id="9968a-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="9968a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9968a-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9968a-114">Child Elements</span></span>  
  
|<span data-ttu-id="9968a-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="9968a-115">Element</span></span>|<span data-ttu-id="9968a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9968a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9968a-117">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="9968a-117">\<filter></span></span>](filter.md)|<span data-ttu-id="9968a-118">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="9968a-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="9968a-119">.</span><span class="sxs-lookup"><span data-stu-id="9968a-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9968a-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9968a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9968a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="9968a-121">Element</span></span>|<span data-ttu-id="9968a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9968a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9968a-123">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="9968a-123">\<routing></span></span>](routing.md)|<span data-ttu-id="9968a-124">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="9968a-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9968a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9968a-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
