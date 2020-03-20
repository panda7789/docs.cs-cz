---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152168"
---
# <a name="etwtracking"></a><span data-ttu-id="3d6f5-101">\<etwSledovací></span><span class="sxs-lookup"><span data-stu-id="3d6f5-101">\<etwTracking></span></span>
<span data-ttu-id="3d6f5-102">Chování služby, které umožňuje službě využívat sledování <xref:System.Activities.Tracking.EtwTrackingParticipant>ETW pomocí .</span><span class="sxs-lookup"><span data-stu-id="3d6f5-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="3d6f5-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3d6f5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3d6f5-104">&nbsp;&nbsp;[**\<Systému.>ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d6f5-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="3d6f5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d6f5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3d6f5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d6f5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3d6f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<chování>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d6f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3d6f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span><span class="sxs-lookup"><span data-stu-id="3d6f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6f5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d6f5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d6f5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d6f5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d6f5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d6f5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d6f5-112">Attributes</span></span>  
  
|<span data-ttu-id="3d6f5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3d6f5-113">Attribute</span></span>|<span data-ttu-id="3d6f5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3d6f5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d6f5-115">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="3d6f5-115">profileName</span></span>|<span data-ttu-id="3d6f5-116">Řetězec, který určuje název profilu sledování přidružené k tomuto chování.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d6f5-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d6f5-117">Child Elements</span></span>  
 <span data-ttu-id="3d6f5-118">Žádné.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d6f5-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d6f5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3d6f5-120">Element</span><span class="sxs-lookup"><span data-stu-id="3d6f5-120">Element</span></span>|<span data-ttu-id="3d6f5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3d6f5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d6f5-122">\<chování> \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3d6f5-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3d6f5-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d6f5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d6f5-124">Remarks</span></span>  
 <span data-ttu-id="3d6f5-125">Po přidání do služby konfiguraci chování, tento element konfigurace konfigurovat účastníkem sledování na službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="3d6f5-126">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="3d6f5-127">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6f5-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d6f5-128">Example</span></span>  
 <span data-ttu-id="3d6f5-129">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="3d6f5-130">Id zprostředkovatele, který účastník sledování ETW používá pro zápis záznamů sledování do ETW je definován v části \*\* \<diagnostics>.\*\*</span><span class="sxs-lookup"><span data-stu-id="3d6f5-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="3d6f5-131">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="3d6f5-132">To je definováno **profileName** atributem \*\* \<elementu add>.\*\*</span><span class="sxs-lookup"><span data-stu-id="3d6f5-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="3d6f5-133">Jakmile jsou definovány, sledování účastník je přidán do \*\* \<etwTracking>\*\* chování služby.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="3d6f5-134">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="3d6f5-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d6f5-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d6f5-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="3d6f5-136">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3d6f5-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3d6f5-137">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="3d6f5-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
