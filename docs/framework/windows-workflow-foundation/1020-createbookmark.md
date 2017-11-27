---
title: 1020 - CreateBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d0584c6eeaf0e08e92ad94e01e1fca765616440f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1020---createbookmark"></a><span data-ttu-id="59534-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="59534-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="59534-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="59534-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59534-104">ID</span><span class="sxs-lookup"><span data-stu-id="59534-104">ID</span></span>|<span data-ttu-id="59534-105">1020</span><span class="sxs-lookup"><span data-stu-id="59534-105">1020</span></span>|  
|<span data-ttu-id="59534-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="59534-106">Keywords</span></span>|<span data-ttu-id="59534-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="59534-107">WFRuntime</span></span>|  
|<span data-ttu-id="59534-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="59534-108">Level</span></span>|<span data-ttu-id="59534-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="59534-109">Verbose</span></span>|  
|<span data-ttu-id="59534-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="59534-110">Channel</span></span>|<span data-ttu-id="59534-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="59534-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="59534-112">Popis</span><span class="sxs-lookup"><span data-stu-id="59534-112">Description</span></span>  
 <span data-ttu-id="59534-113">Označuje, že byla vytvořena záložku pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="59534-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="59534-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="59534-114">Message</span></span>  
 <span data-ttu-id="59534-115">Záložku byl vytvořen pro aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="59534-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="59534-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="59534-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="59534-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="59534-117">Details</span></span>  
  
|<span data-ttu-id="59534-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="59534-118">Data Item Name</span></span>|<span data-ttu-id="59534-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="59534-119">Data Item Type</span></span>|<span data-ttu-id="59534-120">Popis</span><span class="sxs-lookup"><span data-stu-id="59534-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="59534-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="59534-121">Activity</span></span>|<span data-ttu-id="59534-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="59534-122">xs:string</span></span>|<span data-ttu-id="59534-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="59534-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="59534-124">displayName</span><span class="sxs-lookup"><span data-stu-id="59534-124">DisplayName</span></span>|<span data-ttu-id="59534-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="59534-125">xs:string</span></span>|<span data-ttu-id="59534-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="59534-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="59534-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="59534-127">InstanceId</span></span>|<span data-ttu-id="59534-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="59534-128">xs:string</span></span>|<span data-ttu-id="59534-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="59534-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="59534-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="59534-130">BookmarkName</span></span>|<span data-ttu-id="59534-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="59534-131">xs:string</span></span>|<span data-ttu-id="59534-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="59534-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="59534-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="59534-133">BookmarkScope</span></span>|<span data-ttu-id="59534-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="59534-134">xs:string</span></span>|<span data-ttu-id="59534-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="59534-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="59534-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="59534-136">AppDomain</span></span>|<span data-ttu-id="59534-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="59534-137">xs:string</span></span>|<span data-ttu-id="59534-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="59534-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
