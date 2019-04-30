---
title: 1007 – WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: 0b3c290ad06eda6921626c0d7a1c8ec854c30e7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925265"
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="b63c4-102">1007 – WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="b63c4-102">1007 - WorkflowApplicationPersisted</span></span>
## <a name="properties"></a><span data-ttu-id="b63c4-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b63c4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b63c4-104">ID</span><span class="sxs-lookup"><span data-stu-id="b63c4-104">ID</span></span>|<span data-ttu-id="b63c4-105">1007</span><span class="sxs-lookup"><span data-stu-id="b63c4-105">1007</span></span>|  
|<span data-ttu-id="b63c4-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b63c4-106">Keywords</span></span>|<span data-ttu-id="b63c4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b63c4-107">WFRuntime</span></span>|  
|<span data-ttu-id="b63c4-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b63c4-108">Level</span></span>|<span data-ttu-id="b63c4-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="b63c4-109">Information</span></span>|  
|<span data-ttu-id="b63c4-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b63c4-110">Channel</span></span>|<span data-ttu-id="b63c4-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="b63c4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b63c4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b63c4-112">Description</span></span>  
 <span data-ttu-id="b63c4-113">Označuje, že obsahuje trvalé aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b63c4-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b63c4-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b63c4-114">Message</span></span>  
 <span data-ttu-id="b63c4-115">WorkflowApplication Id: '%1' byl trvale uložen.</span><span class="sxs-lookup"><span data-stu-id="b63c4-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b63c4-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b63c4-116">Details</span></span>  
  
|<span data-ttu-id="b63c4-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b63c4-117">Data Item Name</span></span>|<span data-ttu-id="b63c4-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="b63c4-118">Data Item Type</span></span>|<span data-ttu-id="b63c4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b63c4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b63c4-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b63c4-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="b63c4-121">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b63c4-121">The workflow application id</span></span>|  
|<span data-ttu-id="b63c4-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b63c4-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b63c4-123">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b63c4-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
