---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="b2393-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="b2393-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="b2393-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b2393-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2393-104">ID</span><span class="sxs-lookup"><span data-stu-id="b2393-104">ID</span></span>|<span data-ttu-id="b2393-105">1036</span><span class="sxs-lookup"><span data-stu-id="b2393-105">1036</span></span>|  
|<span data-ttu-id="b2393-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b2393-106">Keywords</span></span>|<span data-ttu-id="b2393-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b2393-107">WFRuntime</span></span>|  
|<span data-ttu-id="b2393-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b2393-108">Level</span></span>|<span data-ttu-id="b2393-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b2393-109">Verbose</span></span>|  
|<span data-ttu-id="b2393-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b2393-110">Channel</span></span>|<span data-ttu-id="b2393-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b2393-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b2393-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b2393-112">Description</span></span>  
 <span data-ttu-id="b2393-113">Označuje, že aktivita má naplánované na dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b2393-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b2393-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b2393-114">Message</span></span>  
 <span data-ttu-id="b2393-115">Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' má naplánované dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b2393-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b2393-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b2393-116">Details</span></span>  
  
|<span data-ttu-id="b2393-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b2393-117">Data Item Name</span></span>|<span data-ttu-id="b2393-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b2393-118">Data Item Type</span></span>|<span data-ttu-id="b2393-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b2393-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b2393-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="b2393-120">Activity</span></span>|<span data-ttu-id="b2393-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="b2393-121">xs:string</span></span>|<span data-ttu-id="b2393-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2393-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b2393-123">displayName</span><span class="sxs-lookup"><span data-stu-id="b2393-123">DisplayName</span></span>|<span data-ttu-id="b2393-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="b2393-124">xs:string</span></span>|<span data-ttu-id="b2393-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2393-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b2393-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="b2393-126">InstanceId</span></span>|<span data-ttu-id="b2393-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="b2393-127">xs:string</span></span>|<span data-ttu-id="b2393-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2393-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b2393-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b2393-129">AppDomain</span></span>|<span data-ttu-id="b2393-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="b2393-130">xs:string</span></span>|<span data-ttu-id="b2393-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b2393-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
