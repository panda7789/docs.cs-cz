---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510244"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="2e10d-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="2e10d-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2e10d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2e10d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e10d-104">ID</span><span class="sxs-lookup"><span data-stu-id="2e10d-104">ID</span></span>|<span data-ttu-id="2e10d-105">1032</span><span class="sxs-lookup"><span data-stu-id="2e10d-105">1032</span></span>|  
|<span data-ttu-id="2e10d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2e10d-106">Keywords</span></span>|<span data-ttu-id="2e10d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2e10d-107">WFRuntime</span></span>|  
|<span data-ttu-id="2e10d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2e10d-108">Level</span></span>|<span data-ttu-id="2e10d-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="2e10d-109">Verbose</span></span>|  
|<span data-ttu-id="2e10d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2e10d-110">Channel</span></span>|<span data-ttu-id="2e10d-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="2e10d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2e10d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2e10d-112">Description</span></span>  
 <span data-ttu-id="2e10d-113">Označuje, že bylo naplánováno RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="2e10d-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2e10d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2e10d-114">Message</span></span>  
 <span data-ttu-id="2e10d-115">Modul runtime pracovní položky bylo naplánováno aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2e10d-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2e10d-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2e10d-116">Details</span></span>  
  
|<span data-ttu-id="2e10d-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2e10d-117">Data Item Name</span></span>|<span data-ttu-id="2e10d-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2e10d-118">Data Item Type</span></span>|<span data-ttu-id="2e10d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2e10d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2e10d-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="2e10d-120">Activity</span></span>|<span data-ttu-id="2e10d-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="2e10d-121">xs:string</span></span>|<span data-ttu-id="2e10d-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="2e10d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2e10d-123">displayName</span><span class="sxs-lookup"><span data-stu-id="2e10d-123">DisplayName</span></span>|<span data-ttu-id="2e10d-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="2e10d-124">xs:string</span></span>|<span data-ttu-id="2e10d-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="2e10d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2e10d-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="2e10d-126">InstanceId</span></span>|<span data-ttu-id="2e10d-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="2e10d-127">xs:string</span></span>|<span data-ttu-id="2e10d-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="2e10d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2e10d-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2e10d-129">AppDomain</span></span>|<span data-ttu-id="2e10d-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="2e10d-130">xs:string</span></span>|<span data-ttu-id="2e10d-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2e10d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
