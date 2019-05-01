---
title: 1102 – WorkflowActivityStop
ms.date: 03/30/2017
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
ms.openlocfilehash: 44617e9f53be0e601424746f83b171d33956197e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052791"
---
# <a name="1102---workflowactivitystop"></a><span data-ttu-id="ed74b-102">1102 – WorkflowActivityStop</span><span class="sxs-lookup"><span data-stu-id="ed74b-102">1102 - WorkflowActivityStop</span></span>
## <a name="properties"></a><span data-ttu-id="ed74b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ed74b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed74b-104">ID</span><span class="sxs-lookup"><span data-stu-id="ed74b-104">ID</span></span>|<span data-ttu-id="ed74b-105">1102</span><span class="sxs-lookup"><span data-stu-id="ed74b-105">1102</span></span>|  
|<span data-ttu-id="ed74b-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ed74b-106">Keywords</span></span>|<span data-ttu-id="ed74b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ed74b-107">WFRuntime</span></span>|  
|<span data-ttu-id="ed74b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ed74b-108">Level</span></span>|<span data-ttu-id="ed74b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="ed74b-109">Information</span></span>|  
|<span data-ttu-id="ed74b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ed74b-110">Channel</span></span>|<span data-ttu-id="ed74b-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ed74b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ed74b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ed74b-112">Description</span></span>  
 <span data-ttu-id="ed74b-113">Označuje, že aktivita pracovního postupu byl zastaven.</span><span class="sxs-lookup"><span data-stu-id="ed74b-113">Indicates a workflow activity has stopped.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ed74b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ed74b-114">Message</span></span>  
 <span data-ttu-id="ed74b-115">WorkflowInstance Id: '%1' aktivita E2E</span><span class="sxs-lookup"><span data-stu-id="ed74b-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="ed74b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ed74b-116">Details</span></span>  
  
|<span data-ttu-id="ed74b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ed74b-117">Data Item Name</span></span>|<span data-ttu-id="ed74b-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="ed74b-118">Data Item Type</span></span>|<span data-ttu-id="ed74b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ed74b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ed74b-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ed74b-120">WorkflowInstanceId</span></span>|<span data-ttu-id="ed74b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed74b-121">xs:string</span></span>|<span data-ttu-id="ed74b-122">Id instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ed74b-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="ed74b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ed74b-123">AppDomain</span></span>|<span data-ttu-id="ed74b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed74b-124">xs:string</span></span>|<span data-ttu-id="ed74b-125">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ed74b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
