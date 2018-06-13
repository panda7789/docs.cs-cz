---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514479"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="ae3d1-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="ae3d1-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="ae3d1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ae3d1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae3d1-104">ID</span><span class="sxs-lookup"><span data-stu-id="ae3d1-104">ID</span></span>|<span data-ttu-id="ae3d1-105">39458</span><span class="sxs-lookup"><span data-stu-id="ae3d1-105">39458</span></span>|  
|<span data-ttu-id="ae3d1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ae3d1-106">Keywords</span></span>|<span data-ttu-id="ae3d1-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ae3d1-107">WFTracking</span></span>|  
|<span data-ttu-id="ae3d1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ae3d1-108">Level</span></span>|<span data-ttu-id="ae3d1-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="ae3d1-109">Warning</span></span>|  
|<span data-ttu-id="ae3d1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ae3d1-110">Channel</span></span>|<span data-ttu-id="ae3d1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ae3d1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae3d1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ae3d1-112">Description</span></span>  
 <span data-ttu-id="ae3d1-113">Označuje, že záznam sledování byla zkrácena.</span><span class="sxs-lookup"><span data-stu-id="ae3d1-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="ae3d1-114">Byly odebrány proměnné a poznámky nebo uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="ae3d1-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae3d1-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ae3d1-115">Message</span></span>  
 <span data-ttu-id="ae3d1-116">Zkrácená sledování záznam %1 zapsána do relace trasování událostí pro Windows pomocí zprostředkovatele %2.</span><span class="sxs-lookup"><span data-stu-id="ae3d1-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="ae3d1-117">Odebrali jsme proměnné a poznámky nebo uživatelská data</span><span class="sxs-lookup"><span data-stu-id="ae3d1-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae3d1-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ae3d1-118">Details</span></span>  
  
|<span data-ttu-id="ae3d1-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ae3d1-119">Data Item Name</span></span>|<span data-ttu-id="ae3d1-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ae3d1-120">Data Item Type</span></span>|<span data-ttu-id="ae3d1-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ae3d1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae3d1-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="ae3d1-122">RecordNumber</span></span>|<span data-ttu-id="ae3d1-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae3d1-123">xs:string</span></span>|<span data-ttu-id="ae3d1-124">Počet záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="ae3d1-124">The tracking record number.</span></span>|  
|<span data-ttu-id="ae3d1-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="ae3d1-125">ProviderId</span></span>|<span data-ttu-id="ae3d1-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae3d1-126">xs:string</span></span>|<span data-ttu-id="ae3d1-127">Id zprostředkovatele trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="ae3d1-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="ae3d1-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ae3d1-128">AppDomain</span></span>|<span data-ttu-id="ae3d1-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae3d1-129">xs:string</span></span>|<span data-ttu-id="ae3d1-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ae3d1-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
