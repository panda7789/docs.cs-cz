---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdaa8ca4efeffb3895e0056303721b13cdc1ae27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="12090-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="12090-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="12090-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="12090-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12090-104">ID</span><span class="sxs-lookup"><span data-stu-id="12090-104">ID</span></span>|<span data-ttu-id="12090-105">1009</span><span class="sxs-lookup"><span data-stu-id="12090-105">1009</span></span>|  
|<span data-ttu-id="12090-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="12090-106">Keywords</span></span>|<span data-ttu-id="12090-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="12090-107">WFRuntime</span></span>|  
|<span data-ttu-id="12090-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="12090-108">Level</span></span>|<span data-ttu-id="12090-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="12090-109">Information</span></span>|  
|<span data-ttu-id="12090-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="12090-110">Channel</span></span>|<span data-ttu-id="12090-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="12090-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="12090-112">Popis</span><span class="sxs-lookup"><span data-stu-id="12090-112">Description</span></span>  
 <span data-ttu-id="12090-113">Označuje, že aktivita je naplánován pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="12090-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="12090-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="12090-114">Message</span></span>  
 <span data-ttu-id="12090-115">Nadřazená aktivita %1, DisplayName: %2, identifikátor InstanceId: '%3' naplánované podřízené aktivity "%4", DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="12090-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="12090-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="12090-116">Details</span></span>  
  
|<span data-ttu-id="12090-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="12090-117">Data Item Name</span></span>|<span data-ttu-id="12090-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="12090-118">Data Item Type</span></span>|<span data-ttu-id="12090-119">Popis</span><span class="sxs-lookup"><span data-stu-id="12090-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="12090-120">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="12090-120">ParentActivity</span></span>|<span data-ttu-id="12090-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-121">xs:string</span></span>|<span data-ttu-id="12090-122">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="12090-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="12090-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="12090-123">ParentDisplayName</span></span>|<span data-ttu-id="12090-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-124">xs:string</span></span>|<span data-ttu-id="12090-125">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="12090-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="12090-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="12090-126">ParentInstanceId</span></span>|<span data-ttu-id="12090-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-127">xs:string</span></span>|<span data-ttu-id="12090-128">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="12090-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="12090-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="12090-129">ChildActivity</span></span>|<span data-ttu-id="12090-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-130">xs:string</span></span>|<span data-ttu-id="12090-131">Název typu naplánované podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="12090-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="12090-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="12090-132">ChildDisplayName</span></span>|<span data-ttu-id="12090-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-133">xs:string</span></span>|<span data-ttu-id="12090-134">Zobrazovaný název naplánované podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="12090-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="12090-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="12090-135">ChildInstanceId</span></span>|<span data-ttu-id="12090-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-136">xs:string</span></span>|<span data-ttu-id="12090-137">Id instance plánované podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="12090-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="12090-138">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="12090-138">AppDomain</span></span>|<span data-ttu-id="12090-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="12090-139">xs:string</span></span>|<span data-ttu-id="12090-140">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="12090-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
