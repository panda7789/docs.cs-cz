---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dedb1dd389e2308ea8f70d71f057d17a45172517
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="68517-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="68517-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="68517-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="68517-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68517-104">ID</span><span class="sxs-lookup"><span data-stu-id="68517-104">ID</span></span>|<span data-ttu-id="68517-105">1008</span><span class="sxs-lookup"><span data-stu-id="68517-105">1008</span></span>|  
|<span data-ttu-id="68517-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="68517-106">Keywords</span></span>|<span data-ttu-id="68517-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="68517-107">WFRuntime</span></span>|  
|<span data-ttu-id="68517-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="68517-108">Level</span></span>|<span data-ttu-id="68517-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="68517-109">Information</span></span>|  
|<span data-ttu-id="68517-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="68517-110">Channel</span></span>|<span data-ttu-id="68517-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="68517-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68517-112">Popis</span><span class="sxs-lookup"><span data-stu-id="68517-112">Description</span></span>  
 <span data-ttu-id="68517-113">Označuje, že aplikace pracovního postupu byl uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="68517-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68517-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="68517-114">Message</span></span>  
 <span data-ttu-id="68517-115">Instance pracovního postupu Id: '%1' bylo uvolněno.</span><span class="sxs-lookup"><span data-stu-id="68517-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68517-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="68517-116">Details</span></span>  
  
|<span data-ttu-id="68517-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="68517-117">Data Item Name</span></span>|<span data-ttu-id="68517-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="68517-118">Data Item Type</span></span>|<span data-ttu-id="68517-119">Popis</span><span class="sxs-lookup"><span data-stu-id="68517-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68517-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="68517-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="68517-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="68517-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="68517-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="68517-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="68517-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="68517-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
