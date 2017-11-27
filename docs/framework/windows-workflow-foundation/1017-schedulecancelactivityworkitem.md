---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d348ec18b4d5eff7156d1e9809eb793ac1681d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="6b377-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="6b377-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6b377-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6b377-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b377-104">ID</span><span class="sxs-lookup"><span data-stu-id="6b377-104">ID</span></span>|<span data-ttu-id="6b377-105">1017</span><span class="sxs-lookup"><span data-stu-id="6b377-105">1017</span></span>|  
|<span data-ttu-id="6b377-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6b377-106">Keywords</span></span>|<span data-ttu-id="6b377-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6b377-107">WFRuntime</span></span>|  
|<span data-ttu-id="6b377-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6b377-108">Level</span></span>|<span data-ttu-id="6b377-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="6b377-109">Verbose</span></span>|  
|<span data-ttu-id="6b377-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6b377-110">Channel</span></span>|<span data-ttu-id="6b377-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="6b377-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6b377-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6b377-112">Description</span></span>  
 <span data-ttu-id="6b377-113">Označuje, že bylo naplánováno CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="6b377-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6b377-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6b377-114">Message</span></span>  
 <span data-ttu-id="6b377-115">Bylo naplánováno CancelActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="6b377-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b377-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6b377-116">Details</span></span>  
  
|<span data-ttu-id="6b377-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6b377-117">Data Item Name</span></span>|<span data-ttu-id="6b377-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="6b377-118">Data Item Type</span></span>|<span data-ttu-id="6b377-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6b377-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6b377-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="6b377-120">Activity</span></span>|<span data-ttu-id="6b377-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="6b377-121">xs:string</span></span>|<span data-ttu-id="6b377-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b377-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="6b377-123">displayName</span><span class="sxs-lookup"><span data-stu-id="6b377-123">DisplayName</span></span>|<span data-ttu-id="6b377-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="6b377-124">xs:string</span></span>|<span data-ttu-id="6b377-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b377-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="6b377-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="6b377-126">InstanceId</span></span>|<span data-ttu-id="6b377-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="6b377-127">xs:string</span></span>|<span data-ttu-id="6b377-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="6b377-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6b377-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6b377-129">AppDomain</span></span>|<span data-ttu-id="6b377-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="6b377-130">xs:string</span></span>|<span data-ttu-id="6b377-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6b377-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
