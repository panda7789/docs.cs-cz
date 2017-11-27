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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="31656-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="31656-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="31656-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="31656-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31656-104">ID</span><span class="sxs-lookup"><span data-stu-id="31656-104">ID</span></span>|<span data-ttu-id="31656-105">2577</span><span class="sxs-lookup"><span data-stu-id="31656-105">2577</span></span>|  
|<span data-ttu-id="31656-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="31656-106">Keywords</span></span>|<span data-ttu-id="31656-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="31656-107">WFActivities</span></span>|  
|<span data-ttu-id="31656-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="31656-108">Level</span></span>|<span data-ttu-id="31656-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="31656-109">Warning</span></span>|  
|<span data-ttu-id="31656-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="31656-110">Channel</span></span>|<span data-ttu-id="31656-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="31656-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31656-112">Popis</span><span class="sxs-lookup"><span data-stu-id="31656-112">Description</span></span>  
 <span data-ttu-id="31656-113">Označuje, že podřízené aktivity TryCatch aktivity došlo k výjimce při zrušení.</span><span class="sxs-lookup"><span data-stu-id="31656-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31656-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="31656-114">Message</span></span>  
 <span data-ttu-id="31656-115">Aktivita podřízené aktivity TryCatch '%1' došlo k výjimce při zrušení.</span><span class="sxs-lookup"><span data-stu-id="31656-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31656-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="31656-116">Details</span></span>  
  
|<span data-ttu-id="31656-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="31656-117">Data Item Name</span></span>|<span data-ttu-id="31656-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="31656-118">Data Item Type</span></span>|<span data-ttu-id="31656-119">Popis</span><span class="sxs-lookup"><span data-stu-id="31656-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31656-120">displayName</span><span class="sxs-lookup"><span data-stu-id="31656-120">DisplayName</span></span>|<span data-ttu-id="31656-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="31656-121">xs:string</span></span>|<span data-ttu-id="31656-122">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="31656-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="31656-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="31656-123">AppDomain</span></span>|<span data-ttu-id="31656-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="31656-124">xs:string</span></span>|<span data-ttu-id="31656-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="31656-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
