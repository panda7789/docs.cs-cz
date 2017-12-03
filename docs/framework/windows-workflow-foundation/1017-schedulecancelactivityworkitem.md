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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a632d59ddd75b375ff5e828a9f35aeecb0118f1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="47354-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="47354-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="47354-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="47354-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47354-104">ID</span><span class="sxs-lookup"><span data-stu-id="47354-104">ID</span></span>|<span data-ttu-id="47354-105">1017</span><span class="sxs-lookup"><span data-stu-id="47354-105">1017</span></span>|  
|<span data-ttu-id="47354-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="47354-106">Keywords</span></span>|<span data-ttu-id="47354-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="47354-107">WFRuntime</span></span>|  
|<span data-ttu-id="47354-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="47354-108">Level</span></span>|<span data-ttu-id="47354-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="47354-109">Verbose</span></span>|  
|<span data-ttu-id="47354-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="47354-110">Channel</span></span>|<span data-ttu-id="47354-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="47354-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47354-112">Popis</span><span class="sxs-lookup"><span data-stu-id="47354-112">Description</span></span>  
 <span data-ttu-id="47354-113">Označuje, že bylo naplánováno CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="47354-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47354-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="47354-114">Message</span></span>  
 <span data-ttu-id="47354-115">Bylo naplánováno CancelActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="47354-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47354-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="47354-116">Details</span></span>  
  
|<span data-ttu-id="47354-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="47354-117">Data Item Name</span></span>|<span data-ttu-id="47354-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="47354-118">Data Item Type</span></span>|<span data-ttu-id="47354-119">Popis</span><span class="sxs-lookup"><span data-stu-id="47354-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47354-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="47354-120">Activity</span></span>|<span data-ttu-id="47354-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="47354-121">xs:string</span></span>|<span data-ttu-id="47354-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="47354-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="47354-123">displayName</span><span class="sxs-lookup"><span data-stu-id="47354-123">DisplayName</span></span>|<span data-ttu-id="47354-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="47354-124">xs:string</span></span>|<span data-ttu-id="47354-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="47354-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="47354-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="47354-126">InstanceId</span></span>|<span data-ttu-id="47354-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="47354-127">xs:string</span></span>|<span data-ttu-id="47354-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="47354-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="47354-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="47354-129">AppDomain</span></span>|<span data-ttu-id="47354-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="47354-130">xs:string</span></span>|<span data-ttu-id="47354-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="47354-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
