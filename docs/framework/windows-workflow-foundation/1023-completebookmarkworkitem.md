---
title: 1023 - CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: 8677f25057486247e64879298755fe972bd373d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510319"
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="77127-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="77127-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="77127-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="77127-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77127-104">ID</span><span class="sxs-lookup"><span data-stu-id="77127-104">ID</span></span>|<span data-ttu-id="77127-105">1023</span><span class="sxs-lookup"><span data-stu-id="77127-105">1023</span></span>|  
|<span data-ttu-id="77127-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="77127-106">Keywords</span></span>|<span data-ttu-id="77127-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="77127-107">WFRuntime</span></span>|  
|<span data-ttu-id="77127-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="77127-108">Level</span></span>|<span data-ttu-id="77127-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="77127-109">Verbose</span></span>|  
|<span data-ttu-id="77127-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="77127-110">Channel</span></span>|<span data-ttu-id="77127-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="77127-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77127-112">Popis</span><span class="sxs-lookup"><span data-stu-id="77127-112">Description</span></span>  
 <span data-ttu-id="77127-113">Označuje, že je dokončená BookmarkWorkItem.</span><span class="sxs-lookup"><span data-stu-id="77127-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77127-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="77127-114">Message</span></span>  
 <span data-ttu-id="77127-115">BookmarkWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="77127-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="77127-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="77127-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77127-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="77127-117">Details</span></span>  
  
|<span data-ttu-id="77127-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="77127-118">Data Item Name</span></span>|<span data-ttu-id="77127-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="77127-119">Data Item Type</span></span>|<span data-ttu-id="77127-120">Popis</span><span class="sxs-lookup"><span data-stu-id="77127-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77127-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="77127-121">Activity</span></span>|<span data-ttu-id="77127-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="77127-122">xs:string</span></span>|<span data-ttu-id="77127-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="77127-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="77127-124">displayName</span><span class="sxs-lookup"><span data-stu-id="77127-124">DisplayName</span></span>|<span data-ttu-id="77127-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="77127-125">xs:string</span></span>|<span data-ttu-id="77127-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="77127-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="77127-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="77127-127">InstanceId</span></span>|<span data-ttu-id="77127-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="77127-128">xs:string</span></span>|<span data-ttu-id="77127-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="77127-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="77127-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="77127-130">BookmarkName</span></span>|<span data-ttu-id="77127-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="77127-131">xs:string</span></span>|<span data-ttu-id="77127-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="77127-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="77127-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="77127-133">BookmarkScope</span></span>|<span data-ttu-id="77127-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="77127-134">xs:string</span></span>|<span data-ttu-id="77127-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="77127-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="77127-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="77127-136">AppDomain</span></span>|<span data-ttu-id="77127-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="77127-137">xs:string</span></span>|<span data-ttu-id="77127-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="77127-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
