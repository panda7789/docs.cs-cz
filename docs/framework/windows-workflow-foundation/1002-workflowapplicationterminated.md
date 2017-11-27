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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54ef06c3aded628e18325b78f55e80e4470ecd01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="bf779-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="bf779-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="bf779-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bf779-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf779-104">ID</span><span class="sxs-lookup"><span data-stu-id="bf779-104">ID</span></span>|<span data-ttu-id="bf779-105">1002</span><span class="sxs-lookup"><span data-stu-id="bf779-105">1002</span></span>|  
|<span data-ttu-id="bf779-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bf779-106">Keywords</span></span>|<span data-ttu-id="bf779-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bf779-107">WFRuntime</span></span>|  
|<span data-ttu-id="bf779-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="bf779-108">Level</span></span>|<span data-ttu-id="bf779-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="bf779-109">Information</span></span>|  
|<span data-ttu-id="bf779-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="bf779-110">Channel</span></span>|<span data-ttu-id="bf779-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="bf779-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf779-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bf779-112">Description</span></span>  
 <span data-ttu-id="bf779-113">Označuje, že aplikace pracovního postupu byl ukončen ve stavu chybný s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="bf779-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf779-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bf779-114">Message</span></span>  
 <span data-ttu-id="bf779-115">WorkflowApplication Id: "%1" byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="bf779-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="bf779-116">Dokončil v chybném stavu s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="bf779-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf779-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bf779-117">Details</span></span>  
  
|<span data-ttu-id="bf779-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="bf779-118">Data Item Name</span></span>|<span data-ttu-id="bf779-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="bf779-119">Data Item Type</span></span>|<span data-ttu-id="bf779-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bf779-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf779-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="bf779-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="bf779-122">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf779-122">The workflow application id</span></span>|  
|<span data-ttu-id="bf779-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="bf779-123">Exception</span></span>|`xs:string`|<span data-ttu-id="bf779-124">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="bf779-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="bf779-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bf779-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bf779-126">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bf779-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
