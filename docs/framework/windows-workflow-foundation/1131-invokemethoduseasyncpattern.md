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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f9f8f4e836d5c5b437edcfaff6460c7b97210ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="9711a-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="9711a-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="9711a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9711a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9711a-104">ID</span><span class="sxs-lookup"><span data-stu-id="9711a-104">ID</span></span>|<span data-ttu-id="9711a-105">1131</span><span class="sxs-lookup"><span data-stu-id="9711a-105">1131</span></span>|  
|<span data-ttu-id="9711a-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9711a-106">Keywords</span></span>|<span data-ttu-id="9711a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9711a-107">WFRuntime</span></span>|  
|<span data-ttu-id="9711a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9711a-108">Level</span></span>|<span data-ttu-id="9711a-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="9711a-109">Information</span></span>|  
|<span data-ttu-id="9711a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9711a-110">Channel</span></span>|<span data-ttu-id="9711a-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9711a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9711a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9711a-112">Description</span></span>  
 <span data-ttu-id="9711a-113">Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho vzoru async při volání metody.</span><span class="sxs-lookup"><span data-stu-id="9711a-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9711a-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9711a-114">Message</span></span>  
 <span data-ttu-id="9711a-115">InvokeMethod '%1' - metoda používá asynchronní vzor '%2' a '%3'.</span><span class="sxs-lookup"><span data-stu-id="9711a-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9711a-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9711a-116">Details</span></span>  
  
|<span data-ttu-id="9711a-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9711a-117">Data Item Name</span></span>|<span data-ttu-id="9711a-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9711a-118">Data Item Type</span></span>|<span data-ttu-id="9711a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9711a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9711a-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9711a-120">InvokeMethod</span></span>|<span data-ttu-id="9711a-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="9711a-121">xs:string</span></span>|<span data-ttu-id="9711a-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="9711a-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9711a-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="9711a-123">BeginMethod</span></span>|<span data-ttu-id="9711a-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="9711a-124">xs:string</span></span>|<span data-ttu-id="9711a-125">Název metody begin.</span><span class="sxs-lookup"><span data-stu-id="9711a-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="9711a-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="9711a-126">EndMethod</span></span>|<span data-ttu-id="9711a-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="9711a-127">xs:string</span></span>|<span data-ttu-id="9711a-128">Název metody end.</span><span class="sxs-lookup"><span data-stu-id="9711a-128">The name of the end method.</span></span>|  
|<span data-ttu-id="9711a-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9711a-129">AppDomain</span></span>|<span data-ttu-id="9711a-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="9711a-130">xs:string</span></span>|<span data-ttu-id="9711a-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9711a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
