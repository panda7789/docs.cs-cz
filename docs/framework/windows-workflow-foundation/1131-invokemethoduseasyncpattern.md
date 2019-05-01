---
title: 1131 – InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009952"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="a5eae-102">1131 – InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="a5eae-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="a5eae-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a5eae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5eae-104">ID</span><span class="sxs-lookup"><span data-stu-id="a5eae-104">ID</span></span>|<span data-ttu-id="a5eae-105">1131</span><span class="sxs-lookup"><span data-stu-id="a5eae-105">1131</span></span>|  
|<span data-ttu-id="a5eae-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a5eae-106">Keywords</span></span>|<span data-ttu-id="a5eae-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a5eae-107">WFRuntime</span></span>|  
|<span data-ttu-id="a5eae-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a5eae-108">Level</span></span>|<span data-ttu-id="a5eae-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a5eae-109">Information</span></span>|  
|<span data-ttu-id="a5eae-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a5eae-110">Channel</span></span>|<span data-ttu-id="a5eae-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a5eae-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a5eae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a5eae-112">Description</span></span>  
 <span data-ttu-id="a5eae-113">Během kroku CacheMetadata aktivity InvokeMethod označuje, že používá asynchronní vzorek, při volání metody.</span><span class="sxs-lookup"><span data-stu-id="a5eae-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a5eae-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a5eae-114">Message</span></span>  
 <span data-ttu-id="a5eae-115">InvokeMethod '%1' - metoda používá asynchronní vzorek '%2' a '%3'.</span><span class="sxs-lookup"><span data-stu-id="a5eae-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a5eae-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a5eae-116">Details</span></span>  
  
|<span data-ttu-id="a5eae-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a5eae-117">Data Item Name</span></span>|<span data-ttu-id="a5eae-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="a5eae-118">Data Item Type</span></span>|<span data-ttu-id="a5eae-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a5eae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a5eae-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="a5eae-120">InvokeMethod</span></span>|<span data-ttu-id="a5eae-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5eae-121">xs:string</span></span>|<span data-ttu-id="a5eae-122">Zobrazovaný název aktivity InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="a5eae-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="a5eae-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="a5eae-123">BeginMethod</span></span>|<span data-ttu-id="a5eae-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5eae-124">xs:string</span></span>|<span data-ttu-id="a5eae-125">Název metody begin.</span><span class="sxs-lookup"><span data-stu-id="a5eae-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="a5eae-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="a5eae-126">EndMethod</span></span>|<span data-ttu-id="a5eae-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5eae-127">xs:string</span></span>|<span data-ttu-id="a5eae-128">Název metody end.</span><span class="sxs-lookup"><span data-stu-id="a5eae-128">The name of the end method.</span></span>|  
|<span data-ttu-id="a5eae-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a5eae-129">AppDomain</span></span>|<span data-ttu-id="a5eae-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5eae-130">xs:string</span></span>|<span data-ttu-id="a5eae-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a5eae-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
