---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509677"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="c66b5-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="c66b5-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c66b5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c66b5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c66b5-104">ID</span><span class="sxs-lookup"><span data-stu-id="c66b5-104">ID</span></span>|<span data-ttu-id="c66b5-105">1030</span><span class="sxs-lookup"><span data-stu-id="c66b5-105">1030</span></span>|  
|<span data-ttu-id="c66b5-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c66b5-106">Keywords</span></span>|<span data-ttu-id="c66b5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c66b5-107">WFRuntime</span></span>|  
|<span data-ttu-id="c66b5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="c66b5-108">Level</span></span>|<span data-ttu-id="c66b5-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="c66b5-109">Verbose</span></span>|  
|<span data-ttu-id="c66b5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="c66b5-110">Channel</span></span>|<span data-ttu-id="c66b5-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="c66b5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c66b5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c66b5-112">Description</span></span>  
 <span data-ttu-id="c66b5-113">Označuje, že že faultworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="c66b5-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c66b5-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c66b5-114">Message</span></span>  
 <span data-ttu-id="c66b5-115">Spuštění provádění FaultWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c66b5-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c66b5-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c66b5-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c66b5-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c66b5-117">Details</span></span>  
  
|<span data-ttu-id="c66b5-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="c66b5-118">Data Item Name</span></span>|<span data-ttu-id="c66b5-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="c66b5-119">Data Item Type</span></span>|<span data-ttu-id="c66b5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c66b5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c66b5-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="c66b5-121">FaultActivity</span></span>|<span data-ttu-id="c66b5-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-122">xs:string</span></span>|<span data-ttu-id="c66b5-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="c66b5-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="c66b5-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c66b5-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="c66b5-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-125">xs:string</span></span>|<span data-ttu-id="c66b5-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="c66b5-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="c66b5-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c66b5-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="c66b5-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-128">xs:string</span></span>|<span data-ttu-id="c66b5-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="c66b5-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="c66b5-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="c66b5-130">ExceptionActivity</span></span>|<span data-ttu-id="c66b5-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-131">xs:string</span></span>|<span data-ttu-id="c66b5-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="c66b5-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c66b5-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c66b5-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="c66b5-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-134">xs:string</span></span>|<span data-ttu-id="c66b5-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="c66b5-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c66b5-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c66b5-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="c66b5-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-137">xs:string</span></span>|<span data-ttu-id="c66b5-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="c66b5-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c66b5-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="c66b5-139">Exception</span></span>|<span data-ttu-id="c66b5-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-140">xs:string</span></span>|<span data-ttu-id="c66b5-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="c66b5-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="c66b5-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c66b5-142">AppDomain</span></span>|<span data-ttu-id="c66b5-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="c66b5-143">xs:string</span></span>|<span data-ttu-id="c66b5-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c66b5-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
