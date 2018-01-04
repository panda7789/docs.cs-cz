---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c99ddf9c5d4a8fa468303fb198abc349ace6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="682d9-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="682d9-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="682d9-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="682d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="682d9-104">ID</span><span class="sxs-lookup"><span data-stu-id="682d9-104">ID</span></span>|<span data-ttu-id="682d9-105">1026</span><span class="sxs-lookup"><span data-stu-id="682d9-105">1026</span></span>|  
|<span data-ttu-id="682d9-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="682d9-106">Keywords</span></span>|<span data-ttu-id="682d9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="682d9-107">WFRuntime</span></span>|  
|<span data-ttu-id="682d9-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="682d9-108">Level</span></span>|<span data-ttu-id="682d9-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="682d9-109">Verbose</span></span>|  
|<span data-ttu-id="682d9-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="682d9-110">Channel</span></span>|<span data-ttu-id="682d9-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="682d9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="682d9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="682d9-112">Description</span></span>  
 <span data-ttu-id="682d9-113">Označuje, že bylo naplánováno TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="682d9-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="682d9-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="682d9-114">Message</span></span>  
 <span data-ttu-id="682d9-115">Bylo naplánováno TransactionContextWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="682d9-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="682d9-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="682d9-116">Details</span></span>  
  
|<span data-ttu-id="682d9-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="682d9-117">Data Item Name</span></span>|<span data-ttu-id="682d9-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="682d9-118">Data Item Type</span></span>|<span data-ttu-id="682d9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="682d9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="682d9-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="682d9-120">Activity</span></span>|<span data-ttu-id="682d9-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="682d9-121">xs:string</span></span>|<span data-ttu-id="682d9-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="682d9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="682d9-123">displayName</span><span class="sxs-lookup"><span data-stu-id="682d9-123">DisplayName</span></span>|<span data-ttu-id="682d9-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="682d9-124">xs:string</span></span>|<span data-ttu-id="682d9-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="682d9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="682d9-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="682d9-126">InstanceId</span></span>|<span data-ttu-id="682d9-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="682d9-127">xs:string</span></span>|<span data-ttu-id="682d9-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="682d9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="682d9-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="682d9-129">AppDomain</span></span>|<span data-ttu-id="682d9-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="682d9-130">xs:string</span></span>|<span data-ttu-id="682d9-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="682d9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
