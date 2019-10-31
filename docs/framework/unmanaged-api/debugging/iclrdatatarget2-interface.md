---
title: ICLRDataTarget2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 1f0f4331302e56a90b4aefd657e07981994022ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112316"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="cb228-102">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb228-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="cb228-103">Podtřída [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) , která je používána vrstvou služeb přístupu k datům k manipulaci s oblastmi virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="cb228-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb228-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cb228-104">Methods</span></span>  
  
|<span data-ttu-id="cb228-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb228-105">Method</span></span>|<span data-ttu-id="cb228-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cb228-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb228-107">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="cb228-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="cb228-108">Přidělí paměť v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="cb228-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="cb228-109">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="cb228-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="cb228-110">Uvolní paměť, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="cb228-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb228-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb228-111">Remarks</span></span>  
 <span data-ttu-id="cb228-112">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="cb228-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="cb228-113">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="cb228-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="cb228-114">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="cb228-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb228-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb228-115">Requirements</span></span>  
 <span data-ttu-id="cb228-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb228-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb228-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cb228-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cb228-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cb228-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb228-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb228-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb228-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb228-120">See also</span></span>

- [<span data-ttu-id="cb228-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb228-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="cb228-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cb228-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
