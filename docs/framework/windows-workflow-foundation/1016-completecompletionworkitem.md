---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510293"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="baea1-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="baea1-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="baea1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="baea1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="baea1-104">ID</span><span class="sxs-lookup"><span data-stu-id="baea1-104">ID</span></span>|<span data-ttu-id="baea1-105">1016</span><span class="sxs-lookup"><span data-stu-id="baea1-105">1016</span></span>|  
|<span data-ttu-id="baea1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="baea1-106">Keywords</span></span>|<span data-ttu-id="baea1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="baea1-107">WFRuntime</span></span>|  
|<span data-ttu-id="baea1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="baea1-108">Level</span></span>|<span data-ttu-id="baea1-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="baea1-109">Verbose</span></span>|  
|<span data-ttu-id="baea1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="baea1-110">Channel</span></span>|<span data-ttu-id="baea1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="baea1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="baea1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="baea1-112">Description</span></span>  
 <span data-ttu-id="baea1-113">Označuje, že je dokončená CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="baea1-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="baea1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="baea1-114">Message</span></span>  
 <span data-ttu-id="baea1-115">Bylo dokončeno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="baea1-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="baea1-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="baea1-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="baea1-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="baea1-117">Details</span></span>  
  
|<span data-ttu-id="baea1-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="baea1-118">Data Item Name</span></span>|<span data-ttu-id="baea1-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="baea1-119">Data Item Type</span></span>|<span data-ttu-id="baea1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="baea1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="baea1-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="baea1-121">ParentActivity</span></span>|<span data-ttu-id="baea1-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-122">xs:string</span></span>|<span data-ttu-id="baea1-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="baea1-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="baea1-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="baea1-124">ParentDisplayName</span></span>|<span data-ttu-id="baea1-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-125">xs:string</span></span>|<span data-ttu-id="baea1-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="baea1-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="baea1-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="baea1-127">ParentInstanceId</span></span>|<span data-ttu-id="baea1-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-128">xs:string</span></span>|<span data-ttu-id="baea1-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="baea1-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="baea1-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="baea1-130">CompletedActivity</span></span>|<span data-ttu-id="baea1-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-131">xs:string</span></span>|<span data-ttu-id="baea1-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="baea1-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="baea1-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="baea1-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="baea1-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-134">xs:string</span></span>|<span data-ttu-id="baea1-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="baea1-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="baea1-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="baea1-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="baea1-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-137">xs:string</span></span>|<span data-ttu-id="baea1-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="baea1-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="baea1-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="baea1-139">AppDomain</span></span>|<span data-ttu-id="baea1-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="baea1-140">xs:string</span></span>|<span data-ttu-id="baea1-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="baea1-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
