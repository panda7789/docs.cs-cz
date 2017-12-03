---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12b20ef893db12892636d73eeea2976f12bfccf9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="01f78-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="01f78-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="01f78-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="01f78-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01f78-104">ID</span><span class="sxs-lookup"><span data-stu-id="01f78-104">ID</span></span>|<span data-ttu-id="01f78-105">1001</span><span class="sxs-lookup"><span data-stu-id="01f78-105">1001</span></span>|  
|<span data-ttu-id="01f78-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="01f78-106">Keywords</span></span>|<span data-ttu-id="01f78-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="01f78-107">WFRuntime</span></span>|  
|<span data-ttu-id="01f78-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="01f78-108">Level</span></span>|<span data-ttu-id="01f78-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="01f78-109">Information</span></span>|  
|<span data-ttu-id="01f78-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="01f78-110">Channel</span></span>|<span data-ttu-id="01f78-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="01f78-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01f78-112">Popis</span><span class="sxs-lookup"><span data-stu-id="01f78-112">Description</span></span>  
 <span data-ttu-id="01f78-113">Označuje, že aplikace pracovního postupu byla dokončena v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="01f78-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01f78-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="01f78-114">Message</span></span>  
 <span data-ttu-id="01f78-115">Instance pracovního postupu Id: '%1' byla dokončena v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="01f78-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01f78-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="01f78-116">Details</span></span>  
  
|<span data-ttu-id="01f78-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="01f78-117">Data Item Name</span></span>|<span data-ttu-id="01f78-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="01f78-118">Data Item Type</span></span>|<span data-ttu-id="01f78-119">Popis</span><span class="sxs-lookup"><span data-stu-id="01f78-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01f78-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="01f78-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="01f78-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="01f78-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="01f78-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="01f78-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="01f78-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="01f78-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
