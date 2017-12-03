---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c2031a86a8d46a51b65e60a63a352c56b1a3a53
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="ccf05-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="ccf05-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ccf05-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ccf05-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccf05-104">ID</span><span class="sxs-lookup"><span data-stu-id="ccf05-104">ID</span></span>|<span data-ttu-id="ccf05-105">1029</span><span class="sxs-lookup"><span data-stu-id="ccf05-105">1029</span></span>|  
|<span data-ttu-id="ccf05-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ccf05-106">Keywords</span></span>|<span data-ttu-id="ccf05-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ccf05-107">WFRuntime</span></span>|  
|<span data-ttu-id="ccf05-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ccf05-108">Level</span></span>|<span data-ttu-id="ccf05-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="ccf05-109">Verbose</span></span>|  
|<span data-ttu-id="ccf05-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ccf05-110">Channel</span></span>|<span data-ttu-id="ccf05-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ccf05-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ccf05-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ccf05-112">Description</span></span>  
 <span data-ttu-id="ccf05-113">Označuje, že bylo naplánováno FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="ccf05-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ccf05-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ccf05-114">Message</span></span>  
 <span data-ttu-id="ccf05-115">Bylo naplánováno FaultWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ccf05-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ccf05-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="ccf05-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ccf05-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ccf05-117">Details</span></span>  
  
|<span data-ttu-id="ccf05-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ccf05-118">Data Item Name</span></span>|<span data-ttu-id="ccf05-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ccf05-119">Data Item Type</span></span>|<span data-ttu-id="ccf05-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ccf05-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ccf05-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="ccf05-121">FaultActivity</span></span>|<span data-ttu-id="ccf05-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-122">xs:string</span></span>|<span data-ttu-id="ccf05-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="ccf05-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="ccf05-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ccf05-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="ccf05-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-125">xs:string</span></span>|<span data-ttu-id="ccf05-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="ccf05-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="ccf05-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ccf05-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="ccf05-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-128">xs:string</span></span>|<span data-ttu-id="ccf05-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="ccf05-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="ccf05-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="ccf05-130">ExceptionActivity</span></span>|<span data-ttu-id="ccf05-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-131">xs:string</span></span>|<span data-ttu-id="ccf05-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="ccf05-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ccf05-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ccf05-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="ccf05-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-134">xs:string</span></span>|<span data-ttu-id="ccf05-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="ccf05-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ccf05-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ccf05-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="ccf05-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-137">xs:string</span></span>|<span data-ttu-id="ccf05-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="ccf05-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ccf05-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="ccf05-139">Exception</span></span>|<span data-ttu-id="ccf05-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-140">xs:string</span></span>|<span data-ttu-id="ccf05-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="ccf05-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="ccf05-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ccf05-142">AppDomain</span></span>|<span data-ttu-id="ccf05-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="ccf05-143">xs:string</span></span>|<span data-ttu-id="ccf05-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ccf05-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
