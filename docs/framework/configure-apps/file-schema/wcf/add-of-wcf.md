---
title: <add>služby WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: 0b21bdabc76ec4853a0f2664cdd3cead149417a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850298"
---
# <a name="add-of-wcf"></a><span data-ttu-id="03751-102">\<add>služby WCF</span><span class="sxs-lookup"><span data-stu-id="03751-102">\<add> of WCF</span></span>
<span data-ttu-id="03751-103">Nakonfigurujte účastníkem sledování, která naslouchá na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem, který byl nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="03751-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="03751-104">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="03751-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="03751-105">Další informace o sledování pracovních postupů a sledování účastníků najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Sledování účastníků](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="03751-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="03751-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03751-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03751-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03751-107">Attributes and Elements</span></span>  
 <span data-ttu-id="03751-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03751-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03751-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="03751-109">Attributes</span></span>  
  
|<span data-ttu-id="03751-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="03751-110">Element</span></span>|<span data-ttu-id="03751-111">Description</span><span class="sxs-lookup"><span data-stu-id="03751-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03751-112">name</span><span class="sxs-lookup"><span data-stu-id="03751-112">name</span></span>|<span data-ttu-id="03751-113">Řetězec, který určuje název člena sledování.</span><span class="sxs-lookup"><span data-stu-id="03751-113">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="03751-114">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="03751-114">profileName</span></span>|<span data-ttu-id="03751-115">Řetězec, který určuje název profilu sledování, která definuje sledování záznamů účastník sledování přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="03751-115">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="03751-116">typ</span><span class="sxs-lookup"><span data-stu-id="03751-116">type</span></span>|<span data-ttu-id="03751-117">Řetězec, který určuje typ sledování člena.</span><span class="sxs-lookup"><span data-stu-id="03751-117">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03751-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03751-118">Child Elements</span></span>  
 <span data-ttu-id="03751-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="03751-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03751-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03751-120">Parent Elements</span></span>  
  
|<span data-ttu-id="03751-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="03751-121">Element</span></span>|<span data-ttu-id="03751-122">Description</span><span class="sxs-lookup"><span data-stu-id="03751-122">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="03751-123">Seznam sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="03751-123">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03751-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03751-124">Remarks</span></span>  
 <span data-ttu-id="03751-125">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="03751-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="03751-126">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="03751-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="03751-127">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="03751-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="03751-128">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="03751-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="03751-129">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="03751-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="03751-130">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="03751-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="03751-131">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="03751-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="03751-132">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="03751-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03751-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="03751-133">Example</span></span>  
 <span data-ttu-id="03751-134">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="03751-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="03751-135">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v `<diagnostics>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="03751-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="03751-136">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="03751-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="03751-137">Toto je definován `profileName` atributu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="03751-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="03751-138">Poté, co jsou definovány, sledování účastník bude přidán do `<etwTracking>` služeb chování.</span><span class="sxs-lookup"><span data-stu-id="03751-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="03751-139">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="03751-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03751-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="03751-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="03751-141">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="03751-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="03751-142">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="03751-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
