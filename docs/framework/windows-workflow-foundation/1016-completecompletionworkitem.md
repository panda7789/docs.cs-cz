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
ms.openlocfilehash: b01706f6e84987ea20f52c131139e243e8184c51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="89263-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="89263-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="89263-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="89263-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89263-104">ID</span><span class="sxs-lookup"><span data-stu-id="89263-104">ID</span></span>|<span data-ttu-id="89263-105">1016</span><span class="sxs-lookup"><span data-stu-id="89263-105">1016</span></span>|  
|<span data-ttu-id="89263-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="89263-106">Keywords</span></span>|<span data-ttu-id="89263-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="89263-107">WFRuntime</span></span>|  
|<span data-ttu-id="89263-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="89263-108">Level</span></span>|<span data-ttu-id="89263-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="89263-109">Verbose</span></span>|  
|<span data-ttu-id="89263-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="89263-110">Channel</span></span>|<span data-ttu-id="89263-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="89263-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="89263-112">Popis</span><span class="sxs-lookup"><span data-stu-id="89263-112">Description</span></span>  
 <span data-ttu-id="89263-113">Označuje, že je dokončená CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="89263-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="89263-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="89263-114">Message</span></span>  
 <span data-ttu-id="89263-115">Bylo dokončeno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="89263-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="89263-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="89263-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="89263-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="89263-117">Details</span></span>  
  
|<span data-ttu-id="89263-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="89263-118">Data Item Name</span></span>|<span data-ttu-id="89263-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="89263-119">Data Item Type</span></span>|<span data-ttu-id="89263-120">Popis</span><span class="sxs-lookup"><span data-stu-id="89263-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="89263-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="89263-121">ParentActivity</span></span>|<span data-ttu-id="89263-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-122">xs:string</span></span>|<span data-ttu-id="89263-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="89263-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="89263-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="89263-124">ParentDisplayName</span></span>|<span data-ttu-id="89263-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-125">xs:string</span></span>|<span data-ttu-id="89263-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="89263-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="89263-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="89263-127">ParentInstanceId</span></span>|<span data-ttu-id="89263-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-128">xs:string</span></span>|<span data-ttu-id="89263-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="89263-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="89263-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="89263-130">CompletedActivity</span></span>|<span data-ttu-id="89263-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-131">xs:string</span></span>|<span data-ttu-id="89263-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="89263-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="89263-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="89263-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="89263-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-134">xs:string</span></span>|<span data-ttu-id="89263-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="89263-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="89263-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="89263-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="89263-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-137">xs:string</span></span>|<span data-ttu-id="89263-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="89263-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="89263-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="89263-139">AppDomain</span></span>|<span data-ttu-id="89263-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="89263-140">xs:string</span></span>|<span data-ttu-id="89263-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="89263-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
