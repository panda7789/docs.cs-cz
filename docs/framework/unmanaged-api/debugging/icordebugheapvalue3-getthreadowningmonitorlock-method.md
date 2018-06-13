---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ba09991e9452a86c6b7a1cbb08a38a71ba2aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416761"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="b9142-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="b9142-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="b9142-103">Vrátí spravované vlákno, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="b9142-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9142-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9142-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9142-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9142-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="b9142-106">[out] Spravované vlákno, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="b9142-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="b9142-107">[out] Počet přístupů, se uvolní zámek před vrátí se bez přiřazeného vlastníka tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="b9142-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9142-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9142-108">Return Value</span></span>  
 <span data-ttu-id="b9142-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b9142-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b9142-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9142-110">HRESULT</span></span>|<span data-ttu-id="b9142-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b9142-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9142-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9142-112">S_OK</span></span>|<span data-ttu-id="b9142-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b9142-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b9142-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b9142-114">S_FALSE</span></span>|<span data-ttu-id="b9142-115">Žádné spravované vlákno vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="b9142-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b9142-116">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b9142-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9142-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9142-117">Remarks</span></span>  
 <span data-ttu-id="b9142-118">Pokud spravované vlákno vlastní monitorování zámek na tomto objektu:</span><span class="sxs-lookup"><span data-stu-id="b9142-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="b9142-119">Metoda vrátí S_OK.</span><span class="sxs-lookup"><span data-stu-id="b9142-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="b9142-120">Objekt vlákno je platný, až do konce vlákno.</span><span class="sxs-lookup"><span data-stu-id="b9142-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="b9142-121">Pokud žádné spravované vlákno vlastní monitorování zámek na tomto objektu `ppThread` a `pAcquisitionCount` jsou stejné, a vrátí metoda S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="b9142-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="b9142-122">Pokud `ppThread` nebo `pAcquisitionCount` není platný ukazatel, výsledkem nedefinovaný.</span><span class="sxs-lookup"><span data-stu-id="b9142-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="b9142-123">Pokud dojde k chybě tak, že nelze určit, který případná vlastní vlákna sledování zámku na tento objekt metoda vrátí HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="b9142-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9142-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9142-124">Requirements</span></span>  
 <span data-ttu-id="b9142-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9142-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9142-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9142-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9142-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9142-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9142-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9142-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9142-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9142-129">See Also</span></span>  
 [<span data-ttu-id="b9142-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b9142-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b9142-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="b9142-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
