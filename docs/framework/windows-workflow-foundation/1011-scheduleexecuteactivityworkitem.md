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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 498752bfc896891a43a6a2e7a8245c508795c1ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="3bb31-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="3bb31-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3bb31-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3bb31-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bb31-104">ID</span><span class="sxs-lookup"><span data-stu-id="3bb31-104">ID</span></span>|<span data-ttu-id="3bb31-105">1011</span><span class="sxs-lookup"><span data-stu-id="3bb31-105">1011</span></span>|  
|<span data-ttu-id="3bb31-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3bb31-106">Keywords</span></span>|<span data-ttu-id="3bb31-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3bb31-107">WFRuntime</span></span>|  
|<span data-ttu-id="3bb31-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3bb31-108">Level</span></span>|<span data-ttu-id="3bb31-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="3bb31-109">Verbose</span></span>|  
|<span data-ttu-id="3bb31-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3bb31-110">Channel</span></span>|<span data-ttu-id="3bb31-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="3bb31-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3bb31-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3bb31-112">Description</span></span>  
 <span data-ttu-id="3bb31-113">Označuje, že bylo naplánováno ExecuteActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="3bb31-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3bb31-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3bb31-114">Message</span></span>  
 <span data-ttu-id="3bb31-115">Bylo naplánováno ExecuteActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3bb31-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3bb31-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3bb31-116">Details</span></span>  
  
|<span data-ttu-id="3bb31-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3bb31-117">Data Item Name</span></span>|<span data-ttu-id="3bb31-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="3bb31-118">Data Item Type</span></span>|<span data-ttu-id="3bb31-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3bb31-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3bb31-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="3bb31-120">Activity</span></span>|<span data-ttu-id="3bb31-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="3bb31-121">xs:string</span></span>|<span data-ttu-id="3bb31-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="3bb31-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3bb31-123">displayName</span><span class="sxs-lookup"><span data-stu-id="3bb31-123">DisplayName</span></span>|<span data-ttu-id="3bb31-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="3bb31-124">xs:string</span></span>|<span data-ttu-id="3bb31-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="3bb31-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3bb31-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="3bb31-126">InstanceId</span></span>|<span data-ttu-id="3bb31-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="3bb31-127">xs:string</span></span>|<span data-ttu-id="3bb31-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="3bb31-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3bb31-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="3bb31-129">AppDomain</span></span>|<span data-ttu-id="3bb31-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="3bb31-130">xs:string</span></span>|<span data-ttu-id="3bb31-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3bb31-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
