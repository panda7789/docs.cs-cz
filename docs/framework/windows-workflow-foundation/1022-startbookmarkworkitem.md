---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509805"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="5347c-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="5347c-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5347c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5347c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5347c-104">ID</span><span class="sxs-lookup"><span data-stu-id="5347c-104">ID</span></span>|<span data-ttu-id="5347c-105">1022</span><span class="sxs-lookup"><span data-stu-id="5347c-105">1022</span></span>|  
|<span data-ttu-id="5347c-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5347c-106">Keywords</span></span>|<span data-ttu-id="5347c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5347c-107">WFRuntime</span></span>|  
|<span data-ttu-id="5347c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5347c-108">Level</span></span>|<span data-ttu-id="5347c-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="5347c-109">Verbose</span></span>|  
|<span data-ttu-id="5347c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5347c-110">Channel</span></span>|<span data-ttu-id="5347c-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="5347c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5347c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5347c-112">Description</span></span>  
 <span data-ttu-id="5347c-113">Označuje, že že bookmarkworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="5347c-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5347c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5347c-114">Message</span></span>  
 <span data-ttu-id="5347c-115">Spuštění provádění BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="5347c-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5347c-116">NázevZáložky: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="5347c-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5347c-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5347c-117">Details</span></span>  
  
|<span data-ttu-id="5347c-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5347c-118">Data Item Name</span></span>|<span data-ttu-id="5347c-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5347c-119">Data Item Type</span></span>|<span data-ttu-id="5347c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5347c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5347c-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="5347c-121">Activity</span></span>|<span data-ttu-id="5347c-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="5347c-122">xs:string</span></span>|<span data-ttu-id="5347c-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5347c-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="5347c-124">displayName</span><span class="sxs-lookup"><span data-stu-id="5347c-124">DisplayName</span></span>|<span data-ttu-id="5347c-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="5347c-125">xs:string</span></span>|<span data-ttu-id="5347c-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="5347c-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="5347c-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="5347c-127">InstanceId</span></span>|<span data-ttu-id="5347c-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="5347c-128">xs:string</span></span>|<span data-ttu-id="5347c-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="5347c-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5347c-130">NázevZáložky</span><span class="sxs-lookup"><span data-stu-id="5347c-130">BookmarkName</span></span>|<span data-ttu-id="5347c-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="5347c-131">xs:string</span></span>|<span data-ttu-id="5347c-132">Název záložky</span><span class="sxs-lookup"><span data-stu-id="5347c-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="5347c-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="5347c-133">BookmarkScope</span></span>|<span data-ttu-id="5347c-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="5347c-134">xs:string</span></span>|<span data-ttu-id="5347c-135">Rozsah záložky.</span><span class="sxs-lookup"><span data-stu-id="5347c-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="5347c-136">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5347c-136">AppDomain</span></span>|<span data-ttu-id="5347c-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="5347c-137">xs:string</span></span>|<span data-ttu-id="5347c-138">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5347c-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
