---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1e851a50c9677b2f10ea3478c3599706007d4d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="77d43-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="77d43-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="77d43-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="77d43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77d43-104">ID</span><span class="sxs-lookup"><span data-stu-id="77d43-104">ID</span></span>|<span data-ttu-id="77d43-105">2577</span><span class="sxs-lookup"><span data-stu-id="77d43-105">2577</span></span>|  
|<span data-ttu-id="77d43-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="77d43-106">Keywords</span></span>|<span data-ttu-id="77d43-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="77d43-107">WFActivities</span></span>|  
|<span data-ttu-id="77d43-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="77d43-108">Level</span></span>|<span data-ttu-id="77d43-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="77d43-109">Warning</span></span>|  
|<span data-ttu-id="77d43-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="77d43-110">Channel</span></span>|<span data-ttu-id="77d43-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="77d43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77d43-112">Popis</span><span class="sxs-lookup"><span data-stu-id="77d43-112">Description</span></span>  
 <span data-ttu-id="77d43-113">Označuje, že podřízené aktivity TryCatch aktivity došlo k výjimce při zrušení.</span><span class="sxs-lookup"><span data-stu-id="77d43-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77d43-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="77d43-114">Message</span></span>  
 <span data-ttu-id="77d43-115">Aktivita podřízené aktivity TryCatch '%1' došlo k výjimce při zrušení.</span><span class="sxs-lookup"><span data-stu-id="77d43-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77d43-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="77d43-116">Details</span></span>  
  
|<span data-ttu-id="77d43-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="77d43-117">Data Item Name</span></span>|<span data-ttu-id="77d43-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="77d43-118">Data Item Type</span></span>|<span data-ttu-id="77d43-119">Popis</span><span class="sxs-lookup"><span data-stu-id="77d43-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77d43-120">displayName</span><span class="sxs-lookup"><span data-stu-id="77d43-120">DisplayName</span></span>|<span data-ttu-id="77d43-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="77d43-121">xs:string</span></span>|<span data-ttu-id="77d43-122">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="77d43-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="77d43-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="77d43-123">AppDomain</span></span>|<span data-ttu-id="77d43-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="77d43-124">xs:string</span></span>|<span data-ttu-id="77d43-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="77d43-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
