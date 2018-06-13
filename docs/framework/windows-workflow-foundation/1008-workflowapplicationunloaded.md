---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509558"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="ff358-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="ff358-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="ff358-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ff358-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff358-104">ID</span><span class="sxs-lookup"><span data-stu-id="ff358-104">ID</span></span>|<span data-ttu-id="ff358-105">1008</span><span class="sxs-lookup"><span data-stu-id="ff358-105">1008</span></span>|  
|<span data-ttu-id="ff358-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ff358-106">Keywords</span></span>|<span data-ttu-id="ff358-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ff358-107">WFRuntime</span></span>|  
|<span data-ttu-id="ff358-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ff358-108">Level</span></span>|<span data-ttu-id="ff358-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="ff358-109">Information</span></span>|  
|<span data-ttu-id="ff358-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ff358-110">Channel</span></span>|<span data-ttu-id="ff358-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="ff358-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff358-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ff358-112">Description</span></span>  
 <span data-ttu-id="ff358-113">Označuje, že aplikace pracovního postupu byl uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="ff358-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff358-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ff358-114">Message</span></span>  
 <span data-ttu-id="ff358-115">Instance pracovního postupu Id: '%1' bylo uvolněno.</span><span class="sxs-lookup"><span data-stu-id="ff358-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff358-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ff358-116">Details</span></span>  
  
|<span data-ttu-id="ff358-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ff358-117">Data Item Name</span></span>|<span data-ttu-id="ff358-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ff358-118">Data Item Type</span></span>|<span data-ttu-id="ff358-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ff358-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff358-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ff358-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="ff358-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ff358-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="ff358-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ff358-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ff358-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ff358-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
