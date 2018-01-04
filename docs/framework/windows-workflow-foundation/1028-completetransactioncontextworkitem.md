---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cd2ee443d6c521f168a170a1079eb4e9657e2dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="3cdde-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="3cdde-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3cdde-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3cdde-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cdde-104">ID</span><span class="sxs-lookup"><span data-stu-id="3cdde-104">ID</span></span>|<span data-ttu-id="3cdde-105">1028</span><span class="sxs-lookup"><span data-stu-id="3cdde-105">1028</span></span>|  
|<span data-ttu-id="3cdde-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3cdde-106">Keywords</span></span>|<span data-ttu-id="3cdde-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3cdde-107">WFRuntime</span></span>|  
|<span data-ttu-id="3cdde-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3cdde-108">Level</span></span>|<span data-ttu-id="3cdde-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="3cdde-109">Verbose</span></span>|  
|<span data-ttu-id="3cdde-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3cdde-110">Channel</span></span>|<span data-ttu-id="3cdde-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="3cdde-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3cdde-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3cdde-112">Description</span></span>  
 <span data-ttu-id="3cdde-113">Označuje, že je dokončená TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="3cdde-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3cdde-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3cdde-114">Message</span></span>  
 <span data-ttu-id="3cdde-115">TransactionContextWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3cdde-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3cdde-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3cdde-116">Details</span></span>  
  
|<span data-ttu-id="3cdde-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3cdde-117">Data Item Name</span></span>|<span data-ttu-id="3cdde-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="3cdde-118">Data Item Type</span></span>|<span data-ttu-id="3cdde-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3cdde-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3cdde-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="3cdde-120">Activity</span></span>|<span data-ttu-id="3cdde-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="3cdde-121">xs:string</span></span>|<span data-ttu-id="3cdde-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="3cdde-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3cdde-123">displayName</span><span class="sxs-lookup"><span data-stu-id="3cdde-123">DisplayName</span></span>|<span data-ttu-id="3cdde-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="3cdde-124">xs:string</span></span>|<span data-ttu-id="3cdde-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="3cdde-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3cdde-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="3cdde-126">InstanceId</span></span>|<span data-ttu-id="3cdde-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="3cdde-127">xs:string</span></span>|<span data-ttu-id="3cdde-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="3cdde-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3cdde-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="3cdde-129">AppDomain</span></span>|<span data-ttu-id="3cdde-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="3cdde-130">xs:string</span></span>|<span data-ttu-id="3cdde-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3cdde-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
