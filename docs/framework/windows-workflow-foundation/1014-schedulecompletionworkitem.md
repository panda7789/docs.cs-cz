---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="e47bf-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="e47bf-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e47bf-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e47bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e47bf-104">ID</span><span class="sxs-lookup"><span data-stu-id="e47bf-104">ID</span></span>|<span data-ttu-id="e47bf-105">1014</span><span class="sxs-lookup"><span data-stu-id="e47bf-105">1014</span></span>|  
|<span data-ttu-id="e47bf-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e47bf-106">Keywords</span></span>|<span data-ttu-id="e47bf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e47bf-107">WFRuntime</span></span>|  
|<span data-ttu-id="e47bf-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e47bf-108">Level</span></span>|<span data-ttu-id="e47bf-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="e47bf-109">Verbose</span></span>|  
|<span data-ttu-id="e47bf-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e47bf-110">Channel</span></span>|<span data-ttu-id="e47bf-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e47bf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e47bf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e47bf-112">Description</span></span>  
 <span data-ttu-id="e47bf-113">Označuje, že bylo naplánováno CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="e47bf-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e47bf-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e47bf-114">Message</span></span>  
 <span data-ttu-id="e47bf-115">Bylo naplánováno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e47bf-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e47bf-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e47bf-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e47bf-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e47bf-117">Details</span></span>  
  
|<span data-ttu-id="e47bf-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e47bf-118">Data Item Name</span></span>|<span data-ttu-id="e47bf-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e47bf-119">Data Item Type</span></span>|<span data-ttu-id="e47bf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e47bf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e47bf-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="e47bf-121">ParentActivity</span></span>|<span data-ttu-id="e47bf-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-122">xs:string</span></span>|<span data-ttu-id="e47bf-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e47bf-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="e47bf-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="e47bf-124">ParentDisplayName</span></span>|<span data-ttu-id="e47bf-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-125">xs:string</span></span>|<span data-ttu-id="e47bf-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e47bf-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="e47bf-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="e47bf-127">ParentInstanceId</span></span>|<span data-ttu-id="e47bf-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-128">xs:string</span></span>|<span data-ttu-id="e47bf-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e47bf-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="e47bf-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="e47bf-130">CompletedActivity</span></span>|<span data-ttu-id="e47bf-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-131">xs:string</span></span>|<span data-ttu-id="e47bf-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e47bf-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="e47bf-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e47bf-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="e47bf-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-134">xs:string</span></span>|<span data-ttu-id="e47bf-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e47bf-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="e47bf-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e47bf-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="e47bf-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-137">xs:string</span></span>|<span data-ttu-id="e47bf-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e47bf-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="e47bf-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e47bf-139">AppDomain</span></span>|<span data-ttu-id="e47bf-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="e47bf-140">xs:string</span></span>|<span data-ttu-id="e47bf-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e47bf-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
