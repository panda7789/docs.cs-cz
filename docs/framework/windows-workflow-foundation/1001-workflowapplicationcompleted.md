---
title: 1001 – WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008639"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="7e12b-102">1001 – WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="7e12b-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="7e12b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7e12b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e12b-104">ID</span><span class="sxs-lookup"><span data-stu-id="7e12b-104">ID</span></span>|<span data-ttu-id="7e12b-105">1001</span><span class="sxs-lookup"><span data-stu-id="7e12b-105">1001</span></span>|  
|<span data-ttu-id="7e12b-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7e12b-106">Keywords</span></span>|<span data-ttu-id="7e12b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7e12b-107">WFRuntime</span></span>|  
|<span data-ttu-id="7e12b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="7e12b-108">Level</span></span>|<span data-ttu-id="7e12b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="7e12b-109">Information</span></span>|  
|<span data-ttu-id="7e12b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="7e12b-110">Channel</span></span>|<span data-ttu-id="7e12b-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="7e12b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7e12b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7e12b-112">Description</span></span>  
 <span data-ttu-id="7e12b-113">Označuje, že aplikace pracovního postupu byla dokončena v zavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="7e12b-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7e12b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="7e12b-114">Message</span></span>  
 <span data-ttu-id="7e12b-115">WorkflowInstance Id: '%1' byl dokončen v zavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="7e12b-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7e12b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7e12b-116">Details</span></span>  
  
|<span data-ttu-id="7e12b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="7e12b-117">Data Item Name</span></span>|<span data-ttu-id="7e12b-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="7e12b-118">Data Item Type</span></span>|<span data-ttu-id="7e12b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7e12b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7e12b-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="7e12b-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="7e12b-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="7e12b-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="7e12b-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7e12b-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7e12b-123">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7e12b-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
