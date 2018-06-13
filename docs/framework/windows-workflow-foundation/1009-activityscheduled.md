---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509969"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="c0c85-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="c0c85-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="c0c85-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c0c85-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0c85-104">ID</span><span class="sxs-lookup"><span data-stu-id="c0c85-104">ID</span></span>|<span data-ttu-id="c0c85-105">1009</span><span class="sxs-lookup"><span data-stu-id="c0c85-105">1009</span></span>|  
|<span data-ttu-id="c0c85-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c0c85-106">Keywords</span></span>|<span data-ttu-id="c0c85-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c0c85-107">WFRuntime</span></span>|  
|<span data-ttu-id="c0c85-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="c0c85-108">Level</span></span>|<span data-ttu-id="c0c85-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="c0c85-109">Information</span></span>|  
|<span data-ttu-id="c0c85-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="c0c85-110">Channel</span></span>|<span data-ttu-id="c0c85-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="c0c85-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c0c85-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c85-112">Description</span></span>  
 <span data-ttu-id="c0c85-113">Označuje, že aktivita je naplánován pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="c0c85-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c0c85-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c0c85-114">Message</span></span>  
 <span data-ttu-id="c0c85-115">Nadřazená aktivita %1, DisplayName: %2, identifikátor InstanceId: '%3' naplánované podřízené aktivity "%4", DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c0c85-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c0c85-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c0c85-116">Details</span></span>  
  
|<span data-ttu-id="c0c85-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="c0c85-117">Data Item Name</span></span>|<span data-ttu-id="c0c85-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="c0c85-118">Data Item Type</span></span>|<span data-ttu-id="c0c85-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c85-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c0c85-120">Nadřazená aktivita</span><span class="sxs-lookup"><span data-stu-id="c0c85-120">ParentActivity</span></span>|<span data-ttu-id="c0c85-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-121">xs:string</span></span>|<span data-ttu-id="c0c85-122">Název typu nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="c0c85-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c0c85-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c0c85-123">ParentDisplayName</span></span>|<span data-ttu-id="c0c85-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-124">xs:string</span></span>|<span data-ttu-id="c0c85-125">Zobrazovaný název nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="c0c85-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c0c85-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c0c85-126">ParentInstanceId</span></span>|<span data-ttu-id="c0c85-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-127">xs:string</span></span>|<span data-ttu-id="c0c85-128">Id instance nadřazené aktivity.</span><span class="sxs-lookup"><span data-stu-id="c0c85-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c0c85-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="c0c85-129">ChildActivity</span></span>|<span data-ttu-id="c0c85-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-130">xs:string</span></span>|<span data-ttu-id="c0c85-131">Název typu naplánované podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="c0c85-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c0c85-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="c0c85-132">ChildDisplayName</span></span>|<span data-ttu-id="c0c85-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-133">xs:string</span></span>|<span data-ttu-id="c0c85-134">Zobrazovaný název naplánované podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="c0c85-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c0c85-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="c0c85-135">ChildInstanceId</span></span>|<span data-ttu-id="c0c85-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-136">xs:string</span></span>|<span data-ttu-id="c0c85-137">Id instance plánované podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="c0c85-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c0c85-138">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c0c85-138">AppDomain</span></span>|<span data-ttu-id="c0c85-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="c0c85-139">xs:string</span></span>|<span data-ttu-id="c0c85-140">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c0c85-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
