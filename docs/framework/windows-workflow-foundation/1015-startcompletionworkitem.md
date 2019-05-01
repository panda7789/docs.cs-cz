---
title: 1015 – StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032263"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="e0ad8-102">1015 – StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="e0ad8-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e0ad8-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e0ad8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0ad8-104">ID</span><span class="sxs-lookup"><span data-stu-id="e0ad8-104">ID</span></span>|<span data-ttu-id="e0ad8-105">1015</span><span class="sxs-lookup"><span data-stu-id="e0ad8-105">1015</span></span>|  
|<span data-ttu-id="e0ad8-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e0ad8-106">Keywords</span></span>|<span data-ttu-id="e0ad8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e0ad8-107">WFRuntime</span></span>|  
|<span data-ttu-id="e0ad8-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e0ad8-108">Level</span></span>|<span data-ttu-id="e0ad8-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e0ad8-109">Verbose</span></span>|  
|<span data-ttu-id="e0ad8-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e0ad8-110">Channel</span></span>|<span data-ttu-id="e0ad8-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e0ad8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e0ad8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e0ad8-112">Description</span></span>  
 <span data-ttu-id="e0ad8-113">Označuje, že položka CompletionWorkItem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e0ad8-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e0ad8-114">Message</span></span>  
 <span data-ttu-id="e0ad8-115">Spouštění provedení položky CompletionWorkItem pro nadřízenou aktivitu '%1', DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e0ad8-116">Dokončeno %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e0ad8-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e0ad8-117">Details</span></span>  
  
|<span data-ttu-id="e0ad8-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e0ad8-118">Data Item Name</span></span>|<span data-ttu-id="e0ad8-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e0ad8-119">Data Item Type</span></span>|<span data-ttu-id="e0ad8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e0ad8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e0ad8-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="e0ad8-121">ParentActivity</span></span>|<span data-ttu-id="e0ad8-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-122">xs:string</span></span>|<span data-ttu-id="e0ad8-123">Název typu Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="e0ad8-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="e0ad8-124">ParentDisplayName</span></span>|<span data-ttu-id="e0ad8-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-125">xs:string</span></span>|<span data-ttu-id="e0ad8-126">Zobrazovaný název Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="e0ad8-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="e0ad8-127">ParentInstanceId</span></span>|<span data-ttu-id="e0ad8-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-128">xs:string</span></span>|<span data-ttu-id="e0ad8-129">Id instance Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="e0ad8-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="e0ad8-130">CompletedActivity</span></span>|<span data-ttu-id="e0ad8-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-131">xs:string</span></span>|<span data-ttu-id="e0ad8-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="e0ad8-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e0ad8-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="e0ad8-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-134">xs:string</span></span>|<span data-ttu-id="e0ad8-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="e0ad8-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e0ad8-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="e0ad8-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-137">xs:string</span></span>|<span data-ttu-id="e0ad8-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="e0ad8-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e0ad8-139">AppDomain</span></span>|<span data-ttu-id="e0ad8-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e0ad8-140">xs:string</span></span>|<span data-ttu-id="e0ad8-141">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e0ad8-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
