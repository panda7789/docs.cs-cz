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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a2dad3135de6d3d96328ea039aa36906addb217
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="fa26c-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="fa26c-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="fa26c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fa26c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa26c-104">ID</span><span class="sxs-lookup"><span data-stu-id="fa26c-104">ID</span></span>|<span data-ttu-id="fa26c-105">1006</span><span class="sxs-lookup"><span data-stu-id="fa26c-105">1006</span></span>|  
|<span data-ttu-id="fa26c-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fa26c-106">Keywords</span></span>|<span data-ttu-id="fa26c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fa26c-107">WFRuntime</span></span>|  
|<span data-ttu-id="fa26c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="fa26c-108">Level</span></span>|<span data-ttu-id="fa26c-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="fa26c-109">Error</span></span>|  
|<span data-ttu-id="fa26c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="fa26c-110">Channel</span></span>|<span data-ttu-id="fa26c-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="fa26c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa26c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fa26c-112">Description</span></span>  
 <span data-ttu-id="fa26c-113">Označuje, že aplikace pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="fa26c-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fa26c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="fa26c-114">Message</span></span>  
 <span data-ttu-id="fa26c-115">Id instance pracovního postupu: '%1' došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="fa26c-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="fa26c-116">Výjimka pochází z aktivity %2, DisplayName: '%3'.</span><span class="sxs-lookup"><span data-stu-id="fa26c-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="fa26c-117">Se provedou následující akce: %4.</span><span class="sxs-lookup"><span data-stu-id="fa26c-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fa26c-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fa26c-118">Details</span></span>  
  
|<span data-ttu-id="fa26c-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="fa26c-119">Data Item Name</span></span>|<span data-ttu-id="fa26c-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="fa26c-120">Data Item Type</span></span>|<span data-ttu-id="fa26c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="fa26c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fa26c-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="fa26c-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="fa26c-123">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fa26c-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="fa26c-124">Výjimka</span><span class="sxs-lookup"><span data-stu-id="fa26c-124">Exception</span></span>|`xs:string`|<span data-ttu-id="fa26c-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="fa26c-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="fa26c-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="fa26c-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fa26c-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fa26c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
