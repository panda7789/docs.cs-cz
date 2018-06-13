---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509571"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="cc23e-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="cc23e-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="cc23e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cc23e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cc23e-104">ID</span><span class="sxs-lookup"><span data-stu-id="cc23e-104">ID</span></span>|<span data-ttu-id="cc23e-105">1013</span><span class="sxs-lookup"><span data-stu-id="cc23e-105">1013</span></span>|  
|<span data-ttu-id="cc23e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="cc23e-106">Keywords</span></span>|<span data-ttu-id="cc23e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cc23e-107">WFRuntime</span></span>|  
|<span data-ttu-id="cc23e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="cc23e-108">Level</span></span>|<span data-ttu-id="cc23e-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="cc23e-109">Verbose</span></span>|  
|<span data-ttu-id="cc23e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="cc23e-110">Channel</span></span>|<span data-ttu-id="cc23e-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="cc23e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cc23e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cc23e-112">Description</span></span>  
 <span data-ttu-id="cc23e-113">Označuje, že že executeactivityworkitem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="cc23e-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="cc23e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="cc23e-114">Message</span></span>  
 <span data-ttu-id="cc23e-115">ExecuteActivityWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="cc23e-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cc23e-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cc23e-116">Details</span></span>  
  
|<span data-ttu-id="cc23e-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="cc23e-117">Data Item Name</span></span>|<span data-ttu-id="cc23e-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="cc23e-118">Data Item Type</span></span>|<span data-ttu-id="cc23e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="cc23e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cc23e-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="cc23e-120">Activity</span></span>|<span data-ttu-id="cc23e-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="cc23e-121">xs:string</span></span>|<span data-ttu-id="cc23e-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="cc23e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="cc23e-123">displayName</span><span class="sxs-lookup"><span data-stu-id="cc23e-123">DisplayName</span></span>|<span data-ttu-id="cc23e-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="cc23e-124">xs:string</span></span>|<span data-ttu-id="cc23e-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="cc23e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="cc23e-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="cc23e-126">InstanceId</span></span>|<span data-ttu-id="cc23e-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="cc23e-127">xs:string</span></span>|<span data-ttu-id="cc23e-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="cc23e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="cc23e-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="cc23e-129">AppDomain</span></span>|<span data-ttu-id="cc23e-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="cc23e-130">xs:string</span></span>|<span data-ttu-id="cc23e-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cc23e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
