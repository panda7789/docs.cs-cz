---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75386b56f7926b9ddb883e0ca212d795898fe6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="57c0c-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="57c0c-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="57c0c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57c0c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57c0c-104">ID</span><span class="sxs-lookup"><span data-stu-id="57c0c-104">ID</span></span>|<span data-ttu-id="57c0c-105">1132</span><span class="sxs-lookup"><span data-stu-id="57c0c-105">1132</span></span>|  
|<span data-ttu-id="57c0c-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="57c0c-106">Keywords</span></span>|<span data-ttu-id="57c0c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="57c0c-107">WFRuntime</span></span>|  
|<span data-ttu-id="57c0c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="57c0c-108">Level</span></span>|<span data-ttu-id="57c0c-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="57c0c-109">Information</span></span>|  
|<span data-ttu-id="57c0c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="57c0c-110">Channel</span></span>|<span data-ttu-id="57c0c-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="57c0c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57c0c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="57c0c-112">Description</span></span>  
 <span data-ttu-id="57c0c-113">Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho není vzoru async při volání metody.</span><span class="sxs-lookup"><span data-stu-id="57c0c-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57c0c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="57c0c-114">Message</span></span>  
 <span data-ttu-id="57c0c-115">InvokeMethod '%1' - metoda nepoužívá asynchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="57c0c-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57c0c-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="57c0c-116">Details</span></span>  
  
|<span data-ttu-id="57c0c-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="57c0c-117">Data Item Name</span></span>|<span data-ttu-id="57c0c-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="57c0c-118">Data Item Type</span></span>|<span data-ttu-id="57c0c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="57c0c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57c0c-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="57c0c-120">InvokeMethod</span></span>|<span data-ttu-id="57c0c-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="57c0c-121">xs:string</span></span>|<span data-ttu-id="57c0c-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="57c0c-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="57c0c-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="57c0c-123">AppDomain</span></span>|<span data-ttu-id="57c0c-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="57c0c-124">xs:string</span></span>|<span data-ttu-id="57c0c-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="57c0c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
