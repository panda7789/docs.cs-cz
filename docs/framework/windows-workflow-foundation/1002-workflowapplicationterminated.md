---
title: 1002 – WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008652"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="74821-102">1002 – WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="74821-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="74821-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="74821-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74821-104">ID</span><span class="sxs-lookup"><span data-stu-id="74821-104">ID</span></span>|<span data-ttu-id="74821-105">1002</span><span class="sxs-lookup"><span data-stu-id="74821-105">1002</span></span>|  
|<span data-ttu-id="74821-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="74821-106">Keywords</span></span>|<span data-ttu-id="74821-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="74821-107">WFRuntime</span></span>|  
|<span data-ttu-id="74821-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="74821-108">Level</span></span>|<span data-ttu-id="74821-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="74821-109">Information</span></span>|  
|<span data-ttu-id="74821-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="74821-110">Channel</span></span>|<span data-ttu-id="74821-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="74821-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="74821-112">Popis</span><span class="sxs-lookup"><span data-stu-id="74821-112">Description</span></span>  
 <span data-ttu-id="74821-113">Označuje, že aplikace pracovního postupu byla ukončena v chybovém stavu s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="74821-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="74821-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="74821-114">Message</span></span>  
 <span data-ttu-id="74821-115">WorkflowApplication Id: '%1' byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="74821-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="74821-116">Byla dokončena v chybovém stavu s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="74821-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="74821-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="74821-117">Details</span></span>  
  
|<span data-ttu-id="74821-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="74821-118">Data Item Name</span></span>|<span data-ttu-id="74821-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="74821-119">Data Item Type</span></span>|<span data-ttu-id="74821-120">Popis</span><span class="sxs-lookup"><span data-stu-id="74821-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="74821-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="74821-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="74821-122">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="74821-122">The workflow application id</span></span>|  
|<span data-ttu-id="74821-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="74821-123">Exception</span></span>|`xs:string`|<span data-ttu-id="74821-124">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="74821-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="74821-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="74821-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="74821-126">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="74821-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
