---
title: '&lt;etwTracking&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: f9d1acd5dafb9df181b036db9d3ad783ca618874
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684320"
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="55296-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="55296-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="55296-103">Chování služby, který umožňuje službu, která využívají pomocí sledování ETW <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="55296-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="55296-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="55296-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="55296-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="55296-105">\<behaviors></span></span>  
<span data-ttu-id="55296-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="55296-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="55296-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="55296-107">\<behavior></span></span>  
<span data-ttu-id="55296-108">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="55296-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55296-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55296-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55296-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="55296-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55296-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="55296-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55296-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="55296-112">Attributes</span></span>  
  
|<span data-ttu-id="55296-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="55296-113">Attribute</span></span>|<span data-ttu-id="55296-114">Popis</span><span class="sxs-lookup"><span data-stu-id="55296-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55296-115">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="55296-115">profileName</span></span>|<span data-ttu-id="55296-116">Řetězec, který určuje název profilu sledování přidružené k tomuto chování.</span><span class="sxs-lookup"><span data-stu-id="55296-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55296-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="55296-117">Child Elements</span></span>  
 <span data-ttu-id="55296-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="55296-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55296-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="55296-119">Parent Elements</span></span>  
  
|<span data-ttu-id="55296-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="55296-120">Element</span></span>|<span data-ttu-id="55296-121">Popis</span><span class="sxs-lookup"><span data-stu-id="55296-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55296-122">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="55296-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="55296-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="55296-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55296-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55296-124">Remarks</span></span>  
 <span data-ttu-id="55296-125">Po přidání do služby konfiguraci chování, tento element konfigurace konfigurovat účastníkem sledování na službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="55296-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="55296-126">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="55296-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="55296-127">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="55296-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55296-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="55296-128">Example</span></span>  
 <span data-ttu-id="55296-129">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="55296-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="55296-130">Id zprostředkovatele, které účastník sledování ETW používá k zápisu do ETW sledování záznamů je definována v  **\<diagnostiky >** oddílu.</span><span class="sxs-lookup"><span data-stu-id="55296-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="55296-131">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="55296-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="55296-132">Toto je definován **profileName** atribut  **\<Přidat >** elementu.</span><span class="sxs-lookup"><span data-stu-id="55296-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="55296-133">Jakmile jsou definovány, sledování účastník bude přidán do  **\<etwTracking >** služeb chování.</span><span class="sxs-lookup"><span data-stu-id="55296-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="55296-134">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="55296-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55296-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55296-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="55296-136">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="55296-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="55296-137">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="55296-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
