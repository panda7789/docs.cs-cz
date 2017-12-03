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
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="2f927-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="2f927-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2f927-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2f927-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f927-104">ID</span><span class="sxs-lookup"><span data-stu-id="2f927-104">ID</span></span>|<span data-ttu-id="2f927-105">1031</span><span class="sxs-lookup"><span data-stu-id="2f927-105">1031</span></span>|  
|<span data-ttu-id="2f927-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2f927-106">Keywords</span></span>|<span data-ttu-id="2f927-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2f927-107">WFRuntime</span></span>|  
|<span data-ttu-id="2f927-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2f927-108">Level</span></span>|<span data-ttu-id="2f927-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="2f927-109">Verbose</span></span>|  
|<span data-ttu-id="2f927-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2f927-110">Channel</span></span>|<span data-ttu-id="2f927-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="2f927-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f927-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2f927-112">Description</span></span>  
 <span data-ttu-id="2f927-113">Označuje, že je dokončená FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="2f927-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f927-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2f927-114">Message</span></span>  
 <span data-ttu-id="2f927-115">FaultWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2f927-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="2f927-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="2f927-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f927-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2f927-117">Details</span></span>  
  
|<span data-ttu-id="2f927-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2f927-118">Data Item Name</span></span>|<span data-ttu-id="2f927-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2f927-119">Data Item Type</span></span>|<span data-ttu-id="2f927-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2f927-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f927-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="2f927-121">FaultActivity</span></span>|<span data-ttu-id="2f927-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-122">xs:string</span></span>|<span data-ttu-id="2f927-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f927-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="2f927-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2f927-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="2f927-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-125">xs:string</span></span>|<span data-ttu-id="2f927-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f927-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="2f927-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2f927-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="2f927-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-128">xs:string</span></span>|<span data-ttu-id="2f927-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f927-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="2f927-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="2f927-130">ExceptionActivity</span></span>|<span data-ttu-id="2f927-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-131">xs:string</span></span>|<span data-ttu-id="2f927-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="2f927-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2f927-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2f927-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="2f927-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-134">xs:string</span></span>|<span data-ttu-id="2f927-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="2f927-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2f927-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2f927-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="2f927-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-137">xs:string</span></span>|<span data-ttu-id="2f927-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="2f927-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2f927-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="2f927-139">Exception</span></span>|<span data-ttu-id="2f927-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-140">xs:string</span></span>|<span data-ttu-id="2f927-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="2f927-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="2f927-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2f927-142">AppDomain</span></span>|<span data-ttu-id="2f927-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="2f927-143">xs:string</span></span>|<span data-ttu-id="2f927-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2f927-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
