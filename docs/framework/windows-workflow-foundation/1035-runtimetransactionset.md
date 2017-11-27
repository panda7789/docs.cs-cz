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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="56342-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="56342-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="56342-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="56342-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56342-104">ID</span><span class="sxs-lookup"><span data-stu-id="56342-104">ID</span></span>|<span data-ttu-id="56342-105">1035</span><span class="sxs-lookup"><span data-stu-id="56342-105">1035</span></span>|  
|<span data-ttu-id="56342-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="56342-106">Keywords</span></span>|<span data-ttu-id="56342-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="56342-107">WFRuntime</span></span>|  
|<span data-ttu-id="56342-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="56342-108">Level</span></span>|<span data-ttu-id="56342-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="56342-109">Verbose</span></span>|  
|<span data-ttu-id="56342-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="56342-110">Channel</span></span>|<span data-ttu-id="56342-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="56342-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="56342-112">Popis</span><span class="sxs-lookup"><span data-stu-id="56342-112">Description</span></span>  
 <span data-ttu-id="56342-113">Značí, že aktivita má nastaven runtime transakce.</span><span class="sxs-lookup"><span data-stu-id="56342-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="56342-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="56342-114">Message</span></span>  
 <span data-ttu-id="56342-115">Modul runtime transakce byla nastavena pomocí aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="56342-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="56342-116">Provádění izolované k aktivitě %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="56342-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="56342-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="56342-117">Details</span></span>  
  
|<span data-ttu-id="56342-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="56342-118">Data Item Name</span></span>|<span data-ttu-id="56342-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="56342-119">Data Item Type</span></span>|<span data-ttu-id="56342-120">Popis</span><span class="sxs-lookup"><span data-stu-id="56342-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="56342-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="56342-121">Activity</span></span>|<span data-ttu-id="56342-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-122">xs:string</span></span>|<span data-ttu-id="56342-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="56342-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="56342-124">displayName</span><span class="sxs-lookup"><span data-stu-id="56342-124">DisplayName</span></span>|<span data-ttu-id="56342-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-125">xs:string</span></span>|<span data-ttu-id="56342-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="56342-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="56342-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="56342-127">InstanceId</span></span>|<span data-ttu-id="56342-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-128">xs:string</span></span>|<span data-ttu-id="56342-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="56342-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="56342-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="56342-130">IsolatedActivity</span></span>|<span data-ttu-id="56342-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-131">xs:string</span></span>|<span data-ttu-id="56342-132">Název typu aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="56342-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="56342-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="56342-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="56342-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-134">xs:string</span></span>|<span data-ttu-id="56342-135">Zobrazovaný název aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="56342-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="56342-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="56342-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="56342-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-137">xs:string</span></span>|<span data-ttu-id="56342-138">Id instance aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="56342-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="56342-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="56342-139">AppDomain</span></span>|<span data-ttu-id="56342-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="56342-140">xs:string</span></span>|<span data-ttu-id="56342-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="56342-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
