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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de056ffcdfeb3ea5dee9eaca213fe96ee991d067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="119c5-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="119c5-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="119c5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="119c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="119c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="119c5-104">ID</span></span>|<span data-ttu-id="119c5-105">39456</span><span class="sxs-lookup"><span data-stu-id="119c5-105">39456</span></span>|  
|<span data-ttu-id="119c5-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="119c5-106">Keywords</span></span>|<span data-ttu-id="119c5-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="119c5-107">WFTracking</span></span>|  
|<span data-ttu-id="119c5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="119c5-108">Level</span></span>|<span data-ttu-id="119c5-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="119c5-109">Warning</span></span>|  
|<span data-ttu-id="119c5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="119c5-110">Channel</span></span>|<span data-ttu-id="119c5-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="119c5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="119c5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="119c5-112">Description</span></span>  
 <span data-ttu-id="119c5-113">Označuje, že záznam sledování byla vyřazena, protože jeho velikost překračuje maximální povolenou zprostředkovatele relací trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="119c5-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="119c5-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="119c5-114">Message</span></span>  
 <span data-ttu-id="119c5-115">Velikost sledování záznam %1 překračuje maximální povolenou relace trasování událostí pro Windows pro zprostředkovatele: %2</span><span class="sxs-lookup"><span data-stu-id="119c5-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="119c5-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="119c5-116">Details</span></span>  
  
|<span data-ttu-id="119c5-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="119c5-117">Data Item Name</span></span>|<span data-ttu-id="119c5-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="119c5-118">Data Item Type</span></span>|<span data-ttu-id="119c5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="119c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="119c5-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="119c5-120">Exception</span></span>|<span data-ttu-id="119c5-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="119c5-121">xs:string</span></span>|<span data-ttu-id="119c5-122">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="119c5-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="119c5-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="119c5-123">AppDomain</span></span>|<span data-ttu-id="119c5-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="119c5-124">xs:string</span></span>|<span data-ttu-id="119c5-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="119c5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
