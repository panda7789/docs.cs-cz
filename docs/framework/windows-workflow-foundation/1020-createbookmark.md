---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510456"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="7bb70-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="7bb70-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="7bb70-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7bb70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7bb70-104">ID</span><span class="sxs-lookup"><span data-stu-id="7bb70-104">ID</span></span>|<span data-ttu-id="7bb70-105">1020</span><span class="sxs-lookup"><span data-stu-id="7bb70-105">1020</span></span>|  
|<span data-ttu-id="7bb70-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7bb70-106">Keywords</span></span>|<span data-ttu-id="7bb70-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7bb70-107">WFRuntime</span></span>|  
|<span data-ttu-id="7bb70-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="7bb70-108">Level</span></span>|<span data-ttu-id="7bb70-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="7bb70-109">Verbose</span></span>|  
|<span data-ttu-id="7bb70-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="7bb70-110">Channel</span></span>|<span data-ttu-id="7bb70-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="7bb70-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7bb70-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7bb70-112">Description</span></span>  
 <span data-ttu-id="7bb70-113">Označuje, že byla vytvořena záložku pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="7bb70-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7bb70-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="7bb70-114">Message</span></span>  
 <span data-ttu-id="7bb70-115">Záložku byl vytvořen pro aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="7bb70-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="7bb70-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="7bb70-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7bb70-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7bb70-117">Details</span></span>  
  
|<span data-ttu-id="7bb70-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="7bb70-118">Data Item Name</span></span>|<span data-ttu-id="7bb70-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="7bb70-119">Data Item Type</span></span>|<span data-ttu-id="7bb70-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7bb70-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7bb70-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="7bb70-121">Activity</span></span>|<span data-ttu-id="7bb70-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="7bb70-122">xs:string</span></span>|<span data-ttu-id="7bb70-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7bb70-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="7bb70-124">displayName</span><span class="sxs-lookup"><span data-stu-id="7bb70-124">DisplayName</span></span>|<span data-ttu-id="7bb70-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="7bb70-125">xs:string</span></span>|<span data-ttu-id="7bb70-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="7bb70-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="7bb70-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="7bb70-127">InstanceId</span></span>|<span data-ttu-id="7bb70-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="7bb70-128">xs:string</span></span>|<span data-ttu-id="7bb70-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="7bb70-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7bb70-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="7bb70-130">BookmarkName</span></span>|<span data-ttu-id="7bb70-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="7bb70-131">xs:string</span></span>|<span data-ttu-id="7bb70-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="7bb70-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="7bb70-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="7bb70-133">BookmarkScope</span></span>|<span data-ttu-id="7bb70-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="7bb70-134">xs:string</span></span>|<span data-ttu-id="7bb70-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="7bb70-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="7bb70-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="7bb70-136">AppDomain</span></span>|<span data-ttu-id="7bb70-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="7bb70-137">xs:string</span></span>|<span data-ttu-id="7bb70-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7bb70-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
