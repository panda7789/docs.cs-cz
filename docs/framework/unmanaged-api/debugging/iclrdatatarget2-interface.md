---
title: "ICLRDataTarget2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2
helpviewer_keywords: ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1780df0a4659d232a27faf4fdc2f6c9b13db98a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="c864e-102">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c864e-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="c864e-103">Podtřídou třídy [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) vrstvy služby přístupu k datům jsou používány k manipulaci s oblastí virtuální paměti v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="c864e-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c864e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c864e-104">Methods</span></span>  
  
|<span data-ttu-id="c864e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c864e-105">Method</span></span>|<span data-ttu-id="c864e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c864e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c864e-107">Allocvirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c864e-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="c864e-108">Přidělí paměť v adresním prostoru procesu cíl.</span><span class="sxs-lookup"><span data-stu-id="c864e-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="c864e-109">Freevirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c864e-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="c864e-110">Uvolní paměť, která byla dříve přidělena v adresním prostoru tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="c864e-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c864e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c864e-111">Remarks</span></span>  
 <span data-ttu-id="c864e-112">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="c864e-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="c864e-113">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="c864e-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="c864e-114">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="c864e-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c864e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c864e-115">Requirements</span></span>  
 <span data-ttu-id="c864e-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c864e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c864e-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c864e-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c864e-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c864e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c864e-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c864e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c864e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c864e-120">See Also</span></span>  
 [<span data-ttu-id="c864e-121">ICLRDataTarget – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="c864e-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="c864e-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="c864e-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
