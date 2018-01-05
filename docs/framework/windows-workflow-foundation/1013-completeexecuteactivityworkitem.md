---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dc72081d2e9b89a9979651bb02b6c06448e30e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="16712-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="16712-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="16712-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="16712-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16712-104">ID</span><span class="sxs-lookup"><span data-stu-id="16712-104">ID</span></span>|<span data-ttu-id="16712-105">1013</span><span class="sxs-lookup"><span data-stu-id="16712-105">1013</span></span>|  
|<span data-ttu-id="16712-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="16712-106">Keywords</span></span>|<span data-ttu-id="16712-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="16712-107">WFRuntime</span></span>|  
|<span data-ttu-id="16712-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="16712-108">Level</span></span>|<span data-ttu-id="16712-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="16712-109">Verbose</span></span>|  
|<span data-ttu-id="16712-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="16712-110">Channel</span></span>|<span data-ttu-id="16712-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="16712-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16712-112">Popis</span><span class="sxs-lookup"><span data-stu-id="16712-112">Description</span></span>  
 <span data-ttu-id="16712-113">Označuje, že že executeactivityworkitem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="16712-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="16712-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="16712-114">Message</span></span>  
 <span data-ttu-id="16712-115">ExecuteActivityWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="16712-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16712-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="16712-116">Details</span></span>  
  
|<span data-ttu-id="16712-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="16712-117">Data Item Name</span></span>|<span data-ttu-id="16712-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="16712-118">Data Item Type</span></span>|<span data-ttu-id="16712-119">Popis</span><span class="sxs-lookup"><span data-stu-id="16712-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16712-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="16712-120">Activity</span></span>|<span data-ttu-id="16712-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="16712-121">xs:string</span></span>|<span data-ttu-id="16712-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="16712-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="16712-123">displayName</span><span class="sxs-lookup"><span data-stu-id="16712-123">DisplayName</span></span>|<span data-ttu-id="16712-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="16712-124">xs:string</span></span>|<span data-ttu-id="16712-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="16712-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="16712-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="16712-126">InstanceId</span></span>|<span data-ttu-id="16712-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="16712-127">xs:string</span></span>|<span data-ttu-id="16712-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="16712-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="16712-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="16712-129">AppDomain</span></span>|<span data-ttu-id="16712-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="16712-130">xs:string</span></span>|<span data-ttu-id="16712-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="16712-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
