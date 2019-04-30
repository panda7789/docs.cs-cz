---
title: 1006 – WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924706"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="3797a-102">1006 – WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="3797a-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="3797a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3797a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3797a-104">ID</span><span class="sxs-lookup"><span data-stu-id="3797a-104">ID</span></span>|<span data-ttu-id="3797a-105">1006</span><span class="sxs-lookup"><span data-stu-id="3797a-105">1006</span></span>|  
|<span data-ttu-id="3797a-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3797a-106">Keywords</span></span>|<span data-ttu-id="3797a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3797a-107">WFRuntime</span></span>|  
|<span data-ttu-id="3797a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3797a-108">Level</span></span>|<span data-ttu-id="3797a-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="3797a-109">Error</span></span>|  
|<span data-ttu-id="3797a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3797a-110">Channel</span></span>|<span data-ttu-id="3797a-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="3797a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3797a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3797a-112">Description</span></span>  
 <span data-ttu-id="3797a-113">Označuje, že aplikace pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="3797a-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3797a-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3797a-114">Message</span></span>  
 <span data-ttu-id="3797a-115">WorkflowInstance Id: '%1' došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="3797a-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="3797a-116">Výjimka pochází z aktivity %2, DisplayName: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3797a-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="3797a-117">Se provedou následující akce: %4.</span><span class="sxs-lookup"><span data-stu-id="3797a-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3797a-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3797a-118">Details</span></span>  
  
|<span data-ttu-id="3797a-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3797a-119">Data Item Name</span></span>|<span data-ttu-id="3797a-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="3797a-120">Data Item Type</span></span>|<span data-ttu-id="3797a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3797a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3797a-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3797a-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="3797a-123">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3797a-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="3797a-124">Výjimka</span><span class="sxs-lookup"><span data-stu-id="3797a-124">Exception</span></span>|`xs:string`|<span data-ttu-id="3797a-125">Podrobnosti o výjimce pro výjimku</span><span class="sxs-lookup"><span data-stu-id="3797a-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="3797a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3797a-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3797a-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3797a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
