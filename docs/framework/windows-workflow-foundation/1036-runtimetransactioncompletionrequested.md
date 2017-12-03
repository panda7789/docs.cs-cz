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
ms.openlocfilehash: 112063d5cd550f438541b2d775eaa49124d9cc02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="b7a50-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="b7a50-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="b7a50-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7a50-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7a50-104">ID</span><span class="sxs-lookup"><span data-stu-id="b7a50-104">ID</span></span>|<span data-ttu-id="b7a50-105">1036</span><span class="sxs-lookup"><span data-stu-id="b7a50-105">1036</span></span>|  
|<span data-ttu-id="b7a50-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b7a50-106">Keywords</span></span>|<span data-ttu-id="b7a50-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b7a50-107">WFRuntime</span></span>|  
|<span data-ttu-id="b7a50-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b7a50-108">Level</span></span>|<span data-ttu-id="b7a50-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b7a50-109">Verbose</span></span>|  
|<span data-ttu-id="b7a50-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b7a50-110">Channel</span></span>|<span data-ttu-id="b7a50-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b7a50-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7a50-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b7a50-112">Description</span></span>  
 <span data-ttu-id="b7a50-113">Označuje, že aktivita má naplánované na dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b7a50-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7a50-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b7a50-114">Message</span></span>  
 <span data-ttu-id="b7a50-115">Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' má naplánované dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b7a50-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7a50-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b7a50-116">Details</span></span>  
  
|<span data-ttu-id="b7a50-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b7a50-117">Data Item Name</span></span>|<span data-ttu-id="b7a50-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b7a50-118">Data Item Type</span></span>|<span data-ttu-id="b7a50-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b7a50-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7a50-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="b7a50-120">Activity</span></span>|<span data-ttu-id="b7a50-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7a50-121">xs:string</span></span>|<span data-ttu-id="b7a50-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7a50-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b7a50-123">displayName</span><span class="sxs-lookup"><span data-stu-id="b7a50-123">DisplayName</span></span>|<span data-ttu-id="b7a50-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7a50-124">xs:string</span></span>|<span data-ttu-id="b7a50-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7a50-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b7a50-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="b7a50-126">InstanceId</span></span>|<span data-ttu-id="b7a50-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7a50-127">xs:string</span></span>|<span data-ttu-id="b7a50-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="b7a50-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b7a50-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b7a50-129">AppDomain</span></span>|<span data-ttu-id="b7a50-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7a50-130">xs:string</span></span>|<span data-ttu-id="b7a50-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b7a50-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
