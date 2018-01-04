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
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="cb14f-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="cb14f-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="cb14f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cb14f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb14f-104">ID</span><span class="sxs-lookup"><span data-stu-id="cb14f-104">ID</span></span>|<span data-ttu-id="cb14f-105">1004</span><span class="sxs-lookup"><span data-stu-id="cb14f-105">1004</span></span>|  
|<span data-ttu-id="cb14f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="cb14f-106">Keywords</span></span>|<span data-ttu-id="cb14f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cb14f-107">WFRuntime</span></span>|  
|<span data-ttu-id="cb14f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="cb14f-108">Level</span></span>|<span data-ttu-id="cb14f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="cb14f-109">Information</span></span>|  
|<span data-ttu-id="cb14f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="cb14f-110">Channel</span></span>|<span data-ttu-id="cb14f-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="cb14f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cb14f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cb14f-112">Description</span></span>  
 <span data-ttu-id="cb14f-113">Označuje, že worfklow instance přerušil s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="cb14f-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cb14f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="cb14f-114">Message</span></span>  
 <span data-ttu-id="cb14f-115">Instance pracovního postupu Id: '%1' byla přerušena, s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="cb14f-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cb14f-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cb14f-116">Details</span></span>  
  
|<span data-ttu-id="cb14f-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="cb14f-117">Data Item Name</span></span>|<span data-ttu-id="cb14f-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="cb14f-118">Data Item Type</span></span>|<span data-ttu-id="cb14f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="cb14f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cb14f-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cb14f-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cb14f-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cb14f-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cb14f-122">Výjimka</span><span class="sxs-lookup"><span data-stu-id="cb14f-122">Exception</span></span>|`xs:string`|<span data-ttu-id="cb14f-123">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="cb14f-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="cb14f-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="cb14f-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cb14f-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cb14f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
