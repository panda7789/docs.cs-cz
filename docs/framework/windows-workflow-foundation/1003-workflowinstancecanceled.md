---
title: 1003 – WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008626"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="22300-102">1003 – WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="22300-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="22300-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="22300-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22300-104">ID</span><span class="sxs-lookup"><span data-stu-id="22300-104">ID</span></span>|<span data-ttu-id="22300-105">1003</span><span class="sxs-lookup"><span data-stu-id="22300-105">1003</span></span>|  
|<span data-ttu-id="22300-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="22300-106">Keywords</span></span>|<span data-ttu-id="22300-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="22300-107">WFRuntime</span></span>|  
|<span data-ttu-id="22300-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="22300-108">Level</span></span>|<span data-ttu-id="22300-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="22300-109">Information</span></span>|  
|<span data-ttu-id="22300-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="22300-110">Channel</span></span>|<span data-ttu-id="22300-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="22300-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="22300-112">Popis</span><span class="sxs-lookup"><span data-stu-id="22300-112">Description</span></span>  
 <span data-ttu-id="22300-113">Označuje, že instance pracovního postupu – dokončeno ve zrušeném stavu.</span><span class="sxs-lookup"><span data-stu-id="22300-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="22300-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="22300-114">Message</span></span>  
 <span data-ttu-id="22300-115">WorkflowInstance Id: '%1' byl dokončen ve zrušeném stavu.</span><span class="sxs-lookup"><span data-stu-id="22300-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="22300-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="22300-116">Details</span></span>  
  
|<span data-ttu-id="22300-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="22300-117">Data Item Name</span></span>|<span data-ttu-id="22300-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="22300-118">Data Item Type</span></span>|<span data-ttu-id="22300-119">Popis</span><span class="sxs-lookup"><span data-stu-id="22300-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="22300-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="22300-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="22300-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="22300-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="22300-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="22300-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="22300-123">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="22300-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
