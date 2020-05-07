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
ms.openlocfilehash: 30806394a8895084068acaec6f7d03c6b67bb14b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860562"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="c7c21-102">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7c21-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="c7c21-103">Poskytuje metody pro interakci s cílovou položkou modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c7c21-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7c21-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7c21-104">Methods</span></span>  
  
|<span data-ttu-id="c7c21-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-105">Method</span></span>|<span data-ttu-id="c7c21-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c7c21-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7c21-107">GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="c7c21-108">Načte identifikátor operačního systému pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="c7c21-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="c7c21-109">GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="c7c21-110">Načte základní adresu paměti pro zadanou bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="c7c21-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="c7c21-111">GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="c7c21-112">Získá identifikátor pro druh sady instrukcí, které cílový proces používá.</span><span class="sxs-lookup"><span data-stu-id="c7c21-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="c7c21-113">GetPointerSize – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="c7c21-114">Získá velikost ukazatele na aktuální cíl v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c7c21-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="c7c21-115">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="c7c21-116">Získá ukazatel na kontext vlákna se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="c7c21-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="c7c21-117">GetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="c7c21-118">Získá hodnotu v thread local Storage (TLS) v zadaném indexu pro zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="c7c21-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="c7c21-119">ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="c7c21-120">Načte data ze zadané adresy virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c7c21-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="c7c21-121">Request – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="c7c21-122">Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.</span><span class="sxs-lookup"><span data-stu-id="c7c21-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="c7c21-123">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="c7c21-124">Nastaví aktuální kontext zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="c7c21-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="c7c21-125">SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="c7c21-126">Nastaví hodnotu v thread local Storage (TLS) zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="c7c21-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="c7c21-127">WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c7c21-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="c7c21-128">Zapisuje data ze zadané vyrovnávací paměti do zadané adresy virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="c7c21-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7c21-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7c21-129">Remarks</span></span>  
 <span data-ttu-id="c7c21-130">Klient rozhraní API (to znamená ladicí program) musí implementovat toto rozhraní, jak je to vhodné pro konkrétní cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="c7c21-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="c7c21-131">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="c7c21-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7c21-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7c21-132">Requirements</span></span>  
 <span data-ttu-id="c7c21-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7c21-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7c21-134">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c7c21-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c7c21-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c7c21-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7c21-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7c21-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c21-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7c21-137">See also</span></span>

- [<span data-ttu-id="c7c21-138">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7c21-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="c7c21-139">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7c21-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
