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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="57a30-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="57a30-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="57a30-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57a30-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57a30-104">ID</span><span class="sxs-lookup"><span data-stu-id="57a30-104">ID</span></span>|<span data-ttu-id="57a30-105">1034</span><span class="sxs-lookup"><span data-stu-id="57a30-105">1034</span></span>|  
|<span data-ttu-id="57a30-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="57a30-106">Keywords</span></span>|<span data-ttu-id="57a30-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="57a30-107">WFRuntime</span></span>|  
|<span data-ttu-id="57a30-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="57a30-108">Level</span></span>|<span data-ttu-id="57a30-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="57a30-109">Verbose</span></span>|  
|<span data-ttu-id="57a30-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="57a30-110">Channel</span></span>|<span data-ttu-id="57a30-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="57a30-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57a30-112">Popis</span><span class="sxs-lookup"><span data-stu-id="57a30-112">Description</span></span>  
 <span data-ttu-id="57a30-113">Označuje, že je dokončená RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="57a30-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57a30-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="57a30-114">Message</span></span>  
 <span data-ttu-id="57a30-115">Pracovní položky modulu runtime dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="57a30-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57a30-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="57a30-116">Details</span></span>  
  
|<span data-ttu-id="57a30-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="57a30-117">Data Item Name</span></span>|<span data-ttu-id="57a30-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="57a30-118">Data Item Type</span></span>|<span data-ttu-id="57a30-119">Popis</span><span class="sxs-lookup"><span data-stu-id="57a30-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57a30-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="57a30-120">Activity</span></span>|<span data-ttu-id="57a30-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="57a30-121">xs:string</span></span>|<span data-ttu-id="57a30-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="57a30-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="57a30-123">displayName</span><span class="sxs-lookup"><span data-stu-id="57a30-123">DisplayName</span></span>|<span data-ttu-id="57a30-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="57a30-124">xs:string</span></span>|<span data-ttu-id="57a30-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="57a30-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="57a30-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="57a30-126">InstanceId</span></span>|<span data-ttu-id="57a30-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="57a30-127">xs:string</span></span>|<span data-ttu-id="57a30-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="57a30-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="57a30-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="57a30-129">AppDomain</span></span>|<span data-ttu-id="57a30-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="57a30-130">xs:string</span></span>|<span data-ttu-id="57a30-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="57a30-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
