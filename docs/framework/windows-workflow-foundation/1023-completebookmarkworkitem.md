---
title: 1023 - CompleteBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5db5b106a6bc92c288aefe309d33625f57b0ddad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="10203-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="10203-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="10203-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="10203-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10203-104">ID</span><span class="sxs-lookup"><span data-stu-id="10203-104">ID</span></span>|<span data-ttu-id="10203-105">1023</span><span class="sxs-lookup"><span data-stu-id="10203-105">1023</span></span>|  
|<span data-ttu-id="10203-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="10203-106">Keywords</span></span>|<span data-ttu-id="10203-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="10203-107">WFRuntime</span></span>|  
|<span data-ttu-id="10203-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="10203-108">Level</span></span>|<span data-ttu-id="10203-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="10203-109">Verbose</span></span>|  
|<span data-ttu-id="10203-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="10203-110">Channel</span></span>|<span data-ttu-id="10203-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="10203-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="10203-112">Popis</span><span class="sxs-lookup"><span data-stu-id="10203-112">Description</span></span>  
 <span data-ttu-id="10203-113">Označuje, že je dokončená BookmarkWorkItem.</span><span class="sxs-lookup"><span data-stu-id="10203-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="10203-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="10203-114">Message</span></span>  
 <span data-ttu-id="10203-115">BookmarkWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="10203-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="10203-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="10203-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="10203-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="10203-117">Details</span></span>  
  
|<span data-ttu-id="10203-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="10203-118">Data Item Name</span></span>|<span data-ttu-id="10203-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="10203-119">Data Item Type</span></span>|<span data-ttu-id="10203-120">Popis</span><span class="sxs-lookup"><span data-stu-id="10203-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="10203-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="10203-121">Activity</span></span>|<span data-ttu-id="10203-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="10203-122">xs:string</span></span>|<span data-ttu-id="10203-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="10203-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="10203-124">displayName</span><span class="sxs-lookup"><span data-stu-id="10203-124">DisplayName</span></span>|<span data-ttu-id="10203-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="10203-125">xs:string</span></span>|<span data-ttu-id="10203-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="10203-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="10203-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="10203-127">InstanceId</span></span>|<span data-ttu-id="10203-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="10203-128">xs:string</span></span>|<span data-ttu-id="10203-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="10203-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="10203-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="10203-130">BookmarkName</span></span>|<span data-ttu-id="10203-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="10203-131">xs:string</span></span>|<span data-ttu-id="10203-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="10203-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="10203-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="10203-133">BookmarkScope</span></span>|<span data-ttu-id="10203-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="10203-134">xs:string</span></span>|<span data-ttu-id="10203-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="10203-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="10203-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="10203-136">AppDomain</span></span>|<span data-ttu-id="10203-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="10203-137">xs:string</span></span>|<span data-ttu-id="10203-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="10203-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
