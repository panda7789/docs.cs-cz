---
title: 1031 – CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008795"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="fd054-102">1031 – CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="fd054-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fd054-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fd054-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd054-104">ID</span><span class="sxs-lookup"><span data-stu-id="fd054-104">ID</span></span>|<span data-ttu-id="fd054-105">1031</span><span class="sxs-lookup"><span data-stu-id="fd054-105">1031</span></span>|  
|<span data-ttu-id="fd054-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fd054-106">Keywords</span></span>|<span data-ttu-id="fd054-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fd054-107">WFRuntime</span></span>|  
|<span data-ttu-id="fd054-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="fd054-108">Level</span></span>|<span data-ttu-id="fd054-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fd054-109">Verbose</span></span>|  
|<span data-ttu-id="fd054-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="fd054-110">Channel</span></span>|<span data-ttu-id="fd054-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="fd054-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd054-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fd054-112">Description</span></span>  
 <span data-ttu-id="fd054-113">Označuje, že položka FaultWorkItem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="fd054-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd054-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="fd054-114">Message</span></span>  
 <span data-ttu-id="fd054-115">Položka FaultWorkItem byla dokončena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="fd054-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="fd054-116">Výjimka byla rozšířena z aktivity %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="fd054-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd054-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fd054-117">Details</span></span>  
  
|<span data-ttu-id="fd054-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="fd054-118">Data Item Name</span></span>|<span data-ttu-id="fd054-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="fd054-119">Data Item Type</span></span>|<span data-ttu-id="fd054-120">Popis</span><span class="sxs-lookup"><span data-stu-id="fd054-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd054-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="fd054-121">FaultActivity</span></span>|<span data-ttu-id="fd054-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-122">xs:string</span></span>|<span data-ttu-id="fd054-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="fd054-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="fd054-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fd054-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="fd054-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-125">xs:string</span></span>|<span data-ttu-id="fd054-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="fd054-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="fd054-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fd054-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="fd054-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-128">xs:string</span></span>|<span data-ttu-id="fd054-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="fd054-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="fd054-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="fd054-130">ExceptionActivity</span></span>|<span data-ttu-id="fd054-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-131">xs:string</span></span>|<span data-ttu-id="fd054-132">Název typu aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="fd054-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fd054-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="fd054-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="fd054-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-134">xs:string</span></span>|<span data-ttu-id="fd054-135">Zobrazovaný název aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="fd054-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fd054-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="fd054-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="fd054-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-137">xs:string</span></span>|<span data-ttu-id="fd054-138">Id instance aktivity, která vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="fd054-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="fd054-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="fd054-139">Exception</span></span>|<span data-ttu-id="fd054-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-140">xs:string</span></span>|<span data-ttu-id="fd054-141">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="fd054-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="fd054-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd054-142">AppDomain</span></span>|<span data-ttu-id="fd054-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd054-143">xs:string</span></span>|<span data-ttu-id="fd054-144">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fd054-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
