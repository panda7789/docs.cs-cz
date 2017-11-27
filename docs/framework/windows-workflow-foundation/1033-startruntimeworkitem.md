---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0de8e45a592cae49060f976b28a7a7bcf8781265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="60a02-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="60a02-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="60a02-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="60a02-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60a02-104">ID</span><span class="sxs-lookup"><span data-stu-id="60a02-104">ID</span></span>|<span data-ttu-id="60a02-105">1033</span><span class="sxs-lookup"><span data-stu-id="60a02-105">1033</span></span>|  
|<span data-ttu-id="60a02-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="60a02-106">Keywords</span></span>|<span data-ttu-id="60a02-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="60a02-107">WFRuntime</span></span>|  
|<span data-ttu-id="60a02-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="60a02-108">Level</span></span>|<span data-ttu-id="60a02-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="60a02-109">Verbose</span></span>|  
|<span data-ttu-id="60a02-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="60a02-110">Channel</span></span>|<span data-ttu-id="60a02-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="60a02-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="60a02-112">Popis</span><span class="sxs-lookup"><span data-stu-id="60a02-112">Description</span></span>  
 <span data-ttu-id="60a02-113">Označuje, že že runtimeworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="60a02-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="60a02-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="60a02-114">Message</span></span>  
 <span data-ttu-id="60a02-115">Spouštění spuštění pracovní položky modulu runtime pro aktivitu %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="60a02-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="60a02-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="60a02-116">Details</span></span>  
  
|<span data-ttu-id="60a02-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="60a02-117">Data Item Name</span></span>|<span data-ttu-id="60a02-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="60a02-118">Data Item Type</span></span>|<span data-ttu-id="60a02-119">Popis</span><span class="sxs-lookup"><span data-stu-id="60a02-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="60a02-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="60a02-120">Activity</span></span>|<span data-ttu-id="60a02-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="60a02-121">xs:string</span></span>|<span data-ttu-id="60a02-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="60a02-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="60a02-123">displayName</span><span class="sxs-lookup"><span data-stu-id="60a02-123">DisplayName</span></span>|<span data-ttu-id="60a02-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="60a02-124">xs:string</span></span>|<span data-ttu-id="60a02-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="60a02-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="60a02-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="60a02-126">InstanceId</span></span>|<span data-ttu-id="60a02-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="60a02-127">xs:string</span></span>|<span data-ttu-id="60a02-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="60a02-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="60a02-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="60a02-129">AppDomain</span></span>|<span data-ttu-id="60a02-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="60a02-130">xs:string</span></span>|<span data-ttu-id="60a02-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="60a02-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
