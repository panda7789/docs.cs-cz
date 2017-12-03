---
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e58156d5865f8f9c2cf6c76285458cd55e805db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="115---workflowinstanceabortedrecordwithid"></a><span data-ttu-id="5bd47-102">115 - WorkflowInstanceAbortedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="5bd47-102">115 - WorkflowInstanceAbortedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="5bd47-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5bd47-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bd47-104">ID</span><span class="sxs-lookup"><span data-stu-id="5bd47-104">ID</span></span>|<span data-ttu-id="5bd47-105">115</span><span class="sxs-lookup"><span data-stu-id="5bd47-105">115</span></span>|  
|<span data-ttu-id="5bd47-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5bd47-106">Keywords</span></span>|<span data-ttu-id="5bd47-107">HealthMonitoring WFTracking</span><span class="sxs-lookup"><span data-stu-id="5bd47-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="5bd47-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5bd47-108">Level</span></span>|<span data-ttu-id="5bd47-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="5bd47-109">Warning</span></span>|  
|<span data-ttu-id="5bd47-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5bd47-110">Channel</span></span>|<span data-ttu-id="5bd47-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="5bd47-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5bd47-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5bd47-112">Description</span></span>  
 <span data-ttu-id="5bd47-113">Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když WorkflowInstanceAbortedRecord vysílá instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5bd47-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5bd47-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5bd47-114">Message</span></span>  
 <span data-ttu-id="5bd47-115">TrackRecord = WorkflowInstanceAbortedRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, důvod = %5, poznámky = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="5bd47-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="5bd47-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5bd47-116">Details</span></span>  
  
|<span data-ttu-id="5bd47-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5bd47-117">Data Item Name</span></span>|<span data-ttu-id="5bd47-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5bd47-118">Data Item Type</span></span>|<span data-ttu-id="5bd47-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5bd47-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5bd47-120">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="5bd47-120">InstanceId</span></span>|<span data-ttu-id="5bd47-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="5bd47-121">xs:GUID</span></span>|<span data-ttu-id="5bd47-122">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5bd47-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="5bd47-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="5bd47-123">RecordNumber</span></span>|<span data-ttu-id="5bd47-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="5bd47-124">xs:long</span></span>|<span data-ttu-id="5bd47-125">Pořadové číslo emitovaného záznamu</span><span class="sxs-lookup"><span data-stu-id="5bd47-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="5bd47-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="5bd47-126">EventTime</span></span>|<span data-ttu-id="5bd47-127">xs</span><span class="sxs-lookup"><span data-stu-id="5bd47-127">xs:dateTime</span></span>|<span data-ttu-id="5bd47-128">Čas v UTC při byl vygenerované události</span><span class="sxs-lookup"><span data-stu-id="5bd47-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="5bd47-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="5bd47-129">ActivityDefinitionId</span></span>|<span data-ttu-id="5bd47-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="5bd47-130">xs:string</span></span>|<span data-ttu-id="5bd47-131">Název kořenové aktivity v pracovním postupu</span><span class="sxs-lookup"><span data-stu-id="5bd47-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="5bd47-132">Stav</span><span class="sxs-lookup"><span data-stu-id="5bd47-132">State</span></span>|<span data-ttu-id="5bd47-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="5bd47-133">xs:string</span></span>|<span data-ttu-id="5bd47-134">Aktuální stav pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5bd47-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="5bd47-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bd47-135">Annotations</span></span>|<span data-ttu-id="5bd47-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="5bd47-136">xs:string</span></span>|<span data-ttu-id="5bd47-137">Poznámky, které byly přidány k této události.</span><span class="sxs-lookup"><span data-stu-id="5bd47-137">The annotations that were added to this event.</span></span> <span data-ttu-id="5bd47-138">Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="5bd47-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="5bd47-139">Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >.</span><span class="sxs-lookup"><span data-stu-id="5bd47-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="5bd47-140">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd47-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="5bd47-141">Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.</span><span class="sxs-lookup"><span data-stu-id="5bd47-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="5bd47-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="5bd47-142">ProfileName</span></span>|<span data-ttu-id="5bd47-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="5bd47-143">xs:string</span></span>|<span data-ttu-id="5bd47-144">Název nebo sledování profil, který způsobil v tomto případě se vygenerované</span><span class="sxs-lookup"><span data-stu-id="5bd47-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="5bd47-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="5bd47-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="5bd47-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="5bd47-146">xs:string</span></span>|<span data-ttu-id="5bd47-147">Id definice pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5bd47-147">The workflow definition id</span></span>|  
|<span data-ttu-id="5bd47-148">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5bd47-148">AppDomain</span></span>|<span data-ttu-id="5bd47-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="5bd47-149">xs:string</span></span>|<span data-ttu-id="5bd47-150">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5bd47-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
