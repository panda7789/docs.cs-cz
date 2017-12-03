---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c639de96bd72670b2641707e7283be2642801dbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="b4ac7-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="b4ac7-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b4ac7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b4ac7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4ac7-104">ID</span><span class="sxs-lookup"><span data-stu-id="b4ac7-104">ID</span></span>|<span data-ttu-id="b4ac7-105">1030</span><span class="sxs-lookup"><span data-stu-id="b4ac7-105">1030</span></span>|  
|<span data-ttu-id="b4ac7-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b4ac7-106">Keywords</span></span>|<span data-ttu-id="b4ac7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b4ac7-107">WFRuntime</span></span>|  
|<span data-ttu-id="b4ac7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b4ac7-108">Level</span></span>|<span data-ttu-id="b4ac7-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b4ac7-109">Verbose</span></span>|  
|<span data-ttu-id="b4ac7-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b4ac7-110">Channel</span></span>|<span data-ttu-id="b4ac7-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b4ac7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b4ac7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b4ac7-112">Description</span></span>  
 <span data-ttu-id="b4ac7-113">Označuje, že že faultworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b4ac7-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b4ac7-114">Message</span></span>  
 <span data-ttu-id="b4ac7-115">Spuštění provádění FaultWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="b4ac7-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b4ac7-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b4ac7-117">Details</span></span>  
  
|<span data-ttu-id="b4ac7-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b4ac7-118">Data Item Name</span></span>|<span data-ttu-id="b4ac7-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b4ac7-119">Data Item Type</span></span>|<span data-ttu-id="b4ac7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b4ac7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b4ac7-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="b4ac7-121">FaultActivity</span></span>|<span data-ttu-id="b4ac7-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-122">xs:string</span></span>|<span data-ttu-id="b4ac7-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="b4ac7-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b4ac7-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="b4ac7-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-125">xs:string</span></span>|<span data-ttu-id="b4ac7-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="b4ac7-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b4ac7-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="b4ac7-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-128">xs:string</span></span>|<span data-ttu-id="b4ac7-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="b4ac7-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="b4ac7-130">ExceptionActivity</span></span>|<span data-ttu-id="b4ac7-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-131">xs:string</span></span>|<span data-ttu-id="b4ac7-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b4ac7-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b4ac7-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="b4ac7-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-134">xs:string</span></span>|<span data-ttu-id="b4ac7-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b4ac7-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b4ac7-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="b4ac7-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-137">xs:string</span></span>|<span data-ttu-id="b4ac7-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b4ac7-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="b4ac7-139">Exception</span></span>|<span data-ttu-id="b4ac7-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-140">xs:string</span></span>|<span data-ttu-id="b4ac7-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="b4ac7-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="b4ac7-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b4ac7-142">AppDomain</span></span>|<span data-ttu-id="b4ac7-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="b4ac7-143">xs:string</span></span>|<span data-ttu-id="b4ac7-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b4ac7-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
