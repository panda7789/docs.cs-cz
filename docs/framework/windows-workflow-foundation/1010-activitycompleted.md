---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509694"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="1dcb9-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="1dcb9-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="1dcb9-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1dcb9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1dcb9-104">ID</span><span class="sxs-lookup"><span data-stu-id="1dcb9-104">ID</span></span>|<span data-ttu-id="1dcb9-105">1010</span><span class="sxs-lookup"><span data-stu-id="1dcb9-105">1010</span></span>|  
|<span data-ttu-id="1dcb9-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1dcb9-106">Keywords</span></span>|<span data-ttu-id="1dcb9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1dcb9-107">WFRuntime</span></span>|  
|<span data-ttu-id="1dcb9-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1dcb9-108">Level</span></span>|<span data-ttu-id="1dcb9-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="1dcb9-109">Information</span></span>|  
|<span data-ttu-id="1dcb9-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1dcb9-110">Channel</span></span>|<span data-ttu-id="1dcb9-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="1dcb9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1dcb9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1dcb9-112">Description</span></span>  
 <span data-ttu-id="1dcb9-113">Označuje, že aktivita dokončila spuštění.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1dcb9-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1dcb9-114">Message</span></span>  
 <span data-ttu-id="1dcb9-115">Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' byla dokončena ve stavu "%4".</span><span class="sxs-lookup"><span data-stu-id="1dcb9-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1dcb9-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1dcb9-116">Details</span></span>  
  
|<span data-ttu-id="1dcb9-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1dcb9-117">Data Item Name</span></span>|<span data-ttu-id="1dcb9-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1dcb9-118">Data Item Type</span></span>|<span data-ttu-id="1dcb9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1dcb9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1dcb9-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="1dcb9-120">Activity</span></span>|<span data-ttu-id="1dcb9-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dcb9-121">xs:string</span></span>|<span data-ttu-id="1dcb9-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1dcb9-123">displayName</span><span class="sxs-lookup"><span data-stu-id="1dcb9-123">DisplayName</span></span>|<span data-ttu-id="1dcb9-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dcb9-124">xs:string</span></span>|<span data-ttu-id="1dcb9-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1dcb9-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="1dcb9-126">InstanceId</span></span>|<span data-ttu-id="1dcb9-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dcb9-127">xs:string</span></span>|<span data-ttu-id="1dcb9-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1dcb9-129">Stav</span><span class="sxs-lookup"><span data-stu-id="1dcb9-129">State</span></span>|<span data-ttu-id="1dcb9-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dcb9-130">xs:string</span></span>|<span data-ttu-id="1dcb9-131">Stav aktivity.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-131">The state of the activity.</span></span>|  
|<span data-ttu-id="1dcb9-132">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1dcb9-132">AppDomain</span></span>|<span data-ttu-id="1dcb9-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dcb9-133">xs:string</span></span>|<span data-ttu-id="1dcb9-134">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1dcb9-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
