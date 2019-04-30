---
title: 1017 – ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924485"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="cb13c-102">1017 – ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="cb13c-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="cb13c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cb13c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb13c-104">ID</span><span class="sxs-lookup"><span data-stu-id="cb13c-104">ID</span></span>|<span data-ttu-id="cb13c-105">1017</span><span class="sxs-lookup"><span data-stu-id="cb13c-105">1017</span></span>|  
|<span data-ttu-id="cb13c-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="cb13c-106">Keywords</span></span>|<span data-ttu-id="cb13c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cb13c-107">WFRuntime</span></span>|  
|<span data-ttu-id="cb13c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="cb13c-108">Level</span></span>|<span data-ttu-id="cb13c-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cb13c-109">Verbose</span></span>|  
|<span data-ttu-id="cb13c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="cb13c-110">Channel</span></span>|<span data-ttu-id="cb13c-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="cb13c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cb13c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cb13c-112">Description</span></span>  
 <span data-ttu-id="cb13c-113">Označuje, že položka CancelActivityWorkItem byla plánována.</span><span class="sxs-lookup"><span data-stu-id="cb13c-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cb13c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="cb13c-114">Message</span></span>  
 <span data-ttu-id="cb13c-115">Položka CancelActivityWorkItem byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="cb13c-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cb13c-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cb13c-116">Details</span></span>  
  
|<span data-ttu-id="cb13c-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="cb13c-117">Data Item Name</span></span>|<span data-ttu-id="cb13c-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="cb13c-118">Data Item Type</span></span>|<span data-ttu-id="cb13c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="cb13c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cb13c-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="cb13c-120">Activity</span></span>|<span data-ttu-id="cb13c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="cb13c-121">xs:string</span></span>|<span data-ttu-id="cb13c-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb13c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="cb13c-123">displayName</span><span class="sxs-lookup"><span data-stu-id="cb13c-123">DisplayName</span></span>|<span data-ttu-id="cb13c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="cb13c-124">xs:string</span></span>|<span data-ttu-id="cb13c-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb13c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="cb13c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="cb13c-126">InstanceId</span></span>|<span data-ttu-id="cb13c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="cb13c-127">xs:string</span></span>|<span data-ttu-id="cb13c-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb13c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="cb13c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cb13c-129">AppDomain</span></span>|<span data-ttu-id="cb13c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="cb13c-130">xs:string</span></span>|<span data-ttu-id="cb13c-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cb13c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
