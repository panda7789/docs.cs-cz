---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a03809be5e5d61c505e295e2f769a0298f770f7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="62a78-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="62a78-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="62a78-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="62a78-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62a78-104">ID</span><span class="sxs-lookup"><span data-stu-id="62a78-104">ID</span></span>|<span data-ttu-id="62a78-105">1006</span><span class="sxs-lookup"><span data-stu-id="62a78-105">1006</span></span>|  
|<span data-ttu-id="62a78-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="62a78-106">Keywords</span></span>|<span data-ttu-id="62a78-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="62a78-107">WFRuntime</span></span>|  
|<span data-ttu-id="62a78-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="62a78-108">Level</span></span>|<span data-ttu-id="62a78-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="62a78-109">Error</span></span>|  
|<span data-ttu-id="62a78-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="62a78-110">Channel</span></span>|<span data-ttu-id="62a78-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="62a78-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="62a78-112">Popis</span><span class="sxs-lookup"><span data-stu-id="62a78-112">Description</span></span>  
 <span data-ttu-id="62a78-113">Označuje, že aplikace pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="62a78-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="62a78-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="62a78-114">Message</span></span>  
 <span data-ttu-id="62a78-115">Id instance pracovního postupu: '%1' došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="62a78-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="62a78-116">Výjimka pochází z aktivity %2, DisplayName: '%3'.</span><span class="sxs-lookup"><span data-stu-id="62a78-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="62a78-117">Se provedou následující akce: %4.</span><span class="sxs-lookup"><span data-stu-id="62a78-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="62a78-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="62a78-118">Details</span></span>  
  
|<span data-ttu-id="62a78-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="62a78-119">Data Item Name</span></span>|<span data-ttu-id="62a78-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="62a78-120">Data Item Type</span></span>|<span data-ttu-id="62a78-121">Popis</span><span class="sxs-lookup"><span data-stu-id="62a78-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="62a78-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="62a78-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="62a78-123">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="62a78-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="62a78-124">Výjimka</span><span class="sxs-lookup"><span data-stu-id="62a78-124">Exception</span></span>|`xs:string`|<span data-ttu-id="62a78-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="62a78-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="62a78-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="62a78-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="62a78-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="62a78-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
