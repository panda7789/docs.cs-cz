---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: e6e996bd1cc32258167e30287e9338a4773ce921
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152025"
---
# \<participants>
<span data-ttu-id="ce134-101">Nakonfigurujte seznam Účastníci, které naslouchat na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem jsou nakonfigurovány pro sledování.</span><span class="sxs-lookup"><span data-stu-id="ce134-101">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="ce134-102">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="ce134-102">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="ce134-103">Další informace o sledování pracovních postupů a sledování účastníků najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Sledování účastníků](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="ce134-103">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="ce134-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce134-104">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce134-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ce134-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ce134-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ce134-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce134-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ce134-107">Attributes</span></span>  
 <span data-ttu-id="ce134-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="ce134-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ce134-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ce134-109">Child Elements</span></span>  
  
|<span data-ttu-id="ce134-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="ce134-110">Element</span></span>|<span data-ttu-id="ce134-111">Description</span><span class="sxs-lookup"><span data-stu-id="ce134-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-participants.md)|<span data-ttu-id="ce134-112">Obsahuje nastavení pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="ce134-112">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce134-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ce134-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ce134-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="ce134-114">Element</span></span>|<span data-ttu-id="ce134-115">Description</span><span class="sxs-lookup"><span data-stu-id="ce134-115">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="ce134-116">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ce134-116">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce134-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce134-117">Remarks</span></span>  
 <span data-ttu-id="ce134-118">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="ce134-118">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="ce134-119">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="ce134-119">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="ce134-120">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="ce134-120">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="ce134-121">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="ce134-121">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="ce134-122">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="ce134-122">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ce134-123">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ce134-123">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="ce134-124">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="ce134-124">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="ce134-125">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="ce134-125">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce134-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce134-126">Example</span></span>  
 <span data-ttu-id="ce134-127">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="ce134-127">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="ce134-128">ID zprostředkovatele, které používá účastník sledování ETW k zápisu záznamů sledování do ETW, je definováno v **\<diagnostics>** oddílu.</span><span class="sxs-lookup"><span data-stu-id="ce134-128">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="ce134-129">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="ce134-129">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="ce134-130">Toto je definováno atributem **prosouboru** **\<add>** elementu.</span><span class="sxs-lookup"><span data-stu-id="ce134-130">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="ce134-131">Po definování je účastník sledování přidán do **\<etwTracking>** chování služby.</span><span class="sxs-lookup"><span data-stu-id="ce134-131">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="ce134-132">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="ce134-132">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ce134-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce134-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="ce134-134">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ce134-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ce134-135">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="ce134-135">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
