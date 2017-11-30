---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="40489-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="40489-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="40489-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="40489-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40489-104">ID</span><span class="sxs-lookup"><span data-stu-id="40489-104">ID</span></span>|<span data-ttu-id="40489-105">1008</span><span class="sxs-lookup"><span data-stu-id="40489-105">1008</span></span>|  
|<span data-ttu-id="40489-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="40489-106">Keywords</span></span>|<span data-ttu-id="40489-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="40489-107">WFRuntime</span></span>|  
|<span data-ttu-id="40489-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="40489-108">Level</span></span>|<span data-ttu-id="40489-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="40489-109">Information</span></span>|  
|<span data-ttu-id="40489-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="40489-110">Channel</span></span>|<span data-ttu-id="40489-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="40489-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="40489-112">Popis</span><span class="sxs-lookup"><span data-stu-id="40489-112">Description</span></span>  
 <span data-ttu-id="40489-113">Označuje, že aplikace pracovního postupu byl uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="40489-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="40489-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="40489-114">Message</span></span>  
 <span data-ttu-id="40489-115">Instance pracovního postupu Id: '%1' bylo uvolněno.</span><span class="sxs-lookup"><span data-stu-id="40489-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="40489-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="40489-116">Details</span></span>  
  
|<span data-ttu-id="40489-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="40489-117">Data Item Name</span></span>|<span data-ttu-id="40489-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="40489-118">Data Item Type</span></span>|<span data-ttu-id="40489-119">Popis</span><span class="sxs-lookup"><span data-stu-id="40489-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="40489-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="40489-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="40489-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="40489-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="40489-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="40489-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="40489-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="40489-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
