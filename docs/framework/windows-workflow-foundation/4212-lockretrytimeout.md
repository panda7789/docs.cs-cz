---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f47b383547da5145c5307670fee2eda10fcab402
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="58598-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="58598-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="58598-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58598-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58598-104">ID</span><span class="sxs-lookup"><span data-stu-id="58598-104">ID</span></span>|<span data-ttu-id="58598-105">4212</span><span class="sxs-lookup"><span data-stu-id="58598-105">4212</span></span>|  
|<span data-ttu-id="58598-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="58598-106">Keywords</span></span>|<span data-ttu-id="58598-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="58598-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="58598-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="58598-108">Level</span></span>|<span data-ttu-id="58598-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="58598-109">Warning</span></span>|  
|<span data-ttu-id="58598-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="58598-110">Channel</span></span>|<span data-ttu-id="58598-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="58598-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58598-112">Popis</span><span class="sxs-lookup"><span data-stu-id="58598-112">Description</span></span>  
 <span data-ttu-id="58598-113">Zprostředkovatel SQL došlo k vypršení časového limitu při pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="58598-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58598-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="58598-114">Message</span></span>  
 <span data-ttu-id="58598-115">Časový limit pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="58598-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="58598-116">Operace nebyla dokončena v přiděleném časovém limitu % 1.</span><span class="sxs-lookup"><span data-stu-id="58598-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="58598-117">Čas přidělený tato operace mohla být část delší časový limit.</span><span class="sxs-lookup"><span data-stu-id="58598-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58598-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="58598-118">Details</span></span>  
  
|<span data-ttu-id="58598-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="58598-119">Data Item Name</span></span>|<span data-ttu-id="58598-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="58598-120">Data Item Type</span></span>|<span data-ttu-id="58598-121">Popis</span><span class="sxs-lookup"><span data-stu-id="58598-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58598-122">Zpoždění</span><span class="sxs-lookup"><span data-stu-id="58598-122">Delay</span></span>|<span data-ttu-id="58598-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="58598-123">xs:string</span></span>|<span data-ttu-id="58598-124">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="58598-124">The delay between retries.</span></span>|  
|<span data-ttu-id="58598-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="58598-125">AppDomain</span></span>|<span data-ttu-id="58598-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="58598-126">xs:string</span></span>|<span data-ttu-id="58598-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="58598-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
