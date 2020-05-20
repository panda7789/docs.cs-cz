---
title: ICLROnEventManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703515"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="ff21e-102">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff21e-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="ff21e-103">Poskytuje metody, které umožňují hostiteli registrovat a odregistrovat zpětná volání pro události modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ff21e-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff21e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ff21e-104">Methods</span></span>  
  
|<span data-ttu-id="ff21e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ff21e-105">Method</span></span>|<span data-ttu-id="ff21e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ff21e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff21e-107">RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ff21e-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="ff21e-108">Zaregistruje ukazatel zpětného volání pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="ff21e-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="ff21e-109">UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ff21e-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="ff21e-110">Zruší registraci dříve registrovaného ukazatele zpětného volání pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="ff21e-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff21e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff21e-111">Remarks</span></span>  
 <span data-ttu-id="ff21e-112">Pro registraci a zrušení registrace zpětných volání událostí hostitel získá odkaz na `ICLROnEventManager` volání metody [ICLRControl:: GetCLRManager –](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ff21e-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff21e-113">Události popsané v [EClrEvent –](eclrevent-enumeration.md) lze aktivovat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.</span><span class="sxs-lookup"><span data-stu-id="ff21e-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff21e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff21e-114">Requirements</span></span>  
 <span data-ttu-id="ff21e-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff21e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff21e-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff21e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff21e-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ff21e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff21e-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff21e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff21e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff21e-119">See also</span></span>

- [<span data-ttu-id="ff21e-120">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="ff21e-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="ff21e-121">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff21e-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="ff21e-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff21e-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ff21e-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ff21e-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
