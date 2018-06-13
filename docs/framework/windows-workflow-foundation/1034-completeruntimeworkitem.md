---
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: bd49c608a8f6a6caab6975850507a00a2c0edb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509688"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="0fec4-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="0fec4-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0fec4-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0fec4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fec4-104">ID</span><span class="sxs-lookup"><span data-stu-id="0fec4-104">ID</span></span>|<span data-ttu-id="0fec4-105">1034</span><span class="sxs-lookup"><span data-stu-id="0fec4-105">1034</span></span>|  
|<span data-ttu-id="0fec4-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0fec4-106">Keywords</span></span>|<span data-ttu-id="0fec4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0fec4-107">WFRuntime</span></span>|  
|<span data-ttu-id="0fec4-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0fec4-108">Level</span></span>|<span data-ttu-id="0fec4-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="0fec4-109">Verbose</span></span>|  
|<span data-ttu-id="0fec4-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0fec4-110">Channel</span></span>|<span data-ttu-id="0fec4-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="0fec4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0fec4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0fec4-112">Description</span></span>  
 <span data-ttu-id="0fec4-113">Označuje, že je dokončená RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="0fec4-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0fec4-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0fec4-114">Message</span></span>  
 <span data-ttu-id="0fec4-115">Pracovní položky modulu runtime dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="0fec4-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0fec4-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0fec4-116">Details</span></span>  
  
|<span data-ttu-id="0fec4-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0fec4-117">Data Item Name</span></span>|<span data-ttu-id="0fec4-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="0fec4-118">Data Item Type</span></span>|<span data-ttu-id="0fec4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0fec4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0fec4-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="0fec4-120">Activity</span></span>|<span data-ttu-id="0fec4-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="0fec4-121">xs:string</span></span>|<span data-ttu-id="0fec4-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="0fec4-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0fec4-123">displayName</span><span class="sxs-lookup"><span data-stu-id="0fec4-123">DisplayName</span></span>|<span data-ttu-id="0fec4-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="0fec4-124">xs:string</span></span>|<span data-ttu-id="0fec4-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="0fec4-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0fec4-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="0fec4-126">InstanceId</span></span>|<span data-ttu-id="0fec4-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="0fec4-127">xs:string</span></span>|<span data-ttu-id="0fec4-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="0fec4-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0fec4-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="0fec4-129">AppDomain</span></span>|<span data-ttu-id="0fec4-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="0fec4-130">xs:string</span></span>|<span data-ttu-id="0fec4-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0fec4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
