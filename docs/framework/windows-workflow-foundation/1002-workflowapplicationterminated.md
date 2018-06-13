---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510076"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="89731-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="89731-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="89731-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="89731-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89731-104">ID</span><span class="sxs-lookup"><span data-stu-id="89731-104">ID</span></span>|<span data-ttu-id="89731-105">1002</span><span class="sxs-lookup"><span data-stu-id="89731-105">1002</span></span>|  
|<span data-ttu-id="89731-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="89731-106">Keywords</span></span>|<span data-ttu-id="89731-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="89731-107">WFRuntime</span></span>|  
|<span data-ttu-id="89731-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="89731-108">Level</span></span>|<span data-ttu-id="89731-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="89731-109">Information</span></span>|  
|<span data-ttu-id="89731-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="89731-110">Channel</span></span>|<span data-ttu-id="89731-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="89731-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="89731-112">Popis</span><span class="sxs-lookup"><span data-stu-id="89731-112">Description</span></span>  
 <span data-ttu-id="89731-113">Označuje, že aplikace pracovního postupu byl ukončen ve stavu chybný s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="89731-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="89731-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="89731-114">Message</span></span>  
 <span data-ttu-id="89731-115">WorkflowApplication Id: "%1" byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="89731-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="89731-116">Dokončil v chybném stavu s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="89731-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="89731-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="89731-117">Details</span></span>  
  
|<span data-ttu-id="89731-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="89731-118">Data Item Name</span></span>|<span data-ttu-id="89731-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="89731-119">Data Item Type</span></span>|<span data-ttu-id="89731-120">Popis</span><span class="sxs-lookup"><span data-stu-id="89731-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="89731-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="89731-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="89731-122">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="89731-122">The workflow application id</span></span>|  
|<span data-ttu-id="89731-123">Výjimka</span><span class="sxs-lookup"><span data-stu-id="89731-123">Exception</span></span>|`xs:string`|<span data-ttu-id="89731-124">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="89731-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="89731-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="89731-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="89731-126">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="89731-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
