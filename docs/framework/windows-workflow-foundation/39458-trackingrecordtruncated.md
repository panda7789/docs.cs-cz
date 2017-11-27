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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="542be-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="542be-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="542be-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="542be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="542be-104">ID</span><span class="sxs-lookup"><span data-stu-id="542be-104">ID</span></span>|<span data-ttu-id="542be-105">39458</span><span class="sxs-lookup"><span data-stu-id="542be-105">39458</span></span>|  
|<span data-ttu-id="542be-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="542be-106">Keywords</span></span>|<span data-ttu-id="542be-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="542be-107">WFTracking</span></span>|  
|<span data-ttu-id="542be-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="542be-108">Level</span></span>|<span data-ttu-id="542be-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="542be-109">Warning</span></span>|  
|<span data-ttu-id="542be-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="542be-110">Channel</span></span>|<span data-ttu-id="542be-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="542be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="542be-112">Popis</span><span class="sxs-lookup"><span data-stu-id="542be-112">Description</span></span>  
 <span data-ttu-id="542be-113">Označuje, že záznam sledování byla zkrácena.</span><span class="sxs-lookup"><span data-stu-id="542be-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="542be-114">Byly odebrány proměnné a poznámky nebo uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="542be-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="542be-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="542be-115">Message</span></span>  
 <span data-ttu-id="542be-116">Zkrácená sledování záznam %1 zapsána do relace trasování událostí pro Windows pomocí zprostředkovatele %2.</span><span class="sxs-lookup"><span data-stu-id="542be-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="542be-117">Odebrali jsme proměnné a poznámky nebo uživatelská data</span><span class="sxs-lookup"><span data-stu-id="542be-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="542be-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="542be-118">Details</span></span>  
  
|<span data-ttu-id="542be-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="542be-119">Data Item Name</span></span>|<span data-ttu-id="542be-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="542be-120">Data Item Type</span></span>|<span data-ttu-id="542be-121">Popis</span><span class="sxs-lookup"><span data-stu-id="542be-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="542be-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="542be-122">RecordNumber</span></span>|<span data-ttu-id="542be-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="542be-123">xs:string</span></span>|<span data-ttu-id="542be-124">Počet záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="542be-124">The tracking record number.</span></span>|  
|<span data-ttu-id="542be-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="542be-125">ProviderId</span></span>|<span data-ttu-id="542be-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="542be-126">xs:string</span></span>|<span data-ttu-id="542be-127">Id zprostředkovatele trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="542be-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="542be-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="542be-128">AppDomain</span></span>|<span data-ttu-id="542be-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="542be-129">xs:string</span></span>|<span data-ttu-id="542be-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="542be-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
