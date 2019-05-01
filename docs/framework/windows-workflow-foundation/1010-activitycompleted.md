---
title: 1010 – ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008368"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="c9882-102">1010 – ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="c9882-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="c9882-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9882-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9882-104">ID</span><span class="sxs-lookup"><span data-stu-id="c9882-104">ID</span></span>|<span data-ttu-id="c9882-105">1010</span><span class="sxs-lookup"><span data-stu-id="c9882-105">1010</span></span>|  
|<span data-ttu-id="c9882-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c9882-106">Keywords</span></span>|<span data-ttu-id="c9882-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9882-107">WFRuntime</span></span>|  
|<span data-ttu-id="c9882-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="c9882-108">Level</span></span>|<span data-ttu-id="c9882-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="c9882-109">Information</span></span>|  
|<span data-ttu-id="c9882-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="c9882-110">Channel</span></span>|<span data-ttu-id="c9882-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="c9882-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9882-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c9882-112">Description</span></span>  
 <span data-ttu-id="c9882-113">Označuje, že aktivita byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="c9882-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9882-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c9882-114">Message</span></span>  
 <span data-ttu-id="c9882-115">Aktivita '%1', DisplayName: %2, InstanceId: '%3' byla dokončena ve stavu "%4".</span><span class="sxs-lookup"><span data-stu-id="c9882-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9882-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c9882-116">Details</span></span>  
  
|<span data-ttu-id="c9882-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="c9882-117">Data Item Name</span></span>|<span data-ttu-id="c9882-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="c9882-118">Data Item Type</span></span>|<span data-ttu-id="c9882-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c9882-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9882-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="c9882-120">Activity</span></span>|<span data-ttu-id="c9882-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9882-121">xs:string</span></span>|<span data-ttu-id="c9882-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9882-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c9882-123">displayName</span><span class="sxs-lookup"><span data-stu-id="c9882-123">DisplayName</span></span>|<span data-ttu-id="c9882-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9882-124">xs:string</span></span>|<span data-ttu-id="c9882-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9882-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c9882-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c9882-126">InstanceId</span></span>|<span data-ttu-id="c9882-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9882-127">xs:string</span></span>|<span data-ttu-id="c9882-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9882-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c9882-129">Stav</span><span class="sxs-lookup"><span data-stu-id="c9882-129">State</span></span>|<span data-ttu-id="c9882-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9882-130">xs:string</span></span>|<span data-ttu-id="c9882-131">Stav aktivity.</span><span class="sxs-lookup"><span data-stu-id="c9882-131">The state of the activity.</span></span>|  
|<span data-ttu-id="c9882-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9882-132">AppDomain</span></span>|<span data-ttu-id="c9882-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9882-133">xs:string</span></span>|<span data-ttu-id="c9882-134">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c9882-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
