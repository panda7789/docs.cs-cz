---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510063"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="eead0-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="eead0-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="eead0-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eead0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eead0-104">ID</span><span class="sxs-lookup"><span data-stu-id="eead0-104">ID</span></span>|<span data-ttu-id="eead0-105">1033</span><span class="sxs-lookup"><span data-stu-id="eead0-105">1033</span></span>|  
|<span data-ttu-id="eead0-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="eead0-106">Keywords</span></span>|<span data-ttu-id="eead0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="eead0-107">WFRuntime</span></span>|  
|<span data-ttu-id="eead0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="eead0-108">Level</span></span>|<span data-ttu-id="eead0-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="eead0-109">Verbose</span></span>|  
|<span data-ttu-id="eead0-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="eead0-110">Channel</span></span>|<span data-ttu-id="eead0-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="eead0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eead0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="eead0-112">Description</span></span>  
 <span data-ttu-id="eead0-113">Označuje, že že runtimeworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="eead0-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eead0-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="eead0-114">Message</span></span>  
 <span data-ttu-id="eead0-115">Spouštění spuštění pracovní položky modulu runtime pro aktivitu %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="eead0-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eead0-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="eead0-116">Details</span></span>  
  
|<span data-ttu-id="eead0-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="eead0-117">Data Item Name</span></span>|<span data-ttu-id="eead0-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="eead0-118">Data Item Type</span></span>|<span data-ttu-id="eead0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="eead0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eead0-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="eead0-120">Activity</span></span>|<span data-ttu-id="eead0-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="eead0-121">xs:string</span></span>|<span data-ttu-id="eead0-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="eead0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="eead0-123">displayName</span><span class="sxs-lookup"><span data-stu-id="eead0-123">DisplayName</span></span>|<span data-ttu-id="eead0-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="eead0-124">xs:string</span></span>|<span data-ttu-id="eead0-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="eead0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="eead0-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="eead0-126">InstanceId</span></span>|<span data-ttu-id="eead0-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="eead0-127">xs:string</span></span>|<span data-ttu-id="eead0-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="eead0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="eead0-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="eead0-129">AppDomain</span></span>|<span data-ttu-id="eead0-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="eead0-130">xs:string</span></span>|<span data-ttu-id="eead0-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="eead0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
