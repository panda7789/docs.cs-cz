---
title: "&lt;Účastníci&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e20cc8ed26feccf6fcf7fae40d2a219cd103dbb0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltparticipantsgt"></a><span data-ttu-id="58e9f-102">&lt;Účastníci&gt;</span><span class="sxs-lookup"><span data-stu-id="58e9f-102">&lt;participants&gt;</span></span>
<span data-ttu-id="58e9f-103">Nakonfigurujte seznam Účastníci, které naslouchat na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem jsou nakonfigurovány pro sledování.</span><span class="sxs-lookup"><span data-stu-id="58e9f-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="58e9f-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="58e9f-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="58e9f-105">Další informace v sledování účastníci a sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování účastníky](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="58e9f-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="58e9f-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="58e9f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="58e9f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="58e9f-107">\<tracking></span></span>  
<span data-ttu-id="58e9f-108">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="58e9f-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e9f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e9f-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58e9f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58e9f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="58e9f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58e9f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58e9f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="58e9f-112">Attributes</span></span>  
 <span data-ttu-id="58e9f-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="58e9f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58e9f-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58e9f-114">Child Elements</span></span>  
  
|<span data-ttu-id="58e9f-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="58e9f-115">Element</span></span>|<span data-ttu-id="58e9f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="58e9f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58e9f-117">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="58e9f-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="58e9f-118">Obsahuje nastavení pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="58e9f-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58e9f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58e9f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="58e9f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="58e9f-120">Element</span></span>|<span data-ttu-id="58e9f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="58e9f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58e9f-122">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="58e9f-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="58e9f-123">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="58e9f-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e9f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58e9f-124">Remarks</span></span>  
 <span data-ttu-id="58e9f-125">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="58e9f-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="58e9f-126">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="58e9f-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="58e9f-127">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="58e9f-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="58e9f-128">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="58e9f-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="58e9f-129">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="58e9f-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="58e9f-130">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="58e9f-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="58e9f-131">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="58e9f-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="58e9f-132">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="58e9f-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e9f-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="58e9f-133">Example</span></span>  
 <span data-ttu-id="58e9f-134">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="58e9f-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="58e9f-135">Id zprostředkovatele, které účastník sledování trasování událostí pro Windows používá k zápisu sledování záznamů do trasování událostí pro Windows je definována v  **\<diagnostics >** části.</span><span class="sxs-lookup"><span data-stu-id="58e9f-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="58e9f-136">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="58e9f-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="58e9f-137">To je definováno **profileName** atribut  **\<Přidat >** element.</span><span class="sxs-lookup"><span data-stu-id="58e9f-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="58e9f-138">Jakmile jsou definované, účastník sledování je přidána do  **\<etwTracking >** služby chování.</span><span class="sxs-lookup"><span data-stu-id="58e9f-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="58e9f-139">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="58e9f-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58e9f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="58e9f-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="58e9f-141">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="58e9f-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="58e9f-142">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="58e9f-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
