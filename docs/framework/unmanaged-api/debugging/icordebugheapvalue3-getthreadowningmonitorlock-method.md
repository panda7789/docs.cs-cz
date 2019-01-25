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
ms.openlocfilehash: 8d3e10a3dbae0d1b790c0d80c9286affedaa4c8b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709140"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="96db3-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="96db3-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="96db3-103">Vrátí spravované vlákno, který vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="96db3-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96db3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96db3-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96db3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96db3-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="96db3-106">[out] Spravovaná vlákna, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="96db3-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="96db3-107">[out] Počet pokusů, museli byste toto vlákno uvolní zámek před vrácením se bez přiřazeného vlastníka.</span><span class="sxs-lookup"><span data-stu-id="96db3-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96db3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96db3-108">Return Value</span></span>  
 <span data-ttu-id="96db3-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="96db3-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="96db3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96db3-110">HRESULT</span></span>|<span data-ttu-id="96db3-111">Popis</span><span class="sxs-lookup"><span data-stu-id="96db3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96db3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="96db3-112">S_OK</span></span>|<span data-ttu-id="96db3-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="96db3-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="96db3-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="96db3-114">S_FALSE</span></span>|<span data-ttu-id="96db3-115">Žádné spravované vlákno vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="96db3-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="96db3-116">Výjimky</span><span class="sxs-lookup"><span data-stu-id="96db3-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96db3-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96db3-117">Remarks</span></span>  
 <span data-ttu-id="96db3-118">Pokud spravované vlákno vlastní monitorování zámek na tomto objektu:</span><span class="sxs-lookup"><span data-stu-id="96db3-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="96db3-119">Metoda vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="96db3-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="96db3-120">Objekt vlákna je platná, dokud se vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="96db3-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="96db3-121">Pokud žádné spravované vlákno vlastní monitorování zámek na tomto objektu `ppThread` a `pAcquisitionCount` jsou beze změny, a metoda vrátí S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="96db3-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="96db3-122">Pokud `ppThread` nebo `pAcquisitionCount` není platný ukazatel, výsledek nedefinován.</span><span class="sxs-lookup"><span data-stu-id="96db3-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="96db3-123">Pokud dojde k chybě, takže ji nelze určit, který, pokud existuje, vlákno vlastní monitorování zámek na tomto objektu, metoda vrátí HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="96db3-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96db3-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96db3-124">Requirements</span></span>  
 <span data-ttu-id="96db3-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96db3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96db3-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96db3-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96db3-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96db3-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96db3-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96db3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96db3-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96db3-129">See also</span></span>
- [<span data-ttu-id="96db3-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="96db3-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="96db3-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="96db3-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
