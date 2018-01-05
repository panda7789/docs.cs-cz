---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3f025be90a997839eec2edfea12a099b4c58f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="dac1b-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="dac1b-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="dac1b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dac1b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dac1b-104">ID</span><span class="sxs-lookup"><span data-stu-id="dac1b-104">ID</span></span>|<span data-ttu-id="dac1b-105">1002</span><span class="sxs-lookup"><span data-stu-id="dac1b-105">1002</span></span>|  
|<span data-ttu-id="dac1b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="dac1b-106">Keywords</span></span>|<span data-ttu-id="dac1b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dac1b-107">WFRuntime</span></span>|  
|<span data-ttu-id="dac1b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="dac1b-108">Level</span></span>|<span data-ttu-id="dac1b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="dac1b-109">Information</span></span>|  
|<span data-ttu-id="dac1b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="dac1b-110">Channel</span></span>|<span data-ttu-id="dac1b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="dac1b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dac1b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dac1b-112">Description</span></span>  
 <span data-ttu-id="dac1b-113">Označuje, že aplikace pracovního postupu byl ukončen ve stavu chybný s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="dac1b-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dac1b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="dac1b-114">Message</span></span>  
 <span data-ttu-id="dac1b-115">WorkflowApplication Id: "%1" byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="dac1b-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="dac1b-116">Dokončil v chybném stavu s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="dac1b-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dac1b-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dac1b-117">Details</span></span>  
  
|<span data-ttu-id="dac1b-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="dac1b-118">Data Item Name</span></span>|<span data-ttu-id="dac1b-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="dac1b-119">Data Item Type</span></span>|<span data-ttu-id="dac1b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="dac1b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dac1b-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="dac1b-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="dac1b-122">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="dac1b-122">The workflow application id</span></span>|  
|<span data-ttu-id="dac1b-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="dac1b-123">Exception</span></span>|`xs:string`|<span data-ttu-id="dac1b-124">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="dac1b-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="dac1b-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="dac1b-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dac1b-126">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dac1b-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
