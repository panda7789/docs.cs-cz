---
title: "ICLRDataTarget3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64ecb4ca4dfd829bb140c3067085c55a7b86c919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="0a475-102">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a475-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="0a475-103">Podtřídou třídy [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , který poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="0a475-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a475-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0a475-104">Methods</span></span>  
  
|<span data-ttu-id="0a475-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a475-105">Method</span></span>|<span data-ttu-id="0a475-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0a475-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a475-107">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="0a475-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="0a475-108">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="0a475-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="0a475-109">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="0a475-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="0a475-110">Je volána službami modulu CLR pro přístup k datům za účelem získání záznamu o kontextu souvisejícím s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="0a475-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="0a475-111">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="0a475-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="0a475-112">Voláno rozhraním služby CLR data přístup získat ID podprocesu, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="0a475-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a475-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a475-113">Remarks</span></span>  
 <span data-ttu-id="0a475-114">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="0a475-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0a475-115">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="0a475-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="0a475-116">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="0a475-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a475-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a475-117">Requirements</span></span>  
 <span data-ttu-id="0a475-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a475-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a475-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0a475-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0a475-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a475-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a475-121">**Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a475-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a475-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a475-122">See Also</span></span>  
 [<span data-ttu-id="0a475-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a475-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="0a475-124">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a475-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="0a475-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0a475-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
