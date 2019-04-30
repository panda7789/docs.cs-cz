---
title: 1012 – StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924576"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="ad2ba-102">1012 – StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="ad2ba-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ad2ba-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ad2ba-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad2ba-104">ID</span><span class="sxs-lookup"><span data-stu-id="ad2ba-104">ID</span></span>|<span data-ttu-id="ad2ba-105">1012</span><span class="sxs-lookup"><span data-stu-id="ad2ba-105">1012</span></span>|  
|<span data-ttu-id="ad2ba-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ad2ba-106">Keywords</span></span>|<span data-ttu-id="ad2ba-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ad2ba-107">WFRuntime</span></span>|  
|<span data-ttu-id="ad2ba-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ad2ba-108">Level</span></span>|<span data-ttu-id="ad2ba-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ad2ba-109">Verbose</span></span>|  
|<span data-ttu-id="ad2ba-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ad2ba-110">Channel</span></span>|<span data-ttu-id="ad2ba-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ad2ba-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad2ba-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ad2ba-112">Description</span></span>  
 <span data-ttu-id="ad2ba-113">Označuje, že ExecuteActivityWorkItem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="ad2ba-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad2ba-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ad2ba-114">Message</span></span>  
 <span data-ttu-id="ad2ba-115">Začátek provádění ExecuteActivityWorkItem pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ad2ba-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad2ba-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ad2ba-116">Details</span></span>  
  
|<span data-ttu-id="ad2ba-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ad2ba-117">Data Item Name</span></span>|<span data-ttu-id="ad2ba-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="ad2ba-118">Data Item Type</span></span>|<span data-ttu-id="ad2ba-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ad2ba-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad2ba-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="ad2ba-120">Activity</span></span>|<span data-ttu-id="ad2ba-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad2ba-121">xs:string</span></span>|<span data-ttu-id="ad2ba-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="ad2ba-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ad2ba-123">displayName</span><span class="sxs-lookup"><span data-stu-id="ad2ba-123">DisplayName</span></span>|<span data-ttu-id="ad2ba-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad2ba-124">xs:string</span></span>|<span data-ttu-id="ad2ba-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="ad2ba-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ad2ba-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ad2ba-126">InstanceId</span></span>|<span data-ttu-id="ad2ba-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad2ba-127">xs:string</span></span>|<span data-ttu-id="ad2ba-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="ad2ba-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ad2ba-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ad2ba-129">AppDomain</span></span>|<span data-ttu-id="ad2ba-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad2ba-130">xs:string</span></span>|<span data-ttu-id="ad2ba-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ad2ba-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
