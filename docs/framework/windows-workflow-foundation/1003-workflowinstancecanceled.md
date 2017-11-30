---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b287c99453724f855a51e9a1b8068337dd5e373
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="0eff1-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="0eff1-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="0eff1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0eff1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0eff1-104">ID</span><span class="sxs-lookup"><span data-stu-id="0eff1-104">ID</span></span>|<span data-ttu-id="0eff1-105">1003</span><span class="sxs-lookup"><span data-stu-id="0eff1-105">1003</span></span>|  
|<span data-ttu-id="0eff1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0eff1-106">Keywords</span></span>|<span data-ttu-id="0eff1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0eff1-107">WFRuntime</span></span>|  
|<span data-ttu-id="0eff1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0eff1-108">Level</span></span>|<span data-ttu-id="0eff1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="0eff1-109">Information</span></span>|  
|<span data-ttu-id="0eff1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0eff1-110">Channel</span></span>|<span data-ttu-id="0eff1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="0eff1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0eff1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0eff1-112">Description</span></span>  
 <span data-ttu-id="0eff1-113">Označuje, že je ve stavu zrušeno dokončená instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0eff1-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0eff1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0eff1-114">Message</span></span>  
 <span data-ttu-id="0eff1-115">Id instance pracovního postupu: '%1' byla dokončena v stav zrušeno.</span><span class="sxs-lookup"><span data-stu-id="0eff1-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0eff1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0eff1-116">Details</span></span>  
  
|<span data-ttu-id="0eff1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0eff1-117">Data Item Name</span></span>|<span data-ttu-id="0eff1-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="0eff1-118">Data Item Type</span></span>|<span data-ttu-id="0eff1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0eff1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0eff1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="0eff1-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0eff1-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="0eff1-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="0eff1-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="0eff1-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0eff1-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0eff1-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
