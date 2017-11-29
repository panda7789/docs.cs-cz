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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aaabbdca455d31d22b232ae2b08edef0687ac30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="03dba-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="03dba-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="03dba-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="03dba-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03dba-104">ID</span><span class="sxs-lookup"><span data-stu-id="03dba-104">ID</span></span>|<span data-ttu-id="03dba-105">1022</span><span class="sxs-lookup"><span data-stu-id="03dba-105">1022</span></span>|  
|<span data-ttu-id="03dba-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="03dba-106">Keywords</span></span>|<span data-ttu-id="03dba-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="03dba-107">WFRuntime</span></span>|  
|<span data-ttu-id="03dba-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="03dba-108">Level</span></span>|<span data-ttu-id="03dba-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="03dba-109">Verbose</span></span>|  
|<span data-ttu-id="03dba-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="03dba-110">Channel</span></span>|<span data-ttu-id="03dba-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="03dba-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03dba-112">Popis</span><span class="sxs-lookup"><span data-stu-id="03dba-112">Description</span></span>  
 <span data-ttu-id="03dba-113">Označuje, že že bookmarkworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="03dba-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03dba-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="03dba-114">Message</span></span>  
 <span data-ttu-id="03dba-115">Spuštění provádění BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="03dba-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="03dba-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="03dba-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03dba-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="03dba-117">Details</span></span>  
  
|<span data-ttu-id="03dba-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="03dba-118">Data Item Name</span></span>|<span data-ttu-id="03dba-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="03dba-119">Data Item Type</span></span>|<span data-ttu-id="03dba-120">Popis</span><span class="sxs-lookup"><span data-stu-id="03dba-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03dba-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="03dba-121">Activity</span></span>|<span data-ttu-id="03dba-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="03dba-122">xs:string</span></span>|<span data-ttu-id="03dba-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="03dba-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="03dba-124">displayName</span><span class="sxs-lookup"><span data-stu-id="03dba-124">DisplayName</span></span>|<span data-ttu-id="03dba-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="03dba-125">xs:string</span></span>|<span data-ttu-id="03dba-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="03dba-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="03dba-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="03dba-127">InstanceId</span></span>|<span data-ttu-id="03dba-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="03dba-128">xs:string</span></span>|<span data-ttu-id="03dba-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="03dba-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="03dba-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="03dba-130">BookmarkName</span></span>|<span data-ttu-id="03dba-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="03dba-131">xs:string</span></span>|<span data-ttu-id="03dba-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="03dba-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="03dba-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="03dba-133">BookmarkScope</span></span>|<span data-ttu-id="03dba-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="03dba-134">xs:string</span></span>|<span data-ttu-id="03dba-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="03dba-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="03dba-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="03dba-136">AppDomain</span></span>|<span data-ttu-id="03dba-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="03dba-137">xs:string</span></span>|<span data-ttu-id="03dba-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="03dba-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
