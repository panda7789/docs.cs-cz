---
title: 1028 – CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008808"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="78746-102">1028 – CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="78746-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="78746-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="78746-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78746-104">ID</span><span class="sxs-lookup"><span data-stu-id="78746-104">ID</span></span>|<span data-ttu-id="78746-105">1028</span><span class="sxs-lookup"><span data-stu-id="78746-105">1028</span></span>|  
|<span data-ttu-id="78746-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="78746-106">Keywords</span></span>|<span data-ttu-id="78746-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="78746-107">WFRuntime</span></span>|  
|<span data-ttu-id="78746-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="78746-108">Level</span></span>|<span data-ttu-id="78746-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="78746-109">Verbose</span></span>|  
|<span data-ttu-id="78746-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="78746-110">Channel</span></span>|<span data-ttu-id="78746-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="78746-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="78746-112">Popis</span><span class="sxs-lookup"><span data-stu-id="78746-112">Description</span></span>  
 <span data-ttu-id="78746-113">Označuje, že položka TransactionContextWorkItem byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="78746-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="78746-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="78746-114">Message</span></span>  
 <span data-ttu-id="78746-115">Položka TransactionContextWorkItem byla dokončena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="78746-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="78746-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="78746-116">Details</span></span>  
  
|<span data-ttu-id="78746-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="78746-117">Data Item Name</span></span>|<span data-ttu-id="78746-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="78746-118">Data Item Type</span></span>|<span data-ttu-id="78746-119">Popis</span><span class="sxs-lookup"><span data-stu-id="78746-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="78746-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="78746-120">Activity</span></span>|<span data-ttu-id="78746-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="78746-121">xs:string</span></span>|<span data-ttu-id="78746-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="78746-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="78746-123">displayName</span><span class="sxs-lookup"><span data-stu-id="78746-123">DisplayName</span></span>|<span data-ttu-id="78746-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="78746-124">xs:string</span></span>|<span data-ttu-id="78746-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="78746-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="78746-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="78746-126">InstanceId</span></span>|<span data-ttu-id="78746-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="78746-127">xs:string</span></span>|<span data-ttu-id="78746-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="78746-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="78746-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="78746-129">AppDomain</span></span>|<span data-ttu-id="78746-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="78746-130">xs:string</span></span>|<span data-ttu-id="78746-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="78746-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
