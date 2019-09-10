---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850268"
---
# <a name="backuplists"></a><span data-ttu-id="7109b-101">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="7109b-101">\<backupLists></span></span>
<span data-ttu-id="7109b-102">Představuje konfigurační oddíl pro definování sady záložních služeb použitých při zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="7109b-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="7109b-103">Každý podřízený element je seznam zálohování, který vytvoří výčet sady koncových bodů, které chcete, aby služba Směrování použila v případě, že není dostupný primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7109b-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="7109b-104">Pokud je první koncový bod v seznamu mimo provoz, směrovací služba se v seznamu automaticky převezme na další.</span><span class="sxs-lookup"><span data-stu-id="7109b-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="7109b-105">Díky tomu můžete rychle přidat do své aplikace spolehlivost, aniž byste museli poučit klientské aplikace o tom, jak zpracovávat složité vzory nebo kde jsou nasazené všechny služby.</span><span class="sxs-lookup"><span data-stu-id="7109b-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="7109b-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7109b-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7109b-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7109b-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7109b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="7109b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="7109b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupLists >**</span><span class="sxs-lookup"><span data-stu-id="7109b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7109b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7109b-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7109b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7109b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7109b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7109b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7109b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7109b-113">Attributes</span></span>  
 <span data-ttu-id="7109b-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="7109b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7109b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7109b-115">Child Elements</span></span>  
  
|<span data-ttu-id="7109b-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="7109b-116">Element</span></span>|<span data-ttu-id="7109b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7109b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7109b-118">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="7109b-118">\<filter></span></span>](filter.md)|<span data-ttu-id="7109b-119">Obsahuje seznam koncových bodů, které by služba Směrování měla použít pro případ, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="7109b-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="7109b-120">.</span><span class="sxs-lookup"><span data-stu-id="7109b-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7109b-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7109b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7109b-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7109b-122">Element</span></span>|<span data-ttu-id="7109b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7109b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7109b-124">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="7109b-124">\<routing></span></span>](routing.md)|<span data-ttu-id="7109b-125">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="7109b-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7109b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7109b-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
