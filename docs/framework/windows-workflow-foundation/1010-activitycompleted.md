---
title: 1010 - ActivityCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1378ddd1550db614c9eddc44f79b19ff94ed585c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="9e81b-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="9e81b-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="9e81b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9e81b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e81b-104">ID</span><span class="sxs-lookup"><span data-stu-id="9e81b-104">ID</span></span>|<span data-ttu-id="9e81b-105">1010</span><span class="sxs-lookup"><span data-stu-id="9e81b-105">1010</span></span>|  
|<span data-ttu-id="9e81b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9e81b-106">Keywords</span></span>|<span data-ttu-id="9e81b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9e81b-107">WFRuntime</span></span>|  
|<span data-ttu-id="9e81b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9e81b-108">Level</span></span>|<span data-ttu-id="9e81b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="9e81b-109">Information</span></span>|  
|<span data-ttu-id="9e81b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9e81b-110">Channel</span></span>|<span data-ttu-id="9e81b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9e81b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9e81b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9e81b-112">Description</span></span>  
 <span data-ttu-id="9e81b-113">Označuje, že aktivita dokončila spuštění.</span><span class="sxs-lookup"><span data-stu-id="9e81b-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9e81b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9e81b-114">Message</span></span>  
 <span data-ttu-id="9e81b-115">Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' byla dokončena ve stavu "%4".</span><span class="sxs-lookup"><span data-stu-id="9e81b-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9e81b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9e81b-116">Details</span></span>  
  
|<span data-ttu-id="9e81b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9e81b-117">Data Item Name</span></span>|<span data-ttu-id="9e81b-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9e81b-118">Data Item Type</span></span>|<span data-ttu-id="9e81b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9e81b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9e81b-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="9e81b-120">Activity</span></span>|<span data-ttu-id="9e81b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="9e81b-121">xs:string</span></span>|<span data-ttu-id="9e81b-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e81b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9e81b-123">displayName</span><span class="sxs-lookup"><span data-stu-id="9e81b-123">DisplayName</span></span>|<span data-ttu-id="9e81b-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="9e81b-124">xs:string</span></span>|<span data-ttu-id="9e81b-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e81b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9e81b-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="9e81b-126">InstanceId</span></span>|<span data-ttu-id="9e81b-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="9e81b-127">xs:string</span></span>|<span data-ttu-id="9e81b-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e81b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9e81b-129">Stav</span><span class="sxs-lookup"><span data-stu-id="9e81b-129">State</span></span>|<span data-ttu-id="9e81b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="9e81b-130">xs:string</span></span>|<span data-ttu-id="9e81b-131">Stav aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e81b-131">The state of the activity.</span></span>|  
|<span data-ttu-id="9e81b-132">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9e81b-132">AppDomain</span></span>|<span data-ttu-id="9e81b-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="9e81b-133">xs:string</span></span>|<span data-ttu-id="9e81b-134">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9e81b-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
