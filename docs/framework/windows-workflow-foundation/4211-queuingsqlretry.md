---
title: 4211 – QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774241"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="64a70-102">4211 – QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="64a70-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="64a70-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="64a70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64a70-104">ID</span><span class="sxs-lookup"><span data-stu-id="64a70-104">ID</span></span>|<span data-ttu-id="64a70-105">4211</span><span class="sxs-lookup"><span data-stu-id="64a70-105">4211</span></span>|  
|<span data-ttu-id="64a70-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="64a70-106">Keywords</span></span>|<span data-ttu-id="64a70-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="64a70-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="64a70-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="64a70-108">Level</span></span>|<span data-ttu-id="64a70-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="64a70-109">Warning</span></span>|  
|<span data-ttu-id="64a70-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="64a70-110">Channel</span></span>|<span data-ttu-id="64a70-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="64a70-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="64a70-112">Popis</span><span class="sxs-lookup"><span data-stu-id="64a70-112">Description</span></span>  
 <span data-ttu-id="64a70-113">Označuje zařazení opětovného pokusu SQL.</span><span class="sxs-lookup"><span data-stu-id="64a70-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="64a70-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="64a70-114">Message</span></span>  
 <span data-ttu-id="64a70-115">Zařazení opětovného pokusu SQL s prodlevou %1 MS.</span><span class="sxs-lookup"><span data-stu-id="64a70-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="64a70-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="64a70-116">Details</span></span>  
  
|<span data-ttu-id="64a70-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="64a70-117">Data Item Name</span></span>|<span data-ttu-id="64a70-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="64a70-118">Data Item Type</span></span>|<span data-ttu-id="64a70-119">Popis</span><span class="sxs-lookup"><span data-stu-id="64a70-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="64a70-120">zpoždění</span><span class="sxs-lookup"><span data-stu-id="64a70-120">Delay</span></span>|<span data-ttu-id="64a70-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="64a70-121">xs:string</span></span>|<span data-ttu-id="64a70-122">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="64a70-122">The delay between retries.</span></span>|  
|<span data-ttu-id="64a70-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="64a70-123">AppDomain</span></span>|<span data-ttu-id="64a70-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="64a70-124">xs:string</span></span>|<span data-ttu-id="64a70-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="64a70-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
