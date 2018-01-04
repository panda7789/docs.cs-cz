---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d64d18474ff867ee5679e07c18a288f07185f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="d5663-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="d5663-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d5663-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d5663-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5663-104">ID</span><span class="sxs-lookup"><span data-stu-id="d5663-104">ID</span></span>|<span data-ttu-id="d5663-105">1018</span><span class="sxs-lookup"><span data-stu-id="d5663-105">1018</span></span>|  
|<span data-ttu-id="d5663-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d5663-106">Keywords</span></span>|<span data-ttu-id="d5663-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d5663-107">WFRuntime</span></span>|  
|<span data-ttu-id="d5663-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d5663-108">Level</span></span>|<span data-ttu-id="d5663-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="d5663-109">Verbose</span></span>|  
|<span data-ttu-id="d5663-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d5663-110">Channel</span></span>|<span data-ttu-id="d5663-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="d5663-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d5663-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d5663-112">Description</span></span>  
 <span data-ttu-id="d5663-113">Označuje, že že cancelactivityworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="d5663-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d5663-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d5663-114">Message</span></span>  
 <span data-ttu-id="d5663-115">Spuštění provádění CancelActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d5663-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d5663-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d5663-116">Details</span></span>  
  
|<span data-ttu-id="d5663-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d5663-117">Data Item Name</span></span>|<span data-ttu-id="d5663-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="d5663-118">Data Item Type</span></span>|<span data-ttu-id="d5663-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d5663-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d5663-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="d5663-120">Activity</span></span>|<span data-ttu-id="d5663-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="d5663-121">xs:string</span></span>|<span data-ttu-id="d5663-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d5663-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d5663-123">displayName</span><span class="sxs-lookup"><span data-stu-id="d5663-123">DisplayName</span></span>|<span data-ttu-id="d5663-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d5663-124">xs:string</span></span>|<span data-ttu-id="d5663-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="d5663-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d5663-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="d5663-126">InstanceId</span></span>|<span data-ttu-id="d5663-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="d5663-127">xs:string</span></span>|<span data-ttu-id="d5663-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="d5663-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d5663-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d5663-129">AppDomain</span></span>|<span data-ttu-id="d5663-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="d5663-130">xs:string</span></span>|<span data-ttu-id="d5663-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d5663-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
