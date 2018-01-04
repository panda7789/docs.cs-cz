---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 378f756003e45905e3697e2e9470aa1e582a2ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="76a06-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="76a06-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="76a06-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="76a06-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76a06-104">ID</span><span class="sxs-lookup"><span data-stu-id="76a06-104">ID</span></span>|<span data-ttu-id="76a06-105">1019</span><span class="sxs-lookup"><span data-stu-id="76a06-105">1019</span></span>|  
|<span data-ttu-id="76a06-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="76a06-106">Keywords</span></span>|<span data-ttu-id="76a06-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="76a06-107">WFRuntime</span></span>|  
|<span data-ttu-id="76a06-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="76a06-108">Level</span></span>|<span data-ttu-id="76a06-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="76a06-109">Verbose</span></span>|  
|<span data-ttu-id="76a06-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="76a06-110">Channel</span></span>|<span data-ttu-id="76a06-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="76a06-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="76a06-112">Popis</span><span class="sxs-lookup"><span data-stu-id="76a06-112">Description</span></span>  
 <span data-ttu-id="76a06-113">Označuje, že je dokončená CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="76a06-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="76a06-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="76a06-114">Message</span></span>  
 <span data-ttu-id="76a06-115">CancelActivityWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="76a06-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="76a06-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="76a06-116">Details</span></span>  
  
|<span data-ttu-id="76a06-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="76a06-117">Data Item Name</span></span>|<span data-ttu-id="76a06-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="76a06-118">Data Item Type</span></span>|<span data-ttu-id="76a06-119">Popis</span><span class="sxs-lookup"><span data-stu-id="76a06-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="76a06-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="76a06-120">Activity</span></span>|<span data-ttu-id="76a06-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="76a06-121">xs:string</span></span>|<span data-ttu-id="76a06-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="76a06-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="76a06-123">displayName</span><span class="sxs-lookup"><span data-stu-id="76a06-123">DisplayName</span></span>|<span data-ttu-id="76a06-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="76a06-124">xs:string</span></span>|<span data-ttu-id="76a06-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="76a06-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="76a06-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="76a06-126">InstanceId</span></span>|<span data-ttu-id="76a06-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="76a06-127">xs:string</span></span>|<span data-ttu-id="76a06-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="76a06-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="76a06-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="76a06-129">AppDomain</span></span>|<span data-ttu-id="76a06-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="76a06-130">xs:string</span></span>|<span data-ttu-id="76a06-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="76a06-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
