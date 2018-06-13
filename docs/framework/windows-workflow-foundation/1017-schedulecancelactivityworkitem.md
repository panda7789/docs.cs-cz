---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510169"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="80ea9-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="80ea9-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="80ea9-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="80ea9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80ea9-104">ID</span><span class="sxs-lookup"><span data-stu-id="80ea9-104">ID</span></span>|<span data-ttu-id="80ea9-105">1017</span><span class="sxs-lookup"><span data-stu-id="80ea9-105">1017</span></span>|  
|<span data-ttu-id="80ea9-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="80ea9-106">Keywords</span></span>|<span data-ttu-id="80ea9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="80ea9-107">WFRuntime</span></span>|  
|<span data-ttu-id="80ea9-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="80ea9-108">Level</span></span>|<span data-ttu-id="80ea9-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="80ea9-109">Verbose</span></span>|  
|<span data-ttu-id="80ea9-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="80ea9-110">Channel</span></span>|<span data-ttu-id="80ea9-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="80ea9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80ea9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="80ea9-112">Description</span></span>  
 <span data-ttu-id="80ea9-113">Označuje, že bylo naplánováno CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="80ea9-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80ea9-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="80ea9-114">Message</span></span>  
 <span data-ttu-id="80ea9-115">Bylo naplánováno CancelActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="80ea9-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80ea9-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="80ea9-116">Details</span></span>  
  
|<span data-ttu-id="80ea9-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="80ea9-117">Data Item Name</span></span>|<span data-ttu-id="80ea9-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="80ea9-118">Data Item Type</span></span>|<span data-ttu-id="80ea9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="80ea9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80ea9-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="80ea9-120">Activity</span></span>|<span data-ttu-id="80ea9-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="80ea9-121">xs:string</span></span>|<span data-ttu-id="80ea9-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="80ea9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="80ea9-123">displayName</span><span class="sxs-lookup"><span data-stu-id="80ea9-123">DisplayName</span></span>|<span data-ttu-id="80ea9-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="80ea9-124">xs:string</span></span>|<span data-ttu-id="80ea9-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="80ea9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="80ea9-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="80ea9-126">InstanceId</span></span>|<span data-ttu-id="80ea9-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="80ea9-127">xs:string</span></span>|<span data-ttu-id="80ea9-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="80ea9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="80ea9-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="80ea9-129">AppDomain</span></span>|<span data-ttu-id="80ea9-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="80ea9-130">xs:string</span></span>|<span data-ttu-id="80ea9-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="80ea9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
