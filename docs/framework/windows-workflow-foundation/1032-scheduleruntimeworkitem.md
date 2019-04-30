---
title: 1032 – ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924862"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="e2de7-102">1032 – ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="e2de7-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e2de7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e2de7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2de7-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2de7-104">ID</span></span>|<span data-ttu-id="e2de7-105">1032</span><span class="sxs-lookup"><span data-stu-id="e2de7-105">1032</span></span>|  
|<span data-ttu-id="e2de7-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e2de7-106">Keywords</span></span>|<span data-ttu-id="e2de7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e2de7-107">WFRuntime</span></span>|  
|<span data-ttu-id="e2de7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e2de7-108">Level</span></span>|<span data-ttu-id="e2de7-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e2de7-109">Verbose</span></span>|  
|<span data-ttu-id="e2de7-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e2de7-110">Channel</span></span>|<span data-ttu-id="e2de7-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e2de7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2de7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e2de7-112">Description</span></span>  
 <span data-ttu-id="e2de7-113">Označuje, že je naplánovaná RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="e2de7-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2de7-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e2de7-114">Message</span></span>  
 <span data-ttu-id="e2de7-115">Běhová pracovní položka byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e2de7-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2de7-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e2de7-116">Details</span></span>  
  
|<span data-ttu-id="e2de7-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e2de7-117">Data Item Name</span></span>|<span data-ttu-id="e2de7-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e2de7-118">Data Item Type</span></span>|<span data-ttu-id="e2de7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e2de7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2de7-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="e2de7-120">Activity</span></span>|<span data-ttu-id="e2de7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2de7-121">xs:string</span></span>|<span data-ttu-id="e2de7-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="e2de7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e2de7-123">displayName</span><span class="sxs-lookup"><span data-stu-id="e2de7-123">DisplayName</span></span>|<span data-ttu-id="e2de7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2de7-124">xs:string</span></span>|<span data-ttu-id="e2de7-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="e2de7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e2de7-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e2de7-126">InstanceId</span></span>|<span data-ttu-id="e2de7-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2de7-127">xs:string</span></span>|<span data-ttu-id="e2de7-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="e2de7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e2de7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2de7-129">AppDomain</span></span>|<span data-ttu-id="e2de7-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e2de7-130">xs:string</span></span>|<span data-ttu-id="e2de7-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e2de7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
