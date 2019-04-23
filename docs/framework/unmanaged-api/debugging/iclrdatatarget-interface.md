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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100246"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="93601-102">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93601-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="93601-103">Poskytuje metody pro interakci s cílová položka modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="93601-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93601-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93601-104">Methods</span></span>  
  
|<span data-ttu-id="93601-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93601-105">Method</span></span>|<span data-ttu-id="93601-106">Popis</span><span class="sxs-lookup"><span data-stu-id="93601-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93601-107">GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="93601-108">Získá identifikátor operačního systému pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="93601-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="93601-109">GetImageBase – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="93601-110">Získá adresu základní paměti pro zadané bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="93601-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="93601-111">GetMachineType – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="93601-112">Získá identifikátor pro typ instrukční sadu, která používá cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="93601-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="93601-113">GetPointerSize – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="93601-114">Získá velikost v bajtech, ukazatele na aktuálním cíli.</span><span class="sxs-lookup"><span data-stu-id="93601-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="93601-115">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="93601-116">Získá ukazatel na kontext vlákna se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="93601-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="93601-117">GetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="93601-118">Získá hodnotu, v místním úložišti vláken (TLS) v zadaném indexu pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="93601-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="93601-119">ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="93601-120">Načte data z adresy zadaná virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="93601-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="93601-121">Request – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="93601-122">Voláno rozhraním common language runtime (CLR) data access services požádat o operaci, jak je definováno implementací.</span><span class="sxs-lookup"><span data-stu-id="93601-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="93601-123">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="93601-124">Nastaví aktuální kontext ze zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="93601-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="93601-125">SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="93601-126">Nastaví hodnotu v místním úložišti vláken (TLS) ze zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="93601-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="93601-127">WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="93601-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="93601-128">Zapisuje data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="93601-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93601-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93601-129">Remarks</span></span>  
 <span data-ttu-id="93601-130">Klient API (ladicí program) musí implementovat toto rozhraní podle potřeby pro konkrétní cílovou položku.</span><span class="sxs-lookup"><span data-stu-id="93601-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="93601-131">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="93601-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93601-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93601-132">Requirements</span></span>  
 <span data-ttu-id="93601-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93601-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93601-134">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="93601-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="93601-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93601-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93601-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93601-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93601-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93601-137">See also</span></span>

- [<span data-ttu-id="93601-138">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93601-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="93601-139">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="93601-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
