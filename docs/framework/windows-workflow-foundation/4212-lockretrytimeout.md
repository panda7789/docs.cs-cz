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
ms.openlocfilehash: abe1f560cc984551f069a75873a7e5545aec03cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="0e804-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="0e804-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="0e804-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0e804-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e804-104">ID</span><span class="sxs-lookup"><span data-stu-id="0e804-104">ID</span></span>|<span data-ttu-id="0e804-105">4212</span><span class="sxs-lookup"><span data-stu-id="0e804-105">4212</span></span>|  
|<span data-ttu-id="0e804-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0e804-106">Keywords</span></span>|<span data-ttu-id="0e804-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0e804-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0e804-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0e804-108">Level</span></span>|<span data-ttu-id="0e804-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="0e804-109">Warning</span></span>|  
|<span data-ttu-id="0e804-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0e804-110">Channel</span></span>|<span data-ttu-id="0e804-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="0e804-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0e804-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0e804-112">Description</span></span>  
 <span data-ttu-id="0e804-113">Zprostředkovatel SQL došlo k vypršení časového limitu při pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="0e804-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0e804-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0e804-114">Message</span></span>  
 <span data-ttu-id="0e804-115">Časový limit pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="0e804-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="0e804-116">Operace nebyla dokončena v přiděleném časovém limitu % 1.</span><span class="sxs-lookup"><span data-stu-id="0e804-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="0e804-117">Čas přidělený tato operace mohla být část delší časový limit.</span><span class="sxs-lookup"><span data-stu-id="0e804-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0e804-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0e804-118">Details</span></span>  
  
|<span data-ttu-id="0e804-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0e804-119">Data Item Name</span></span>|<span data-ttu-id="0e804-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="0e804-120">Data Item Type</span></span>|<span data-ttu-id="0e804-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0e804-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0e804-122">Zpoždění</span><span class="sxs-lookup"><span data-stu-id="0e804-122">Delay</span></span>|<span data-ttu-id="0e804-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="0e804-123">xs:string</span></span>|<span data-ttu-id="0e804-124">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="0e804-124">The delay between retries.</span></span>|  
|<span data-ttu-id="0e804-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="0e804-125">AppDomain</span></span>|<span data-ttu-id="0e804-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="0e804-126">xs:string</span></span>|<span data-ttu-id="0e804-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0e804-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
