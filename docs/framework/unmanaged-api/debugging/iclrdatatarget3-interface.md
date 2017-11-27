---
title: "ICLRDataTarget3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16e2d2aa1a2626f4124e1b43ff85abcdd17f6990
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="09051-102">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09051-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="09051-103">Podtřídou třídy [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , který poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="09051-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09051-104">Metody</span><span class="sxs-lookup"><span data-stu-id="09051-104">Methods</span></span>  
  
|<span data-ttu-id="09051-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="09051-105">Method</span></span>|<span data-ttu-id="09051-106">Popis</span><span class="sxs-lookup"><span data-stu-id="09051-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09051-107">Getexceptionrecord – metoda</span><span class="sxs-lookup"><span data-stu-id="09051-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="09051-108">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="09051-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="09051-109">Metoda GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="09051-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="09051-110">Je volána službami modulu CLR pro přístup k datům za účelem získání záznamu o kontextu souvisejícím s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="09051-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="09051-111">Metoda GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="09051-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="09051-112">Voláno rozhraním služby CLR data přístup získat ID podprocesu, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="09051-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09051-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09051-113">Remarks</span></span>  
 <span data-ttu-id="09051-114">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="09051-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="09051-115">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="09051-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="09051-116">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="09051-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09051-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09051-117">Requirements</span></span>  
 <span data-ttu-id="09051-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09051-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09051-119">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="09051-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="09051-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09051-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09051-121">**Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09051-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09051-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="09051-122">See Also</span></span>  
 [<span data-ttu-id="09051-123">ICLRDataTarget – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="09051-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="09051-124">Iclrdatatarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09051-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="09051-125">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="09051-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
