---
title: <add> z <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152356"
---
# <a name="add-of-participants"></a><span data-ttu-id="8f694-102">\<přidat> \<účastníků></span><span class="sxs-lookup"><span data-stu-id="8f694-102">\<add> of \<participants></span></span>
<span data-ttu-id="8f694-103">Nakonfigurujte účastníkem sledování, která naslouchá na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem, který byl nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="8f694-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="8f694-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="8f694-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="8f694-105">Další informace o účastnících sledování a sledování pracovního postupu naleznete v [tématu Sledování pracovního postupu a sledování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [sledování účastníků](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="8f694-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="8f694-106">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f694-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f694-107">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="8f694-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="8f694-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sledování>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="8f694-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="8f694-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<účastníci>**](participants.md)</span><span class="sxs-lookup"><span data-stu-id="8f694-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="8f694-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="8f694-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f694-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f694-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f694-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f694-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8f694-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f694-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f694-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f694-114">Attributes</span></span>  
  
|<span data-ttu-id="8f694-115">Element</span><span class="sxs-lookup"><span data-stu-id="8f694-115">Element</span></span>|<span data-ttu-id="8f694-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8f694-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f694-117">jméno</span><span class="sxs-lookup"><span data-stu-id="8f694-117">name</span></span>|<span data-ttu-id="8f694-118">Řetězec, který určuje název člena sledování.</span><span class="sxs-lookup"><span data-stu-id="8f694-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="8f694-119">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="8f694-119">profileName</span></span>|<span data-ttu-id="8f694-120">Řetězec, který určuje název profilu sledování, která definuje sledování záznamů účastník sledování přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="8f694-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="8f694-121">type</span><span class="sxs-lookup"><span data-stu-id="8f694-121">type</span></span>|<span data-ttu-id="8f694-122">Řetězec, který určuje typ sledování člena.</span><span class="sxs-lookup"><span data-stu-id="8f694-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f694-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f694-123">Child Elements</span></span>  
 <span data-ttu-id="8f694-124">Žádné.</span><span class="sxs-lookup"><span data-stu-id="8f694-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f694-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f694-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8f694-126">Element</span><span class="sxs-lookup"><span data-stu-id="8f694-126">Element</span></span>|<span data-ttu-id="8f694-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8f694-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f694-128">\<účastníci></span><span class="sxs-lookup"><span data-stu-id="8f694-128">\<participants></span></span>](participants.md)|<span data-ttu-id="8f694-129">Seznam sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="8f694-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f694-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f694-130">Remarks</span></span>  
 <span data-ttu-id="8f694-131">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="8f694-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="8f694-132">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="8f694-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="8f694-133">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="8f694-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="8f694-134">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="8f694-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="8f694-135">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="8f694-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="8f694-136">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8f694-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="8f694-137">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="8f694-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="8f694-138">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="8f694-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f694-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f694-139">Example</span></span>  
 <span data-ttu-id="8f694-140">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="8f694-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="8f694-141">Id zprostředkovatele, který účastník sledování ETW používá pro zápis záznamů sledování do ETW je definován v části \*\* \<diagnostics>.\*\*</span><span class="sxs-lookup"><span data-stu-id="8f694-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="8f694-142">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="8f694-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="8f694-143">To je definováno **profileName** atributem \*\* \<elementu add>.\*\*</span><span class="sxs-lookup"><span data-stu-id="8f694-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="8f694-144">Jakmile jsou definovány, sledování účastník je přidán do \*\* \<etwTracking>\*\* chování služby.</span><span class="sxs-lookup"><span data-stu-id="8f694-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="8f694-145">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="8f694-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f694-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f694-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="8f694-147">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8f694-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8f694-148">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="8f694-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
