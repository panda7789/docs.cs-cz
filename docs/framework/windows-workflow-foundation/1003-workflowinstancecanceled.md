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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6930aeed8c3cd224d5d37dcecf357195e78390ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="05f8b-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="05f8b-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="05f8b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="05f8b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05f8b-104">ID</span><span class="sxs-lookup"><span data-stu-id="05f8b-104">ID</span></span>|<span data-ttu-id="05f8b-105">1003</span><span class="sxs-lookup"><span data-stu-id="05f8b-105">1003</span></span>|  
|<span data-ttu-id="05f8b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="05f8b-106">Keywords</span></span>|<span data-ttu-id="05f8b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="05f8b-107">WFRuntime</span></span>|  
|<span data-ttu-id="05f8b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="05f8b-108">Level</span></span>|<span data-ttu-id="05f8b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="05f8b-109">Information</span></span>|  
|<span data-ttu-id="05f8b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="05f8b-110">Channel</span></span>|<span data-ttu-id="05f8b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="05f8b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="05f8b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="05f8b-112">Description</span></span>  
 <span data-ttu-id="05f8b-113">Označuje, že je ve stavu zrušeno dokončená instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="05f8b-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="05f8b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="05f8b-114">Message</span></span>  
 <span data-ttu-id="05f8b-115">Id instance pracovního postupu: '%1' byla dokončena v stav zrušeno.</span><span class="sxs-lookup"><span data-stu-id="05f8b-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="05f8b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="05f8b-116">Details</span></span>  
  
|<span data-ttu-id="05f8b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="05f8b-117">Data Item Name</span></span>|<span data-ttu-id="05f8b-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="05f8b-118">Data Item Type</span></span>|<span data-ttu-id="05f8b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="05f8b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="05f8b-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="05f8b-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="05f8b-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="05f8b-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="05f8b-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="05f8b-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="05f8b-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="05f8b-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
