---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d1eaf3cf107a6b5e244cc2d9372ee68d387ef6c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510663"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="a9172-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="a9172-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="a9172-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9172-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9172-104">ID</span><span class="sxs-lookup"><span data-stu-id="a9172-104">ID</span></span>|<span data-ttu-id="a9172-105">1004</span><span class="sxs-lookup"><span data-stu-id="a9172-105">1004</span></span>|  
|<span data-ttu-id="a9172-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a9172-106">Keywords</span></span>|<span data-ttu-id="a9172-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a9172-107">WFRuntime</span></span>|  
|<span data-ttu-id="a9172-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a9172-108">Level</span></span>|<span data-ttu-id="a9172-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a9172-109">Information</span></span>|  
|<span data-ttu-id="a9172-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a9172-110">Channel</span></span>|<span data-ttu-id="a9172-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a9172-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9172-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a9172-112">Description</span></span>  
 <span data-ttu-id="a9172-113">Označuje, že worfklow instance přerušil s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="a9172-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9172-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a9172-114">Message</span></span>  
 <span data-ttu-id="a9172-115">Instance pracovního postupu Id: '%1' byla přerušena, s výjimkou.</span><span class="sxs-lookup"><span data-stu-id="a9172-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9172-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a9172-116">Details</span></span>  
  
|<span data-ttu-id="a9172-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a9172-117">Data Item Name</span></span>|<span data-ttu-id="a9172-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a9172-118">Data Item Type</span></span>|<span data-ttu-id="a9172-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a9172-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9172-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a9172-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="a9172-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a9172-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a9172-122">Výjimka</span><span class="sxs-lookup"><span data-stu-id="a9172-122">Exception</span></span>|`xs:string`|<span data-ttu-id="a9172-123">Podrobnosti o výjimce pro výjimky</span><span class="sxs-lookup"><span data-stu-id="a9172-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="a9172-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a9172-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a9172-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a9172-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
