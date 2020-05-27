---
title: IHostAutoEvent – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: a24939ac0b0808546ef3615fae4909c6c3cf8a2e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804996"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="26d53-102">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26d53-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="26d53-103">Poskytuje reprezentaci implementace události automatického resetování hostitele.</span><span class="sxs-lookup"><span data-stu-id="26d53-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26d53-104">Metody</span><span class="sxs-lookup"><span data-stu-id="26d53-104">Methods</span></span>  
  
|<span data-ttu-id="26d53-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="26d53-105">Method</span></span>|<span data-ttu-id="26d53-106">Popis</span><span class="sxs-lookup"><span data-stu-id="26d53-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26d53-107">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="26d53-107">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="26d53-108">Nastaví aktuální `IHostAutoEvent` instanci na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="26d53-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="26d53-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="26d53-109">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="26d53-110">Způsobí, že aktuální `IHostAutoEvent` instance počká, dokud událost nevlastníte nebo dokud neuplyne zadaný čas.</span><span class="sxs-lookup"><span data-stu-id="26d53-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26d53-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26d53-111">Requirements</span></span>  
 <span data-ttu-id="26d53-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d53-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d53-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26d53-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26d53-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26d53-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26d53-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d53-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d53-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="26d53-116">See also</span></span>

- [<span data-ttu-id="26d53-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26d53-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="26d53-118">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26d53-118">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="26d53-119">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26d53-119">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="26d53-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="26d53-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
