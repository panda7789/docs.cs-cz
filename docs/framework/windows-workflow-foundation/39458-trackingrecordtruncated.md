---
title: 39458 – TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774410"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="961f5-102">39458 – TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="961f5-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="961f5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="961f5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="961f5-104">ID</span><span class="sxs-lookup"><span data-stu-id="961f5-104">ID</span></span>|<span data-ttu-id="961f5-105">39458</span><span class="sxs-lookup"><span data-stu-id="961f5-105">39458</span></span>|  
|<span data-ttu-id="961f5-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="961f5-106">Keywords</span></span>|<span data-ttu-id="961f5-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="961f5-107">WFTracking</span></span>|  
|<span data-ttu-id="961f5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="961f5-108">Level</span></span>|<span data-ttu-id="961f5-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="961f5-109">Warning</span></span>|  
|<span data-ttu-id="961f5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="961f5-110">Channel</span></span>|<span data-ttu-id="961f5-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="961f5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="961f5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="961f5-112">Description</span></span>  
 <span data-ttu-id="961f5-113">Označuje, že byl zkrácen záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="961f5-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="961f5-114">Byly odebrány proměnné, poznámky a uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="961f5-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="961f5-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="961f5-115">Message</span></span>  
 <span data-ttu-id="961f5-116">Oříznutá záznam sledování %1 byl zapsán do relace ETW s poskytovatelem %2.</span><span class="sxs-lookup"><span data-stu-id="961f5-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="961f5-117">Byly odebrány proměnné, poznámky a uživatelská data</span><span class="sxs-lookup"><span data-stu-id="961f5-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="961f5-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="961f5-118">Details</span></span>  
  
|<span data-ttu-id="961f5-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="961f5-119">Data Item Name</span></span>|<span data-ttu-id="961f5-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="961f5-120">Data Item Type</span></span>|<span data-ttu-id="961f5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="961f5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="961f5-122">Číslo záznamu</span><span class="sxs-lookup"><span data-stu-id="961f5-122">RecordNumber</span></span>|<span data-ttu-id="961f5-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="961f5-123">xs:string</span></span>|<span data-ttu-id="961f5-124">Počet záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="961f5-124">The tracking record number.</span></span>|  
|<span data-ttu-id="961f5-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="961f5-125">ProviderId</span></span>|<span data-ttu-id="961f5-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="961f5-126">xs:string</span></span>|<span data-ttu-id="961f5-127">Id poskytovatele trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="961f5-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="961f5-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="961f5-128">AppDomain</span></span>|<span data-ttu-id="961f5-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="961f5-129">xs:string</span></span>|<span data-ttu-id="961f5-130">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="961f5-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
