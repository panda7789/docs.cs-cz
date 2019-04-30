---
title: 1030 – StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924316"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="4aea5-102">1030 – StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="4aea5-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4aea5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4aea5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4aea5-104">ID</span><span class="sxs-lookup"><span data-stu-id="4aea5-104">ID</span></span>|<span data-ttu-id="4aea5-105">1030</span><span class="sxs-lookup"><span data-stu-id="4aea5-105">1030</span></span>|  
|<span data-ttu-id="4aea5-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4aea5-106">Keywords</span></span>|<span data-ttu-id="4aea5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4aea5-107">WFRuntime</span></span>|  
|<span data-ttu-id="4aea5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="4aea5-108">Level</span></span>|<span data-ttu-id="4aea5-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4aea5-109">Verbose</span></span>|  
|<span data-ttu-id="4aea5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="4aea5-110">Channel</span></span>|<span data-ttu-id="4aea5-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="4aea5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4aea5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4aea5-112">Description</span></span>  
 <span data-ttu-id="4aea5-113">Označuje, že položka FaultWorkItem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="4aea5-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4aea5-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="4aea5-114">Message</span></span>  
 <span data-ttu-id="4aea5-115">Začátek provádění položky FaultWorkItem pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="4aea5-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="4aea5-116">Výjimka byla rozšířena z aktivity %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="4aea5-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4aea5-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4aea5-117">Details</span></span>  
  
|<span data-ttu-id="4aea5-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="4aea5-118">Data Item Name</span></span>|<span data-ttu-id="4aea5-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="4aea5-119">Data Item Type</span></span>|<span data-ttu-id="4aea5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="4aea5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4aea5-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="4aea5-121">FaultActivity</span></span>|<span data-ttu-id="4aea5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-122">xs:string</span></span>|<span data-ttu-id="4aea5-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="4aea5-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="4aea5-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="4aea5-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="4aea5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-125">xs:string</span></span>|<span data-ttu-id="4aea5-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="4aea5-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="4aea5-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="4aea5-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="4aea5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-128">xs:string</span></span>|<span data-ttu-id="4aea5-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="4aea5-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="4aea5-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="4aea5-130">ExceptionActivity</span></span>|<span data-ttu-id="4aea5-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-131">xs:string</span></span>|<span data-ttu-id="4aea5-132">Název typu aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="4aea5-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="4aea5-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="4aea5-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="4aea5-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-134">xs:string</span></span>|<span data-ttu-id="4aea5-135">Zobrazovaný název aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="4aea5-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="4aea5-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="4aea5-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="4aea5-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-137">xs:string</span></span>|<span data-ttu-id="4aea5-138">Id instance aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="4aea5-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="4aea5-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="4aea5-139">Exception</span></span>|<span data-ttu-id="4aea5-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-140">xs:string</span></span>|<span data-ttu-id="4aea5-141">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="4aea5-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="4aea5-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4aea5-142">AppDomain</span></span>|<span data-ttu-id="4aea5-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="4aea5-143">xs:string</span></span>|<span data-ttu-id="4aea5-144">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4aea5-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
