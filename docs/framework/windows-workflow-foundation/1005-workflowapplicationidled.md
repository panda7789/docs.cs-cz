---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="521ed-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="521ed-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="521ed-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="521ed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="521ed-104">ID</span><span class="sxs-lookup"><span data-stu-id="521ed-104">ID</span></span>|<span data-ttu-id="521ed-105">1005</span><span class="sxs-lookup"><span data-stu-id="521ed-105">1005</span></span>|  
|<span data-ttu-id="521ed-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="521ed-106">Keywords</span></span>|<span data-ttu-id="521ed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="521ed-107">WFRuntime</span></span>|  
|<span data-ttu-id="521ed-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="521ed-108">Level</span></span>|<span data-ttu-id="521ed-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="521ed-109">Information</span></span>|  
|<span data-ttu-id="521ed-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="521ed-110">Channel</span></span>|<span data-ttu-id="521ed-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="521ed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="521ed-112">Popis</span><span class="sxs-lookup"><span data-stu-id="521ed-112">Description</span></span>  
 <span data-ttu-id="521ed-113">Označuje, že má nečinný aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="521ed-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="521ed-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="521ed-114">Message</span></span>  
 <span data-ttu-id="521ed-115">WorkflowApplication Id: "%1" se nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="521ed-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="521ed-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="521ed-116">Details</span></span>  
  
|<span data-ttu-id="521ed-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="521ed-117">Data Item Name</span></span>|<span data-ttu-id="521ed-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="521ed-118">Data Item Type</span></span>|<span data-ttu-id="521ed-119">Popis</span><span class="sxs-lookup"><span data-stu-id="521ed-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="521ed-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="521ed-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="521ed-121">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="521ed-121">The workflow application id</span></span>|  
|<span data-ttu-id="521ed-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="521ed-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="521ed-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="521ed-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
