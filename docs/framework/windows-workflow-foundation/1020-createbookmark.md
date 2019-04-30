---
title: 1020 – CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924745"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="836cc-102">1020 – CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="836cc-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="836cc-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="836cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="836cc-104">ID</span><span class="sxs-lookup"><span data-stu-id="836cc-104">ID</span></span>|<span data-ttu-id="836cc-105">1020</span><span class="sxs-lookup"><span data-stu-id="836cc-105">1020</span></span>|  
|<span data-ttu-id="836cc-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="836cc-106">Keywords</span></span>|<span data-ttu-id="836cc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="836cc-107">WFRuntime</span></span>|  
|<span data-ttu-id="836cc-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="836cc-108">Level</span></span>|<span data-ttu-id="836cc-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="836cc-109">Verbose</span></span>|  
|<span data-ttu-id="836cc-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="836cc-110">Channel</span></span>|<span data-ttu-id="836cc-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="836cc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="836cc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="836cc-112">Description</span></span>  
 <span data-ttu-id="836cc-113">Označuje, že byla záložka vytvořena pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="836cc-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="836cc-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="836cc-114">Message</span></span>  
 <span data-ttu-id="836cc-115">Záložka byla vytvořena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="836cc-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="836cc-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="836cc-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="836cc-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="836cc-117">Details</span></span>  
  
|<span data-ttu-id="836cc-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="836cc-118">Data Item Name</span></span>|<span data-ttu-id="836cc-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="836cc-119">Data Item Type</span></span>|<span data-ttu-id="836cc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="836cc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="836cc-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="836cc-121">Activity</span></span>|<span data-ttu-id="836cc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="836cc-122">xs:string</span></span>|<span data-ttu-id="836cc-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="836cc-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="836cc-124">displayName</span><span class="sxs-lookup"><span data-stu-id="836cc-124">DisplayName</span></span>|<span data-ttu-id="836cc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="836cc-125">xs:string</span></span>|<span data-ttu-id="836cc-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="836cc-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="836cc-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="836cc-127">InstanceId</span></span>|<span data-ttu-id="836cc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="836cc-128">xs:string</span></span>|<span data-ttu-id="836cc-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="836cc-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="836cc-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="836cc-130">BookmarkName</span></span>|<span data-ttu-id="836cc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="836cc-131">xs:string</span></span>|<span data-ttu-id="836cc-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="836cc-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="836cc-133">Rozsah BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="836cc-133">BookmarkScope</span></span>|<span data-ttu-id="836cc-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="836cc-134">xs:string</span></span>|<span data-ttu-id="836cc-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="836cc-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="836cc-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="836cc-136">AppDomain</span></span>|<span data-ttu-id="836cc-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="836cc-137">xs:string</span></span>|<span data-ttu-id="836cc-138">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="836cc-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
