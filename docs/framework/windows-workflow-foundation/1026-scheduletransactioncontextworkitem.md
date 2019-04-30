---
title: 1026 – ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924628"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="e79ee-102">1026 – ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="e79ee-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e79ee-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e79ee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e79ee-104">ID</span><span class="sxs-lookup"><span data-stu-id="e79ee-104">ID</span></span>|<span data-ttu-id="e79ee-105">1026</span><span class="sxs-lookup"><span data-stu-id="e79ee-105">1026</span></span>|  
|<span data-ttu-id="e79ee-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e79ee-106">Keywords</span></span>|<span data-ttu-id="e79ee-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e79ee-107">WFRuntime</span></span>|  
|<span data-ttu-id="e79ee-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e79ee-108">Level</span></span>|<span data-ttu-id="e79ee-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e79ee-109">Verbose</span></span>|  
|<span data-ttu-id="e79ee-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e79ee-110">Channel</span></span>|<span data-ttu-id="e79ee-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e79ee-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e79ee-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e79ee-112">Description</span></span>  
 <span data-ttu-id="e79ee-113">Označuje, že položka TransactionContextWorkItem byla plánována.</span><span class="sxs-lookup"><span data-stu-id="e79ee-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e79ee-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e79ee-114">Message</span></span>  
 <span data-ttu-id="e79ee-115">Položka TransactionContextWorkItem byla plánována pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e79ee-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e79ee-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e79ee-116">Details</span></span>  
  
|<span data-ttu-id="e79ee-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e79ee-117">Data Item Name</span></span>|<span data-ttu-id="e79ee-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e79ee-118">Data Item Type</span></span>|<span data-ttu-id="e79ee-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e79ee-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e79ee-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="e79ee-120">Activity</span></span>|<span data-ttu-id="e79ee-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79ee-121">xs:string</span></span>|<span data-ttu-id="e79ee-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="e79ee-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e79ee-123">displayName</span><span class="sxs-lookup"><span data-stu-id="e79ee-123">DisplayName</span></span>|<span data-ttu-id="e79ee-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79ee-124">xs:string</span></span>|<span data-ttu-id="e79ee-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="e79ee-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e79ee-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e79ee-126">InstanceId</span></span>|<span data-ttu-id="e79ee-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79ee-127">xs:string</span></span>|<span data-ttu-id="e79ee-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="e79ee-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e79ee-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e79ee-129">AppDomain</span></span>|<span data-ttu-id="e79ee-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79ee-130">xs:string</span></span>|<span data-ttu-id="e79ee-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e79ee-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
