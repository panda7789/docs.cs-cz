---
title: 1041 – WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924186"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="80dfa-102">1041 – WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="80dfa-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="80dfa-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="80dfa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80dfa-104">ID</span><span class="sxs-lookup"><span data-stu-id="80dfa-104">ID</span></span>|<span data-ttu-id="80dfa-105">1041</span><span class="sxs-lookup"><span data-stu-id="80dfa-105">1041</span></span>|  
|<span data-ttu-id="80dfa-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="80dfa-106">Keywords</span></span>|<span data-ttu-id="80dfa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="80dfa-107">WFRuntime</span></span>|  
|<span data-ttu-id="80dfa-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="80dfa-108">Level</span></span>|<span data-ttu-id="80dfa-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="80dfa-109">Information</span></span>|  
|<span data-ttu-id="80dfa-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="80dfa-110">Channel</span></span>|<span data-ttu-id="80dfa-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="80dfa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80dfa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="80dfa-112">Description</span></span>  
 <span data-ttu-id="80dfa-113">Označuje, že aplikace pracovního postupu je nečinná a trvalá.</span><span class="sxs-lookup"><span data-stu-id="80dfa-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="80dfa-114">Aplikace pracovního postupu bude nečinný nebo trvalé.</span><span class="sxs-lookup"><span data-stu-id="80dfa-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80dfa-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="80dfa-115">Message</span></span>  
 <span data-ttu-id="80dfa-116">WorkflowApplication Id: '%1' je nečinná a trvalá.</span><span class="sxs-lookup"><span data-stu-id="80dfa-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="80dfa-117">Se provedou následující akce: %2.</span><span class="sxs-lookup"><span data-stu-id="80dfa-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80dfa-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="80dfa-118">Details</span></span>  
  
|<span data-ttu-id="80dfa-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="80dfa-119">Data Item Name</span></span>|<span data-ttu-id="80dfa-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="80dfa-120">Data Item Type</span></span>|<span data-ttu-id="80dfa-121">Popis</span><span class="sxs-lookup"><span data-stu-id="80dfa-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80dfa-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="80dfa-122">WorkflowApplicationId</span></span>|<span data-ttu-id="80dfa-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="80dfa-123">xs:string</span></span>|<span data-ttu-id="80dfa-124">Id aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="80dfa-124">The workflow application id</span></span>|  
|<span data-ttu-id="80dfa-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="80dfa-125">ActionTaken</span></span>|<span data-ttu-id="80dfa-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="80dfa-126">xs:string</span></span>|<span data-ttu-id="80dfa-127">Akce, které se provedou na aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="80dfa-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="80dfa-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80dfa-128">AppDomain</span></span>|<span data-ttu-id="80dfa-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="80dfa-129">xs:string</span></span>|<span data-ttu-id="80dfa-130">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="80dfa-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
