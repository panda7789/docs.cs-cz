---
title: 114 - WorkflowInstanceRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7535a37574f3f42a4de4eea8d1e1cdf67b2a995e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="114---workflowinstancerecordwithid"></a><span data-ttu-id="8ce72-102">114 - WorkflowInstanceRecordWithId</span><span class="sxs-lookup"><span data-stu-id="8ce72-102">114 - WorkflowInstanceRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="8ce72-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8ce72-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ce72-104">ID</span><span class="sxs-lookup"><span data-stu-id="8ce72-104">ID</span></span>|<span data-ttu-id="8ce72-105">114</span><span class="sxs-lookup"><span data-stu-id="8ce72-105">114</span></span>|  
|<span data-ttu-id="8ce72-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8ce72-106">Keywords</span></span>|<span data-ttu-id="8ce72-107">HealthMonitoring WFTracking</span><span class="sxs-lookup"><span data-stu-id="8ce72-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="8ce72-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8ce72-108">Level</span></span>|<span data-ttu-id="8ce72-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="8ce72-109">Information</span></span>|  
|<span data-ttu-id="8ce72-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8ce72-110">Channel</span></span>|<span data-ttu-id="8ce72-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="8ce72-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8ce72-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8ce72-112">Description</span></span>  
 <span data-ttu-id="8ce72-113">Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, pokud instance pracovního postupu vysílá WorkflowInstanceRecord stavů pracovního postupu: spuštění, byl obnoven, jako trvalé, nečinnosti, odstranit, byla dokončena, došlo ke zrušení, odpojeno, pozastavení.</span><span class="sxs-lookup"><span data-stu-id="8ce72-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8ce72-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8ce72-114">Message</span></span>  
 <span data-ttu-id="8ce72-115">TrackRecord = WorkflowInstanceRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stav = %5, poznámky = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="8ce72-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="8ce72-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8ce72-116">Details</span></span>  
  
|<span data-ttu-id="8ce72-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8ce72-117">Data Item Name</span></span>|<span data-ttu-id="8ce72-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8ce72-118">Data Item Type</span></span>|<span data-ttu-id="8ce72-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8ce72-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8ce72-120">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="8ce72-120">InstanceId</span></span>|<span data-ttu-id="8ce72-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="8ce72-121">xs:GUID</span></span>|<span data-ttu-id="8ce72-122">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8ce72-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="8ce72-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="8ce72-123">RecordNumber</span></span>|<span data-ttu-id="8ce72-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="8ce72-124">xs:long</span></span>|<span data-ttu-id="8ce72-125">Pořadové číslo emitovaného záznamu</span><span class="sxs-lookup"><span data-stu-id="8ce72-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="8ce72-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="8ce72-126">EventTime</span></span>|<span data-ttu-id="8ce72-127">xs</span><span class="sxs-lookup"><span data-stu-id="8ce72-127">xs:dateTime</span></span>|<span data-ttu-id="8ce72-128">Čas v UTC při byl vygenerované události</span><span class="sxs-lookup"><span data-stu-id="8ce72-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="8ce72-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="8ce72-129">ActivityDefinitionId</span></span>|<span data-ttu-id="8ce72-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ce72-130">xs:string</span></span>|<span data-ttu-id="8ce72-131">Název kořenové aktivity v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="8ce72-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="8ce72-132">Stav</span><span class="sxs-lookup"><span data-stu-id="8ce72-132">State</span></span>|<span data-ttu-id="8ce72-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ce72-133">xs:string</span></span>|<span data-ttu-id="8ce72-134">Aktuální stav pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8ce72-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="8ce72-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ce72-135">Annotations</span></span>|<span data-ttu-id="8ce72-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ce72-136">xs:string</span></span>|<span data-ttu-id="8ce72-137">Poznámky, které byly přidány k této události.</span><span class="sxs-lookup"><span data-stu-id="8ce72-137">The annotations that were added to this event.</span></span> <span data-ttu-id="8ce72-138">Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="8ce72-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="8ce72-139">Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >.</span><span class="sxs-lookup"><span data-stu-id="8ce72-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="8ce72-140">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="8ce72-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="8ce72-141">Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="8ce72-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="8ce72-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="8ce72-142">ProfileName</span></span>|<span data-ttu-id="8ce72-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ce72-143">xs:string</span></span>|<span data-ttu-id="8ce72-144">Název nebo sledování profil, který způsobil v tomto případě se vygenerované</span><span class="sxs-lookup"><span data-stu-id="8ce72-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="8ce72-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8ce72-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="8ce72-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ce72-146">xs:string</span></span>|<span data-ttu-id="8ce72-147">Id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8ce72-147">The workflow definition id</span></span>|  
|<span data-ttu-id="8ce72-148">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8ce72-148">AppDomain</span></span>|<span data-ttu-id="8ce72-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ce72-149">xs:string</span></span>|<span data-ttu-id="8ce72-150">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8ce72-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
