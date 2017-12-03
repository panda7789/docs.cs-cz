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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2603621eb23747275e6db22a1743c5260967c6a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="79243-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="79243-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="79243-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="79243-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79243-104">ID</span><span class="sxs-lookup"><span data-stu-id="79243-104">ID</span></span>|<span data-ttu-id="79243-105">1005</span><span class="sxs-lookup"><span data-stu-id="79243-105">1005</span></span>|  
|<span data-ttu-id="79243-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="79243-106">Keywords</span></span>|<span data-ttu-id="79243-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="79243-107">WFRuntime</span></span>|  
|<span data-ttu-id="79243-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="79243-108">Level</span></span>|<span data-ttu-id="79243-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="79243-109">Information</span></span>|  
|<span data-ttu-id="79243-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="79243-110">Channel</span></span>|<span data-ttu-id="79243-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="79243-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="79243-112">Popis</span><span class="sxs-lookup"><span data-stu-id="79243-112">Description</span></span>  
 <span data-ttu-id="79243-113">Označuje, že má nečinný aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="79243-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="79243-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="79243-114">Message</span></span>  
 <span data-ttu-id="79243-115">WorkflowApplication Id: "%1" se nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="79243-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79243-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="79243-116">Details</span></span>  
  
|<span data-ttu-id="79243-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="79243-117">Data Item Name</span></span>|<span data-ttu-id="79243-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="79243-118">Data Item Type</span></span>|<span data-ttu-id="79243-119">Popis</span><span class="sxs-lookup"><span data-stu-id="79243-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="79243-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="79243-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="79243-121">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="79243-121">The workflow application id</span></span>|  
|<span data-ttu-id="79243-122">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="79243-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="79243-123">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="79243-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
