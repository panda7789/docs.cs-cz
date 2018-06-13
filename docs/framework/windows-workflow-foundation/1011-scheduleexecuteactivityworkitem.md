---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509612"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="462b2-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="462b2-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="462b2-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="462b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="462b2-104">ID</span><span class="sxs-lookup"><span data-stu-id="462b2-104">ID</span></span>|<span data-ttu-id="462b2-105">1011</span><span class="sxs-lookup"><span data-stu-id="462b2-105">1011</span></span>|  
|<span data-ttu-id="462b2-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="462b2-106">Keywords</span></span>|<span data-ttu-id="462b2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="462b2-107">WFRuntime</span></span>|  
|<span data-ttu-id="462b2-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="462b2-108">Level</span></span>|<span data-ttu-id="462b2-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="462b2-109">Verbose</span></span>|  
|<span data-ttu-id="462b2-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="462b2-110">Channel</span></span>|<span data-ttu-id="462b2-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="462b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="462b2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="462b2-112">Description</span></span>  
 <span data-ttu-id="462b2-113">Označuje, že bylo naplánováno ExecuteActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="462b2-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="462b2-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="462b2-114">Message</span></span>  
 <span data-ttu-id="462b2-115">Bylo naplánováno ExecuteActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="462b2-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="462b2-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="462b2-116">Details</span></span>  
  
|<span data-ttu-id="462b2-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="462b2-117">Data Item Name</span></span>|<span data-ttu-id="462b2-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="462b2-118">Data Item Type</span></span>|<span data-ttu-id="462b2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="462b2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="462b2-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="462b2-120">Activity</span></span>|<span data-ttu-id="462b2-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="462b2-121">xs:string</span></span>|<span data-ttu-id="462b2-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="462b2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="462b2-123">displayName</span><span class="sxs-lookup"><span data-stu-id="462b2-123">DisplayName</span></span>|<span data-ttu-id="462b2-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="462b2-124">xs:string</span></span>|<span data-ttu-id="462b2-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="462b2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="462b2-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="462b2-126">InstanceId</span></span>|<span data-ttu-id="462b2-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="462b2-127">xs:string</span></span>|<span data-ttu-id="462b2-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="462b2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="462b2-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="462b2-129">AppDomain</span></span>|<span data-ttu-id="462b2-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="462b2-130">xs:string</span></span>|<span data-ttu-id="462b2-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="462b2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
