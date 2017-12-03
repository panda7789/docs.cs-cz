---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564e94d94dc5e3579dc4a80d734db78e90db91fb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="a5ccd-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="a5ccd-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="a5ccd-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a5ccd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5ccd-104">ID</span><span class="sxs-lookup"><span data-stu-id="a5ccd-104">ID</span></span>|<span data-ttu-id="a5ccd-105">1004</span><span class="sxs-lookup"><span data-stu-id="a5ccd-105">1004</span></span>|  
|<span data-ttu-id="a5ccd-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a5ccd-106">Keywords</span></span>|<span data-ttu-id="a5ccd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a5ccd-107">WFRuntime</span></span>|  
|<span data-ttu-id="a5ccd-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a5ccd-108">Level</span></span>|<span data-ttu-id="a5ccd-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a5ccd-109">Information</span></span>|  
|<span data-ttu-id="a5ccd-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a5ccd-110">Channel</span></span>|<span data-ttu-id="a5ccd-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a5ccd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a5ccd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a5ccd-112">Description</span></span>  
 <span data-ttu-id="a5ccd-113">Označuje, že worfklow instance přerušil s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="a5ccd-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a5ccd-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a5ccd-114">Message</span></span>  
 <span data-ttu-id="a5ccd-115">Instance pracovního postupu Id: '%1' byla přerušena, s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="a5ccd-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a5ccd-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a5ccd-116">Details</span></span>  
  
|<span data-ttu-id="a5ccd-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a5ccd-117">Data Item Name</span></span>|<span data-ttu-id="a5ccd-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a5ccd-118">Data Item Type</span></span>|<span data-ttu-id="a5ccd-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a5ccd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a5ccd-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a5ccd-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="a5ccd-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a5ccd-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a5ccd-122">Výjimka</span><span class="sxs-lookup"><span data-stu-id="a5ccd-122">Exception</span></span>|`xs:string`|<span data-ttu-id="a5ccd-123">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="a5ccd-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="a5ccd-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a5ccd-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a5ccd-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a5ccd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
