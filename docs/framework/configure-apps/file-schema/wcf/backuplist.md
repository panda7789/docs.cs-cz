---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: b0a6c604b5741c1355c35fca510cd10544dab9f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135730"
---
# <a name="backuplist"></a><span data-ttu-id="04e4e-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="04e4e-101">\<backupList></span></span>
<span data-ttu-id="04e4e-102">Představuje konfigurační oddíl pro definování zálohování seznamu, který uvádí sady koncových bodů, které byste chtěli směrovací služba použít v případě, že nelze dosáhnout primárního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="04e4e-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="04e4e-103">Pokud je první koncový bod v seznamu dolů, směrovací služba se automaticky převzetí služby při selhání k dalším objektem v seznamu.</span><span class="sxs-lookup"><span data-stu-id="04e4e-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="04e4e-104">To umožňuje rychlé přidání spolehlivosti do aplikace bez nutnosti představuje klientskou aplikaci, jak zpracovávat složité vzory nebo všechny služby, ve které jsou nasazené.</span><span class="sxs-lookup"><span data-stu-id="04e4e-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="04e4e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04e4e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="04e4e-106">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="04e4e-106">\<routing></span></span>  
<span data-ttu-id="04e4e-107">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="04e4e-107">\<backupLists></span></span>  
<span data-ttu-id="04e4e-108">\<backupList></span><span class="sxs-lookup"><span data-stu-id="04e4e-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e4e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e4e-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04e4e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04e4e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04e4e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04e4e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04e4e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="04e4e-112">Attributes</span></span>  
  
|<span data-ttu-id="04e4e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="04e4e-113">Attribute</span></span>|<span data-ttu-id="04e4e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="04e4e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04e4e-115">name</span><span class="sxs-lookup"><span data-stu-id="04e4e-115">name</span></span>|<span data-ttu-id="04e4e-116">Řetězec určující název používaný k identifikaci tohoto seznamu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="04e4e-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04e4e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04e4e-117">Child Elements</span></span>  
  
|<span data-ttu-id="04e4e-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="04e4e-118">Element</span></span>|<span data-ttu-id="04e4e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="04e4e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04e4e-120">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="04e4e-120">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="04e4e-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04e4e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="04e4e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="04e4e-122">Element</span></span>|<span data-ttu-id="04e4e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="04e4e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04e4e-124">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="04e4e-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="04e4e-125">Seznamu zálohy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="04e4e-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04e4e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04e4e-126">Remarks</span></span>  
 <span data-ttu-id="04e4e-127">Tato část obsahuje řazená kolekce koncových bodů, které zprávy budou předány v případě výjimky komunikace při odesílání na primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="04e4e-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="04e4e-128">Pokud uvedený na seznamu odeslat na primární koncový bod `endpointName` atribut [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) selže s výjimkou komunikace, směrovací služba se pokusí o odeslání zprávy na první koncový bod v tomto konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="04e4e-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="04e4e-129">Pokud to je také neúspěšná, s výjimkou komunikace, směrovací služba se pokusí odeslat zprávu na další zprávu obsažené v této části, až do pokusu o odeslání úspěšná, vrátí selhání než výjimky komunikace nebo všechny koncové body v kolekce mají vrátila chybu.</span><span class="sxs-lookup"><span data-stu-id="04e4e-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="04e4e-130">V následujícím příkladu Pokud odeslat na primární koncový bod s názvem "Cíl" vrátí výjimky komunikace, služba se pokusí odeslání zprávy do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="04e4e-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="04e4e-131">Pokud tento pokus také vrátí hodnotu výjimky komunikace, směrovací služba se pokusí odeslat zprávu do další koncový bod v kolekci.</span><span class="sxs-lookup"><span data-stu-id="04e4e-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04e4e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04e4e-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
