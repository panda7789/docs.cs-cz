---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152168"
---
# \<etwTracking>
<span data-ttu-id="76280-101">Chování služby, které umožňuje službě využívat sledování ETW pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="76280-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="76280-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76280-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76280-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76280-103">Attributes and Elements</span></span>  
 <span data-ttu-id="76280-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76280-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76280-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="76280-105">Attributes</span></span>  
  
|<span data-ttu-id="76280-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="76280-106">Attribute</span></span>|<span data-ttu-id="76280-107">Popis</span><span class="sxs-lookup"><span data-stu-id="76280-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76280-108">Název_profilu</span><span class="sxs-lookup"><span data-stu-id="76280-108">profileName</span></span>|<span data-ttu-id="76280-109">Řetězec, který určuje název profilu sledování přidružené k tomuto chování.</span><span class="sxs-lookup"><span data-stu-id="76280-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76280-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76280-110">Child Elements</span></span>  
 <span data-ttu-id="76280-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="76280-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76280-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76280-112">Parent Elements</span></span>  
  
|<span data-ttu-id="76280-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="76280-113">Element</span></span>|<span data-ttu-id="76280-114">Description</span><span class="sxs-lookup"><span data-stu-id="76280-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76280-115">\<behavior>tohoto\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="76280-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="76280-116">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="76280-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76280-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76280-117">Remarks</span></span>  
 <span data-ttu-id="76280-118">Po přidání do služby konfiguraci chování, tento element konfigurace konfigurovat účastníkem sledování na službě pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="76280-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="76280-119">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="76280-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="76280-120">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="76280-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76280-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="76280-121">Example</span></span>  
 <span data-ttu-id="76280-122">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="76280-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="76280-123">ID zprostředkovatele, které používá účastník sledování ETW k zápisu záznamů sledování do ETW, je definováno v **\<diagnostics>** oddílu.</span><span class="sxs-lookup"><span data-stu-id="76280-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="76280-124">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="76280-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="76280-125">Toto je definováno atributem **prosouboru** **\<add>** elementu.</span><span class="sxs-lookup"><span data-stu-id="76280-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="76280-126">Po definování je účastník sledování přidán do **\<etwTracking>** chování služby.</span><span class="sxs-lookup"><span data-stu-id="76280-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="76280-127">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="76280-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76280-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="76280-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="76280-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="76280-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="76280-130">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="76280-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
