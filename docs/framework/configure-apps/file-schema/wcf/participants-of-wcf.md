---
title: <participants> služby WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: f714d7992266dbd6fc0c50a2bfadd61588179577
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227428"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="a5aaa-102">\<participants > služby WCF</span><span class="sxs-lookup"><span data-stu-id="a5aaa-102">\<participants> of WCF</span></span>
<span data-ttu-id="a5aaa-103">Nakonfigurujte seznam Účastníci, které naslouchat na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem jsou nakonfigurovány pro sledování.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="a5aaa-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="a5aaa-105">Další informace v sledování pracovních postupů a sledování účastníci naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování účastníci](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="a5aaa-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="a5aaa-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a5aaa-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a5aaa-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a5aaa-107">\<tracking></span></span>  
<span data-ttu-id="a5aaa-108">\<participants ></span><span class="sxs-lookup"><span data-stu-id="a5aaa-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5aaa-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5aaa-109">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5aaa-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5aaa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5aaa-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5aaa-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5aaa-112">Attributes</span></span>  
 <span data-ttu-id="a5aaa-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5aaa-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5aaa-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a5aaa-114">Child Elements</span></span>  
  
|<span data-ttu-id="a5aaa-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5aaa-115">Element</span></span>|<span data-ttu-id="a5aaa-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a5aaa-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5aaa-117">\<add></span><span class="sxs-lookup"><span data-stu-id="a5aaa-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="a5aaa-118">Obsahuje nastavení pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5aaa-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a5aaa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a5aaa-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5aaa-120">Element</span></span>|<span data-ttu-id="a5aaa-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a5aaa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5aaa-122">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a5aaa-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="a5aaa-123">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5aaa-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5aaa-124">Remarks</span></span>  
 <span data-ttu-id="a5aaa-125">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="a5aaa-126">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="a5aaa-127">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="a5aaa-128">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="a5aaa-129">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="a5aaa-130">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="a5aaa-131">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="a5aaa-132">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5aaa-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5aaa-133">Example</span></span>  
 <span data-ttu-id="a5aaa-134">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="a5aaa-135">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v `<diagnostics>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="a5aaa-136">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="a5aaa-137">Toto je definován `profileName` atributu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="a5aaa-138">Poté, co jsou definovány, sledování účastník bude přidán do `<etwTracking>` služeb chování.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="a5aaa-139">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="a5aaa-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5aaa-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5aaa-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="a5aaa-141">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a5aaa-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5aaa-142">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="a5aaa-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
