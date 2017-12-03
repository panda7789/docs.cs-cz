---
title: 116 - WorkflowInstanceSuspendedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59b77e2fac36dea3afce77a74e0ccacb432a2ada
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a><span data-ttu-id="a370f-102">116 - WorkflowInstanceSuspendedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="a370f-102">116 - WorkflowInstanceSuspendedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="a370f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a370f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a370f-104">ID</span><span class="sxs-lookup"><span data-stu-id="a370f-104">ID</span></span>|<span data-ttu-id="a370f-105">116</span><span class="sxs-lookup"><span data-stu-id="a370f-105">116</span></span>|  
|<span data-ttu-id="a370f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a370f-106">Keywords</span></span>|<span data-ttu-id="a370f-107">HealthMonitoring WFTracking</span><span class="sxs-lookup"><span data-stu-id="a370f-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="a370f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a370f-108">Level</span></span>|<span data-ttu-id="a370f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a370f-109">Information</span></span>|  
|<span data-ttu-id="a370f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a370f-110">Channel</span></span>|<span data-ttu-id="a370f-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="a370f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a370f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a370f-112">Description</span></span>  
 <span data-ttu-id="a370f-113">Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když instanci pracovního postupu vysílá WorkflowInstanceSuspended záznam.</span><span class="sxs-lookup"><span data-stu-id="a370f-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a370f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a370f-114">Message</span></span>  
 <span data-ttu-id="a370f-115">TrackRecord = WorkflowInstanceSuspendedRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, důvod = %5, poznámky = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="a370f-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="a370f-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a370f-116">Details</span></span>  
  
|<span data-ttu-id="a370f-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a370f-117">Data Item Name</span></span>|<span data-ttu-id="a370f-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a370f-118">Data Item Type</span></span>|<span data-ttu-id="a370f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a370f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a370f-120">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="a370f-120">InstanceId</span></span>|<span data-ttu-id="a370f-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="a370f-121">xs:GUID</span></span>|<span data-ttu-id="a370f-122">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a370f-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a370f-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="a370f-123">RecordNumber</span></span>|<span data-ttu-id="a370f-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="a370f-124">xs:long</span></span>|<span data-ttu-id="a370f-125">Pořadové číslo emitovaného záznamu</span><span class="sxs-lookup"><span data-stu-id="a370f-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="a370f-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="a370f-126">EventTime</span></span>|<span data-ttu-id="a370f-127">xs</span><span class="sxs-lookup"><span data-stu-id="a370f-127">xs:dateTime</span></span>|<span data-ttu-id="a370f-128">Čas v UTC při byl vygenerované události</span><span class="sxs-lookup"><span data-stu-id="a370f-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="a370f-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="a370f-129">ActivityDefinitionId</span></span>|<span data-ttu-id="a370f-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="a370f-130">xs:string</span></span>|<span data-ttu-id="a370f-131">Název kořenové aktivity v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="a370f-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="a370f-132">Stav</span><span class="sxs-lookup"><span data-stu-id="a370f-132">State</span></span>|<span data-ttu-id="a370f-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="a370f-133">xs:string</span></span>|<span data-ttu-id="a370f-134">Aktuální stav pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a370f-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="a370f-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a370f-135">Annotations</span></span>|<span data-ttu-id="a370f-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="a370f-136">xs:string</span></span>|<span data-ttu-id="a370f-137">Poznámky, které byly přidány k této události.</span><span class="sxs-lookup"><span data-stu-id="a370f-137">The annotations that were added to this event.</span></span> <span data-ttu-id="a370f-138">Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="a370f-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="a370f-139">Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >.</span><span class="sxs-lookup"><span data-stu-id="a370f-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="a370f-140">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a370f-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="a370f-141">Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="a370f-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="a370f-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="a370f-142">ProfileName</span></span>|<span data-ttu-id="a370f-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="a370f-143">xs:string</span></span>|<span data-ttu-id="a370f-144">Název nebo sledování profil, který způsobil v tomto případě se vygenerované</span><span class="sxs-lookup"><span data-stu-id="a370f-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="a370f-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="a370f-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="a370f-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="a370f-146">xs:string</span></span>|<span data-ttu-id="a370f-147">Id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a370f-147">The workflow definition id</span></span>|  
|<span data-ttu-id="a370f-148">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a370f-148">AppDomain</span></span>|<span data-ttu-id="a370f-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="a370f-149">xs:string</span></span>|<span data-ttu-id="a370f-150">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a370f-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
