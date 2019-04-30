---
title: 1029 – ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924355"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="f6a60-102">1029 – ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="f6a60-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f6a60-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f6a60-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6a60-104">ID</span><span class="sxs-lookup"><span data-stu-id="f6a60-104">ID</span></span>|<span data-ttu-id="f6a60-105">1029</span><span class="sxs-lookup"><span data-stu-id="f6a60-105">1029</span></span>|  
|<span data-ttu-id="f6a60-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f6a60-106">Keywords</span></span>|<span data-ttu-id="f6a60-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f6a60-107">WFRuntime</span></span>|  
|<span data-ttu-id="f6a60-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f6a60-108">Level</span></span>|<span data-ttu-id="f6a60-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f6a60-109">Verbose</span></span>|  
|<span data-ttu-id="f6a60-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f6a60-110">Channel</span></span>|<span data-ttu-id="f6a60-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="f6a60-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6a60-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f6a60-112">Description</span></span>  
 <span data-ttu-id="f6a60-113">Označuje, že položka FaultWorkItem byla plánována.</span><span class="sxs-lookup"><span data-stu-id="f6a60-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6a60-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f6a60-114">Message</span></span>  
 <span data-ttu-id="f6a60-115">Položka FaultWorkItem byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="f6a60-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="f6a60-116">Výjimka byla rozšířena z aktivity %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="f6a60-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6a60-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f6a60-117">Details</span></span>  
  
|<span data-ttu-id="f6a60-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f6a60-118">Data Item Name</span></span>|<span data-ttu-id="f6a60-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="f6a60-119">Data Item Type</span></span>|<span data-ttu-id="f6a60-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f6a60-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6a60-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="f6a60-121">FaultActivity</span></span>|<span data-ttu-id="f6a60-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-122">xs:string</span></span>|<span data-ttu-id="f6a60-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="f6a60-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="f6a60-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f6a60-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="f6a60-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-125">xs:string</span></span>|<span data-ttu-id="f6a60-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="f6a60-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="f6a60-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f6a60-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="f6a60-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-128">xs:string</span></span>|<span data-ttu-id="f6a60-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="f6a60-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="f6a60-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="f6a60-130">ExceptionActivity</span></span>|<span data-ttu-id="f6a60-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-131">xs:string</span></span>|<span data-ttu-id="f6a60-132">Název typu aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="f6a60-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f6a60-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f6a60-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="f6a60-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-134">xs:string</span></span>|<span data-ttu-id="f6a60-135">Zobrazovaný název aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="f6a60-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f6a60-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f6a60-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="f6a60-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-137">xs:string</span></span>|<span data-ttu-id="f6a60-138">Id instance aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="f6a60-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f6a60-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="f6a60-139">Exception</span></span>|<span data-ttu-id="f6a60-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-140">xs:string</span></span>|<span data-ttu-id="f6a60-141">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="f6a60-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="f6a60-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6a60-142">AppDomain</span></span>|<span data-ttu-id="f6a60-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="f6a60-143">xs:string</span></span>|<span data-ttu-id="f6a60-144">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f6a60-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
