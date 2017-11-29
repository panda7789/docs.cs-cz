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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c318ee6509ce8b96a1e7e78a13f4aeb7c76dde6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="2cc2d-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="2cc2d-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="2cc2d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2cc2d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2cc2d-104">ID</span><span class="sxs-lookup"><span data-stu-id="2cc2d-104">ID</span></span>|<span data-ttu-id="2cc2d-105">4211</span><span class="sxs-lookup"><span data-stu-id="2cc2d-105">4211</span></span>|  
|<span data-ttu-id="2cc2d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2cc2d-106">Keywords</span></span>|<span data-ttu-id="2cc2d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="2cc2d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="2cc2d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2cc2d-108">Level</span></span>|<span data-ttu-id="2cc2d-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="2cc2d-109">Warning</span></span>|  
|<span data-ttu-id="2cc2d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2cc2d-110">Channel</span></span>|<span data-ttu-id="2cc2d-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="2cc2d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2cc2d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc2d-112">Description</span></span>  
 <span data-ttu-id="2cc2d-113">Určuje řazení do fronty opakování SQL.</span><span class="sxs-lookup"><span data-stu-id="2cc2d-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2cc2d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2cc2d-114">Message</span></span>  
 <span data-ttu-id="2cc2d-115">Řízení front opakování SQL s zpoždění %1 milisekundách.</span><span class="sxs-lookup"><span data-stu-id="2cc2d-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2cc2d-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2cc2d-116">Details</span></span>  
  
|<span data-ttu-id="2cc2d-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2cc2d-117">Data Item Name</span></span>|<span data-ttu-id="2cc2d-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2cc2d-118">Data Item Type</span></span>|<span data-ttu-id="2cc2d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc2d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2cc2d-120">Zpoždění</span><span class="sxs-lookup"><span data-stu-id="2cc2d-120">Delay</span></span>|<span data-ttu-id="2cc2d-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="2cc2d-121">xs:string</span></span>|<span data-ttu-id="2cc2d-122">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="2cc2d-122">The delay between retries.</span></span>|  
|<span data-ttu-id="2cc2d-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2cc2d-123">AppDomain</span></span>|<span data-ttu-id="2cc2d-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="2cc2d-124">xs:string</span></span>|<span data-ttu-id="2cc2d-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2cc2d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
