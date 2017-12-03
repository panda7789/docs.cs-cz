---
title: "&lt;workflow&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8177f04f921585b422c2567bd7282dba02fedb70
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowgt-of-wcf"></a><span data-ttu-id="b360b-102">&lt;workflow&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="b360b-102">&lt;workflow&gt; of WCF</span></span>
<span data-ttu-id="b360b-103">Nakonfigurujte účastníkem sledování, která naslouchá na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem, který byl nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="b360b-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="b360b-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="b360b-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="b360b-105">Další informace v sledování účastníci a sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování účastníky](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="b360b-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="b360b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b360b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b360b-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b360b-107">\<tracking></span></span>  
<span data-ttu-id="b360b-108">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="b360b-108">\<participants></span></span>  
<span data-ttu-id="b360b-109">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="b360b-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b360b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b360b-110">Syntax</span></span>  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b360b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b360b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b360b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b360b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b360b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b360b-113">Attributes</span></span>  
  
|<span data-ttu-id="b360b-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="b360b-114">Element</span></span>|<span data-ttu-id="b360b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b360b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b360b-116">name</span><span class="sxs-lookup"><span data-stu-id="b360b-116">name</span></span>|<span data-ttu-id="b360b-117">Řetězec, který určuje název člena sledování.</span><span class="sxs-lookup"><span data-stu-id="b360b-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="b360b-118">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="b360b-118">profileName</span></span>|<span data-ttu-id="b360b-119">Řetězec, který určuje název profilu sledování, která definuje sledování záznamů účastník sledování přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="b360b-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="b360b-120">– typ</span><span class="sxs-lookup"><span data-stu-id="b360b-120">type</span></span>|<span data-ttu-id="b360b-121">Řetězec, který určuje typ sledování člena.</span><span class="sxs-lookup"><span data-stu-id="b360b-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b360b-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b360b-122">Child Elements</span></span>  
 <span data-ttu-id="b360b-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="b360b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b360b-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b360b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b360b-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="b360b-125">Element</span></span>|<span data-ttu-id="b360b-126">Popis</span><span class="sxs-lookup"><span data-stu-id="b360b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b360b-127">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="b360b-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="b360b-128">Seznam sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="b360b-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b360b-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b360b-129">Remarks</span></span>  
 <span data-ttu-id="b360b-130">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="b360b-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="b360b-131">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="b360b-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="b360b-132">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="b360b-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="b360b-133">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="b360b-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="b360b-134">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="b360b-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b360b-135">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b360b-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="b360b-136">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="b360b-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="b360b-137">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="b360b-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b360b-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b360b-138">Example</span></span>  
 <span data-ttu-id="b360b-139">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="b360b-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="b360b-140">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v `<diagnostics>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="b360b-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="b360b-141">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="b360b-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="b360b-142">Toto je definován `profileName` atributu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b360b-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="b360b-143">Poté, co jsou definovány, sledování účastník bude přidán do `<etwTracking>` služeb chování.</span><span class="sxs-lookup"><span data-stu-id="b360b-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="b360b-144">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="b360b-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b360b-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="b360b-145">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="b360b-146">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="b360b-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b360b-147">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="b360b-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
