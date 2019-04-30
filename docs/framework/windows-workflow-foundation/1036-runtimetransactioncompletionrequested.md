---
title: 1036 – RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924836"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="66413-102">1036 – RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="66413-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="66413-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="66413-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66413-104">ID</span><span class="sxs-lookup"><span data-stu-id="66413-104">ID</span></span>|<span data-ttu-id="66413-105">1036</span><span class="sxs-lookup"><span data-stu-id="66413-105">1036</span></span>|  
|<span data-ttu-id="66413-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="66413-106">Keywords</span></span>|<span data-ttu-id="66413-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="66413-107">WFRuntime</span></span>|  
|<span data-ttu-id="66413-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="66413-108">Level</span></span>|<span data-ttu-id="66413-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="66413-109">Verbose</span></span>|  
|<span data-ttu-id="66413-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="66413-110">Channel</span></span>|<span data-ttu-id="66413-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="66413-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66413-112">Popis</span><span class="sxs-lookup"><span data-stu-id="66413-112">Description</span></span>  
 <span data-ttu-id="66413-113">Označuje, že aktivita bylo plánováno dokončení běhové transakce.</span><span class="sxs-lookup"><span data-stu-id="66413-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="66413-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="66413-114">Message</span></span>  
 <span data-ttu-id="66413-115">Aktivita '%1', DisplayName: %2, InstanceId: '%3' bylo plánováno dokončení běhové transakce.</span><span class="sxs-lookup"><span data-stu-id="66413-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="66413-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="66413-116">Details</span></span>  
  
|<span data-ttu-id="66413-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="66413-117">Data Item Name</span></span>|<span data-ttu-id="66413-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="66413-118">Data Item Type</span></span>|<span data-ttu-id="66413-119">Popis</span><span class="sxs-lookup"><span data-stu-id="66413-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="66413-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="66413-120">Activity</span></span>|<span data-ttu-id="66413-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="66413-121">xs:string</span></span>|<span data-ttu-id="66413-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="66413-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="66413-123">displayName</span><span class="sxs-lookup"><span data-stu-id="66413-123">DisplayName</span></span>|<span data-ttu-id="66413-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="66413-124">xs:string</span></span>|<span data-ttu-id="66413-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="66413-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="66413-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="66413-126">InstanceId</span></span>|<span data-ttu-id="66413-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="66413-127">xs:string</span></span>|<span data-ttu-id="66413-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="66413-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="66413-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="66413-129">AppDomain</span></span>|<span data-ttu-id="66413-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="66413-130">xs:string</span></span>|<span data-ttu-id="66413-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="66413-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
