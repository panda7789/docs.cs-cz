---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a62a8448319e7b07a3ea302f00f2fa269bf654ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="d8d34-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="d8d34-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="d8d34-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d8d34-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8d34-104">ID</span><span class="sxs-lookup"><span data-stu-id="d8d34-104">ID</span></span>|<span data-ttu-id="d8d34-105">1001</span><span class="sxs-lookup"><span data-stu-id="d8d34-105">1001</span></span>|  
|<span data-ttu-id="d8d34-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d8d34-106">Keywords</span></span>|<span data-ttu-id="d8d34-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d8d34-107">WFRuntime</span></span>|  
|<span data-ttu-id="d8d34-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d8d34-108">Level</span></span>|<span data-ttu-id="d8d34-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="d8d34-109">Information</span></span>|  
|<span data-ttu-id="d8d34-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d8d34-110">Channel</span></span>|<span data-ttu-id="d8d34-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="d8d34-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d8d34-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d8d34-112">Description</span></span>  
 <span data-ttu-id="d8d34-113">Označuje, že aplikace pracovního postupu byla dokončena v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="d8d34-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d8d34-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d8d34-114">Message</span></span>  
 <span data-ttu-id="d8d34-115">Instance pracovního postupu Id: '%1' byla dokončena v uzavřeném stavu.</span><span class="sxs-lookup"><span data-stu-id="d8d34-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d8d34-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d8d34-116">Details</span></span>  
  
|<span data-ttu-id="d8d34-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d8d34-117">Data Item Name</span></span>|<span data-ttu-id="d8d34-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="d8d34-118">Data Item Type</span></span>|<span data-ttu-id="d8d34-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d8d34-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d8d34-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d8d34-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="d8d34-121">Id instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d8d34-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="d8d34-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d8d34-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d8d34-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d8d34-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
