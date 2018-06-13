---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510031"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="aa268-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="aa268-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="aa268-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aa268-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa268-104">ID</span><span class="sxs-lookup"><span data-stu-id="aa268-104">ID</span></span>|<span data-ttu-id="aa268-105">1035</span><span class="sxs-lookup"><span data-stu-id="aa268-105">1035</span></span>|  
|<span data-ttu-id="aa268-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="aa268-106">Keywords</span></span>|<span data-ttu-id="aa268-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aa268-107">WFRuntime</span></span>|  
|<span data-ttu-id="aa268-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="aa268-108">Level</span></span>|<span data-ttu-id="aa268-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="aa268-109">Verbose</span></span>|  
|<span data-ttu-id="aa268-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="aa268-110">Channel</span></span>|<span data-ttu-id="aa268-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="aa268-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aa268-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aa268-112">Description</span></span>  
 <span data-ttu-id="aa268-113">Značí, že aktivita má nastaven runtime transakce.</span><span class="sxs-lookup"><span data-stu-id="aa268-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aa268-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="aa268-114">Message</span></span>  
 <span data-ttu-id="aa268-115">Modul runtime transakce byla nastavena pomocí aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="aa268-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="aa268-116">Provádění izolované k aktivitě %4, DisplayName: '%5', identifikátor InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="aa268-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aa268-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aa268-117">Details</span></span>  
  
|<span data-ttu-id="aa268-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="aa268-118">Data Item Name</span></span>|<span data-ttu-id="aa268-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="aa268-119">Data Item Type</span></span>|<span data-ttu-id="aa268-120">Popis</span><span class="sxs-lookup"><span data-stu-id="aa268-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aa268-121">Aktivita</span><span class="sxs-lookup"><span data-stu-id="aa268-121">Activity</span></span>|<span data-ttu-id="aa268-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-122">xs:string</span></span>|<span data-ttu-id="aa268-123">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="aa268-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="aa268-124">displayName</span><span class="sxs-lookup"><span data-stu-id="aa268-124">DisplayName</span></span>|<span data-ttu-id="aa268-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-125">xs:string</span></span>|<span data-ttu-id="aa268-126">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="aa268-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="aa268-127">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="aa268-127">InstanceId</span></span>|<span data-ttu-id="aa268-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-128">xs:string</span></span>|<span data-ttu-id="aa268-129">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="aa268-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="aa268-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="aa268-130">IsolatedActivity</span></span>|<span data-ttu-id="aa268-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-131">xs:string</span></span>|<span data-ttu-id="aa268-132">Název typu aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="aa268-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="aa268-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="aa268-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="aa268-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-134">xs:string</span></span>|<span data-ttu-id="aa268-135">Zobrazovaný název aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="aa268-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="aa268-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="aa268-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="aa268-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-137">xs:string</span></span>|<span data-ttu-id="aa268-138">Id instance aktivity, která je pro izolované transakce.</span><span class="sxs-lookup"><span data-stu-id="aa268-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="aa268-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aa268-139">AppDomain</span></span>|<span data-ttu-id="aa268-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="aa268-140">xs:string</span></span>|<span data-ttu-id="aa268-141">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aa268-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
