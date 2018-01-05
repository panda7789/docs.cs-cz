---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="1015e-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="1015e-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1015e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1015e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1015e-104">ID</span><span class="sxs-lookup"><span data-stu-id="1015e-104">ID</span></span>|<span data-ttu-id="1015e-105">1016</span><span class="sxs-lookup"><span data-stu-id="1015e-105">1016</span></span>|  
|<span data-ttu-id="1015e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1015e-106">Keywords</span></span>|<span data-ttu-id="1015e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1015e-107">WFRuntime</span></span>|  
|<span data-ttu-id="1015e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1015e-108">Level</span></span>|<span data-ttu-id="1015e-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="1015e-109">Verbose</span></span>|  
|<span data-ttu-id="1015e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1015e-110">Channel</span></span>|<span data-ttu-id="1015e-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="1015e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1015e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1015e-112">Description</span></span>  
 <span data-ttu-id="1015e-113">Označuje, že je dokončená CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="1015e-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1015e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1015e-114">Message</span></span>  
 <span data-ttu-id="1015e-115">Bylo dokončeno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="1015e-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1015e-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="1015e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1015e-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1015e-117">Details</span></span>  
  
|<span data-ttu-id="1015e-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1015e-118">Data Item Name</span></span>|<span data-ttu-id="1015e-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1015e-119">Data Item Type</span></span>|<span data-ttu-id="1015e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1015e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1015e-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="1015e-121">ParentActivity</span></span>|<span data-ttu-id="1015e-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-122">xs:string</span></span>|<span data-ttu-id="1015e-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="1015e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1015e-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="1015e-124">ParentDisplayName</span></span>|<span data-ttu-id="1015e-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-125">xs:string</span></span>|<span data-ttu-id="1015e-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="1015e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1015e-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1015e-127">ParentInstanceId</span></span>|<span data-ttu-id="1015e-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-128">xs:string</span></span>|<span data-ttu-id="1015e-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="1015e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1015e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="1015e-130">CompletedActivity</span></span>|<span data-ttu-id="1015e-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-131">xs:string</span></span>|<span data-ttu-id="1015e-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="1015e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="1015e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1015e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="1015e-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-134">xs:string</span></span>|<span data-ttu-id="1015e-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="1015e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="1015e-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1015e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="1015e-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-137">xs:string</span></span>|<span data-ttu-id="1015e-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="1015e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="1015e-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1015e-139">AppDomain</span></span>|<span data-ttu-id="1015e-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="1015e-140">xs:string</span></span>|<span data-ttu-id="1015e-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1015e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
