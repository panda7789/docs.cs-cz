---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec89acb9d83a28ac280db7c3d536bfe63669fa97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="25274-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="25274-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="25274-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25274-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25274-104">ID</span><span class="sxs-lookup"><span data-stu-id="25274-104">ID</span></span>|<span data-ttu-id="25274-105">1011</span><span class="sxs-lookup"><span data-stu-id="25274-105">1011</span></span>|  
|<span data-ttu-id="25274-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="25274-106">Keywords</span></span>|<span data-ttu-id="25274-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="25274-107">WFRuntime</span></span>|  
|<span data-ttu-id="25274-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="25274-108">Level</span></span>|<span data-ttu-id="25274-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="25274-109">Verbose</span></span>|  
|<span data-ttu-id="25274-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="25274-110">Channel</span></span>|<span data-ttu-id="25274-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="25274-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25274-112">Popis</span><span class="sxs-lookup"><span data-stu-id="25274-112">Description</span></span>  
 <span data-ttu-id="25274-113">Označuje, že bylo naplánováno ExecuteActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="25274-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25274-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="25274-114">Message</span></span>  
 <span data-ttu-id="25274-115">Bylo naplánováno ExecuteActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="25274-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25274-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="25274-116">Details</span></span>  
  
|<span data-ttu-id="25274-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="25274-117">Data Item Name</span></span>|<span data-ttu-id="25274-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="25274-118">Data Item Type</span></span>|<span data-ttu-id="25274-119">Popis</span><span class="sxs-lookup"><span data-stu-id="25274-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25274-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="25274-120">Activity</span></span>|<span data-ttu-id="25274-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="25274-121">xs:string</span></span>|<span data-ttu-id="25274-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="25274-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="25274-123">displayName</span><span class="sxs-lookup"><span data-stu-id="25274-123">DisplayName</span></span>|<span data-ttu-id="25274-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="25274-124">xs:string</span></span>|<span data-ttu-id="25274-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="25274-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="25274-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="25274-126">InstanceId</span></span>|<span data-ttu-id="25274-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="25274-127">xs:string</span></span>|<span data-ttu-id="25274-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="25274-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="25274-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="25274-129">AppDomain</span></span>|<span data-ttu-id="25274-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="25274-130">xs:string</span></span>|<span data-ttu-id="25274-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="25274-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
