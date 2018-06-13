---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509792"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="785c1-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="785c1-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="785c1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="785c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="785c1-104">ID</span><span class="sxs-lookup"><span data-stu-id="785c1-104">ID</span></span>|<span data-ttu-id="785c1-105">1001</span><span class="sxs-lookup"><span data-stu-id="785c1-105">1001</span></span>|  
|<span data-ttu-id="785c1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="785c1-106">Keywords</span></span>|<span data-ttu-id="785c1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="785c1-107">WFRuntime</span></span>|  
|<span data-ttu-id="785c1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="785c1-108">Level</span></span>|<span data-ttu-id="785c1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="785c1-109">Information</span></span>|  
|<span data-ttu-id="785c1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="785c1-110">Channel</span></span>|<span data-ttu-id="785c1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="785c1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="785c1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="785c1-112">Description</span></span>  
 <span data-ttu-id="785c1-113">Označuje, že aplikace pracovního postupu byla dokončena v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="785c1-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="785c1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="785c1-114">Message</span></span>  
 <span data-ttu-id="785c1-115">Instance pracovního postupu Id: '%1' byla dokončena v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="785c1-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="785c1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="785c1-116">Details</span></span>  
  
|<span data-ttu-id="785c1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="785c1-117">Data Item Name</span></span>|<span data-ttu-id="785c1-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="785c1-118">Data Item Type</span></span>|<span data-ttu-id="785c1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="785c1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="785c1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="785c1-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="785c1-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="785c1-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="785c1-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="785c1-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="785c1-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="785c1-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
