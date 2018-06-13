---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510754"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="9fc7b-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="9fc7b-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="9fc7b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9fc7b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9fc7b-104">ID</span><span class="sxs-lookup"><span data-stu-id="9fc7b-104">ID</span></span>|<span data-ttu-id="9fc7b-105">1006</span><span class="sxs-lookup"><span data-stu-id="9fc7b-105">1006</span></span>|  
|<span data-ttu-id="9fc7b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9fc7b-106">Keywords</span></span>|<span data-ttu-id="9fc7b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9fc7b-107">WFRuntime</span></span>|  
|<span data-ttu-id="9fc7b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9fc7b-108">Level</span></span>|<span data-ttu-id="9fc7b-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="9fc7b-109">Error</span></span>|  
|<span data-ttu-id="9fc7b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9fc7b-110">Channel</span></span>|<span data-ttu-id="9fc7b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9fc7b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9fc7b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9fc7b-112">Description</span></span>  
 <span data-ttu-id="9fc7b-113">Označuje, že aplikace pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9fc7b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9fc7b-114">Message</span></span>  
 <span data-ttu-id="9fc7b-115">Id instance pracovního postupu: '%1' došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="9fc7b-116">Výjimka pochází z aktivity %2, DisplayName: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="9fc7b-117">Se provedou následující akce: %4.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9fc7b-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9fc7b-118">Details</span></span>  
  
|<span data-ttu-id="9fc7b-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9fc7b-119">Data Item Name</span></span>|<span data-ttu-id="9fc7b-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9fc7b-120">Data Item Type</span></span>|<span data-ttu-id="9fc7b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9fc7b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9fc7b-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9fc7b-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9fc7b-123">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9fc7b-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9fc7b-124">Výjimka</span><span class="sxs-lookup"><span data-stu-id="9fc7b-124">Exception</span></span>|`xs:string`|<span data-ttu-id="9fc7b-125">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="9fc7b-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="9fc7b-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9fc7b-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9fc7b-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
