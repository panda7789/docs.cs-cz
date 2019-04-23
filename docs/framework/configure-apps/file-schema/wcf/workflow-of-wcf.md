---
title: <workflow> služby WCF
ms.date: 03/30/2017
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
ms.openlocfilehash: 190e66096cf2dfa2028c95b22526fc3c84712ab8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122067"
---
# <a name="workflow-of-wcf"></a><span data-ttu-id="a0b07-102">\<Workflow > služby WCF</span><span class="sxs-lookup"><span data-stu-id="a0b07-102">\<workflow> of WCF</span></span>
<span data-ttu-id="a0b07-103">Nakonfigurujte účastníkem sledování, která naslouchá na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem, který byl nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="a0b07-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="a0b07-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="a0b07-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="a0b07-105">Další informace v sledování pracovních postupů a sledování účastníci naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování účastníci](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="a0b07-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="a0b07-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a0b07-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a0b07-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a0b07-107">\<tracking></span></span>  
<span data-ttu-id="a0b07-108">\<participants ></span><span class="sxs-lookup"><span data-stu-id="a0b07-108">\<participants></span></span>  
<span data-ttu-id="a0b07-109">\<add></span><span class="sxs-lookup"><span data-stu-id="a0b07-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b07-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0b07-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0b07-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0b07-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a0b07-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0b07-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0b07-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0b07-113">Attributes</span></span>  
  
|<span data-ttu-id="a0b07-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0b07-114">Element</span></span>|<span data-ttu-id="a0b07-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a0b07-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0b07-116">name</span><span class="sxs-lookup"><span data-stu-id="a0b07-116">name</span></span>|<span data-ttu-id="a0b07-117">Řetězec, který určuje název člena sledování.</span><span class="sxs-lookup"><span data-stu-id="a0b07-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="a0b07-118">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="a0b07-118">profileName</span></span>|<span data-ttu-id="a0b07-119">Řetězec, který určuje název profilu sledování, která definuje sledování záznamů účastník sledování přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="a0b07-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="a0b07-120"> – typ</span><span class="sxs-lookup"><span data-stu-id="a0b07-120">type</span></span>|<span data-ttu-id="a0b07-121">Řetězec, který určuje typ sledování člena.</span><span class="sxs-lookup"><span data-stu-id="a0b07-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0b07-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0b07-122">Child Elements</span></span>  
 <span data-ttu-id="a0b07-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0b07-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0b07-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0b07-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a0b07-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0b07-125">Element</span></span>|<span data-ttu-id="a0b07-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a0b07-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0b07-127">\<participants></span><span class="sxs-lookup"><span data-stu-id="a0b07-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="a0b07-128">Seznam sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="a0b07-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0b07-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0b07-129">Remarks</span></span>  
 <span data-ttu-id="a0b07-130">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="a0b07-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="a0b07-131">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="a0b07-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="a0b07-132">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="a0b07-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="a0b07-133">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="a0b07-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="a0b07-134">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="a0b07-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="a0b07-135">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a0b07-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="a0b07-136">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="a0b07-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="a0b07-137">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="a0b07-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b07-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0b07-138">Example</span></span>  
 <span data-ttu-id="a0b07-139">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="a0b07-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="a0b07-140">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v `<diagnostics>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="a0b07-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="a0b07-141">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="a0b07-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="a0b07-142">Toto je definován `profileName` atributu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a0b07-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="a0b07-143">Poté, co jsou definovány, sledování účastník bude přidán do `<etwTracking>` služeb chování.</span><span class="sxs-lookup"><span data-stu-id="a0b07-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="a0b07-144">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="a0b07-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="a0b07-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0b07-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="a0b07-146">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a0b07-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a0b07-147">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="a0b07-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
