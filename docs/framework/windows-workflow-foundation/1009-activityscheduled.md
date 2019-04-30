---
title: 1009 – ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924654"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="6ff3f-102">1009 – ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="6ff3f-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="6ff3f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6ff3f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ff3f-104">ID</span><span class="sxs-lookup"><span data-stu-id="6ff3f-104">ID</span></span>|<span data-ttu-id="6ff3f-105">1009</span><span class="sxs-lookup"><span data-stu-id="6ff3f-105">1009</span></span>|  
|<span data-ttu-id="6ff3f-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6ff3f-106">Keywords</span></span>|<span data-ttu-id="6ff3f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6ff3f-107">WFRuntime</span></span>|  
|<span data-ttu-id="6ff3f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6ff3f-108">Level</span></span>|<span data-ttu-id="6ff3f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="6ff3f-109">Information</span></span>|  
|<span data-ttu-id="6ff3f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6ff3f-110">Channel</span></span>|<span data-ttu-id="6ff3f-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="6ff3f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6ff3f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6ff3f-112">Description</span></span>  
 <span data-ttu-id="6ff3f-113">Označuje, že pro spuštění je naplánované aktivity.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6ff3f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6ff3f-114">Message</span></span>  
 <span data-ttu-id="6ff3f-115">Nadřazená aktivita %1, DisplayName: %2, InstanceId: '%3' naplánovala podřízenou aktivitu "%4", DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6ff3f-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6ff3f-116">Details</span></span>  
  
|<span data-ttu-id="6ff3f-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6ff3f-117">Data Item Name</span></span>|<span data-ttu-id="6ff3f-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="6ff3f-118">Data Item Type</span></span>|<span data-ttu-id="6ff3f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6ff3f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6ff3f-120">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="6ff3f-120">ParentActivity</span></span>|<span data-ttu-id="6ff3f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-121">xs:string</span></span>|<span data-ttu-id="6ff3f-122">Název typu Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="6ff3f-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="6ff3f-123">ParentDisplayName</span></span>|<span data-ttu-id="6ff3f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-124">xs:string</span></span>|<span data-ttu-id="6ff3f-125">Zobrazovaný název Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="6ff3f-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="6ff3f-126">ParentInstanceId</span></span>|<span data-ttu-id="6ff3f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-127">xs:string</span></span>|<span data-ttu-id="6ff3f-128">Id instance Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="6ff3f-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="6ff3f-129">ChildActivity</span></span>|<span data-ttu-id="6ff3f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-130">xs:string</span></span>|<span data-ttu-id="6ff3f-131">Název typu naplánovala podřízenou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="6ff3f-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="6ff3f-132">ChildDisplayName</span></span>|<span data-ttu-id="6ff3f-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-133">xs:string</span></span>|<span data-ttu-id="6ff3f-134">Zobrazovaný název naplánovala podřízenou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="6ff3f-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="6ff3f-135">ChildInstanceId</span></span>|<span data-ttu-id="6ff3f-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-136">xs:string</span></span>|<span data-ttu-id="6ff3f-137">Id instance naplánovala podřízenou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="6ff3f-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6ff3f-138">AppDomain</span></span>|<span data-ttu-id="6ff3f-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="6ff3f-139">xs:string</span></span>|<span data-ttu-id="6ff3f-140">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6ff3f-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
