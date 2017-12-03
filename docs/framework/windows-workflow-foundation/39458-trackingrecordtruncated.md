---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="a05fb-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="a05fb-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="a05fb-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a05fb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a05fb-104">ID</span><span class="sxs-lookup"><span data-stu-id="a05fb-104">ID</span></span>|<span data-ttu-id="a05fb-105">39458</span><span class="sxs-lookup"><span data-stu-id="a05fb-105">39458</span></span>|  
|<span data-ttu-id="a05fb-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a05fb-106">Keywords</span></span>|<span data-ttu-id="a05fb-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="a05fb-107">WFTracking</span></span>|  
|<span data-ttu-id="a05fb-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a05fb-108">Level</span></span>|<span data-ttu-id="a05fb-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="a05fb-109">Warning</span></span>|  
|<span data-ttu-id="a05fb-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a05fb-110">Channel</span></span>|<span data-ttu-id="a05fb-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a05fb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a05fb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a05fb-112">Description</span></span>  
 <span data-ttu-id="a05fb-113">Označuje, že záznam sledování byla zkrácena.</span><span class="sxs-lookup"><span data-stu-id="a05fb-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="a05fb-114">Byly odebrány proměnné a poznámky nebo uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="a05fb-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a05fb-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a05fb-115">Message</span></span>  
 <span data-ttu-id="a05fb-116">Zkrácená sledování záznam %1 zapsána do relace trasování událostí pro Windows pomocí zprostředkovatele %2.</span><span class="sxs-lookup"><span data-stu-id="a05fb-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="a05fb-117">Odebrali jsme proměnné a poznámky nebo uživatelská data</span><span class="sxs-lookup"><span data-stu-id="a05fb-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="a05fb-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a05fb-118">Details</span></span>  
  
|<span data-ttu-id="a05fb-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a05fb-119">Data Item Name</span></span>|<span data-ttu-id="a05fb-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a05fb-120">Data Item Type</span></span>|<span data-ttu-id="a05fb-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a05fb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a05fb-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="a05fb-122">RecordNumber</span></span>|<span data-ttu-id="a05fb-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="a05fb-123">xs:string</span></span>|<span data-ttu-id="a05fb-124">Počet záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="a05fb-124">The tracking record number.</span></span>|  
|<span data-ttu-id="a05fb-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="a05fb-125">ProviderId</span></span>|<span data-ttu-id="a05fb-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="a05fb-126">xs:string</span></span>|<span data-ttu-id="a05fb-127">Id zprostředkovatele trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a05fb-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="a05fb-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a05fb-128">AppDomain</span></span>|<span data-ttu-id="a05fb-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="a05fb-129">xs:string</span></span>|<span data-ttu-id="a05fb-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a05fb-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
