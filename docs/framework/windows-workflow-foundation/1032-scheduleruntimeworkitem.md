---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4de69b1fc2647d7723db8aebb02942938db7478f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="25106-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="25106-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="25106-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25106-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25106-104">ID</span><span class="sxs-lookup"><span data-stu-id="25106-104">ID</span></span>|<span data-ttu-id="25106-105">1032</span><span class="sxs-lookup"><span data-stu-id="25106-105">1032</span></span>|  
|<span data-ttu-id="25106-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="25106-106">Keywords</span></span>|<span data-ttu-id="25106-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="25106-107">WFRuntime</span></span>|  
|<span data-ttu-id="25106-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="25106-108">Level</span></span>|<span data-ttu-id="25106-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="25106-109">Verbose</span></span>|  
|<span data-ttu-id="25106-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="25106-110">Channel</span></span>|<span data-ttu-id="25106-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="25106-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25106-112">Popis</span><span class="sxs-lookup"><span data-stu-id="25106-112">Description</span></span>  
 <span data-ttu-id="25106-113">Označuje, že bylo naplánováno RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="25106-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25106-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="25106-114">Message</span></span>  
 <span data-ttu-id="25106-115">Modul runtime pracovní položky bylo naplánováno aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="25106-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25106-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="25106-116">Details</span></span>  
  
|<span data-ttu-id="25106-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="25106-117">Data Item Name</span></span>|<span data-ttu-id="25106-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="25106-118">Data Item Type</span></span>|<span data-ttu-id="25106-119">Popis</span><span class="sxs-lookup"><span data-stu-id="25106-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25106-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="25106-120">Activity</span></span>|<span data-ttu-id="25106-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="25106-121">xs:string</span></span>|<span data-ttu-id="25106-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="25106-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="25106-123">displayName</span><span class="sxs-lookup"><span data-stu-id="25106-123">DisplayName</span></span>|<span data-ttu-id="25106-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="25106-124">xs:string</span></span>|<span data-ttu-id="25106-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="25106-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="25106-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="25106-126">InstanceId</span></span>|<span data-ttu-id="25106-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="25106-127">xs:string</span></span>|<span data-ttu-id="25106-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="25106-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="25106-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="25106-129">AppDomain</span></span>|<span data-ttu-id="25106-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="25106-130">xs:string</span></span>|<span data-ttu-id="25106-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="25106-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
