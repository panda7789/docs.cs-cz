---
title: 2577 – TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755620"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="e2258-102">2577 – TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="e2258-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="e2258-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e2258-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2258-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2258-104">ID</span></span>|<span data-ttu-id="e2258-105">2577</span><span class="sxs-lookup"><span data-stu-id="e2258-105">2577</span></span>|  
|<span data-ttu-id="e2258-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e2258-106">Keywords</span></span>|<span data-ttu-id="e2258-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="e2258-107">WFActivities</span></span>|  
|<span data-ttu-id="e2258-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e2258-108">Level</span></span>|<span data-ttu-id="e2258-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="e2258-109">Warning</span></span>|  
|<span data-ttu-id="e2258-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e2258-110">Channel</span></span>|<span data-ttu-id="e2258-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e2258-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2258-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e2258-112">Description</span></span>  
 <span data-ttu-id="e2258-113">Označuje, že podřízená aktivita aktivity TryCatch generovala výjimku při stornování.</span><span class="sxs-lookup"><span data-stu-id="e2258-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2258-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e2258-114">Message</span></span>  
 <span data-ttu-id="e2258-115">Podřízená aktivita aktivity TryCatch '%1' vyvolal výjimku při stornování.</span><span class="sxs-lookup"><span data-stu-id="e2258-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2258-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e2258-116">Details</span></span>  
  
|<span data-ttu-id="e2258-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e2258-117">Data Item Name</span></span>|<span data-ttu-id="e2258-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e2258-118">Data Item Type</span></span>|<span data-ttu-id="e2258-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e2258-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2258-120">displayName</span><span class="sxs-lookup"><span data-stu-id="e2258-120">DisplayName</span></span>|<span data-ttu-id="e2258-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2258-121">xs:string</span></span>|<span data-ttu-id="e2258-122">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="e2258-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="e2258-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2258-123">AppDomain</span></span>|<span data-ttu-id="e2258-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2258-124">xs:string</span></span>|<span data-ttu-id="e2258-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2258-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
