---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdb6af10c45e7a93e9a68e6150e5d239002cce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="75bd8-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="75bd8-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="75bd8-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="75bd8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75bd8-104">ID</span><span class="sxs-lookup"><span data-stu-id="75bd8-104">ID</span></span>|<span data-ttu-id="75bd8-105">1022</span><span class="sxs-lookup"><span data-stu-id="75bd8-105">1022</span></span>|  
|<span data-ttu-id="75bd8-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="75bd8-106">Keywords</span></span>|<span data-ttu-id="75bd8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="75bd8-107">WFRuntime</span></span>|  
|<span data-ttu-id="75bd8-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="75bd8-108">Level</span></span>|<span data-ttu-id="75bd8-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="75bd8-109">Verbose</span></span>|  
|<span data-ttu-id="75bd8-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="75bd8-110">Channel</span></span>|<span data-ttu-id="75bd8-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="75bd8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="75bd8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="75bd8-112">Description</span></span>  
 <span data-ttu-id="75bd8-113">Označuje, že že bookmarkworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="75bd8-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="75bd8-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="75bd8-114">Message</span></span>  
 <span data-ttu-id="75bd8-115">Spuštění provádění BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="75bd8-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="75bd8-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="75bd8-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="75bd8-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="75bd8-117">Details</span></span>  
  
|<span data-ttu-id="75bd8-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="75bd8-118">Data Item Name</span></span>|<span data-ttu-id="75bd8-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="75bd8-119">Data Item Type</span></span>|<span data-ttu-id="75bd8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="75bd8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="75bd8-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="75bd8-121">Activity</span></span>|<span data-ttu-id="75bd8-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd8-122">xs:string</span></span>|<span data-ttu-id="75bd8-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="75bd8-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="75bd8-124">displayName</span><span class="sxs-lookup"><span data-stu-id="75bd8-124">DisplayName</span></span>|<span data-ttu-id="75bd8-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd8-125">xs:string</span></span>|<span data-ttu-id="75bd8-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="75bd8-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="75bd8-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="75bd8-127">InstanceId</span></span>|<span data-ttu-id="75bd8-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd8-128">xs:string</span></span>|<span data-ttu-id="75bd8-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="75bd8-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="75bd8-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="75bd8-130">BookmarkName</span></span>|<span data-ttu-id="75bd8-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd8-131">xs:string</span></span>|<span data-ttu-id="75bd8-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="75bd8-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="75bd8-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="75bd8-133">BookmarkScope</span></span>|<span data-ttu-id="75bd8-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd8-134">xs:string</span></span>|<span data-ttu-id="75bd8-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="75bd8-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="75bd8-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="75bd8-136">AppDomain</span></span>|<span data-ttu-id="75bd8-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd8-137">xs:string</span></span>|<span data-ttu-id="75bd8-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="75bd8-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
