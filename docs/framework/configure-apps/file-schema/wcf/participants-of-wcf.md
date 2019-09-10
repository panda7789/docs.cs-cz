---
title: <participants>služby WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 35ed7a49967143838a6f74c51e77c553817bd09a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855091"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="c64fe-102">\<Účastníci > služby WCF</span><span class="sxs-lookup"><span data-stu-id="c64fe-102">\<participants> of WCF</span></span>
<span data-ttu-id="c64fe-103">Nakonfigurujte seznam Účastníci, které naslouchat na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem jsou nakonfigurovány pro sledování.</span><span class="sxs-lookup"><span data-stu-id="c64fe-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="c64fe-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="c64fe-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="c64fe-105">Další informace o sledování pracovních postupů a sledování účastníků najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Sledování účastníků](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="c64fe-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="c64fe-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c64fe-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c64fe-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c64fe-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c64fe-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c64fe-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>  
<span data-ttu-id="c64fe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Účastníci >**</span><span class="sxs-lookup"><span data-stu-id="c64fe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c64fe-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c64fe-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c64fe-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c64fe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c64fe-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c64fe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c64fe-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c64fe-113">Attributes</span></span>  
 <span data-ttu-id="c64fe-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="c64fe-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c64fe-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c64fe-115">Child Elements</span></span>  
  
|<span data-ttu-id="c64fe-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="c64fe-116">Element</span></span>|<span data-ttu-id="c64fe-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c64fe-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c64fe-118">\<add></span><span class="sxs-lookup"><span data-stu-id="c64fe-118">\<add></span></span>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="c64fe-119">Obsahuje nastavení pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="c64fe-119">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c64fe-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c64fe-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c64fe-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c64fe-121">Element</span></span>|<span data-ttu-id="c64fe-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c64fe-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c64fe-123">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="c64fe-123">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="c64fe-124">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c64fe-124">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c64fe-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c64fe-125">Remarks</span></span>  
 <span data-ttu-id="c64fe-126">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="c64fe-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="c64fe-127">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="c64fe-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="c64fe-128">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="c64fe-128">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="c64fe-129">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="c64fe-129">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="c64fe-130">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="c64fe-130">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="c64fe-131">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c64fe-131">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="c64fe-132">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="c64fe-132">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="c64fe-133">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="c64fe-133">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c64fe-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="c64fe-134">Example</span></span>  
 <span data-ttu-id="c64fe-135">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="c64fe-135">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="c64fe-136">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v `<diagnostics>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="c64fe-136">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="c64fe-137">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="c64fe-137">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="c64fe-138">Toto je definován `profileName` atributu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c64fe-138">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="c64fe-139">Poté, co jsou definovány, sledování účastník bude přidán do `<etwTracking>` služeb chování.</span><span class="sxs-lookup"><span data-stu-id="c64fe-139">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="c64fe-140">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="c64fe-140">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c64fe-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c64fe-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="c64fe-142">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c64fe-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c64fe-143">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="c64fe-143">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
