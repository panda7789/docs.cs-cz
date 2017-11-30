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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 897e6ef8b739654a61058106966c870c47f8129a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="5175d-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="5175d-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="5175d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5175d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5175d-104">ID</span><span class="sxs-lookup"><span data-stu-id="5175d-104">ID</span></span>|<span data-ttu-id="5175d-105">4212</span><span class="sxs-lookup"><span data-stu-id="5175d-105">4212</span></span>|  
|<span data-ttu-id="5175d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5175d-106">Keywords</span></span>|<span data-ttu-id="5175d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5175d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5175d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5175d-108">Level</span></span>|<span data-ttu-id="5175d-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="5175d-109">Warning</span></span>|  
|<span data-ttu-id="5175d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5175d-110">Channel</span></span>|<span data-ttu-id="5175d-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="5175d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5175d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5175d-112">Description</span></span>  
 <span data-ttu-id="5175d-113">Zprostředkovatel SQL došlo k vypršení časového limitu při pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="5175d-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5175d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5175d-114">Message</span></span>  
 <span data-ttu-id="5175d-115">Časový limit pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="5175d-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="5175d-116">Operace nebyla dokončena v přiděleném časovém limitu % 1.</span><span class="sxs-lookup"><span data-stu-id="5175d-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="5175d-117">Čas přidělený tato operace mohla být část delší časový limit.</span><span class="sxs-lookup"><span data-stu-id="5175d-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5175d-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5175d-118">Details</span></span>  
  
|<span data-ttu-id="5175d-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5175d-119">Data Item Name</span></span>|<span data-ttu-id="5175d-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5175d-120">Data Item Type</span></span>|<span data-ttu-id="5175d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5175d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5175d-122">Zpoždění</span><span class="sxs-lookup"><span data-stu-id="5175d-122">Delay</span></span>|<span data-ttu-id="5175d-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="5175d-123">xs:string</span></span>|<span data-ttu-id="5175d-124">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="5175d-124">The delay between retries.</span></span>|  
|<span data-ttu-id="5175d-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5175d-125">AppDomain</span></span>|<span data-ttu-id="5175d-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="5175d-126">xs:string</span></span>|<span data-ttu-id="5175d-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5175d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
