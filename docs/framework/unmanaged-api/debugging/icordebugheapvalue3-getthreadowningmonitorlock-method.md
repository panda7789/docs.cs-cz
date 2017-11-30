---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="26772-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="26772-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="26772-103">Vrátí spravované vlákno, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="26772-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26772-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26772-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26772-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26772-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="26772-106">[out] Spravované vlákno, které vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="26772-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="26772-107">[out] Počet přístupů, se uvolní zámek před vrátí se bez přiřazeného vlastníka tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="26772-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26772-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26772-108">Return Value</span></span>  
 <span data-ttu-id="26772-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="26772-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26772-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26772-110">HRESULT</span></span>|<span data-ttu-id="26772-111">Popis</span><span class="sxs-lookup"><span data-stu-id="26772-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26772-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="26772-112">S_OK</span></span>|<span data-ttu-id="26772-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="26772-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="26772-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="26772-114">S_FALSE</span></span>|<span data-ttu-id="26772-115">Žádné spravované vlákno vlastní monitorování zámek na tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="26772-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="26772-116">Výjimky</span><span class="sxs-lookup"><span data-stu-id="26772-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26772-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26772-117">Remarks</span></span>  
 <span data-ttu-id="26772-118">Pokud spravované vlákno vlastní monitorování zámek na tomto objektu:</span><span class="sxs-lookup"><span data-stu-id="26772-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="26772-119">Metoda vrátí S_OK.</span><span class="sxs-lookup"><span data-stu-id="26772-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="26772-120">Objekt vlákno je platný, až do konce vlákno.</span><span class="sxs-lookup"><span data-stu-id="26772-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="26772-121">Pokud žádné spravované vlákno vlastní monitorování zámek na tomto objektu `ppThread` a `pAcquisitionCount` jsou stejné, a vrátí metoda S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="26772-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="26772-122">Pokud `ppThread` nebo `pAcquisitionCount` není platný ukazatel, výsledkem nedefinovaný.</span><span class="sxs-lookup"><span data-stu-id="26772-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="26772-123">Pokud dojde k chybě tak, že nelze určit, který případná vlastní vlákna sledování zámku na tento objekt metoda vrátí HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="26772-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26772-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26772-124">Requirements</span></span>  
 <span data-ttu-id="26772-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26772-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26772-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26772-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26772-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26772-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26772-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26772-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26772-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="26772-129">See Also</span></span>  
 [<span data-ttu-id="26772-130">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="26772-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="26772-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="26772-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
