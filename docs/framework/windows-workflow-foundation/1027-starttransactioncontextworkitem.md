---
title: 1027 – StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008821"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="a4c82-102">1027 – StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="a4c82-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a4c82-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a4c82-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4c82-104">ID</span><span class="sxs-lookup"><span data-stu-id="a4c82-104">ID</span></span>|<span data-ttu-id="a4c82-105">1027</span><span class="sxs-lookup"><span data-stu-id="a4c82-105">1027</span></span>|  
|<span data-ttu-id="a4c82-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a4c82-106">Keywords</span></span>|<span data-ttu-id="a4c82-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a4c82-107">WFRuntime</span></span>|  
|<span data-ttu-id="a4c82-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a4c82-108">Level</span></span>|<span data-ttu-id="a4c82-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a4c82-109">Verbose</span></span>|  
|<span data-ttu-id="a4c82-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a4c82-110">Channel</span></span>|<span data-ttu-id="a4c82-111">Aplikace Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a4c82-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4c82-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a4c82-112">Description</span></span>  
 <span data-ttu-id="a4c82-113">Označuje, že položka TransactionContextWorkItem je spuštění.</span><span class="sxs-lookup"><span data-stu-id="a4c82-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4c82-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a4c82-114">Message</span></span>  
 <span data-ttu-id="a4c82-115">Začátek provádění položky TransactionContextWorkItem pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="a4c82-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4c82-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a4c82-116">Details</span></span>  
  
|<span data-ttu-id="a4c82-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a4c82-117">Data Item Name</span></span>|<span data-ttu-id="a4c82-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="a4c82-118">Data Item Type</span></span>|<span data-ttu-id="a4c82-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a4c82-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4c82-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="a4c82-120">Activity</span></span>|<span data-ttu-id="a4c82-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4c82-121">xs:string</span></span>|<span data-ttu-id="a4c82-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="a4c82-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a4c82-123">displayName</span><span class="sxs-lookup"><span data-stu-id="a4c82-123">DisplayName</span></span>|<span data-ttu-id="a4c82-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4c82-124">xs:string</span></span>|<span data-ttu-id="a4c82-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="a4c82-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a4c82-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a4c82-126">InstanceId</span></span>|<span data-ttu-id="a4c82-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4c82-127">xs:string</span></span>|<span data-ttu-id="a4c82-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="a4c82-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a4c82-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a4c82-129">AppDomain</span></span>|<span data-ttu-id="a4c82-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4c82-130">xs:string</span></span>|<span data-ttu-id="a4c82-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a4c82-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
