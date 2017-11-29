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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 260647b56d945600afea5609f06d36385fa66014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="860ce-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="860ce-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="860ce-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="860ce-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="860ce-104">ID</span><span class="sxs-lookup"><span data-stu-id="860ce-104">ID</span></span>|<span data-ttu-id="860ce-105">1031</span><span class="sxs-lookup"><span data-stu-id="860ce-105">1031</span></span>|  
|<span data-ttu-id="860ce-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="860ce-106">Keywords</span></span>|<span data-ttu-id="860ce-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="860ce-107">WFRuntime</span></span>|  
|<span data-ttu-id="860ce-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="860ce-108">Level</span></span>|<span data-ttu-id="860ce-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="860ce-109">Verbose</span></span>|  
|<span data-ttu-id="860ce-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="860ce-110">Channel</span></span>|<span data-ttu-id="860ce-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="860ce-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="860ce-112">Popis</span><span class="sxs-lookup"><span data-stu-id="860ce-112">Description</span></span>  
 <span data-ttu-id="860ce-113">Označuje, že je dokončená FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="860ce-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="860ce-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="860ce-114">Message</span></span>  
 <span data-ttu-id="860ce-115">FaultWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="860ce-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="860ce-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="860ce-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="860ce-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="860ce-117">Details</span></span>  
  
|<span data-ttu-id="860ce-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="860ce-118">Data Item Name</span></span>|<span data-ttu-id="860ce-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="860ce-119">Data Item Type</span></span>|<span data-ttu-id="860ce-120">Popis</span><span class="sxs-lookup"><span data-stu-id="860ce-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="860ce-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="860ce-121">FaultActivity</span></span>|<span data-ttu-id="860ce-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-122">xs:string</span></span>|<span data-ttu-id="860ce-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="860ce-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="860ce-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="860ce-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="860ce-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-125">xs:string</span></span>|<span data-ttu-id="860ce-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="860ce-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="860ce-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="860ce-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="860ce-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-128">xs:string</span></span>|<span data-ttu-id="860ce-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="860ce-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="860ce-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="860ce-130">ExceptionActivity</span></span>|<span data-ttu-id="860ce-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-131">xs:string</span></span>|<span data-ttu-id="860ce-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="860ce-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="860ce-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="860ce-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="860ce-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-134">xs:string</span></span>|<span data-ttu-id="860ce-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="860ce-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="860ce-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="860ce-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="860ce-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-137">xs:string</span></span>|<span data-ttu-id="860ce-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="860ce-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="860ce-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="860ce-139">Exception</span></span>|<span data-ttu-id="860ce-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-140">xs:string</span></span>|<span data-ttu-id="860ce-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="860ce-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="860ce-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="860ce-142">AppDomain</span></span>|<span data-ttu-id="860ce-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="860ce-143">xs:string</span></span>|<span data-ttu-id="860ce-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="860ce-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
