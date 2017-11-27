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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea6b31a83df6e15fe34f9e4be31a4eb53bc5bb51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="b7f19-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="b7f19-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="b7f19-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7f19-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7f19-104">ID</span><span class="sxs-lookup"><span data-stu-id="b7f19-104">ID</span></span>|<span data-ttu-id="b7f19-105">1041</span><span class="sxs-lookup"><span data-stu-id="b7f19-105">1041</span></span>|  
|<span data-ttu-id="b7f19-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b7f19-106">Keywords</span></span>|<span data-ttu-id="b7f19-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b7f19-107">WFRuntime</span></span>|  
|<span data-ttu-id="b7f19-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b7f19-108">Level</span></span>|<span data-ttu-id="b7f19-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="b7f19-109">Information</span></span>|  
|<span data-ttu-id="b7f19-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b7f19-110">Channel</span></span>|<span data-ttu-id="b7f19-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b7f19-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7f19-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b7f19-112">Description</span></span>  
 <span data-ttu-id="b7f19-113">Označuje, že je aplikace pracovního postupu nečinnosti a trvalá.</span><span class="sxs-lookup"><span data-stu-id="b7f19-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="b7f19-114">Pracovní postup aplikace nečinný nebo trvalé.</span><span class="sxs-lookup"><span data-stu-id="b7f19-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7f19-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b7f19-115">Message</span></span>  
 <span data-ttu-id="b7f19-116">WorkflowApplication Id: '%1' je nečinnosti a trvalá.</span><span class="sxs-lookup"><span data-stu-id="b7f19-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="b7f19-117">Se provedou následující akce: %2.</span><span class="sxs-lookup"><span data-stu-id="b7f19-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7f19-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b7f19-118">Details</span></span>  
  
|<span data-ttu-id="b7f19-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b7f19-119">Data Item Name</span></span>|<span data-ttu-id="b7f19-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b7f19-120">Data Item Type</span></span>|<span data-ttu-id="b7f19-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b7f19-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7f19-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b7f19-122">WorkflowApplicationId</span></span>|<span data-ttu-id="b7f19-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7f19-123">xs:string</span></span>|<span data-ttu-id="b7f19-124">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b7f19-124">The workflow application id</span></span>|  
|<span data-ttu-id="b7f19-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="b7f19-125">ActionTaken</span></span>|<span data-ttu-id="b7f19-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7f19-126">xs:string</span></span>|<span data-ttu-id="b7f19-127">Akce, která budete přesměrováni na aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b7f19-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="b7f19-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b7f19-128">AppDomain</span></span>|<span data-ttu-id="b7f19-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="b7f19-129">xs:string</span></span>|<span data-ttu-id="b7f19-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b7f19-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
