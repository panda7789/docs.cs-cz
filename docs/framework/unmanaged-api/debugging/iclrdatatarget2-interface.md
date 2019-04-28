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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21bced214242866c47f40f392593f3f51cda02f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697937"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="3455b-102">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3455b-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="3455b-103">Podtřída [iclrdatatarget –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) vrstvou služeb přístupu k data, která se používá k manipulaci s oblastmi virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="3455b-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3455b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3455b-104">Methods</span></span>  
  
|<span data-ttu-id="3455b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3455b-105">Method</span></span>|<span data-ttu-id="3455b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3455b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3455b-107">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="3455b-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="3455b-108">Přidělí paměť v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="3455b-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="3455b-109">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="3455b-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="3455b-110">Uvolnění paměti, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="3455b-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3455b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3455b-111">Remarks</span></span>  
 <span data-ttu-id="3455b-112">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="3455b-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="3455b-113">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="3455b-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="3455b-114">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="3455b-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3455b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3455b-115">Requirements</span></span>  
 <span data-ttu-id="3455b-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3455b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3455b-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3455b-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3455b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3455b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3455b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3455b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3455b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3455b-120">See also</span></span>

- [<span data-ttu-id="3455b-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3455b-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="3455b-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3455b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
