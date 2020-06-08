---
title: IActionOnCLREvent – rozhraní
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: f577e9252d97ec188ff1076fd8340336b16c8257
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504326"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="bd5e2-102">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd5e2-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="bd5e2-103">Poskytuje metodu [IActionOnCLREvent –::](iactiononclrevent-onevent-method.md) ICLROnEventManager, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání metody [:: RegisterActionOnEvent –](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bd5e2-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd5e2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd5e2-104">Methods</span></span>  
  
|<span data-ttu-id="bd5e2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd5e2-105">Method</span></span>|<span data-ttu-id="bd5e2-106">Description</span><span class="sxs-lookup"><span data-stu-id="bd5e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd5e2-107">OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="bd5e2-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="bd5e2-108">Provede zpětné volání pro registrovanou událost.</span><span class="sxs-lookup"><span data-stu-id="bd5e2-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd5e2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd5e2-109">Requirements</span></span>  
 <span data-ttu-id="bd5e2-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd5e2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd5e2-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bd5e2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd5e2-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bd5e2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd5e2-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd5e2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5e2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd5e2-114">See also</span></span>

- [<span data-ttu-id="bd5e2-115">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="bd5e2-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="bd5e2-116">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd5e2-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="bd5e2-117">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd5e2-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="bd5e2-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="bd5e2-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
