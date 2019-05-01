---
title: 1103 – WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 4311bd8dc1c5e2c43bf21b411a4c52a7bfc7b230
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052778"
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="ffe3b-102">1103 – WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="ffe3b-102">1103 - WorkflowActivitySuspend</span></span>
## <a name="properties"></a><span data-ttu-id="ffe3b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ffe3b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffe3b-104">ID</span><span class="sxs-lookup"><span data-stu-id="ffe3b-104">ID</span></span>|<span data-ttu-id="ffe3b-105">1103</span><span class="sxs-lookup"><span data-stu-id="ffe3b-105">1103</span></span>|  
|<span data-ttu-id="ffe3b-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ffe3b-106">Keywords</span></span>|<span data-ttu-id="ffe3b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ffe3b-107">WFRuntime</span></span>|  
|<span data-ttu-id="ffe3b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ffe3b-108">Level</span></span>|<span data-ttu-id="ffe3b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="ffe3b-109">Information</span></span>|  
|<span data-ttu-id="ffe3b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ffe3b-110">Channel</span></span>|<span data-ttu-id="ffe3b-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ffe3b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ffe3b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ffe3b-112">Description</span></span>  
 <span data-ttu-id="ffe3b-113">Označuje, že aktivita pracovního postupu je pozastavená.</span><span class="sxs-lookup"><span data-stu-id="ffe3b-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ffe3b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ffe3b-114">Message</span></span>  
 <span data-ttu-id="ffe3b-115">WorkflowInstance Id: '%1' aktivita E2E</span><span class="sxs-lookup"><span data-stu-id="ffe3b-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="ffe3b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ffe3b-116">Details</span></span>  
  
|<span data-ttu-id="ffe3b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ffe3b-117">Data Item Name</span></span>|<span data-ttu-id="ffe3b-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="ffe3b-118">Data Item Type</span></span>|<span data-ttu-id="ffe3b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ffe3b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ffe3b-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ffe3b-120">WorkflowInstanceId</span></span>|<span data-ttu-id="ffe3b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffe3b-121">xs:string</span></span>|<span data-ttu-id="ffe3b-122">Id instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ffe3b-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="ffe3b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ffe3b-123">AppDomain</span></span>|<span data-ttu-id="ffe3b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ffe3b-124">xs:string</span></span>|<span data-ttu-id="ffe3b-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ffe3b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
