---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509740"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="9aaeb-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="9aaeb-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9aaeb-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9aaeb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9aaeb-104">ID</span><span class="sxs-lookup"><span data-stu-id="9aaeb-104">ID</span></span>|<span data-ttu-id="9aaeb-105">1031</span><span class="sxs-lookup"><span data-stu-id="9aaeb-105">1031</span></span>|  
|<span data-ttu-id="9aaeb-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9aaeb-106">Keywords</span></span>|<span data-ttu-id="9aaeb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9aaeb-107">WFRuntime</span></span>|  
|<span data-ttu-id="9aaeb-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9aaeb-108">Level</span></span>|<span data-ttu-id="9aaeb-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="9aaeb-109">Verbose</span></span>|  
|<span data-ttu-id="9aaeb-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9aaeb-110">Channel</span></span>|<span data-ttu-id="9aaeb-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9aaeb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9aaeb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9aaeb-112">Description</span></span>  
 <span data-ttu-id="9aaeb-113">Označuje, že je dokončená FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9aaeb-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9aaeb-114">Message</span></span>  
 <span data-ttu-id="9aaeb-115">FaultWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="9aaeb-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9aaeb-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9aaeb-117">Details</span></span>  
  
|<span data-ttu-id="9aaeb-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9aaeb-118">Data Item Name</span></span>|<span data-ttu-id="9aaeb-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9aaeb-119">Data Item Type</span></span>|<span data-ttu-id="9aaeb-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9aaeb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9aaeb-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="9aaeb-121">FaultActivity</span></span>|<span data-ttu-id="9aaeb-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-122">xs:string</span></span>|<span data-ttu-id="9aaeb-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="9aaeb-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9aaeb-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="9aaeb-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-125">xs:string</span></span>|<span data-ttu-id="9aaeb-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="9aaeb-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9aaeb-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="9aaeb-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-128">xs:string</span></span>|<span data-ttu-id="9aaeb-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="9aaeb-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="9aaeb-130">ExceptionActivity</span></span>|<span data-ttu-id="9aaeb-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-131">xs:string</span></span>|<span data-ttu-id="9aaeb-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9aaeb-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9aaeb-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="9aaeb-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-134">xs:string</span></span>|<span data-ttu-id="9aaeb-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9aaeb-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9aaeb-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="9aaeb-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-137">xs:string</span></span>|<span data-ttu-id="9aaeb-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9aaeb-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="9aaeb-139">Exception</span></span>|<span data-ttu-id="9aaeb-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-140">xs:string</span></span>|<span data-ttu-id="9aaeb-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="9aaeb-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="9aaeb-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9aaeb-142">AppDomain</span></span>|<span data-ttu-id="9aaeb-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="9aaeb-143">xs:string</span></span>|<span data-ttu-id="9aaeb-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9aaeb-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
