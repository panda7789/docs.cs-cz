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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3dc30100cb134740f51e6b2b38c00b2054d2ab0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="9d47d-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="9d47d-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9d47d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9d47d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d47d-104">ID</span><span class="sxs-lookup"><span data-stu-id="9d47d-104">ID</span></span>|<span data-ttu-id="9d47d-105">1021</span><span class="sxs-lookup"><span data-stu-id="9d47d-105">1021</span></span>|  
|<span data-ttu-id="9d47d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9d47d-106">Keywords</span></span>|<span data-ttu-id="9d47d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9d47d-107">WFRuntime</span></span>|  
|<span data-ttu-id="9d47d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9d47d-108">Level</span></span>|<span data-ttu-id="9d47d-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="9d47d-109">Verbose</span></span>|  
|<span data-ttu-id="9d47d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9d47d-110">Channel</span></span>|<span data-ttu-id="9d47d-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9d47d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d47d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9d47d-112">Description</span></span>  
 <span data-ttu-id="9d47d-113">Označuje, že bylo naplánováno BookmarkWorkItem.</span><span class="sxs-lookup"><span data-stu-id="9d47d-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d47d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9d47d-114">Message</span></span>  
 <span data-ttu-id="9d47d-115">Bylo naplánováno BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9d47d-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="9d47d-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="9d47d-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d47d-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9d47d-117">Details</span></span>  
  
|<span data-ttu-id="9d47d-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9d47d-118">Data Item Name</span></span>|<span data-ttu-id="9d47d-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9d47d-119">Data Item Type</span></span>|<span data-ttu-id="9d47d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9d47d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d47d-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="9d47d-121">Activity</span></span>|<span data-ttu-id="9d47d-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="9d47d-122">xs:string</span></span>|<span data-ttu-id="9d47d-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="9d47d-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="9d47d-124">displayName</span><span class="sxs-lookup"><span data-stu-id="9d47d-124">DisplayName</span></span>|<span data-ttu-id="9d47d-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="9d47d-125">xs:string</span></span>|<span data-ttu-id="9d47d-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="9d47d-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="9d47d-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="9d47d-127">InstanceId</span></span>|<span data-ttu-id="9d47d-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="9d47d-128">xs:string</span></span>|<span data-ttu-id="9d47d-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="9d47d-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9d47d-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="9d47d-130">BookmarkName</span></span>|<span data-ttu-id="9d47d-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="9d47d-131">xs:string</span></span>|<span data-ttu-id="9d47d-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="9d47d-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="9d47d-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="9d47d-133">BookmarkScope</span></span>|<span data-ttu-id="9d47d-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="9d47d-134">xs:string</span></span>|<span data-ttu-id="9d47d-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="9d47d-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="9d47d-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9d47d-136">AppDomain</span></span>|<span data-ttu-id="9d47d-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="9d47d-137">xs:string</span></span>|<span data-ttu-id="9d47d-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9d47d-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
