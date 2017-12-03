---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="8cfcb-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="8cfcb-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="8cfcb-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8cfcb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8cfcb-104">ID</span><span class="sxs-lookup"><span data-stu-id="8cfcb-104">ID</span></span>|<span data-ttu-id="8cfcb-105">4211</span><span class="sxs-lookup"><span data-stu-id="8cfcb-105">4211</span></span>|  
|<span data-ttu-id="8cfcb-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8cfcb-106">Keywords</span></span>|<span data-ttu-id="8cfcb-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="8cfcb-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8cfcb-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8cfcb-108">Level</span></span>|<span data-ttu-id="8cfcb-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="8cfcb-109">Warning</span></span>|  
|<span data-ttu-id="8cfcb-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8cfcb-110">Channel</span></span>|<span data-ttu-id="8cfcb-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="8cfcb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8cfcb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8cfcb-112">Description</span></span>  
 <span data-ttu-id="8cfcb-113">Určuje řazení do fronty opakování SQL.</span><span class="sxs-lookup"><span data-stu-id="8cfcb-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8cfcb-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8cfcb-114">Message</span></span>  
 <span data-ttu-id="8cfcb-115">Řízení front opakování SQL s zpoždění %1 milisekundách.</span><span class="sxs-lookup"><span data-stu-id="8cfcb-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8cfcb-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8cfcb-116">Details</span></span>  
  
|<span data-ttu-id="8cfcb-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8cfcb-117">Data Item Name</span></span>|<span data-ttu-id="8cfcb-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8cfcb-118">Data Item Type</span></span>|<span data-ttu-id="8cfcb-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8cfcb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8cfcb-120">Zpoždění</span><span class="sxs-lookup"><span data-stu-id="8cfcb-120">Delay</span></span>|<span data-ttu-id="8cfcb-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="8cfcb-121">xs:string</span></span>|<span data-ttu-id="8cfcb-122">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="8cfcb-122">The delay between retries.</span></span>|  
|<span data-ttu-id="8cfcb-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8cfcb-123">AppDomain</span></span>|<span data-ttu-id="8cfcb-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="8cfcb-124">xs:string</span></span>|<span data-ttu-id="8cfcb-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8cfcb-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
