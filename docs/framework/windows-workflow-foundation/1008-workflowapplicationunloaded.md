---
title: 1008 – WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925226"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="9c203-102">1008 – WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="9c203-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="9c203-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9c203-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c203-104">ID</span><span class="sxs-lookup"><span data-stu-id="9c203-104">ID</span></span>|<span data-ttu-id="9c203-105">1008</span><span class="sxs-lookup"><span data-stu-id="9c203-105">1008</span></span>|  
|<span data-ttu-id="9c203-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9c203-106">Keywords</span></span>|<span data-ttu-id="9c203-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9c203-107">WFRuntime</span></span>|  
|<span data-ttu-id="9c203-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9c203-108">Level</span></span>|<span data-ttu-id="9c203-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="9c203-109">Information</span></span>|  
|<span data-ttu-id="9c203-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9c203-110">Channel</span></span>|<span data-ttu-id="9c203-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9c203-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9c203-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9c203-112">Description</span></span>  
 <span data-ttu-id="9c203-113">Označuje, že aplikace pracovního postupu byl uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="9c203-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9c203-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9c203-114">Message</span></span>  
 <span data-ttu-id="9c203-115">WorkflowInstance Id: '%1' bylo uvolněno.</span><span class="sxs-lookup"><span data-stu-id="9c203-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9c203-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9c203-116">Details</span></span>  
  
|<span data-ttu-id="9c203-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9c203-117">Data Item Name</span></span>|<span data-ttu-id="9c203-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="9c203-118">Data Item Type</span></span>|<span data-ttu-id="9c203-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9c203-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9c203-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9c203-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9c203-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9c203-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9c203-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9c203-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9c203-123">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9c203-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
