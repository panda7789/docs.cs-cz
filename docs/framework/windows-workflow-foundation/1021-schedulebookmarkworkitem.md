---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509753"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="17478-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="17478-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="17478-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="17478-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17478-104">ID</span><span class="sxs-lookup"><span data-stu-id="17478-104">ID</span></span>|<span data-ttu-id="17478-105">1021</span><span class="sxs-lookup"><span data-stu-id="17478-105">1021</span></span>|  
|<span data-ttu-id="17478-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="17478-106">Keywords</span></span>|<span data-ttu-id="17478-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="17478-107">WFRuntime</span></span>|  
|<span data-ttu-id="17478-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="17478-108">Level</span></span>|<span data-ttu-id="17478-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="17478-109">Verbose</span></span>|  
|<span data-ttu-id="17478-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="17478-110">Channel</span></span>|<span data-ttu-id="17478-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="17478-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17478-112">Popis</span><span class="sxs-lookup"><span data-stu-id="17478-112">Description</span></span>  
 <span data-ttu-id="17478-113">Označuje, že bylo naplánováno BookmarkWorkItem.</span><span class="sxs-lookup"><span data-stu-id="17478-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17478-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="17478-114">Message</span></span>  
 <span data-ttu-id="17478-115">Bylo naplánováno BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="17478-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="17478-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="17478-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17478-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="17478-117">Details</span></span>  
  
|<span data-ttu-id="17478-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="17478-118">Data Item Name</span></span>|<span data-ttu-id="17478-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="17478-119">Data Item Type</span></span>|<span data-ttu-id="17478-120">Popis</span><span class="sxs-lookup"><span data-stu-id="17478-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17478-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="17478-121">Activity</span></span>|<span data-ttu-id="17478-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="17478-122">xs:string</span></span>|<span data-ttu-id="17478-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="17478-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="17478-124">displayName</span><span class="sxs-lookup"><span data-stu-id="17478-124">DisplayName</span></span>|<span data-ttu-id="17478-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="17478-125">xs:string</span></span>|<span data-ttu-id="17478-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="17478-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="17478-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="17478-127">InstanceId</span></span>|<span data-ttu-id="17478-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="17478-128">xs:string</span></span>|<span data-ttu-id="17478-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="17478-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="17478-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="17478-130">BookmarkName</span></span>|<span data-ttu-id="17478-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="17478-131">xs:string</span></span>|<span data-ttu-id="17478-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="17478-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="17478-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="17478-133">BookmarkScope</span></span>|<span data-ttu-id="17478-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="17478-134">xs:string</span></span>|<span data-ttu-id="17478-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="17478-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="17478-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="17478-136">AppDomain</span></span>|<span data-ttu-id="17478-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="17478-137">xs:string</span></span>|<span data-ttu-id="17478-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="17478-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
