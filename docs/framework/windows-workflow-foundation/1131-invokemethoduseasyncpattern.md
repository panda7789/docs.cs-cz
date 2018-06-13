---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512662"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="87c4b-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="87c4b-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="87c4b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="87c4b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87c4b-104">ID</span><span class="sxs-lookup"><span data-stu-id="87c4b-104">ID</span></span>|<span data-ttu-id="87c4b-105">1131</span><span class="sxs-lookup"><span data-stu-id="87c4b-105">1131</span></span>|  
|<span data-ttu-id="87c4b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="87c4b-106">Keywords</span></span>|<span data-ttu-id="87c4b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="87c4b-107">WFRuntime</span></span>|  
|<span data-ttu-id="87c4b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="87c4b-108">Level</span></span>|<span data-ttu-id="87c4b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="87c4b-109">Information</span></span>|  
|<span data-ttu-id="87c4b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="87c4b-110">Channel</span></span>|<span data-ttu-id="87c4b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="87c4b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="87c4b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="87c4b-112">Description</span></span>  
 <span data-ttu-id="87c4b-113">Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho vzoru async při volání metody.</span><span class="sxs-lookup"><span data-stu-id="87c4b-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="87c4b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="87c4b-114">Message</span></span>  
 <span data-ttu-id="87c4b-115">InvokeMethod '%1' - metoda používá asynchronní vzor '%2' a '%3'.</span><span class="sxs-lookup"><span data-stu-id="87c4b-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="87c4b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="87c4b-116">Details</span></span>  
  
|<span data-ttu-id="87c4b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="87c4b-117">Data Item Name</span></span>|<span data-ttu-id="87c4b-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="87c4b-118">Data Item Type</span></span>|<span data-ttu-id="87c4b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="87c4b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="87c4b-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="87c4b-120">InvokeMethod</span></span>|<span data-ttu-id="87c4b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="87c4b-121">xs:string</span></span>|<span data-ttu-id="87c4b-122">Zobrazovaný název InvokeMethod aktivity.</span><span class="sxs-lookup"><span data-stu-id="87c4b-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="87c4b-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="87c4b-123">BeginMethod</span></span>|<span data-ttu-id="87c4b-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="87c4b-124">xs:string</span></span>|<span data-ttu-id="87c4b-125">Název metody begin.</span><span class="sxs-lookup"><span data-stu-id="87c4b-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="87c4b-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="87c4b-126">EndMethod</span></span>|<span data-ttu-id="87c4b-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="87c4b-127">xs:string</span></span>|<span data-ttu-id="87c4b-128">Název metody end.</span><span class="sxs-lookup"><span data-stu-id="87c4b-128">The name of the end method.</span></span>|  
|<span data-ttu-id="87c4b-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="87c4b-129">AppDomain</span></span>|<span data-ttu-id="87c4b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="87c4b-130">xs:string</span></span>|<span data-ttu-id="87c4b-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="87c4b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
