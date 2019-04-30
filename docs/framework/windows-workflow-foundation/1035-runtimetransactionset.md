---
title: 1035 – RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924849"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="65f8a-102">1035 – RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="65f8a-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="65f8a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="65f8a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65f8a-104">ID</span><span class="sxs-lookup"><span data-stu-id="65f8a-104">ID</span></span>|<span data-ttu-id="65f8a-105">1035</span><span class="sxs-lookup"><span data-stu-id="65f8a-105">1035</span></span>|  
|<span data-ttu-id="65f8a-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="65f8a-106">Keywords</span></span>|<span data-ttu-id="65f8a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="65f8a-107">WFRuntime</span></span>|  
|<span data-ttu-id="65f8a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="65f8a-108">Level</span></span>|<span data-ttu-id="65f8a-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="65f8a-109">Verbose</span></span>|  
|<span data-ttu-id="65f8a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="65f8a-110">Channel</span></span>|<span data-ttu-id="65f8a-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="65f8a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="65f8a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="65f8a-112">Description</span></span>  
 <span data-ttu-id="65f8a-113">Označuje, že aktivita nastavil běhové transakce.</span><span class="sxs-lookup"><span data-stu-id="65f8a-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="65f8a-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="65f8a-114">Message</span></span>  
 <span data-ttu-id="65f8a-115">Běhová transakce byla nastavena aktivitou %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="65f8a-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="65f8a-116">Provádění bylo izolováno na aktivitu na %4, DisplayName: %5, InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="65f8a-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="65f8a-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="65f8a-117">Details</span></span>  
  
|<span data-ttu-id="65f8a-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="65f8a-118">Data Item Name</span></span>|<span data-ttu-id="65f8a-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="65f8a-119">Data Item Type</span></span>|<span data-ttu-id="65f8a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="65f8a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="65f8a-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="65f8a-121">Activity</span></span>|<span data-ttu-id="65f8a-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-122">xs:string</span></span>|<span data-ttu-id="65f8a-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="65f8a-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="65f8a-124">displayName</span><span class="sxs-lookup"><span data-stu-id="65f8a-124">DisplayName</span></span>|<span data-ttu-id="65f8a-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-125">xs:string</span></span>|<span data-ttu-id="65f8a-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="65f8a-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="65f8a-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="65f8a-127">InstanceId</span></span>|<span data-ttu-id="65f8a-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-128">xs:string</span></span>|<span data-ttu-id="65f8a-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="65f8a-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="65f8a-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="65f8a-130">IsolatedActivity</span></span>|<span data-ttu-id="65f8a-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-131">xs:string</span></span>|<span data-ttu-id="65f8a-132">Název typu aktivity, která transakce je izolovaná na.</span><span class="sxs-lookup"><span data-stu-id="65f8a-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="65f8a-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="65f8a-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="65f8a-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-134">xs:string</span></span>|<span data-ttu-id="65f8a-135">Zobrazovaný název aktivity, která transakce je izolováno na.</span><span class="sxs-lookup"><span data-stu-id="65f8a-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="65f8a-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="65f8a-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="65f8a-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-137">xs:string</span></span>|<span data-ttu-id="65f8a-138">Id instance, která transakce je izolovaná na aktivity.</span><span class="sxs-lookup"><span data-stu-id="65f8a-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="65f8a-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="65f8a-139">AppDomain</span></span>|<span data-ttu-id="65f8a-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="65f8a-140">xs:string</span></span>|<span data-ttu-id="65f8a-141">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="65f8a-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
