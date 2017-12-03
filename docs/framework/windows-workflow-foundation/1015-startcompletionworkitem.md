---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44ef71e254a2407b416a0efc4b560bf2f6013a74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="10159-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="10159-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="10159-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="10159-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10159-104">ID</span><span class="sxs-lookup"><span data-stu-id="10159-104">ID</span></span>|<span data-ttu-id="10159-105">1015</span><span class="sxs-lookup"><span data-stu-id="10159-105">1015</span></span>|  
|<span data-ttu-id="10159-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="10159-106">Keywords</span></span>|<span data-ttu-id="10159-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="10159-107">WFRuntime</span></span>|  
|<span data-ttu-id="10159-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="10159-108">Level</span></span>|<span data-ttu-id="10159-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="10159-109">Verbose</span></span>|  
|<span data-ttu-id="10159-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="10159-110">Channel</span></span>|<span data-ttu-id="10159-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="10159-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="10159-112">Popis</span><span class="sxs-lookup"><span data-stu-id="10159-112">Description</span></span>  
 <span data-ttu-id="10159-113">Označuje, že že completionworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="10159-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="10159-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="10159-114">Message</span></span>  
 <span data-ttu-id="10159-115">Spuštění provádění CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="10159-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="10159-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="10159-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="10159-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="10159-117">Details</span></span>  
  
|<span data-ttu-id="10159-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="10159-118">Data Item Name</span></span>|<span data-ttu-id="10159-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="10159-119">Data Item Type</span></span>|<span data-ttu-id="10159-120">Popis</span><span class="sxs-lookup"><span data-stu-id="10159-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="10159-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="10159-121">ParentActivity</span></span>|<span data-ttu-id="10159-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-122">xs:string</span></span>|<span data-ttu-id="10159-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="10159-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="10159-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="10159-124">ParentDisplayName</span></span>|<span data-ttu-id="10159-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-125">xs:string</span></span>|<span data-ttu-id="10159-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="10159-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="10159-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="10159-127">ParentInstanceId</span></span>|<span data-ttu-id="10159-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-128">xs:string</span></span>|<span data-ttu-id="10159-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="10159-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="10159-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="10159-130">CompletedActivity</span></span>|<span data-ttu-id="10159-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-131">xs:string</span></span>|<span data-ttu-id="10159-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="10159-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="10159-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="10159-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="10159-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-134">xs:string</span></span>|<span data-ttu-id="10159-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="10159-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="10159-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="10159-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="10159-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-137">xs:string</span></span>|<span data-ttu-id="10159-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="10159-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="10159-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="10159-139">AppDomain</span></span>|<span data-ttu-id="10159-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="10159-140">xs:string</span></span>|<span data-ttu-id="10159-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="10159-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
