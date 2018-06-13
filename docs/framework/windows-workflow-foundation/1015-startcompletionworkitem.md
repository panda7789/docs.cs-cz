---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509625"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="b7ace-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="b7ace-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b7ace-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7ace-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7ace-104">ID</span><span class="sxs-lookup"><span data-stu-id="b7ace-104">ID</span></span>|<span data-ttu-id="b7ace-105">1015</span><span class="sxs-lookup"><span data-stu-id="b7ace-105">1015</span></span>|  
|<span data-ttu-id="b7ace-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b7ace-106">Keywords</span></span>|<span data-ttu-id="b7ace-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b7ace-107">WFRuntime</span></span>|  
|<span data-ttu-id="b7ace-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b7ace-108">Level</span></span>|<span data-ttu-id="b7ace-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b7ace-109">Verbose</span></span>|  
|<span data-ttu-id="b7ace-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b7ace-110">Channel</span></span>|<span data-ttu-id="b7ace-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b7ace-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7ace-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b7ace-112">Description</span></span>  
 <span data-ttu-id="b7ace-113">Označuje, že že completionworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="b7ace-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7ace-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b7ace-114">Message</span></span>  
 <span data-ttu-id="b7ace-115">Spuštění provádění CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b7ace-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="b7ace-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="b7ace-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7ace-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b7ace-117">Details</span></span>  
  
|<span data-ttu-id="b7ace-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b7ace-118">Data Item Name</span></span>|<span data-ttu-id="b7ace-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b7ace-119">Data Item Type</span></span>|<span data-ttu-id="b7ace-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b7ace-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7ace-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="b7ace-121">ParentActivity</span></span>|<span data-ttu-id="b7ace-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-122">xs:string</span></span>|<span data-ttu-id="b7ace-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7ace-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="b7ace-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7ace-124">ParentDisplayName</span></span>|<span data-ttu-id="b7ace-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-125">xs:string</span></span>|<span data-ttu-id="b7ace-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7ace-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="b7ace-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7ace-127">ParentInstanceId</span></span>|<span data-ttu-id="b7ace-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-128">xs:string</span></span>|<span data-ttu-id="b7ace-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7ace-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="b7ace-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="b7ace-130">CompletedActivity</span></span>|<span data-ttu-id="b7ace-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-131">xs:string</span></span>|<span data-ttu-id="b7ace-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7ace-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="b7ace-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7ace-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="b7ace-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-134">xs:string</span></span>|<span data-ttu-id="b7ace-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7ace-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="b7ace-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7ace-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="b7ace-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-137">xs:string</span></span>|<span data-ttu-id="b7ace-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7ace-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="b7ace-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b7ace-139">AppDomain</span></span>|<span data-ttu-id="b7ace-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7ace-140">xs:string</span></span>|<span data-ttu-id="b7ace-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b7ace-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
