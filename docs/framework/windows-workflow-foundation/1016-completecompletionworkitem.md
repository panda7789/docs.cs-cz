---
title: 1016 – CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925083"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="e4199-102">1016 – CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="e4199-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e4199-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e4199-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4199-104">ID</span><span class="sxs-lookup"><span data-stu-id="e4199-104">ID</span></span>|<span data-ttu-id="e4199-105">1016</span><span class="sxs-lookup"><span data-stu-id="e4199-105">1016</span></span>|  
|<span data-ttu-id="e4199-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e4199-106">Keywords</span></span>|<span data-ttu-id="e4199-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e4199-107">WFRuntime</span></span>|  
|<span data-ttu-id="e4199-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e4199-108">Level</span></span>|<span data-ttu-id="e4199-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e4199-109">Verbose</span></span>|  
|<span data-ttu-id="e4199-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e4199-110">Channel</span></span>|<span data-ttu-id="e4199-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e4199-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e4199-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e4199-112">Description</span></span>  
 <span data-ttu-id="e4199-113">Označuje, že položka CompletionWorkItem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="e4199-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e4199-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e4199-114">Message</span></span>  
 <span data-ttu-id="e4199-115">Položka CompletionWorkItem byla dokončena pro nadřazenou aktivitu '%1', DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e4199-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e4199-116">Dokončeno %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e4199-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e4199-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e4199-117">Details</span></span>  
  
|<span data-ttu-id="e4199-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e4199-118">Data Item Name</span></span>|<span data-ttu-id="e4199-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e4199-119">Data Item Type</span></span>|<span data-ttu-id="e4199-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e4199-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e4199-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="e4199-121">ParentActivity</span></span>|<span data-ttu-id="e4199-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-122">xs:string</span></span>|<span data-ttu-id="e4199-123">Název typu Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e4199-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="e4199-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="e4199-124">ParentDisplayName</span></span>|<span data-ttu-id="e4199-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-125">xs:string</span></span>|<span data-ttu-id="e4199-126">Zobrazovaný název Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e4199-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="e4199-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="e4199-127">ParentInstanceId</span></span>|<span data-ttu-id="e4199-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-128">xs:string</span></span>|<span data-ttu-id="e4199-129">Id instance Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e4199-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="e4199-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="e4199-130">CompletedActivity</span></span>|<span data-ttu-id="e4199-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-131">xs:string</span></span>|<span data-ttu-id="e4199-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e4199-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="e4199-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e4199-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="e4199-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-134">xs:string</span></span>|<span data-ttu-id="e4199-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e4199-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="e4199-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e4199-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="e4199-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-137">xs:string</span></span>|<span data-ttu-id="e4199-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e4199-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="e4199-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e4199-139">AppDomain</span></span>|<span data-ttu-id="e4199-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e4199-140">xs:string</span></span>|<span data-ttu-id="e4199-141">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e4199-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
