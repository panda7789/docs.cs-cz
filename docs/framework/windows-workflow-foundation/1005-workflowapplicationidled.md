---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509291"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="73c25-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="73c25-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="73c25-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="73c25-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73c25-104">ID</span><span class="sxs-lookup"><span data-stu-id="73c25-104">ID</span></span>|<span data-ttu-id="73c25-105">1005</span><span class="sxs-lookup"><span data-stu-id="73c25-105">1005</span></span>|  
|<span data-ttu-id="73c25-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="73c25-106">Keywords</span></span>|<span data-ttu-id="73c25-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="73c25-107">WFRuntime</span></span>|  
|<span data-ttu-id="73c25-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="73c25-108">Level</span></span>|<span data-ttu-id="73c25-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="73c25-109">Information</span></span>|  
|<span data-ttu-id="73c25-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="73c25-110">Channel</span></span>|<span data-ttu-id="73c25-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="73c25-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73c25-112">Popis</span><span class="sxs-lookup"><span data-stu-id="73c25-112">Description</span></span>  
 <span data-ttu-id="73c25-113">Označuje, že má nečinný aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="73c25-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73c25-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="73c25-114">Message</span></span>  
 <span data-ttu-id="73c25-115">WorkflowApplication Id: "%1" se nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="73c25-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73c25-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="73c25-116">Details</span></span>  
  
|<span data-ttu-id="73c25-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="73c25-117">Data Item Name</span></span>|<span data-ttu-id="73c25-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="73c25-118">Data Item Type</span></span>|<span data-ttu-id="73c25-119">Popis</span><span class="sxs-lookup"><span data-stu-id="73c25-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73c25-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="73c25-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="73c25-121">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="73c25-121">The workflow application id</span></span>|  
|<span data-ttu-id="73c25-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="73c25-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="73c25-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="73c25-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
