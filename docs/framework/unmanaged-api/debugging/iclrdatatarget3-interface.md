---
title: ICLRDataTarget3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74e106e17c0f0e5702927c4599fb143fb3554ce3
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065944"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="d7f79-102">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7f79-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="d7f79-103">Podtřída [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="d7f79-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7f79-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d7f79-104">Methods</span></span>  
  
|<span data-ttu-id="d7f79-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d7f79-105">Method</span></span>|<span data-ttu-id="d7f79-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d7f79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7f79-107">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="d7f79-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="d7f79-108">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="d7f79-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="d7f79-109">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="d7f79-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="d7f79-110">Je volána službami modulu CLR pro přístup k datům za účelem získání záznamu o kontextu souvisejícím s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="d7f79-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="d7f79-111">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="d7f79-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="d7f79-112">Je voláno CLR data access services k získání ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="d7f79-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7f79-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7f79-113">Remarks</span></span>  
 <span data-ttu-id="d7f79-114">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="d7f79-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="d7f79-115">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="d7f79-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="d7f79-116">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="d7f79-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7f79-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7f79-117">Requirements</span></span>  
 <span data-ttu-id="d7f79-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7f79-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7f79-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d7f79-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d7f79-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7f79-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7f79-121">**Verze rozhraní .NET framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d7f79-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f79-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7f79-122">See also</span></span>
- [<span data-ttu-id="d7f79-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7f79-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="d7f79-124">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7f79-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="d7f79-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d7f79-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
