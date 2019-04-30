---
title: 1101 – WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 1e6db97284b7ca83d532166d96d7a42df0a51091
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924147"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="d4cfa-102">1101 – WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="d4cfa-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="d4cfa-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d4cfa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4cfa-104">ID</span><span class="sxs-lookup"><span data-stu-id="d4cfa-104">ID</span></span>|<span data-ttu-id="d4cfa-105">1101</span><span class="sxs-lookup"><span data-stu-id="d4cfa-105">1101</span></span>|  
|<span data-ttu-id="d4cfa-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d4cfa-106">Keywords</span></span>|<span data-ttu-id="d4cfa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d4cfa-107">WFRuntime</span></span>|  
|<span data-ttu-id="d4cfa-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d4cfa-108">Level</span></span>|<span data-ttu-id="d4cfa-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="d4cfa-109">Information</span></span>|  
|<span data-ttu-id="d4cfa-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d4cfa-110">Channel</span></span>|<span data-ttu-id="d4cfa-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="d4cfa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d4cfa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d4cfa-112">Description</span></span>  
 <span data-ttu-id="d4cfa-113">Označuje, že byla spuštěna aktivita pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d4cfa-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d4cfa-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d4cfa-114">Message</span></span>  
 <span data-ttu-id="d4cfa-115">WorkflowInstance Id: '%1' aktivita E2E</span><span class="sxs-lookup"><span data-stu-id="d4cfa-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="d4cfa-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d4cfa-116">Details</span></span>  
  
|<span data-ttu-id="d4cfa-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d4cfa-117">Data Item Name</span></span>|<span data-ttu-id="d4cfa-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="d4cfa-118">Data Item Type</span></span>|<span data-ttu-id="d4cfa-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d4cfa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d4cfa-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d4cfa-120">WorkflowInstanceId</span></span>|<span data-ttu-id="d4cfa-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d4cfa-121">xs:string</span></span>|<span data-ttu-id="d4cfa-122">Id instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d4cfa-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="d4cfa-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d4cfa-123">AppDomain</span></span>|<span data-ttu-id="d4cfa-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d4cfa-124">xs:string</span></span>|<span data-ttu-id="d4cfa-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d4cfa-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
