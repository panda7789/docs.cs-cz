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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc60af91088fd61910dc0301b93844f4771177af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="635cf-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="635cf-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="635cf-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="635cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="635cf-104">ID</span><span class="sxs-lookup"><span data-stu-id="635cf-104">ID</span></span>|<span data-ttu-id="635cf-105">1012</span><span class="sxs-lookup"><span data-stu-id="635cf-105">1012</span></span>|  
|<span data-ttu-id="635cf-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="635cf-106">Keywords</span></span>|<span data-ttu-id="635cf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="635cf-107">WFRuntime</span></span>|  
|<span data-ttu-id="635cf-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="635cf-108">Level</span></span>|<span data-ttu-id="635cf-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="635cf-109">Verbose</span></span>|  
|<span data-ttu-id="635cf-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="635cf-110">Channel</span></span>|<span data-ttu-id="635cf-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="635cf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="635cf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="635cf-112">Description</span></span>  
 <span data-ttu-id="635cf-113">Označuje, že že executeactivityworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="635cf-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="635cf-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="635cf-114">Message</span></span>  
 <span data-ttu-id="635cf-115">Od spuštění ExecuteActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="635cf-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="635cf-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="635cf-116">Details</span></span>  
  
|<span data-ttu-id="635cf-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="635cf-117">Data Item Name</span></span>|<span data-ttu-id="635cf-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="635cf-118">Data Item Type</span></span>|<span data-ttu-id="635cf-119">Popis</span><span class="sxs-lookup"><span data-stu-id="635cf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="635cf-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="635cf-120">Activity</span></span>|<span data-ttu-id="635cf-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="635cf-121">xs:string</span></span>|<span data-ttu-id="635cf-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="635cf-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="635cf-123">displayName</span><span class="sxs-lookup"><span data-stu-id="635cf-123">DisplayName</span></span>|<span data-ttu-id="635cf-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="635cf-124">xs:string</span></span>|<span data-ttu-id="635cf-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="635cf-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="635cf-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="635cf-126">InstanceId</span></span>|<span data-ttu-id="635cf-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="635cf-127">xs:string</span></span>|<span data-ttu-id="635cf-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="635cf-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="635cf-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="635cf-129">AppDomain</span></span>|<span data-ttu-id="635cf-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="635cf-130">xs:string</span></span>|<span data-ttu-id="635cf-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="635cf-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
