---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a8a4ab6212a5e83b59fd7523df9cd875e7b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="bd04b-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="bd04b-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="bd04b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bd04b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd04b-104">ID</span><span class="sxs-lookup"><span data-stu-id="bd04b-104">ID</span></span>|<span data-ttu-id="bd04b-105">1035</span><span class="sxs-lookup"><span data-stu-id="bd04b-105">1035</span></span>|  
|<span data-ttu-id="bd04b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bd04b-106">Keywords</span></span>|<span data-ttu-id="bd04b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bd04b-107">WFRuntime</span></span>|  
|<span data-ttu-id="bd04b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="bd04b-108">Level</span></span>|<span data-ttu-id="bd04b-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="bd04b-109">Verbose</span></span>|  
|<span data-ttu-id="bd04b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="bd04b-110">Channel</span></span>|<span data-ttu-id="bd04b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="bd04b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bd04b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bd04b-112">Description</span></span>  
 <span data-ttu-id="bd04b-113">Značí, že aktivita má nastaven runtime transakce.</span><span class="sxs-lookup"><span data-stu-id="bd04b-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bd04b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bd04b-114">Message</span></span>  
 <span data-ttu-id="bd04b-115">Modul runtime transakce byla nastavena pomocí aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="bd04b-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="bd04b-116">Provádění izolované k aktivitě %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="bd04b-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bd04b-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bd04b-117">Details</span></span>  
  
|<span data-ttu-id="bd04b-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="bd04b-118">Data Item Name</span></span>|<span data-ttu-id="bd04b-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="bd04b-119">Data Item Type</span></span>|<span data-ttu-id="bd04b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bd04b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bd04b-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="bd04b-121">Activity</span></span>|<span data-ttu-id="bd04b-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-122">xs:string</span></span>|<span data-ttu-id="bd04b-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="bd04b-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="bd04b-124">displayName</span><span class="sxs-lookup"><span data-stu-id="bd04b-124">DisplayName</span></span>|<span data-ttu-id="bd04b-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-125">xs:string</span></span>|<span data-ttu-id="bd04b-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="bd04b-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="bd04b-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="bd04b-127">InstanceId</span></span>|<span data-ttu-id="bd04b-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-128">xs:string</span></span>|<span data-ttu-id="bd04b-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="bd04b-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bd04b-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="bd04b-130">IsolatedActivity</span></span>|<span data-ttu-id="bd04b-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-131">xs:string</span></span>|<span data-ttu-id="bd04b-132">Název typu aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="bd04b-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="bd04b-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="bd04b-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="bd04b-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-134">xs:string</span></span>|<span data-ttu-id="bd04b-135">Zobrazovaný název aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="bd04b-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="bd04b-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="bd04b-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="bd04b-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-137">xs:string</span></span>|<span data-ttu-id="bd04b-138">Id instance aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="bd04b-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="bd04b-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bd04b-139">AppDomain</span></span>|<span data-ttu-id="bd04b-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="bd04b-140">xs:string</span></span>|<span data-ttu-id="bd04b-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bd04b-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
