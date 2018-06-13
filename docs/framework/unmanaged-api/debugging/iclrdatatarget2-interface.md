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
ms.openlocfilehash: 6fc26694bded2c7df1a53a96e8743f3be73c93eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408501"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="7d65a-102">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d65a-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="7d65a-103">Podtřídou třídy [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) vrstvy služby přístupu k datům jsou používány k manipulaci s oblastí virtuální paměti v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="7d65a-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d65a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7d65a-104">Methods</span></span>  
  
|<span data-ttu-id="7d65a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7d65a-105">Method</span></span>|<span data-ttu-id="7d65a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7d65a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d65a-107">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7d65a-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="7d65a-108">Přidělí paměť v adresním prostoru procesu cíl.</span><span class="sxs-lookup"><span data-stu-id="7d65a-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="7d65a-109">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7d65a-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="7d65a-110">Uvolní paměť, která byla dříve přidělena v adresním prostoru tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="7d65a-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d65a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d65a-111">Remarks</span></span>  
 <span data-ttu-id="7d65a-112">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="7d65a-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="7d65a-113">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="7d65a-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="7d65a-114">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="7d65a-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d65a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d65a-115">Requirements</span></span>  
 <span data-ttu-id="7d65a-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d65a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d65a-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7d65a-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7d65a-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d65a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d65a-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d65a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d65a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d65a-120">See Also</span></span>  
 [<span data-ttu-id="7d65a-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d65a-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="7d65a-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7d65a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
