---
title: 4212 – LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774215"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="54d73-102">4212 – LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="54d73-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="54d73-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="54d73-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54d73-104">ID</span><span class="sxs-lookup"><span data-stu-id="54d73-104">ID</span></span>|<span data-ttu-id="54d73-105">4212</span><span class="sxs-lookup"><span data-stu-id="54d73-105">4212</span></span>|  
|<span data-ttu-id="54d73-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="54d73-106">Keywords</span></span>|<span data-ttu-id="54d73-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="54d73-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="54d73-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="54d73-108">Level</span></span>|<span data-ttu-id="54d73-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="54d73-109">Warning</span></span>|  
|<span data-ttu-id="54d73-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="54d73-110">Channel</span></span>|<span data-ttu-id="54d73-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="54d73-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54d73-112">Popis</span><span class="sxs-lookup"><span data-stu-id="54d73-112">Description</span></span>  
 <span data-ttu-id="54d73-113">Zprostředkovatel SQL došlo k pokusu o získání zámku instance vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="54d73-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54d73-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="54d73-114">Message</span></span>  
 <span data-ttu-id="54d73-115">Časový limit pokusu o získání zámku instance.</span><span class="sxs-lookup"><span data-stu-id="54d73-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="54d73-116">Operace nebyla dokončena ve vyhrazeném časovém intervalu %1.</span><span class="sxs-lookup"><span data-stu-id="54d73-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="54d73-117">Čas přidělený této operaci pravděpodobně částí delšího časového limitu.</span><span class="sxs-lookup"><span data-stu-id="54d73-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54d73-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="54d73-118">Details</span></span>  
  
|<span data-ttu-id="54d73-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="54d73-119">Data Item Name</span></span>|<span data-ttu-id="54d73-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="54d73-120">Data Item Type</span></span>|<span data-ttu-id="54d73-121">Popis</span><span class="sxs-lookup"><span data-stu-id="54d73-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54d73-122">zpoždění</span><span class="sxs-lookup"><span data-stu-id="54d73-122">Delay</span></span>|<span data-ttu-id="54d73-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="54d73-123">xs:string</span></span>|<span data-ttu-id="54d73-124">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="54d73-124">The delay between retries.</span></span>|  
|<span data-ttu-id="54d73-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="54d73-125">AppDomain</span></span>|<span data-ttu-id="54d73-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="54d73-126">xs:string</span></span>|<span data-ttu-id="54d73-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="54d73-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
