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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7394ebbcb14850af89d906b0b573c4f677346825
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="2f689-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="2f689-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="2f689-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2f689-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f689-104">ID</span><span class="sxs-lookup"><span data-stu-id="2f689-104">ID</span></span>|<span data-ttu-id="2f689-105">1004</span><span class="sxs-lookup"><span data-stu-id="2f689-105">1004</span></span>|  
|<span data-ttu-id="2f689-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2f689-106">Keywords</span></span>|<span data-ttu-id="2f689-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2f689-107">WFRuntime</span></span>|  
|<span data-ttu-id="2f689-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2f689-108">Level</span></span>|<span data-ttu-id="2f689-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="2f689-109">Information</span></span>|  
|<span data-ttu-id="2f689-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2f689-110">Channel</span></span>|<span data-ttu-id="2f689-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="2f689-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f689-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2f689-112">Description</span></span>  
 <span data-ttu-id="2f689-113">Označuje, že worfklow instance přerušil s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="2f689-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f689-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2f689-114">Message</span></span>  
 <span data-ttu-id="2f689-115">Instance pracovního postupu Id: '%1' byla přerušena, s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="2f689-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f689-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2f689-116">Details</span></span>  
  
|<span data-ttu-id="2f689-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2f689-117">Data Item Name</span></span>|<span data-ttu-id="2f689-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2f689-118">Data Item Type</span></span>|<span data-ttu-id="2f689-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2f689-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f689-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2f689-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2f689-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2f689-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2f689-122">Výjimka</span><span class="sxs-lookup"><span data-stu-id="2f689-122">Exception</span></span>|`xs:string`|<span data-ttu-id="2f689-123">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="2f689-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="2f689-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2f689-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2f689-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2f689-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
