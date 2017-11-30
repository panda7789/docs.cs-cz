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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57eab386e8d0486caa98a6e2f3d2f72e9e89fab7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="114---workflowinstancerecordwithid"></a><span data-ttu-id="6fa85-102">114 - WorkflowInstanceRecordWithId</span><span class="sxs-lookup"><span data-stu-id="6fa85-102">114 - WorkflowInstanceRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="6fa85-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6fa85-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6fa85-104">ID</span><span class="sxs-lookup"><span data-stu-id="6fa85-104">ID</span></span>|<span data-ttu-id="6fa85-105">114</span><span class="sxs-lookup"><span data-stu-id="6fa85-105">114</span></span>|  
|<span data-ttu-id="6fa85-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6fa85-106">Keywords</span></span>|<span data-ttu-id="6fa85-107">HealthMonitoring WFTracking</span><span class="sxs-lookup"><span data-stu-id="6fa85-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="6fa85-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6fa85-108">Level</span></span>|<span data-ttu-id="6fa85-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="6fa85-109">Information</span></span>|  
|<span data-ttu-id="6fa85-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6fa85-110">Channel</span></span>|<span data-ttu-id="6fa85-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="6fa85-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6fa85-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6fa85-112">Description</span></span>  
 <span data-ttu-id="6fa85-113">Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, pokud instance pracovního postupu vysílá WorkflowInstanceRecord stavů pracovního postupu: spuštění, byl obnoven, jako trvalé, nečinnosti, odstranit, byla dokončena, došlo ke zrušení, odpojeno, pozastavení.</span><span class="sxs-lookup"><span data-stu-id="6fa85-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6fa85-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6fa85-114">Message</span></span>  
 <span data-ttu-id="6fa85-115">TrackRecord = WorkflowInstanceRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stav = %5, poznámky = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="6fa85-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="6fa85-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6fa85-116">Details</span></span>  
  
|<span data-ttu-id="6fa85-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6fa85-117">Data Item Name</span></span>|<span data-ttu-id="6fa85-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="6fa85-118">Data Item Type</span></span>|<span data-ttu-id="6fa85-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6fa85-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6fa85-120">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="6fa85-120">InstanceId</span></span>|<span data-ttu-id="6fa85-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="6fa85-121">xs:GUID</span></span>|<span data-ttu-id="6fa85-122">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6fa85-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="6fa85-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="6fa85-123">RecordNumber</span></span>|<span data-ttu-id="6fa85-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="6fa85-124">xs:long</span></span>|<span data-ttu-id="6fa85-125">Pořadové číslo emitovaného záznamu</span><span class="sxs-lookup"><span data-stu-id="6fa85-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="6fa85-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="6fa85-126">EventTime</span></span>|<span data-ttu-id="6fa85-127">xs</span><span class="sxs-lookup"><span data-stu-id="6fa85-127">xs:dateTime</span></span>|<span data-ttu-id="6fa85-128">Čas v UTC při byl vygenerované události</span><span class="sxs-lookup"><span data-stu-id="6fa85-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="6fa85-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="6fa85-129">ActivityDefinitionId</span></span>|<span data-ttu-id="6fa85-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fa85-130">xs:string</span></span>|<span data-ttu-id="6fa85-131">Název kořenové aktivity v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="6fa85-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="6fa85-132">Stav</span><span class="sxs-lookup"><span data-stu-id="6fa85-132">State</span></span>|<span data-ttu-id="6fa85-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fa85-133">xs:string</span></span>|<span data-ttu-id="6fa85-134">Aktuální stav pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6fa85-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="6fa85-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fa85-135">Annotations</span></span>|<span data-ttu-id="6fa85-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fa85-136">xs:string</span></span>|<span data-ttu-id="6fa85-137">Poznámky, které byly přidány k této události.</span><span class="sxs-lookup"><span data-stu-id="6fa85-137">The annotations that were added to this event.</span></span> <span data-ttu-id="6fa85-138">Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="6fa85-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="6fa85-139">Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >.</span><span class="sxs-lookup"><span data-stu-id="6fa85-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="6fa85-140">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="6fa85-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="6fa85-141">Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="6fa85-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="6fa85-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="6fa85-142">ProfileName</span></span>|<span data-ttu-id="6fa85-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fa85-143">xs:string</span></span>|<span data-ttu-id="6fa85-144">Název nebo sledování profil, který způsobil v tomto případě se vygenerované</span><span class="sxs-lookup"><span data-stu-id="6fa85-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="6fa85-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="6fa85-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="6fa85-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fa85-146">xs:string</span></span>|<span data-ttu-id="6fa85-147">Id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6fa85-147">The workflow definition id</span></span>|  
|<span data-ttu-id="6fa85-148">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6fa85-148">AppDomain</span></span>|<span data-ttu-id="6fa85-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="6fa85-149">xs:string</span></span>|<span data-ttu-id="6fa85-150">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6fa85-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
