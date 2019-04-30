---
title: 1104 – WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 4c9ae5fd386fc93ea19578097aa4e0afdda527e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924121"
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="07e8f-102">1104 – WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="07e8f-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="07e8f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="07e8f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07e8f-104">ID</span><span class="sxs-lookup"><span data-stu-id="07e8f-104">ID</span></span>|<span data-ttu-id="07e8f-105">1104</span><span class="sxs-lookup"><span data-stu-id="07e8f-105">1104</span></span>|  
|<span data-ttu-id="07e8f-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="07e8f-106">Keywords</span></span>|<span data-ttu-id="07e8f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="07e8f-107">WFRuntime</span></span>|  
|<span data-ttu-id="07e8f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="07e8f-108">Level</span></span>|<span data-ttu-id="07e8f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="07e8f-109">Information</span></span>|  
|<span data-ttu-id="07e8f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="07e8f-110">Channel</span></span>|<span data-ttu-id="07e8f-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="07e8f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="07e8f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="07e8f-112">Description</span></span>  
 <span data-ttu-id="07e8f-113">Označuje, že aktivita pracovního postupu byl obnoven.</span><span class="sxs-lookup"><span data-stu-id="07e8f-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="07e8f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="07e8f-114">Message</span></span>  
 <span data-ttu-id="07e8f-115">WorkflowInstance Id: '%1' aktivita E2E</span><span class="sxs-lookup"><span data-stu-id="07e8f-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="07e8f-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="07e8f-116">Details</span></span>  
  
|<span data-ttu-id="07e8f-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="07e8f-117">Data Item Name</span></span>|<span data-ttu-id="07e8f-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="07e8f-118">Data Item Type</span></span>|<span data-ttu-id="07e8f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="07e8f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="07e8f-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="07e8f-120">WorkflowInstanceId</span></span>|<span data-ttu-id="07e8f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="07e8f-121">xs:string</span></span>|<span data-ttu-id="07e8f-122">Id instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="07e8f-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="07e8f-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="07e8f-123">AppDomain</span></span>|<span data-ttu-id="07e8f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="07e8f-124">xs:string</span></span>|<span data-ttu-id="07e8f-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="07e8f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
