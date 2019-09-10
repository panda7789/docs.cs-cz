---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850271"
---
# <a name="backuplist"></a><span data-ttu-id="a5083-101">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="a5083-101">\<backupList></span></span>
<span data-ttu-id="a5083-102">Představuje konfigurační oddíl pro definování seznamu zálohování, který vytvoří výčet sady koncových bodů, které chcete, aby služba Směrování použila v případě, že není dostupný primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a5083-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a5083-103">Pokud je první koncový bod v seznamu mimo provoz, směrovací služba se v seznamu automaticky převezme na další.</span><span class="sxs-lookup"><span data-stu-id="a5083-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="a5083-104">Díky tomu můžete rychle přidat do své aplikace spolehlivost, aniž byste museli poučit klientské aplikace o tom, jak zpracovávat složité vzory nebo kde jsou nasazené všechny služby.</span><span class="sxs-lookup"><span data-stu-id="a5083-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="a5083-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5083-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5083-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a5083-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a5083-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="a5083-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="a5083-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="a5083-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="a5083-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupList >**</span><span class="sxs-lookup"><span data-stu-id="a5083-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5083-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5083-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5083-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5083-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a5083-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5083-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5083-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5083-113">Attributes</span></span>  
  
|<span data-ttu-id="a5083-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a5083-114">Attribute</span></span>|<span data-ttu-id="a5083-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a5083-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5083-116">name</span><span class="sxs-lookup"><span data-stu-id="a5083-116">name</span></span>|<span data-ttu-id="a5083-117">Řetězec, který určuje název, který slouží k identifikaci tohoto seznamu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="a5083-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5083-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a5083-118">Child Elements</span></span>  
  
|<span data-ttu-id="a5083-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5083-119">Element</span></span>|<span data-ttu-id="a5083-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a5083-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5083-121">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="a5083-121">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="a5083-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a5083-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a5083-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5083-123">Element</span></span>|<span data-ttu-id="a5083-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a5083-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5083-125">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="a5083-125">\<routing></span></span>](routing.md)|<span data-ttu-id="a5083-126">Seznam koncových bodů zálohy.</span><span class="sxs-lookup"><span data-stu-id="a5083-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5083-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5083-127">Remarks</span></span>  
 <span data-ttu-id="a5083-128">Tato část obsahuje uspořádanou kolekci koncových bodů, na které se v případě výjimky komunikace při odesílání do primárního koncového bodu přenáší zpráva.</span><span class="sxs-lookup"><span data-stu-id="a5083-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="a5083-129">Pokud se odeslání do primárního koncového bodu uvedeného v `endpointName` [ \<atributu Add >](add-of-entries.md) nezdaří s výjimkou komunikace, služba Směrování se pokusí odeslat zprávu do prvního koncového bodu v této části konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a5083-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="a5083-130">Pokud se tím také nezdaří s výjimkou komunikace, směrovací služba se pokusí odeslat zprávu na další zprávu obsaženou v této části, dokud pokus o odeslání nebude úspěšný, vrátí chybu jinou než výjimka komunikace nebo všechny koncové body v kolekce vrátila chybu.</span><span class="sxs-lookup"><span data-stu-id="a5083-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="a5083-131">V následujícím příkladu, pokud odeslání do primárního koncového bodu s názvem "cíl" vrátí výjimku komunikace, služba se pokusí odeslat zprávu do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="a5083-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="a5083-132">Pokud se tento pokus vrátí taky výjimku komunikace, pokusí se služba Směrování odeslat zprávu na další koncový bod v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a5083-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5083-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5083-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
