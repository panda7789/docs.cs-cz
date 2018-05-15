---
title: '&lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 6684dcc485ef1ee2c3e5501f2fbc43898e172958
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="d4e02-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="d4e02-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="d4e02-103">Představuje konfigurační oddíl pro definování zálohování seznamu, který se zobrazí sada koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný.</span><span class="sxs-lookup"><span data-stu-id="d4e02-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="d4e02-104">Pokud první koncový bod v seznamu je vypnutý, směrovací služby bude automaticky selhání na další stránku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d4e02-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="d4e02-105">To vám dává rychlý způsob, jak přidat spolehlivost k vaší aplikaci bez nutnosti naučit klientskou aplikaci, jak bude zpracováván komplexní vzory nebo všech služeb, kde jsou nasazeny.</span><span class="sxs-lookup"><span data-stu-id="d4e02-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="d4e02-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d4e02-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d4e02-107">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="d4e02-107">\<routing></span></span>  
<span data-ttu-id="d4e02-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="d4e02-108">\<backupLists></span></span>  
<span data-ttu-id="d4e02-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="d4e02-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e02-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4e02-110">Syntax</span></span>  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4e02-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4e02-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d4e02-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4e02-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4e02-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4e02-113">Attributes</span></span>  
  
|<span data-ttu-id="d4e02-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4e02-114">Attribute</span></span>|<span data-ttu-id="d4e02-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d4e02-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4e02-116">name</span><span class="sxs-lookup"><span data-stu-id="d4e02-116">name</span></span>|<span data-ttu-id="d4e02-117">Řetězec, který určuje název sloužící k identifikaci tento seznam koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d4e02-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4e02-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4e02-118">Child Elements</span></span>  
  
|<span data-ttu-id="d4e02-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4e02-119">Element</span></span>|<span data-ttu-id="d4e02-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d4e02-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e02-121">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="d4e02-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="d4e02-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4e02-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d4e02-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4e02-123">Element</span></span>|<span data-ttu-id="d4e02-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d4e02-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e02-125">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="d4e02-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d4e02-126">Seznam koncových bodů zálohování.</span><span class="sxs-lookup"><span data-stu-id="d4e02-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4e02-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4e02-127">Remarks</span></span>  
 <span data-ttu-id="d4e02-128">Tato část obsahuje uspořádanou kolekci koncových bodů, které zprávy budou předány v případě výjimky komunikace při odesílání na primární koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d4e02-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="d4e02-129">Pokud odeslání primární koncový bod uvedený v `endpointName` atribut [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) selže s výjimkou komunikace, směrovací služby pokusí odeslat zprávu na první koncový bod v tomto konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="d4e02-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="d4e02-130">Pokud se to nezdaří ani s výjimkou komunikace, se pokusí odeslat zprávu na další zprávu obsažené v této části, dokud nebude pokusu o odeslání úspěšné, vrátí selhání než výjimka komunikaci nebo všechny koncové body ve směrovací služby kolekce mají vrátila chybu.</span><span class="sxs-lookup"><span data-stu-id="d4e02-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="d4e02-131">V následujícím příkladu Pokud odeslání primární koncový bod s názvem "Cílové" vrátí komunikace výjimky, službu pokusí odeslat zprávu do "alternateServiceQueue".</span><span class="sxs-lookup"><span data-stu-id="d4e02-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="d4e02-132">Pokud tento pokus také vrátí hodnotu výjimka komunikace, směrovací služby pokusí odeslat zprávu na další koncový bod v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d4e02-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4e02-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4e02-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
