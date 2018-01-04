---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 739357df85ceb73e246adcb2b09f88d270d853ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="88c57-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="88c57-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="88c57-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="88c57-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="88c57-104">ID</span><span class="sxs-lookup"><span data-stu-id="88c57-104">ID</span></span>|<span data-ttu-id="88c57-105">1131</span><span class="sxs-lookup"><span data-stu-id="88c57-105">1131</span></span>|  
|<span data-ttu-id="88c57-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="88c57-106">Keywords</span></span>|<span data-ttu-id="88c57-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="88c57-107">WFRuntime</span></span>|  
|<span data-ttu-id="88c57-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="88c57-108">Level</span></span>|<span data-ttu-id="88c57-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="88c57-109">Information</span></span>|  
|<span data-ttu-id="88c57-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="88c57-110">Channel</span></span>|<span data-ttu-id="88c57-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="88c57-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="88c57-112">Popis</span><span class="sxs-lookup"><span data-stu-id="88c57-112">Description</span></span>  
 <span data-ttu-id="88c57-113">Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho vzoru async při volání metody.</span><span class="sxs-lookup"><span data-stu-id="88c57-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="88c57-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="88c57-114">Message</span></span>  
 <span data-ttu-id="88c57-115">InvokeMethod '%1' - metoda používá asynchronní vzor '%2' a '%3'.</span><span class="sxs-lookup"><span data-stu-id="88c57-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="88c57-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="88c57-116">Details</span></span>  
  
|<span data-ttu-id="88c57-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="88c57-117">Data Item Name</span></span>|<span data-ttu-id="88c57-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="88c57-118">Data Item Type</span></span>|<span data-ttu-id="88c57-119">Popis</span><span class="sxs-lookup"><span data-stu-id="88c57-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="88c57-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="88c57-120">InvokeMethod</span></span>|<span data-ttu-id="88c57-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="88c57-121">xs:string</span></span>|<span data-ttu-id="88c57-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="88c57-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="88c57-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="88c57-123">BeginMethod</span></span>|<span data-ttu-id="88c57-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="88c57-124">xs:string</span></span>|<span data-ttu-id="88c57-125">Název metody begin.</span><span class="sxs-lookup"><span data-stu-id="88c57-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="88c57-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="88c57-126">EndMethod</span></span>|<span data-ttu-id="88c57-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="88c57-127">xs:string</span></span>|<span data-ttu-id="88c57-128">Název metody end.</span><span class="sxs-lookup"><span data-stu-id="88c57-128">The name of the end method.</span></span>|  
|<span data-ttu-id="88c57-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="88c57-129">AppDomain</span></span>|<span data-ttu-id="88c57-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="88c57-130">xs:string</span></span>|<span data-ttu-id="88c57-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="88c57-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
