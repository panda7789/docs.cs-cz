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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="454bc-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="454bc-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="454bc-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="454bc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="454bc-104">ID</span><span class="sxs-lookup"><span data-stu-id="454bc-104">ID</span></span>|<span data-ttu-id="454bc-105">1032</span><span class="sxs-lookup"><span data-stu-id="454bc-105">1032</span></span>|  
|<span data-ttu-id="454bc-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="454bc-106">Keywords</span></span>|<span data-ttu-id="454bc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="454bc-107">WFRuntime</span></span>|  
|<span data-ttu-id="454bc-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="454bc-108">Level</span></span>|<span data-ttu-id="454bc-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="454bc-109">Verbose</span></span>|  
|<span data-ttu-id="454bc-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="454bc-110">Channel</span></span>|<span data-ttu-id="454bc-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="454bc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="454bc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="454bc-112">Description</span></span>  
 <span data-ttu-id="454bc-113">Označuje, že bylo naplánováno RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="454bc-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="454bc-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="454bc-114">Message</span></span>  
 <span data-ttu-id="454bc-115">Modul runtime pracovní položky bylo naplánováno aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="454bc-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="454bc-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="454bc-116">Details</span></span>  
  
|<span data-ttu-id="454bc-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="454bc-117">Data Item Name</span></span>|<span data-ttu-id="454bc-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="454bc-118">Data Item Type</span></span>|<span data-ttu-id="454bc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="454bc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="454bc-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="454bc-120">Activity</span></span>|<span data-ttu-id="454bc-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="454bc-121">xs:string</span></span>|<span data-ttu-id="454bc-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="454bc-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="454bc-123">displayName</span><span class="sxs-lookup"><span data-stu-id="454bc-123">DisplayName</span></span>|<span data-ttu-id="454bc-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="454bc-124">xs:string</span></span>|<span data-ttu-id="454bc-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="454bc-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="454bc-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="454bc-126">InstanceId</span></span>|<span data-ttu-id="454bc-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="454bc-127">xs:string</span></span>|<span data-ttu-id="454bc-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="454bc-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="454bc-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="454bc-129">AppDomain</span></span>|<span data-ttu-id="454bc-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="454bc-130">xs:string</span></span>|<span data-ttu-id="454bc-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="454bc-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
