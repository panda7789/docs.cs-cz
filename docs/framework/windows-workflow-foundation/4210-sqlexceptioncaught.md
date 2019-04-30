---
title: 4210 – SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774254"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="6538a-102">4210 – SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="6538a-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="6538a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6538a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6538a-104">ID</span><span class="sxs-lookup"><span data-stu-id="6538a-104">ID</span></span>|<span data-ttu-id="6538a-105">4210</span><span class="sxs-lookup"><span data-stu-id="6538a-105">4210</span></span>|  
|<span data-ttu-id="6538a-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6538a-106">Keywords</span></span>|<span data-ttu-id="6538a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="6538a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="6538a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6538a-108">Level</span></span>|<span data-ttu-id="6538a-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="6538a-109">Warning</span></span>|  
|<span data-ttu-id="6538a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6538a-110">Channel</span></span>|<span data-ttu-id="6538a-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="6538a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6538a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6538a-112">Description</span></span>  
 <span data-ttu-id="6538a-113">Označuje, že byla zachycena výjimka SQL.</span><span class="sxs-lookup"><span data-stu-id="6538a-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6538a-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6538a-114">Message</span></span>  
 <span data-ttu-id="6538a-115">Byla zachycena výjimka SQL číslem %1 a zprávou %2.</span><span class="sxs-lookup"><span data-stu-id="6538a-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6538a-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6538a-116">Details</span></span>  
  
|<span data-ttu-id="6538a-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6538a-117">Data Item Name</span></span>|<span data-ttu-id="6538a-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="6538a-118">Data Item Type</span></span>|<span data-ttu-id="6538a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6538a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6538a-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="6538a-120">ErrorNumber</span></span>|<span data-ttu-id="6538a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6538a-121">xs:string</span></span>|<span data-ttu-id="6538a-122">Číslo chyby SQL.</span><span class="sxs-lookup"><span data-stu-id="6538a-122">The SQL error number.</span></span>|  
|<span data-ttu-id="6538a-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="6538a-123">ExceptionMessage</span></span>|<span data-ttu-id="6538a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6538a-124">xs:string</span></span>|<span data-ttu-id="6538a-125">Zpráva z výjimky SQL.</span><span class="sxs-lookup"><span data-stu-id="6538a-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="6538a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6538a-126">AppDomain</span></span>|<span data-ttu-id="6538a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6538a-127">xs:string</span></span>|<span data-ttu-id="6538a-128">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6538a-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
