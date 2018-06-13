---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509650"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="8ad38-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="8ad38-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="8ad38-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8ad38-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ad38-104">ID</span><span class="sxs-lookup"><span data-stu-id="8ad38-104">ID</span></span>|<span data-ttu-id="8ad38-105">1041</span><span class="sxs-lookup"><span data-stu-id="8ad38-105">1041</span></span>|  
|<span data-ttu-id="8ad38-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8ad38-106">Keywords</span></span>|<span data-ttu-id="8ad38-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8ad38-107">WFRuntime</span></span>|  
|<span data-ttu-id="8ad38-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8ad38-108">Level</span></span>|<span data-ttu-id="8ad38-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="8ad38-109">Information</span></span>|  
|<span data-ttu-id="8ad38-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8ad38-110">Channel</span></span>|<span data-ttu-id="8ad38-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="8ad38-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8ad38-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8ad38-112">Description</span></span>  
 <span data-ttu-id="8ad38-113">Označuje, že je aplikace pracovního postupu nečinnosti a trvalá.</span><span class="sxs-lookup"><span data-stu-id="8ad38-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="8ad38-114">Pracovní postup aplikace nečinný nebo trvalé.</span><span class="sxs-lookup"><span data-stu-id="8ad38-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8ad38-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8ad38-115">Message</span></span>  
 <span data-ttu-id="8ad38-116">WorkflowApplication Id: '%1' je nečinnosti a trvalá.</span><span class="sxs-lookup"><span data-stu-id="8ad38-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="8ad38-117">Se provedou následující akce: %2.</span><span class="sxs-lookup"><span data-stu-id="8ad38-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8ad38-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8ad38-118">Details</span></span>  
  
|<span data-ttu-id="8ad38-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8ad38-119">Data Item Name</span></span>|<span data-ttu-id="8ad38-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8ad38-120">Data Item Type</span></span>|<span data-ttu-id="8ad38-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8ad38-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8ad38-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="8ad38-122">WorkflowApplicationId</span></span>|<span data-ttu-id="8ad38-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ad38-123">xs:string</span></span>|<span data-ttu-id="8ad38-124">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8ad38-124">The workflow application id</span></span>|  
|<span data-ttu-id="8ad38-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="8ad38-125">ActionTaken</span></span>|<span data-ttu-id="8ad38-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ad38-126">xs:string</span></span>|<span data-ttu-id="8ad38-127">Akce, která budete přesměrováni na aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8ad38-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="8ad38-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8ad38-128">AppDomain</span></span>|<span data-ttu-id="8ad38-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="8ad38-129">xs:string</span></span>|<span data-ttu-id="8ad38-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8ad38-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
