---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514566"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="32437-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="32437-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="32437-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="32437-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32437-104">ID</span><span class="sxs-lookup"><span data-stu-id="32437-104">ID</span></span>|<span data-ttu-id="32437-105">4211</span><span class="sxs-lookup"><span data-stu-id="32437-105">4211</span></span>|  
|<span data-ttu-id="32437-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="32437-106">Keywords</span></span>|<span data-ttu-id="32437-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="32437-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="32437-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="32437-108">Level</span></span>|<span data-ttu-id="32437-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="32437-109">Warning</span></span>|  
|<span data-ttu-id="32437-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="32437-110">Channel</span></span>|<span data-ttu-id="32437-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="32437-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32437-112">Popis</span><span class="sxs-lookup"><span data-stu-id="32437-112">Description</span></span>  
 <span data-ttu-id="32437-113">Určuje řazení do fronty opakování SQL.</span><span class="sxs-lookup"><span data-stu-id="32437-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32437-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="32437-114">Message</span></span>  
 <span data-ttu-id="32437-115">Řízení front opakování SQL s zpoždění %1 milisekundách.</span><span class="sxs-lookup"><span data-stu-id="32437-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32437-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="32437-116">Details</span></span>  
  
|<span data-ttu-id="32437-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="32437-117">Data Item Name</span></span>|<span data-ttu-id="32437-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="32437-118">Data Item Type</span></span>|<span data-ttu-id="32437-119">Popis</span><span class="sxs-lookup"><span data-stu-id="32437-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32437-120">Zpoždění</span><span class="sxs-lookup"><span data-stu-id="32437-120">Delay</span></span>|<span data-ttu-id="32437-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="32437-121">xs:string</span></span>|<span data-ttu-id="32437-122">Zpoždění mezi opakovanými pokusy.</span><span class="sxs-lookup"><span data-stu-id="32437-122">The delay between retries.</span></span>|  
|<span data-ttu-id="32437-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="32437-123">AppDomain</span></span>|<span data-ttu-id="32437-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="32437-124">xs:string</span></span>|<span data-ttu-id="32437-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="32437-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
