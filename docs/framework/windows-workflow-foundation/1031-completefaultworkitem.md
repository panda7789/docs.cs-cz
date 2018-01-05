---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a87ecb0a50437d83dd3c80d213553c8ac2143968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="b50f3-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="b50f3-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b50f3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b50f3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b50f3-104">ID</span><span class="sxs-lookup"><span data-stu-id="b50f3-104">ID</span></span>|<span data-ttu-id="b50f3-105">1031</span><span class="sxs-lookup"><span data-stu-id="b50f3-105">1031</span></span>|  
|<span data-ttu-id="b50f3-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b50f3-106">Keywords</span></span>|<span data-ttu-id="b50f3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b50f3-107">WFRuntime</span></span>|  
|<span data-ttu-id="b50f3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b50f3-108">Level</span></span>|<span data-ttu-id="b50f3-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="b50f3-109">Verbose</span></span>|  
|<span data-ttu-id="b50f3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b50f3-110">Channel</span></span>|<span data-ttu-id="b50f3-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b50f3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b50f3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b50f3-112">Description</span></span>  
 <span data-ttu-id="b50f3-113">Označuje, že je dokončená FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="b50f3-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b50f3-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b50f3-114">Message</span></span>  
 <span data-ttu-id="b50f3-115">FaultWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b50f3-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="b50f3-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="b50f3-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b50f3-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b50f3-117">Details</span></span>  
  
|<span data-ttu-id="b50f3-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b50f3-118">Data Item Name</span></span>|<span data-ttu-id="b50f3-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b50f3-119">Data Item Type</span></span>|<span data-ttu-id="b50f3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b50f3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b50f3-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="b50f3-121">FaultActivity</span></span>|<span data-ttu-id="b50f3-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-122">xs:string</span></span>|<span data-ttu-id="b50f3-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="b50f3-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="b50f3-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b50f3-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="b50f3-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-125">xs:string</span></span>|<span data-ttu-id="b50f3-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="b50f3-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="b50f3-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b50f3-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="b50f3-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-128">xs:string</span></span>|<span data-ttu-id="b50f3-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="b50f3-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="b50f3-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="b50f3-130">ExceptionActivity</span></span>|<span data-ttu-id="b50f3-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-131">xs:string</span></span>|<span data-ttu-id="b50f3-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="b50f3-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b50f3-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b50f3-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="b50f3-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-134">xs:string</span></span>|<span data-ttu-id="b50f3-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="b50f3-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b50f3-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b50f3-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="b50f3-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-137">xs:string</span></span>|<span data-ttu-id="b50f3-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="b50f3-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b50f3-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="b50f3-139">Exception</span></span>|<span data-ttu-id="b50f3-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-140">xs:string</span></span>|<span data-ttu-id="b50f3-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="b50f3-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="b50f3-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b50f3-142">AppDomain</span></span>|<span data-ttu-id="b50f3-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="b50f3-143">xs:string</span></span>|<span data-ttu-id="b50f3-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b50f3-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
