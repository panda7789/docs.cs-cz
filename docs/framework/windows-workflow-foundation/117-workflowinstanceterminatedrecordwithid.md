---
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fd8ece3245b99a5d976058135492e8503dd1c8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a><span data-ttu-id="d22c0-102">117 - WorkflowInstanceTerminatedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="d22c0-102">117 - WorkflowInstanceTerminatedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="d22c0-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d22c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d22c0-104">ID</span><span class="sxs-lookup"><span data-stu-id="d22c0-104">ID</span></span>|<span data-ttu-id="d22c0-105">117</span><span class="sxs-lookup"><span data-stu-id="d22c0-105">117</span></span>|  
|<span data-ttu-id="d22c0-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d22c0-106">Keywords</span></span>|<span data-ttu-id="d22c0-107">HealthMonitoring WFTracking</span><span class="sxs-lookup"><span data-stu-id="d22c0-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="d22c0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d22c0-108">Level</span></span>|<span data-ttu-id="d22c0-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="d22c0-109">Error</span></span>|  
|<span data-ttu-id="d22c0-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d22c0-110">Channel</span></span>|<span data-ttu-id="d22c0-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="d22c0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d22c0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d22c0-112">Description</span></span>  
 <span data-ttu-id="d22c0-113">Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když WorkflowInstanceTerminatedRecord vysílá instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d22c0-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d22c0-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d22c0-114">Message</span></span>  
 <span data-ttu-id="d22c0-115">TrackRecord = WorkflowInstanceTerminatedRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, důvod = %5, poznámky = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="d22c0-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="d22c0-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d22c0-116">Details</span></span>  
  
|<span data-ttu-id="d22c0-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d22c0-117">Data Item Name</span></span>|<span data-ttu-id="d22c0-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="d22c0-118">Data Item Type</span></span>|<span data-ttu-id="d22c0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d22c0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d22c0-120">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="d22c0-120">InstanceId</span></span>|<span data-ttu-id="d22c0-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="d22c0-121">xs:GUID</span></span>|<span data-ttu-id="d22c0-122">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d22c0-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="d22c0-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="d22c0-123">RecordNumber</span></span>|<span data-ttu-id="d22c0-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="d22c0-124">xs:long</span></span>|<span data-ttu-id="d22c0-125">Pořadové číslo emitovaného záznamu</span><span class="sxs-lookup"><span data-stu-id="d22c0-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="d22c0-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="d22c0-126">EventTime</span></span>|<span data-ttu-id="d22c0-127">xs</span><span class="sxs-lookup"><span data-stu-id="d22c0-127">xs:dateTime</span></span>|<span data-ttu-id="d22c0-128">Čas v UTC při byl vygenerované události</span><span class="sxs-lookup"><span data-stu-id="d22c0-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="d22c0-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="d22c0-129">ActivityDefinitionId</span></span>|<span data-ttu-id="d22c0-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="d22c0-130">xs:string</span></span>|<span data-ttu-id="d22c0-131">Název kořenové aktivity v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="d22c0-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="d22c0-132">Stav</span><span class="sxs-lookup"><span data-stu-id="d22c0-132">State</span></span>|<span data-ttu-id="d22c0-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="d22c0-133">xs:string</span></span>|<span data-ttu-id="d22c0-134">Aktuální stav pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d22c0-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="d22c0-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d22c0-135">Annotations</span></span>|<span data-ttu-id="d22c0-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="d22c0-136">xs:string</span></span>|<span data-ttu-id="d22c0-137">Poznámky, které byly přidány k této události.</span><span class="sxs-lookup"><span data-stu-id="d22c0-137">The annotations that were added to this event.</span></span> <span data-ttu-id="d22c0-138">Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="d22c0-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="d22c0-139">Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >.</span><span class="sxs-lookup"><span data-stu-id="d22c0-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="d22c0-140">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="d22c0-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="d22c0-141">Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="d22c0-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="d22c0-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="d22c0-142">ProfileName</span></span>|<span data-ttu-id="d22c0-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="d22c0-143">xs:string</span></span>|<span data-ttu-id="d22c0-144">Název nebo sledování profil, který způsobil v tomto případě se vygenerované</span><span class="sxs-lookup"><span data-stu-id="d22c0-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="d22c0-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="d22c0-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="d22c0-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="d22c0-146">xs:string</span></span>|<span data-ttu-id="d22c0-147">Id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d22c0-147">The workflow definition id</span></span>|  
|<span data-ttu-id="d22c0-148">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d22c0-148">AppDomain</span></span>|<span data-ttu-id="d22c0-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="d22c0-149">xs:string</span></span>|<span data-ttu-id="d22c0-150">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d22c0-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
