---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 4c9ae5fd386fc93ea19578097aa4e0afdda527e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511053"
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="51ce1-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="51ce1-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="51ce1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="51ce1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51ce1-104">ID</span><span class="sxs-lookup"><span data-stu-id="51ce1-104">ID</span></span>|<span data-ttu-id="51ce1-105">1104</span><span class="sxs-lookup"><span data-stu-id="51ce1-105">1104</span></span>|  
|<span data-ttu-id="51ce1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="51ce1-106">Keywords</span></span>|<span data-ttu-id="51ce1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="51ce1-107">WFRuntime</span></span>|  
|<span data-ttu-id="51ce1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="51ce1-108">Level</span></span>|<span data-ttu-id="51ce1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="51ce1-109">Information</span></span>|  
|<span data-ttu-id="51ce1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="51ce1-110">Channel</span></span>|<span data-ttu-id="51ce1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="51ce1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="51ce1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="51ce1-112">Description</span></span>  
 <span data-ttu-id="51ce1-113">Označuje, že byl obnoven aktivit pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="51ce1-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="51ce1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="51ce1-114">Message</span></span>  
 <span data-ttu-id="51ce1-115">Instance pracovního postupu Id: '%1' E2E aktivity</span><span class="sxs-lookup"><span data-stu-id="51ce1-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="51ce1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="51ce1-116">Details</span></span>  
  
|<span data-ttu-id="51ce1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="51ce1-117">Data Item Name</span></span>|<span data-ttu-id="51ce1-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="51ce1-118">Data Item Type</span></span>|<span data-ttu-id="51ce1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="51ce1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="51ce1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="51ce1-120">WorkflowInstanceId</span></span>|<span data-ttu-id="51ce1-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="51ce1-121">xs:string</span></span>|<span data-ttu-id="51ce1-122">Id instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="51ce1-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="51ce1-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="51ce1-123">AppDomain</span></span>|<span data-ttu-id="51ce1-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="51ce1-124">xs:string</span></span>|<span data-ttu-id="51ce1-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="51ce1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
