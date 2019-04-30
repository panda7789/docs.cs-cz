---
title: 1013 – CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925187"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="1333c-102">1013 – CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="1333c-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1333c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1333c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1333c-104">ID</span><span class="sxs-lookup"><span data-stu-id="1333c-104">ID</span></span>|<span data-ttu-id="1333c-105">1013</span><span class="sxs-lookup"><span data-stu-id="1333c-105">1013</span></span>|  
|<span data-ttu-id="1333c-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1333c-106">Keywords</span></span>|<span data-ttu-id="1333c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1333c-107">WFRuntime</span></span>|  
|<span data-ttu-id="1333c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1333c-108">Level</span></span>|<span data-ttu-id="1333c-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1333c-109">Verbose</span></span>|  
|<span data-ttu-id="1333c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1333c-110">Channel</span></span>|<span data-ttu-id="1333c-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="1333c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1333c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1333c-112">Description</span></span>  
 <span data-ttu-id="1333c-113">Indikuje, že se že položka ExecuteActivityWorkItem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="1333c-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="1333c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1333c-114">Message</span></span>  
 <span data-ttu-id="1333c-115">Položka ExecuteActivityWorkItem byla dokončena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="1333c-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1333c-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1333c-116">Details</span></span>  
  
|<span data-ttu-id="1333c-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1333c-117">Data Item Name</span></span>|<span data-ttu-id="1333c-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="1333c-118">Data Item Type</span></span>|<span data-ttu-id="1333c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1333c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1333c-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="1333c-120">Activity</span></span>|<span data-ttu-id="1333c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1333c-121">xs:string</span></span>|<span data-ttu-id="1333c-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="1333c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1333c-123">displayName</span><span class="sxs-lookup"><span data-stu-id="1333c-123">DisplayName</span></span>|<span data-ttu-id="1333c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1333c-124">xs:string</span></span>|<span data-ttu-id="1333c-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="1333c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1333c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1333c-126">InstanceId</span></span>|<span data-ttu-id="1333c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1333c-127">xs:string</span></span>|<span data-ttu-id="1333c-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="1333c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1333c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1333c-129">AppDomain</span></span>|<span data-ttu-id="1333c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1333c-130">xs:string</span></span>|<span data-ttu-id="1333c-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1333c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
