---
title: 1018 – StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008860"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="9abe6-102">1018 – StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="9abe6-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9abe6-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9abe6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9abe6-104">ID</span><span class="sxs-lookup"><span data-stu-id="9abe6-104">ID</span></span>|<span data-ttu-id="9abe6-105">1018</span><span class="sxs-lookup"><span data-stu-id="9abe6-105">1018</span></span>|  
|<span data-ttu-id="9abe6-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9abe6-106">Keywords</span></span>|<span data-ttu-id="9abe6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9abe6-107">WFRuntime</span></span>|  
|<span data-ttu-id="9abe6-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9abe6-108">Level</span></span>|<span data-ttu-id="9abe6-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9abe6-109">Verbose</span></span>|  
|<span data-ttu-id="9abe6-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9abe6-110">Channel</span></span>|<span data-ttu-id="9abe6-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="9abe6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9abe6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9abe6-112">Description</span></span>  
 <span data-ttu-id="9abe6-113">Označuje, že položka CancelActivityWorkItem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="9abe6-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9abe6-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9abe6-114">Message</span></span>  
 <span data-ttu-id="9abe6-115">Začátek provádění položky CancelActivityWorkItem pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9abe6-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9abe6-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9abe6-116">Details</span></span>  
  
|<span data-ttu-id="9abe6-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9abe6-117">Data Item Name</span></span>|<span data-ttu-id="9abe6-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="9abe6-118">Data Item Type</span></span>|<span data-ttu-id="9abe6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9abe6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9abe6-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="9abe6-120">Activity</span></span>|<span data-ttu-id="9abe6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9abe6-121">xs:string</span></span>|<span data-ttu-id="9abe6-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="9abe6-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9abe6-123">displayName</span><span class="sxs-lookup"><span data-stu-id="9abe6-123">DisplayName</span></span>|<span data-ttu-id="9abe6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9abe6-124">xs:string</span></span>|<span data-ttu-id="9abe6-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="9abe6-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9abe6-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9abe6-126">InstanceId</span></span>|<span data-ttu-id="9abe6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="9abe6-127">xs:string</span></span>|<span data-ttu-id="9abe6-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="9abe6-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9abe6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9abe6-129">AppDomain</span></span>|<span data-ttu-id="9abe6-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="9abe6-130">xs:string</span></span>|<span data-ttu-id="9abe6-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9abe6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
