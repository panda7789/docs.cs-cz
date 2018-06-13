---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509727"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="8075f-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="8075f-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8075f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8075f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8075f-104">ID</span><span class="sxs-lookup"><span data-stu-id="8075f-104">ID</span></span>|<span data-ttu-id="8075f-105">1029</span><span class="sxs-lookup"><span data-stu-id="8075f-105">1029</span></span>|  
|<span data-ttu-id="8075f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8075f-106">Keywords</span></span>|<span data-ttu-id="8075f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8075f-107">WFRuntime</span></span>|  
|<span data-ttu-id="8075f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8075f-108">Level</span></span>|<span data-ttu-id="8075f-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="8075f-109">Verbose</span></span>|  
|<span data-ttu-id="8075f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8075f-110">Channel</span></span>|<span data-ttu-id="8075f-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="8075f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8075f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8075f-112">Description</span></span>  
 <span data-ttu-id="8075f-113">Označuje, že bylo naplánováno FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="8075f-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8075f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8075f-114">Message</span></span>  
 <span data-ttu-id="8075f-115">Bylo naplánováno FaultWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="8075f-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="8075f-116">Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8075f-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8075f-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8075f-117">Details</span></span>  
  
|<span data-ttu-id="8075f-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8075f-118">Data Item Name</span></span>|<span data-ttu-id="8075f-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8075f-119">Data Item Type</span></span>|<span data-ttu-id="8075f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="8075f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8075f-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="8075f-121">FaultActivity</span></span>|<span data-ttu-id="8075f-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-122">xs:string</span></span>|<span data-ttu-id="8075f-123">Název typu selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="8075f-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="8075f-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8075f-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="8075f-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-125">xs:string</span></span>|<span data-ttu-id="8075f-126">Zobrazovaný název selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="8075f-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="8075f-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8075f-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="8075f-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-128">xs:string</span></span>|<span data-ttu-id="8075f-129">Id instance selhání aktivity.</span><span class="sxs-lookup"><span data-stu-id="8075f-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="8075f-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="8075f-130">ExceptionActivity</span></span>|<span data-ttu-id="8075f-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-131">xs:string</span></span>|<span data-ttu-id="8075f-132">Název typu aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="8075f-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8075f-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8075f-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="8075f-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-134">xs:string</span></span>|<span data-ttu-id="8075f-135">Zobrazovaný název aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="8075f-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8075f-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8075f-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="8075f-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-137">xs:string</span></span>|<span data-ttu-id="8075f-138">Id instance aktivity, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="8075f-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8075f-139">Výjimka</span><span class="sxs-lookup"><span data-stu-id="8075f-139">Exception</span></span>|<span data-ttu-id="8075f-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-140">xs:string</span></span>|<span data-ttu-id="8075f-141">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="8075f-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="8075f-142">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8075f-142">AppDomain</span></span>|<span data-ttu-id="8075f-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="8075f-143">xs:string</span></span>|<span data-ttu-id="8075f-144">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8075f-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
