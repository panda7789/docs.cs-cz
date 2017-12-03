---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48161ca9c9268fb52c8b8ab9f3fb6d6ce894efa4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="aa13e-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="aa13e-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="aa13e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aa13e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa13e-104">ID</span><span class="sxs-lookup"><span data-stu-id="aa13e-104">ID</span></span>|<span data-ttu-id="aa13e-105">1034</span><span class="sxs-lookup"><span data-stu-id="aa13e-105">1034</span></span>|  
|<span data-ttu-id="aa13e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="aa13e-106">Keywords</span></span>|<span data-ttu-id="aa13e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aa13e-107">WFRuntime</span></span>|  
|<span data-ttu-id="aa13e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="aa13e-108">Level</span></span>|<span data-ttu-id="aa13e-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="aa13e-109">Verbose</span></span>|  
|<span data-ttu-id="aa13e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="aa13e-110">Channel</span></span>|<span data-ttu-id="aa13e-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="aa13e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aa13e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aa13e-112">Description</span></span>  
 <span data-ttu-id="aa13e-113">Označuje, že je dokončená RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="aa13e-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aa13e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="aa13e-114">Message</span></span>  
 <span data-ttu-id="aa13e-115">Pracovní položky modulu runtime dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="aa13e-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aa13e-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aa13e-116">Details</span></span>  
  
|<span data-ttu-id="aa13e-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="aa13e-117">Data Item Name</span></span>|<span data-ttu-id="aa13e-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="aa13e-118">Data Item Type</span></span>|<span data-ttu-id="aa13e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="aa13e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aa13e-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="aa13e-120">Activity</span></span>|<span data-ttu-id="aa13e-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa13e-121">xs:string</span></span>|<span data-ttu-id="aa13e-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="aa13e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="aa13e-123">displayName</span><span class="sxs-lookup"><span data-stu-id="aa13e-123">DisplayName</span></span>|<span data-ttu-id="aa13e-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa13e-124">xs:string</span></span>|<span data-ttu-id="aa13e-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="aa13e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="aa13e-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="aa13e-126">InstanceId</span></span>|<span data-ttu-id="aa13e-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa13e-127">xs:string</span></span>|<span data-ttu-id="aa13e-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="aa13e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="aa13e-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aa13e-129">AppDomain</span></span>|<span data-ttu-id="aa13e-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa13e-130">xs:string</span></span>|<span data-ttu-id="aa13e-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aa13e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
