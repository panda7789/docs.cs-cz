---
title: ICLRDataTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113492"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="7ddce-102">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ddce-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="7ddce-103">Poskytuje metody pro interakci s cílovou položkou modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="7ddce-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ddce-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ddce-104">Methods</span></span>  
  
|<span data-ttu-id="7ddce-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-105">Method</span></span>|<span data-ttu-id="7ddce-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7ddce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ddce-107">GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="7ddce-108">Načte identifikátor operačního systému pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="7ddce-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="7ddce-109">GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="7ddce-110">Načte základní adresu paměti pro zadanou bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="7ddce-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="7ddce-111">GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="7ddce-112">Získá identifikátor pro druh sady instrukcí, které cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="7ddce-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="7ddce-113">GetPointerSize – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="7ddce-114">Získá velikost ukazatele na aktuální cíl v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7ddce-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="7ddce-115">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="7ddce-116">Získá ukazatel na kontext vlákna se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="7ddce-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="7ddce-117">GetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="7ddce-118">Získá hodnotu v thread local Storage (TLS) v zadaném indexu pro zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="7ddce-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="7ddce-119">ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="7ddce-120">Načte data ze zadané adresy virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7ddce-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="7ddce-121">Request – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="7ddce-122">Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.</span><span class="sxs-lookup"><span data-stu-id="7ddce-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="7ddce-123">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="7ddce-124">Nastaví aktuální kontext zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="7ddce-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="7ddce-125">SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="7ddce-126">Nastaví hodnotu v thread local Storage (TLS) zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="7ddce-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="7ddce-127">WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7ddce-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="7ddce-128">Zapisuje data ze zadané vyrovnávací paměti do zadané adresy virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="7ddce-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ddce-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ddce-129">Remarks</span></span>  
 <span data-ttu-id="7ddce-130">Klient rozhraní API (to znamená ladicí program) musí implementovat toto rozhraní, jak je to vhodné pro konkrétní cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="7ddce-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="7ddce-131">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="7ddce-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ddce-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ddce-132">Requirements</span></span>  
 <span data-ttu-id="7ddce-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ddce-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ddce-134">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7ddce-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7ddce-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7ddce-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ddce-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ddce-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddce-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ddce-137">See also</span></span>

- [<span data-ttu-id="7ddce-138">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ddce-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="7ddce-139">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7ddce-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
