---
title: 1011 – ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982251"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="6cbee-102">1011 – ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="6cbee-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6cbee-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6cbee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cbee-104">ID</span><span class="sxs-lookup"><span data-stu-id="6cbee-104">ID</span></span>|<span data-ttu-id="6cbee-105">1011</span><span class="sxs-lookup"><span data-stu-id="6cbee-105">1011</span></span>|  
|<span data-ttu-id="6cbee-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6cbee-106">Keywords</span></span>|<span data-ttu-id="6cbee-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6cbee-107">WFRuntime</span></span>|  
|<span data-ttu-id="6cbee-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6cbee-108">Level</span></span>|<span data-ttu-id="6cbee-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6cbee-109">Verbose</span></span>|  
|<span data-ttu-id="6cbee-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6cbee-110">Channel</span></span>|<span data-ttu-id="6cbee-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="6cbee-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6cbee-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6cbee-112">Description</span></span>  
 <span data-ttu-id="6cbee-113">Označuje, že položka ExecuteActivityWorkItem byla plánována.</span><span class="sxs-lookup"><span data-stu-id="6cbee-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6cbee-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6cbee-114">Message</span></span>  
 <span data-ttu-id="6cbee-115">Položka ExecuteActivityWorkItem byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="6cbee-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6cbee-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6cbee-116">Details</span></span>  
  
|<span data-ttu-id="6cbee-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6cbee-117">Data Item Name</span></span>|<span data-ttu-id="6cbee-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="6cbee-118">Data Item Type</span></span>|<span data-ttu-id="6cbee-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6cbee-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6cbee-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="6cbee-120">Activity</span></span>|<span data-ttu-id="6cbee-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cbee-121">xs:string</span></span>|<span data-ttu-id="6cbee-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="6cbee-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="6cbee-123">displayName</span><span class="sxs-lookup"><span data-stu-id="6cbee-123">DisplayName</span></span>|<span data-ttu-id="6cbee-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cbee-124">xs:string</span></span>|<span data-ttu-id="6cbee-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="6cbee-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="6cbee-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6cbee-126">InstanceId</span></span>|<span data-ttu-id="6cbee-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cbee-127">xs:string</span></span>|<span data-ttu-id="6cbee-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="6cbee-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6cbee-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6cbee-129">AppDomain</span></span>|<span data-ttu-id="6cbee-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cbee-130">xs:string</span></span>|<span data-ttu-id="6cbee-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6cbee-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
