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
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="544b2-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="544b2-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="544b2-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="544b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="544b2-104">ID</span><span class="sxs-lookup"><span data-stu-id="544b2-104">ID</span></span>|<span data-ttu-id="544b2-105">1132</span><span class="sxs-lookup"><span data-stu-id="544b2-105">1132</span></span>|  
|<span data-ttu-id="544b2-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="544b2-106">Keywords</span></span>|<span data-ttu-id="544b2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="544b2-107">WFRuntime</span></span>|  
|<span data-ttu-id="544b2-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="544b2-108">Level</span></span>|<span data-ttu-id="544b2-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="544b2-109">Information</span></span>|  
|<span data-ttu-id="544b2-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="544b2-110">Channel</span></span>|<span data-ttu-id="544b2-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="544b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="544b2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="544b2-112">Description</span></span>  
 <span data-ttu-id="544b2-113">Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho není vzoru async při volání metody.</span><span class="sxs-lookup"><span data-stu-id="544b2-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="544b2-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="544b2-114">Message</span></span>  
 <span data-ttu-id="544b2-115">InvokeMethod '%1' - metoda nepoužívá asynchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="544b2-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="544b2-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="544b2-116">Details</span></span>  
  
|<span data-ttu-id="544b2-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="544b2-117">Data Item Name</span></span>|<span data-ttu-id="544b2-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="544b2-118">Data Item Type</span></span>|<span data-ttu-id="544b2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="544b2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="544b2-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="544b2-120">InvokeMethod</span></span>|<span data-ttu-id="544b2-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="544b2-121">xs:string</span></span>|<span data-ttu-id="544b2-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="544b2-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="544b2-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="544b2-123">AppDomain</span></span>|<span data-ttu-id="544b2-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="544b2-124">xs:string</span></span>|<span data-ttu-id="544b2-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="544b2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
