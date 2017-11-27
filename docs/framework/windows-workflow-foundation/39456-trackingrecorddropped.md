---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e663cced42252112e1948f4907bc8c81ef941f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="33874-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="33874-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="33874-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="33874-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33874-104">ID</span><span class="sxs-lookup"><span data-stu-id="33874-104">ID</span></span>|<span data-ttu-id="33874-105">39456</span><span class="sxs-lookup"><span data-stu-id="33874-105">39456</span></span>|  
|<span data-ttu-id="33874-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="33874-106">Keywords</span></span>|<span data-ttu-id="33874-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="33874-107">WFTracking</span></span>|  
|<span data-ttu-id="33874-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="33874-108">Level</span></span>|<span data-ttu-id="33874-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="33874-109">Warning</span></span>|  
|<span data-ttu-id="33874-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="33874-110">Channel</span></span>|<span data-ttu-id="33874-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="33874-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="33874-112">Popis</span><span class="sxs-lookup"><span data-stu-id="33874-112">Description</span></span>  
 <span data-ttu-id="33874-113">Označuje, že záznam sledování byla vyřazena, protože jeho velikost překračuje maximální povolenou zprostředkovatele relací trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="33874-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="33874-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="33874-114">Message</span></span>  
 <span data-ttu-id="33874-115">Velikost sledování záznam %1 překračuje maximální povolenou relace trasování událostí pro Windows pro zprostředkovatele: %2</span><span class="sxs-lookup"><span data-stu-id="33874-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="33874-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="33874-116">Details</span></span>  
  
|<span data-ttu-id="33874-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="33874-117">Data Item Name</span></span>|<span data-ttu-id="33874-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="33874-118">Data Item Type</span></span>|<span data-ttu-id="33874-119">Popis</span><span class="sxs-lookup"><span data-stu-id="33874-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="33874-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="33874-120">Exception</span></span>|<span data-ttu-id="33874-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="33874-121">xs:string</span></span>|<span data-ttu-id="33874-122">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="33874-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="33874-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="33874-123">AppDomain</span></span>|<span data-ttu-id="33874-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="33874-124">xs:string</span></span>|<span data-ttu-id="33874-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="33874-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
