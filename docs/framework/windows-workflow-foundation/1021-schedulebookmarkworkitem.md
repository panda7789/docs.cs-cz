---
title: 1021 – ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924420"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="acfbc-102">1021 – ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="acfbc-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="acfbc-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="acfbc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="acfbc-104">ID</span><span class="sxs-lookup"><span data-stu-id="acfbc-104">ID</span></span>|<span data-ttu-id="acfbc-105">1021</span><span class="sxs-lookup"><span data-stu-id="acfbc-105">1021</span></span>|  
|<span data-ttu-id="acfbc-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="acfbc-106">Keywords</span></span>|<span data-ttu-id="acfbc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="acfbc-107">WFRuntime</span></span>|  
|<span data-ttu-id="acfbc-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="acfbc-108">Level</span></span>|<span data-ttu-id="acfbc-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="acfbc-109">Verbose</span></span>|  
|<span data-ttu-id="acfbc-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="acfbc-110">Channel</span></span>|<span data-ttu-id="acfbc-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="acfbc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="acfbc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="acfbc-112">Description</span></span>  
 <span data-ttu-id="acfbc-113">Označuje, že položka BookmarkWorkItem byla plánována.</span><span class="sxs-lookup"><span data-stu-id="acfbc-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="acfbc-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="acfbc-114">Message</span></span>  
 <span data-ttu-id="acfbc-115">Položka BookmarkWorkItem byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="acfbc-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="acfbc-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="acfbc-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="acfbc-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="acfbc-117">Details</span></span>  
  
|<span data-ttu-id="acfbc-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="acfbc-118">Data Item Name</span></span>|<span data-ttu-id="acfbc-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="acfbc-119">Data Item Type</span></span>|<span data-ttu-id="acfbc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="acfbc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="acfbc-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="acfbc-121">Activity</span></span>|<span data-ttu-id="acfbc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="acfbc-122">xs:string</span></span>|<span data-ttu-id="acfbc-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="acfbc-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="acfbc-124">displayName</span><span class="sxs-lookup"><span data-stu-id="acfbc-124">DisplayName</span></span>|<span data-ttu-id="acfbc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="acfbc-125">xs:string</span></span>|<span data-ttu-id="acfbc-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="acfbc-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="acfbc-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="acfbc-127">InstanceId</span></span>|<span data-ttu-id="acfbc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="acfbc-128">xs:string</span></span>|<span data-ttu-id="acfbc-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="acfbc-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="acfbc-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="acfbc-130">BookmarkName</span></span>|<span data-ttu-id="acfbc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="acfbc-131">xs:string</span></span>|<span data-ttu-id="acfbc-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="acfbc-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="acfbc-133">Rozsah BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="acfbc-133">BookmarkScope</span></span>|<span data-ttu-id="acfbc-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="acfbc-134">xs:string</span></span>|<span data-ttu-id="acfbc-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="acfbc-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="acfbc-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="acfbc-136">AppDomain</span></span>|<span data-ttu-id="acfbc-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="acfbc-137">xs:string</span></span>|<span data-ttu-id="acfbc-138">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="acfbc-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
