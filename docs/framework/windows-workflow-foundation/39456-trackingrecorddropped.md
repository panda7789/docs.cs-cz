---
title: 39456 – TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774423"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="ac0af-102">39456 – TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="ac0af-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="ac0af-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ac0af-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac0af-104">ID</span><span class="sxs-lookup"><span data-stu-id="ac0af-104">ID</span></span>|<span data-ttu-id="ac0af-105">39456</span><span class="sxs-lookup"><span data-stu-id="ac0af-105">39456</span></span>|  
|<span data-ttu-id="ac0af-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ac0af-106">Keywords</span></span>|<span data-ttu-id="ac0af-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ac0af-107">WFTracking</span></span>|  
|<span data-ttu-id="ac0af-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ac0af-108">Level</span></span>|<span data-ttu-id="ac0af-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="ac0af-109">Warning</span></span>|  
|<span data-ttu-id="ac0af-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ac0af-110">Channel</span></span>|<span data-ttu-id="ac0af-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ac0af-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ac0af-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ac0af-112">Description</span></span>  
 <span data-ttu-id="ac0af-113">Označuje, že záznamem sledování byla vyřazena, protože její velikost přesahuje maximální povolenou poskytovatelem relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="ac0af-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ac0af-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ac0af-114">Message</span></span>  
 <span data-ttu-id="ac0af-115">Velikost záznamu sledování %1 překračuje maximum povolené relací ETW pro poskytovatele %2</span><span class="sxs-lookup"><span data-stu-id="ac0af-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="ac0af-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ac0af-116">Details</span></span>  
  
|<span data-ttu-id="ac0af-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ac0af-117">Data Item Name</span></span>|<span data-ttu-id="ac0af-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="ac0af-118">Data Item Type</span></span>|<span data-ttu-id="ac0af-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ac0af-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ac0af-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="ac0af-120">Exception</span></span>|<span data-ttu-id="ac0af-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ac0af-121">xs:string</span></span>|<span data-ttu-id="ac0af-122">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="ac0af-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="ac0af-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ac0af-123">AppDomain</span></span>|<span data-ttu-id="ac0af-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ac0af-124">xs:string</span></span>|<span data-ttu-id="ac0af-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ac0af-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
