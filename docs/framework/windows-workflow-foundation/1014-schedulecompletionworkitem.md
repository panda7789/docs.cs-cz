---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510364"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="ec7cf-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="ec7cf-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ec7cf-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ec7cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec7cf-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec7cf-104">ID</span></span>|<span data-ttu-id="ec7cf-105">1014</span><span class="sxs-lookup"><span data-stu-id="ec7cf-105">1014</span></span>|  
|<span data-ttu-id="ec7cf-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ec7cf-106">Keywords</span></span>|<span data-ttu-id="ec7cf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ec7cf-107">WFRuntime</span></span>|  
|<span data-ttu-id="ec7cf-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ec7cf-108">Level</span></span>|<span data-ttu-id="ec7cf-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="ec7cf-109">Verbose</span></span>|  
|<span data-ttu-id="ec7cf-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ec7cf-110">Channel</span></span>|<span data-ttu-id="ec7cf-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ec7cf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec7cf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ec7cf-112">Description</span></span>  
 <span data-ttu-id="ec7cf-113">Označuje, že bylo naplánováno CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec7cf-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ec7cf-114">Message</span></span>  
 <span data-ttu-id="ec7cf-115">Bylo naplánováno CompletionWorkItem pro nadřazené aktivity '%1', DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ec7cf-116">Dokončení aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec7cf-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ec7cf-117">Details</span></span>  
  
|<span data-ttu-id="ec7cf-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ec7cf-118">Data Item Name</span></span>|<span data-ttu-id="ec7cf-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ec7cf-119">Data Item Type</span></span>|<span data-ttu-id="ec7cf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ec7cf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec7cf-121">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="ec7cf-121">ParentActivity</span></span>|<span data-ttu-id="ec7cf-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-122">xs:string</span></span>|<span data-ttu-id="ec7cf-123">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="ec7cf-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="ec7cf-124">ParentDisplayName</span></span>|<span data-ttu-id="ec7cf-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-125">xs:string</span></span>|<span data-ttu-id="ec7cf-126">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="ec7cf-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="ec7cf-127">ParentInstanceId</span></span>|<span data-ttu-id="ec7cf-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-128">xs:string</span></span>|<span data-ttu-id="ec7cf-129">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="ec7cf-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="ec7cf-130">CompletedActivity</span></span>|<span data-ttu-id="ec7cf-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-131">xs:string</span></span>|<span data-ttu-id="ec7cf-132">Název typu dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="ec7cf-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ec7cf-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="ec7cf-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-134">xs:string</span></span>|<span data-ttu-id="ec7cf-135">Zobrazovaný název dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="ec7cf-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ec7cf-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="ec7cf-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-137">xs:string</span></span>|<span data-ttu-id="ec7cf-138">Id instance dokončené aktivity.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="ec7cf-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ec7cf-139">AppDomain</span></span>|<span data-ttu-id="ec7cf-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="ec7cf-140">xs:string</span></span>|<span data-ttu-id="ec7cf-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ec7cf-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
