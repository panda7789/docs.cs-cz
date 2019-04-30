---
title: 1022 – StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924719"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="1e11f-102">1022 – StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="1e11f-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1e11f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1e11f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e11f-104">ID</span><span class="sxs-lookup"><span data-stu-id="1e11f-104">ID</span></span>|<span data-ttu-id="1e11f-105">1022</span><span class="sxs-lookup"><span data-stu-id="1e11f-105">1022</span></span>|  
|<span data-ttu-id="1e11f-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1e11f-106">Keywords</span></span>|<span data-ttu-id="1e11f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1e11f-107">WFRuntime</span></span>|  
|<span data-ttu-id="1e11f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1e11f-108">Level</span></span>|<span data-ttu-id="1e11f-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1e11f-109">Verbose</span></span>|  
|<span data-ttu-id="1e11f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1e11f-110">Channel</span></span>|<span data-ttu-id="1e11f-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="1e11f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e11f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1e11f-112">Description</span></span>  
 <span data-ttu-id="1e11f-113">Označuje, že položka BookmarkWorkItem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="1e11f-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e11f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1e11f-114">Message</span></span>  
 <span data-ttu-id="1e11f-115">Spouštění provedení položky BookmarkWorkItem pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="1e11f-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="1e11f-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="1e11f-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e11f-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1e11f-117">Details</span></span>  
  
|<span data-ttu-id="1e11f-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1e11f-118">Data Item Name</span></span>|<span data-ttu-id="1e11f-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="1e11f-119">Data Item Type</span></span>|<span data-ttu-id="1e11f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1e11f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e11f-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="1e11f-121">Activity</span></span>|<span data-ttu-id="1e11f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e11f-122">xs:string</span></span>|<span data-ttu-id="1e11f-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e11f-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="1e11f-124">displayName</span><span class="sxs-lookup"><span data-stu-id="1e11f-124">DisplayName</span></span>|<span data-ttu-id="1e11f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e11f-125">xs:string</span></span>|<span data-ttu-id="1e11f-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e11f-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="1e11f-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1e11f-127">InstanceId</span></span>|<span data-ttu-id="1e11f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e11f-128">xs:string</span></span>|<span data-ttu-id="1e11f-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e11f-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1e11f-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="1e11f-130">BookmarkName</span></span>|<span data-ttu-id="1e11f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e11f-131">xs:string</span></span>|<span data-ttu-id="1e11f-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="1e11f-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="1e11f-133">Rozsah BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="1e11f-133">BookmarkScope</span></span>|<span data-ttu-id="1e11f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e11f-134">xs:string</span></span>|<span data-ttu-id="1e11f-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="1e11f-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="1e11f-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e11f-136">AppDomain</span></span>|<span data-ttu-id="1e11f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e11f-137">xs:string</span></span>|<span data-ttu-id="1e11f-138">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1e11f-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
