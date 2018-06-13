---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510702"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="be231-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="be231-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="be231-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="be231-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be231-104">ID</span><span class="sxs-lookup"><span data-stu-id="be231-104">ID</span></span>|<span data-ttu-id="be231-105">39456</span><span class="sxs-lookup"><span data-stu-id="be231-105">39456</span></span>|  
|<span data-ttu-id="be231-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="be231-106">Keywords</span></span>|<span data-ttu-id="be231-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="be231-107">WFTracking</span></span>|  
|<span data-ttu-id="be231-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="be231-108">Level</span></span>|<span data-ttu-id="be231-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="be231-109">Warning</span></span>|  
|<span data-ttu-id="be231-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="be231-110">Channel</span></span>|<span data-ttu-id="be231-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="be231-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be231-112">Popis</span><span class="sxs-lookup"><span data-stu-id="be231-112">Description</span></span>  
 <span data-ttu-id="be231-113">Označuje, že záznam sledování byla vyřazena, protože jeho velikost překračuje maximální povolenou zprostředkovatele relací trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="be231-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be231-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="be231-114">Message</span></span>  
 <span data-ttu-id="be231-115">Velikost sledování záznam %1 překračuje maximální povolenou relace trasování událostí pro Windows pro zprostředkovatele: %2</span><span class="sxs-lookup"><span data-stu-id="be231-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="be231-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="be231-116">Details</span></span>  
  
|<span data-ttu-id="be231-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="be231-117">Data Item Name</span></span>|<span data-ttu-id="be231-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="be231-118">Data Item Type</span></span>|<span data-ttu-id="be231-119">Popis</span><span class="sxs-lookup"><span data-stu-id="be231-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be231-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="be231-120">Exception</span></span>|<span data-ttu-id="be231-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="be231-121">xs:string</span></span>|<span data-ttu-id="be231-122">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="be231-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="be231-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="be231-123">AppDomain</span></span>|<span data-ttu-id="be231-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="be231-124">xs:string</span></span>|<span data-ttu-id="be231-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="be231-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
