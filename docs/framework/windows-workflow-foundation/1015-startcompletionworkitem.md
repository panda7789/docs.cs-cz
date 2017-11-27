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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="5fd7c-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="5fd7c-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5fd7c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5fd7c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fd7c-104">ID</span><span class="sxs-lookup"><span data-stu-id="5fd7c-104">ID</span></span>|<span data-ttu-id="5fd7c-105">1015</span><span class="sxs-lookup"><span data-stu-id="5fd7c-105">1015</span></span>|  
|<span data-ttu-id="5fd7c-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5fd7c-106">Keywords</span></span>|<span data-ttu-id="5fd7c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5fd7c-107">WFRuntime</span></span>|  
|<span data-ttu-id="5fd7c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5fd7c-108">Level</span></span>|<span data-ttu-id="5fd7c-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="5fd7c-109">Verbose</span></span>|  
|<span data-ttu-id="5fd7c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5fd7c-110">Channel</span></span>|<span data-ttu-id="5fd7c-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="5fd7c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5fd7c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5fd7c-112">Description</span></span>  
 <span data-ttu-id="5fd7c-113">Označuje, že že completionworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5fd7c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5fd7c-114">Message</span></span>  
 <span data-ttu-id="5fd7c-115">Spuštění provádění CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="5fd7c-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5fd7c-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5fd7c-117">Details</span></span>  
  
|<span data-ttu-id="5fd7c-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5fd7c-118">Data Item Name</span></span>|<span data-ttu-id="5fd7c-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5fd7c-119">Data Item Type</span></span>|<span data-ttu-id="5fd7c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5fd7c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5fd7c-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="5fd7c-121">ParentActivity</span></span>|<span data-ttu-id="5fd7c-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-122">xs:string</span></span>|<span data-ttu-id="5fd7c-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="5fd7c-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="5fd7c-124">ParentDisplayName</span></span>|<span data-ttu-id="5fd7c-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-125">xs:string</span></span>|<span data-ttu-id="5fd7c-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="5fd7c-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="5fd7c-127">ParentInstanceId</span></span>|<span data-ttu-id="5fd7c-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-128">xs:string</span></span>|<span data-ttu-id="5fd7c-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="5fd7c-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="5fd7c-130">CompletedActivity</span></span>|<span data-ttu-id="5fd7c-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-131">xs:string</span></span>|<span data-ttu-id="5fd7c-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="5fd7c-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="5fd7c-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="5fd7c-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-134">xs:string</span></span>|<span data-ttu-id="5fd7c-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="5fd7c-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="5fd7c-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="5fd7c-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-137">xs:string</span></span>|<span data-ttu-id="5fd7c-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="5fd7c-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5fd7c-139">AppDomain</span></span>|<span data-ttu-id="5fd7c-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fd7c-140">xs:string</span></span>|<span data-ttu-id="5fd7c-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5fd7c-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
