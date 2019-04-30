---
title: 1033 – StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924238"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="d9eb2-102">1033 – StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="d9eb2-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d9eb2-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d9eb2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9eb2-104">ID</span><span class="sxs-lookup"><span data-stu-id="d9eb2-104">ID</span></span>|<span data-ttu-id="d9eb2-105">1033</span><span class="sxs-lookup"><span data-stu-id="d9eb2-105">1033</span></span>|  
|<span data-ttu-id="d9eb2-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d9eb2-106">Keywords</span></span>|<span data-ttu-id="d9eb2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d9eb2-107">WFRuntime</span></span>|  
|<span data-ttu-id="d9eb2-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d9eb2-108">Level</span></span>|<span data-ttu-id="d9eb2-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d9eb2-109">Verbose</span></span>|  
|<span data-ttu-id="d9eb2-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d9eb2-110">Channel</span></span>|<span data-ttu-id="d9eb2-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="d9eb2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d9eb2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d9eb2-112">Description</span></span>  
 <span data-ttu-id="d9eb2-113">Označuje, že že runtimeworkitem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="d9eb2-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d9eb2-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d9eb2-114">Message</span></span>  
 <span data-ttu-id="d9eb2-115">Spouštění provedení běhové pracovní položky pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d9eb2-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d9eb2-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d9eb2-116">Details</span></span>  
  
|<span data-ttu-id="d9eb2-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d9eb2-117">Data Item Name</span></span>|<span data-ttu-id="d9eb2-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="d9eb2-118">Data Item Type</span></span>|<span data-ttu-id="d9eb2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d9eb2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d9eb2-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="d9eb2-120">Activity</span></span>|<span data-ttu-id="d9eb2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d9eb2-121">xs:string</span></span>|<span data-ttu-id="d9eb2-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9eb2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d9eb2-123">displayName</span><span class="sxs-lookup"><span data-stu-id="d9eb2-123">DisplayName</span></span>|<span data-ttu-id="d9eb2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d9eb2-124">xs:string</span></span>|<span data-ttu-id="d9eb2-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9eb2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d9eb2-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d9eb2-126">InstanceId</span></span>|<span data-ttu-id="d9eb2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d9eb2-127">xs:string</span></span>|<span data-ttu-id="d9eb2-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9eb2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d9eb2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d9eb2-129">AppDomain</span></span>|<span data-ttu-id="d9eb2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="d9eb2-130">xs:string</span></span>|<span data-ttu-id="d9eb2-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d9eb2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
