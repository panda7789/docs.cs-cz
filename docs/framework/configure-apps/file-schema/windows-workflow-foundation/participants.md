---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: 368b37f3ff10b660260ddd5735c70b8d72063e11
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398703"
---
# <a name="participants"></a><span data-ttu-id="d80e7-101">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="d80e7-101">\<participants></span></span>
<span data-ttu-id="d80e7-102">Nakonfigurujte seznam Účastníci, které naslouchat na sledování záznamy probíhá emitovány přímo z modulu runtime a jejich zpracování libovolné způsobem jsou nakonfigurovány pro sledování.</span><span class="sxs-lookup"><span data-stu-id="d80e7-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="d80e7-103">Jedná se o zápis do konkrétní výstupu (např. soubor, konzoly, ETW), zpracování/agregaci záznamů nebo libovolnou kombinaci, který může být vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="d80e7-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="d80e7-104">Další informace o sledování pracovních postupů a sledování účastníků najdete v tématu [sledování pracovních postupů a trasování](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) a [Sledování účastníků](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="d80e7-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="d80e7-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d80e7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d80e7-106">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d80e7-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d80e7-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d80e7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d80e7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Účastníci >**</span><span class="sxs-lookup"><span data-stu-id="d80e7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80e7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d80e7-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d80e7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d80e7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d80e7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d80e7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d80e7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d80e7-112">Attributes</span></span>  
 <span data-ttu-id="d80e7-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="d80e7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d80e7-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d80e7-114">Child Elements</span></span>  
  
|<span data-ttu-id="d80e7-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="d80e7-115">Element</span></span>|<span data-ttu-id="d80e7-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d80e7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80e7-117">\<add></span><span class="sxs-lookup"><span data-stu-id="d80e7-117">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="d80e7-118">Obsahuje nastavení pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="d80e7-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d80e7-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d80e7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d80e7-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="d80e7-120">Element</span></span>|<span data-ttu-id="d80e7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d80e7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80e7-122">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d80e7-122">\<tracking></span></span>](tracking.md)|<span data-ttu-id="d80e7-123">Představuje konfiguračního oddílu pro definování nastavení sledování služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d80e7-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d80e7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d80e7-124">Remarks</span></span>  
 <span data-ttu-id="d80e7-125">Sledování účastníci se používají pro získání data sledování vyzařovaného z pracovního postupu a uložit je do různá média.</span><span class="sxs-lookup"><span data-stu-id="d80e7-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="d80e7-126">Stejně tak jakýkoli příspěvek zpracování na sledování, které záznamy lze provést také v rámci tohoto sledování.</span><span class="sxs-lookup"><span data-stu-id="d80e7-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="d80e7-127">Více sledování účastníci můžou událostí sledování současně.</span><span class="sxs-lookup"><span data-stu-id="d80e7-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="d80e7-128">Každý účastník sledování může být přidružen k profilu různých sledování.</span><span class="sxs-lookup"><span data-stu-id="d80e7-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="d80e7-129">Účastník standardní sledování je poskytován, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="d80e7-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="d80e7-130">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="d80e7-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="d80e7-131">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="d80e7-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="d80e7-132">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="d80e7-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d80e7-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="d80e7-133">Example</span></span>  
 <span data-ttu-id="d80e7-134">Následující příklad konfigurace ukazuje standardní účastník sledování ETW konfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="d80e7-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="d80e7-135">ID zprostředkovatele, které používá účastník sledování ETW k zápisu záznamů sledování do ETW, je definováno v  **\<části > diagnostiky** .</span><span class="sxs-lookup"><span data-stu-id="d80e7-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="d80e7-136">Účastník sledování má vlastní profil přidružen k určení záznamy sledování, které se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="d80e7-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="d80e7-137">Tato definice je definována atributem  **\<** **proformátu** elementu add >.</span><span class="sxs-lookup"><span data-stu-id="d80e7-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="d80e7-138">Po definování je účastník sledování přidán do  **\<chování služby etwTracking >** Service.</span><span class="sxs-lookup"><span data-stu-id="d80e7-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="d80e7-139">Vybrané sledování účastníci bude přidán do instance pracovního postupu rozšíření, tak, aby začnou záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="d80e7-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d80e7-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d80e7-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="d80e7-141">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d80e7-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d80e7-142">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="d80e7-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
