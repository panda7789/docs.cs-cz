---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61c67792f807907f58480f3bfa3d192b811766b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="0b74f-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="0b74f-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0b74f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0b74f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b74f-104">ID</span><span class="sxs-lookup"><span data-stu-id="0b74f-104">ID</span></span>|<span data-ttu-id="0b74f-105">1021</span><span class="sxs-lookup"><span data-stu-id="0b74f-105">1021</span></span>|  
|<span data-ttu-id="0b74f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0b74f-106">Keywords</span></span>|<span data-ttu-id="0b74f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0b74f-107">WFRuntime</span></span>|  
|<span data-ttu-id="0b74f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0b74f-108">Level</span></span>|<span data-ttu-id="0b74f-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="0b74f-109">Verbose</span></span>|  
|<span data-ttu-id="0b74f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0b74f-110">Channel</span></span>|<span data-ttu-id="0b74f-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="0b74f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0b74f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0b74f-112">Description</span></span>  
 <span data-ttu-id="0b74f-113">Označuje, že bylo naplánováno BookmarkWorkItem.</span><span class="sxs-lookup"><span data-stu-id="0b74f-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0b74f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0b74f-114">Message</span></span>  
 <span data-ttu-id="0b74f-115">Bylo naplánováno BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="0b74f-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0b74f-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="0b74f-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0b74f-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0b74f-117">Details</span></span>  
  
|<span data-ttu-id="0b74f-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0b74f-118">Data Item Name</span></span>|<span data-ttu-id="0b74f-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="0b74f-119">Data Item Type</span></span>|<span data-ttu-id="0b74f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0b74f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0b74f-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="0b74f-121">Activity</span></span>|<span data-ttu-id="0b74f-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="0b74f-122">xs:string</span></span>|<span data-ttu-id="0b74f-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="0b74f-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="0b74f-124">displayName</span><span class="sxs-lookup"><span data-stu-id="0b74f-124">DisplayName</span></span>|<span data-ttu-id="0b74f-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="0b74f-125">xs:string</span></span>|<span data-ttu-id="0b74f-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="0b74f-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="0b74f-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="0b74f-127">InstanceId</span></span>|<span data-ttu-id="0b74f-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="0b74f-128">xs:string</span></span>|<span data-ttu-id="0b74f-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="0b74f-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0b74f-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="0b74f-130">BookmarkName</span></span>|<span data-ttu-id="0b74f-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="0b74f-131">xs:string</span></span>|<span data-ttu-id="0b74f-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="0b74f-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="0b74f-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="0b74f-133">BookmarkScope</span></span>|<span data-ttu-id="0b74f-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="0b74f-134">xs:string</span></span>|<span data-ttu-id="0b74f-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="0b74f-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="0b74f-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="0b74f-136">AppDomain</span></span>|<span data-ttu-id="0b74f-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="0b74f-137">xs:string</span></span>|<span data-ttu-id="0b74f-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0b74f-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
