---
title: 1034 – CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: bd49c608a8f6a6caab6975850507a00a2c0edb03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924550"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="fb8ea-102">1034 – CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="fb8ea-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fb8ea-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fb8ea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb8ea-104">ID</span><span class="sxs-lookup"><span data-stu-id="fb8ea-104">ID</span></span>|<span data-ttu-id="fb8ea-105">1034</span><span class="sxs-lookup"><span data-stu-id="fb8ea-105">1034</span></span>|  
|<span data-ttu-id="fb8ea-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fb8ea-106">Keywords</span></span>|<span data-ttu-id="fb8ea-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fb8ea-107">WFRuntime</span></span>|  
|<span data-ttu-id="fb8ea-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="fb8ea-108">Level</span></span>|<span data-ttu-id="fb8ea-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fb8ea-109">Verbose</span></span>|  
|<span data-ttu-id="fb8ea-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="fb8ea-110">Channel</span></span>|<span data-ttu-id="fb8ea-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="fb8ea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fb8ea-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fb8ea-112">Description</span></span>  
 <span data-ttu-id="fb8ea-113">Označuje, že že runtimeworkitem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="fb8ea-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fb8ea-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="fb8ea-114">Message</span></span>  
 <span data-ttu-id="fb8ea-115">Běhová pracovní položka byla dokončena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="fb8ea-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fb8ea-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fb8ea-116">Details</span></span>  
  
|<span data-ttu-id="fb8ea-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="fb8ea-117">Data Item Name</span></span>|<span data-ttu-id="fb8ea-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="fb8ea-118">Data Item Type</span></span>|<span data-ttu-id="fb8ea-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fb8ea-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fb8ea-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="fb8ea-120">Activity</span></span>|<span data-ttu-id="fb8ea-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb8ea-121">xs:string</span></span>|<span data-ttu-id="fb8ea-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb8ea-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="fb8ea-123">displayName</span><span class="sxs-lookup"><span data-stu-id="fb8ea-123">DisplayName</span></span>|<span data-ttu-id="fb8ea-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb8ea-124">xs:string</span></span>|<span data-ttu-id="fb8ea-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb8ea-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="fb8ea-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fb8ea-126">InstanceId</span></span>|<span data-ttu-id="fb8ea-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb8ea-127">xs:string</span></span>|<span data-ttu-id="fb8ea-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="fb8ea-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="fb8ea-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fb8ea-129">AppDomain</span></span>|<span data-ttu-id="fb8ea-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="fb8ea-130">xs:string</span></span>|<span data-ttu-id="fb8ea-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fb8ea-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
