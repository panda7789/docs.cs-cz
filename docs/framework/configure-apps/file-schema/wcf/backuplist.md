---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850271"
---
# \<backupList>
<span data-ttu-id="4037c-101">Představuje konfigurační oddíl pro definování seznamu zálohování, který vytvoří výčet sady koncových bodů, které chcete, aby služba Směrování použila v případě, že není dostupný primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4037c-101">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4037c-102">Pokud je první koncový bod v seznamu mimo provoz, směrovací služba se v seznamu automaticky převezme na další.</span><span class="sxs-lookup"><span data-stu-id="4037c-102">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="4037c-103">Díky tomu můžete rychle přidat do své aplikace spolehlivost, aniž byste museli poučit klientské aplikace o tom, jak zpracovávat složité vzory nebo kde jsou nasazené všechny služby.</span><span class="sxs-lookup"><span data-stu-id="4037c-103">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="4037c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4037c-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4037c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4037c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4037c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4037c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4037c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="4037c-107">Attributes</span></span>  
  
|<span data-ttu-id="4037c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4037c-108">Attribute</span></span>|<span data-ttu-id="4037c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4037c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4037c-110">name</span><span class="sxs-lookup"><span data-stu-id="4037c-110">name</span></span>|<span data-ttu-id="4037c-111">Řetězec, který určuje název, který slouží k identifikaci tohoto seznamu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4037c-111">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4037c-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4037c-112">Child Elements</span></span>  
  
|<span data-ttu-id="4037c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="4037c-113">Element</span></span>|<span data-ttu-id="4037c-114">Description</span><span class="sxs-lookup"><span data-stu-id="4037c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="4037c-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4037c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4037c-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="4037c-116">Element</span></span>|<span data-ttu-id="4037c-117">Description</span><span class="sxs-lookup"><span data-stu-id="4037c-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="4037c-118">Seznam koncových bodů zálohy.</span><span class="sxs-lookup"><span data-stu-id="4037c-118">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4037c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4037c-119">Remarks</span></span>  
 <span data-ttu-id="4037c-120">Tato část obsahuje uspořádanou kolekci koncových bodů, na které se v případě výjimky komunikace při odesílání do primárního koncového bodu přenáší zpráva.</span><span class="sxs-lookup"><span data-stu-id="4037c-120">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="4037c-121">Pokud odeslání do primárního koncového bodu uvedeného v `endpointName` atributu [\<add>](add-of-entries.md) selže s výjimkou komunikace, služba Směrování se pokusí odeslat zprávu do prvního koncového bodu v této části konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4037c-121">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="4037c-122">Pokud se tím také nezdaří s výjimkou komunikace, směrovací služba se pokusí odeslat zprávu na další zprávu obsaženou v této části, dokud pokus o odeslání nebude úspěšný, vrátí chybu jinou než výjimka komunikace nebo všechny koncové body v kolekci vrátily chybu.</span><span class="sxs-lookup"><span data-stu-id="4037c-122">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="4037c-123">V následujícím příkladu, pokud odeslání do primárního koncového bodu s názvem "cíl" vrátí výjimku komunikace, služba se pokusí odeslat zprávu do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="4037c-123">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="4037c-124">Pokud se tento pokus vrátí taky výjimku komunikace, pokusí se služba Směrování odeslat zprávu na další koncový bod v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4037c-124">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="4037c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4037c-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
