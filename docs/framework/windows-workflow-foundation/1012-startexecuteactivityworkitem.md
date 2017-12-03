---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a06cec1ab251b8f7e82aef71589bd56e5f55f2e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="5b727-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="5b727-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5b727-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5b727-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b727-104">ID</span><span class="sxs-lookup"><span data-stu-id="5b727-104">ID</span></span>|<span data-ttu-id="5b727-105">1012</span><span class="sxs-lookup"><span data-stu-id="5b727-105">1012</span></span>|  
|<span data-ttu-id="5b727-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5b727-106">Keywords</span></span>|<span data-ttu-id="5b727-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5b727-107">WFRuntime</span></span>|  
|<span data-ttu-id="5b727-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5b727-108">Level</span></span>|<span data-ttu-id="5b727-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="5b727-109">Verbose</span></span>|  
|<span data-ttu-id="5b727-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5b727-110">Channel</span></span>|<span data-ttu-id="5b727-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="5b727-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5b727-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5b727-112">Description</span></span>  
 <span data-ttu-id="5b727-113">Označuje, že že executeactivityworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="5b727-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5b727-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5b727-114">Message</span></span>  
 <span data-ttu-id="5b727-115">Od spuštění ExecuteActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="5b727-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5b727-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5b727-116">Details</span></span>  
  
|<span data-ttu-id="5b727-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5b727-117">Data Item Name</span></span>|<span data-ttu-id="5b727-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5b727-118">Data Item Type</span></span>|<span data-ttu-id="5b727-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5b727-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5b727-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="5b727-120">Activity</span></span>|<span data-ttu-id="5b727-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="5b727-121">xs:string</span></span>|<span data-ttu-id="5b727-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="5b727-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="5b727-123">displayName</span><span class="sxs-lookup"><span data-stu-id="5b727-123">DisplayName</span></span>|<span data-ttu-id="5b727-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="5b727-124">xs:string</span></span>|<span data-ttu-id="5b727-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="5b727-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="5b727-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="5b727-126">InstanceId</span></span>|<span data-ttu-id="5b727-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="5b727-127">xs:string</span></span>|<span data-ttu-id="5b727-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="5b727-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5b727-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5b727-129">AppDomain</span></span>|<span data-ttu-id="5b727-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="5b727-130">xs:string</span></span>|<span data-ttu-id="5b727-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5b727-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
