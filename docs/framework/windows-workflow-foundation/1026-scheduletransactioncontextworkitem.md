---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510280"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="62cce-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="62cce-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="62cce-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="62cce-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62cce-104">ID</span><span class="sxs-lookup"><span data-stu-id="62cce-104">ID</span></span>|<span data-ttu-id="62cce-105">1026</span><span class="sxs-lookup"><span data-stu-id="62cce-105">1026</span></span>|  
|<span data-ttu-id="62cce-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="62cce-106">Keywords</span></span>|<span data-ttu-id="62cce-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="62cce-107">WFRuntime</span></span>|  
|<span data-ttu-id="62cce-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="62cce-108">Level</span></span>|<span data-ttu-id="62cce-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="62cce-109">Verbose</span></span>|  
|<span data-ttu-id="62cce-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="62cce-110">Channel</span></span>|<span data-ttu-id="62cce-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="62cce-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="62cce-112">Popis</span><span class="sxs-lookup"><span data-stu-id="62cce-112">Description</span></span>  
 <span data-ttu-id="62cce-113">Označuje, že bylo naplánováno TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="62cce-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="62cce-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="62cce-114">Message</span></span>  
 <span data-ttu-id="62cce-115">Bylo naplánováno TransactionContextWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="62cce-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="62cce-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="62cce-116">Details</span></span>  
  
|<span data-ttu-id="62cce-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="62cce-117">Data Item Name</span></span>|<span data-ttu-id="62cce-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="62cce-118">Data Item Type</span></span>|<span data-ttu-id="62cce-119">Popis</span><span class="sxs-lookup"><span data-stu-id="62cce-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="62cce-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="62cce-120">Activity</span></span>|<span data-ttu-id="62cce-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="62cce-121">xs:string</span></span>|<span data-ttu-id="62cce-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="62cce-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="62cce-123">displayName</span><span class="sxs-lookup"><span data-stu-id="62cce-123">DisplayName</span></span>|<span data-ttu-id="62cce-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="62cce-124">xs:string</span></span>|<span data-ttu-id="62cce-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="62cce-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="62cce-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="62cce-126">InstanceId</span></span>|<span data-ttu-id="62cce-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="62cce-127">xs:string</span></span>|<span data-ttu-id="62cce-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="62cce-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="62cce-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="62cce-129">AppDomain</span></span>|<span data-ttu-id="62cce-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="62cce-130">xs:string</span></span>|<span data-ttu-id="62cce-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="62cce-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
