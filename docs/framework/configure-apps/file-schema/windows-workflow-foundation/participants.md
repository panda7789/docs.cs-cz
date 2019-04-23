---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: ffc16f78b266b69e80023f177f10ad6f367b5623
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104881"
---
# <a name="participants"></a><span data-ttu-id="b9f04-101">\<participants ></span><span class="sxs-lookup"><span data-stu-id="b9f04-101">\<participants></span></span>
<span data-ttu-id="b9f04-102">Nakonfigurujte seznam Účastníci, které naslouchat na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem jsou nakonfigurovány pro sledování.</span><span class="sxs-lookup"><span data-stu-id="b9f04-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="b9f04-103">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="b9f04-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="b9f04-104">Další informace v sledování pracovních postupů a sledování účastníci naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování účastníci](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="b9f04-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="b9f04-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b9f04-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b9f04-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b9f04-106">\<tracking></span></span>  
<span data-ttu-id="b9f04-107">\<participants ></span><span class="sxs-lookup"><span data-stu-id="b9f04-107">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f04-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9f04-108">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9f04-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b9f04-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b9f04-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b9f04-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9f04-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9f04-111">Attributes</span></span>  
 <span data-ttu-id="b9f04-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="b9f04-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b9f04-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b9f04-113">Child Elements</span></span>  
  
|<span data-ttu-id="b9f04-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9f04-114">Element</span></span>|<span data-ttu-id="b9f04-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b9f04-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9f04-116">\<add></span><span class="sxs-lookup"><span data-stu-id="b9f04-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="b9f04-117">Obsahuje nastavení pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="b9f04-117">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9f04-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b9f04-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b9f04-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9f04-119">Element</span></span>|<span data-ttu-id="b9f04-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b9f04-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9f04-121">\<tracking></span><span class="sxs-lookup"><span data-stu-id="b9f04-121">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="b9f04-122">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b9f04-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9f04-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9f04-123">Remarks</span></span>  
 <span data-ttu-id="b9f04-124">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="b9f04-124">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="b9f04-125">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="b9f04-125">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="b9f04-126">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="b9f04-126">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="b9f04-127">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="b9f04-127">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="b9f04-128">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="b9f04-128">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b9f04-129">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b9f04-129">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="b9f04-130">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="b9f04-130">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="b9f04-131">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="b9f04-131">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9f04-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9f04-132">Example</span></span>  
 <span data-ttu-id="b9f04-133">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="b9f04-133">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="b9f04-134">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v  **\<diagnostiky >** oddílu.</span><span class="sxs-lookup"><span data-stu-id="b9f04-134">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="b9f04-135">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="b9f04-135">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="b9f04-136">Toto je definován **profileName** atribut  **\<Přidat >** elementu.</span><span class="sxs-lookup"><span data-stu-id="b9f04-136">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="b9f04-137">Jakmile jsou definovány, sledování účastník bude přidán do  **\<etwTracking >** služeb chování.</span><span class="sxs-lookup"><span data-stu-id="b9f04-137">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="b9f04-138">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="b9f04-138">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9f04-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9f04-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="b9f04-140">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b9f04-140">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b9f04-141">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="b9f04-141">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
