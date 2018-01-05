---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1efc32ed0304d5b0d222054e5c65abe279ef93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="2ea28-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="2ea28-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="2ea28-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2ea28-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ea28-104">ID</span><span class="sxs-lookup"><span data-stu-id="2ea28-104">ID</span></span>|<span data-ttu-id="2ea28-105">1041</span><span class="sxs-lookup"><span data-stu-id="2ea28-105">1041</span></span>|  
|<span data-ttu-id="2ea28-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2ea28-106">Keywords</span></span>|<span data-ttu-id="2ea28-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2ea28-107">WFRuntime</span></span>|  
|<span data-ttu-id="2ea28-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2ea28-108">Level</span></span>|<span data-ttu-id="2ea28-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="2ea28-109">Information</span></span>|  
|<span data-ttu-id="2ea28-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2ea28-110">Channel</span></span>|<span data-ttu-id="2ea28-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="2ea28-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2ea28-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2ea28-112">Description</span></span>  
 <span data-ttu-id="2ea28-113">Označuje, že je aplikace pracovního postupu nečinnosti a trvalá.</span><span class="sxs-lookup"><span data-stu-id="2ea28-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="2ea28-114">Pracovní postup aplikace nečinný nebo trvalé.</span><span class="sxs-lookup"><span data-stu-id="2ea28-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2ea28-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2ea28-115">Message</span></span>  
 <span data-ttu-id="2ea28-116">WorkflowApplication Id: '%1' je nečinnosti a trvalá.</span><span class="sxs-lookup"><span data-stu-id="2ea28-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="2ea28-117">Se provedou následující akce: %2.</span><span class="sxs-lookup"><span data-stu-id="2ea28-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2ea28-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2ea28-118">Details</span></span>  
  
|<span data-ttu-id="2ea28-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2ea28-119">Data Item Name</span></span>|<span data-ttu-id="2ea28-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2ea28-120">Data Item Type</span></span>|<span data-ttu-id="2ea28-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2ea28-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2ea28-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="2ea28-122">WorkflowApplicationId</span></span>|<span data-ttu-id="2ea28-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="2ea28-123">xs:string</span></span>|<span data-ttu-id="2ea28-124">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2ea28-124">The workflow application id</span></span>|  
|<span data-ttu-id="2ea28-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="2ea28-125">ActionTaken</span></span>|<span data-ttu-id="2ea28-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="2ea28-126">xs:string</span></span>|<span data-ttu-id="2ea28-127">Akce, která budete přesměrováni na aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2ea28-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="2ea28-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2ea28-128">AppDomain</span></span>|<span data-ttu-id="2ea28-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="2ea28-129">xs:string</span></span>|<span data-ttu-id="2ea28-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2ea28-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
