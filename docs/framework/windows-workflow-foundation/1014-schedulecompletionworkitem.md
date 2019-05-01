---
title: 1014 – ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982264"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="64950-102">1014 – ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="64950-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="64950-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="64950-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64950-104">ID</span><span class="sxs-lookup"><span data-stu-id="64950-104">ID</span></span>|<span data-ttu-id="64950-105">1014</span><span class="sxs-lookup"><span data-stu-id="64950-105">1014</span></span>|  
|<span data-ttu-id="64950-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="64950-106">Keywords</span></span>|<span data-ttu-id="64950-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="64950-107">WFRuntime</span></span>|  
|<span data-ttu-id="64950-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="64950-108">Level</span></span>|<span data-ttu-id="64950-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="64950-109">Verbose</span></span>|  
|<span data-ttu-id="64950-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="64950-110">Channel</span></span>|<span data-ttu-id="64950-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="64950-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="64950-112">Popis</span><span class="sxs-lookup"><span data-stu-id="64950-112">Description</span></span>  
 <span data-ttu-id="64950-113">Označuje, že položka CompletionWorkItem byla plánována.</span><span class="sxs-lookup"><span data-stu-id="64950-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="64950-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="64950-114">Message</span></span>  
 <span data-ttu-id="64950-115">Položka CompletionWorkItem byla plánována-Nadřazená aktivita '%1', DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="64950-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="64950-116">Dokončeno %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="64950-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="64950-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="64950-117">Details</span></span>  
  
|<span data-ttu-id="64950-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="64950-118">Data Item Name</span></span>|<span data-ttu-id="64950-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="64950-119">Data Item Type</span></span>|<span data-ttu-id="64950-120">Popis</span><span class="sxs-lookup"><span data-stu-id="64950-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="64950-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="64950-121">ParentActivity</span></span>|<span data-ttu-id="64950-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-122">xs:string</span></span>|<span data-ttu-id="64950-123">Název typu Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="64950-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="64950-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="64950-124">ParentDisplayName</span></span>|<span data-ttu-id="64950-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-125">xs:string</span></span>|<span data-ttu-id="64950-126">Zobrazovaný název Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="64950-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="64950-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="64950-127">ParentInstanceId</span></span>|<span data-ttu-id="64950-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-128">xs:string</span></span>|<span data-ttu-id="64950-129">Id instance Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="64950-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="64950-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="64950-130">CompletedActivity</span></span>|<span data-ttu-id="64950-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-131">xs:string</span></span>|<span data-ttu-id="64950-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="64950-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="64950-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="64950-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="64950-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-134">xs:string</span></span>|<span data-ttu-id="64950-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="64950-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="64950-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="64950-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="64950-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-137">xs:string</span></span>|<span data-ttu-id="64950-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="64950-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="64950-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="64950-139">AppDomain</span></span>|<span data-ttu-id="64950-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="64950-140">xs:string</span></span>|<span data-ttu-id="64950-141">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="64950-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
