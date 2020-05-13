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
ms.openlocfilehash: 9cc68e39dfef096b8ab6a8ba743f7a516cc349be
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210407"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="dc3a2-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda</span><span class="sxs-lookup"><span data-stu-id="dc3a2-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="dc3a2-103">Vrátí spravované vlákno, které vlastní zámek monitorování tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc3a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc3a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc3a2-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="dc3a2-106">mimo Spravované vlákno, které pro tento objekt vlastní zámek monitoru.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="dc3a2-107">mimo Počet, kolikrát by toto vlákno muselo uvolnit zámek předtím, než se vrátí k nevlastnictví.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc3a2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc3a2-108">Return Value</span></span>  
 <span data-ttu-id="dc3a2-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dc3a2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc3a2-110">HRESULT</span></span>|<span data-ttu-id="dc3a2-111">Popis</span><span class="sxs-lookup"><span data-stu-id="dc3a2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc3a2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc3a2-112">S_OK</span></span>|<span data-ttu-id="dc3a2-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="dc3a2-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dc3a2-114">S_FALSE</span></span>|<span data-ttu-id="dc3a2-115">Žádné spravované vlákno nevlastní na tomto objektu zámek monitorování.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dc3a2-116">Výjimky</span><span class="sxs-lookup"><span data-stu-id="dc3a2-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc3a2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc3a2-117">Remarks</span></span>  
 <span data-ttu-id="dc3a2-118">Pokud spravované vlákno vlastní zámek monitoru u tohoto objektu:</span><span class="sxs-lookup"><span data-stu-id="dc3a2-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="dc3a2-119">Metoda vrací S_OK.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="dc3a2-120">Objekt vlákna je platný, dokud vlákno neskončí.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="dc3a2-121">Pokud žádné spravované vlákno nevlastní na tomto objektu zámek monitoru `ppThread` a `pAcquisitionCount` jsou beze změny a metoda vrátí S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="dc3a2-122">Pokud `ppThread` nebo není `pAcquisitionCount` platný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="dc3a2-123">Pokud dojde k chybě, kterou nelze určit, která, pokud existuje, je vláknom zámku monitoru pro tento objekt, metoda vrátí hodnotu HRESULT, která označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="dc3a2-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc3a2-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc3a2-124">Requirements</span></span>  
 <span data-ttu-id="dc3a2-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc3a2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc3a2-126">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc3a2-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc3a2-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dc3a2-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc3a2-128">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc3a2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc3a2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc3a2-129">See also</span></span>

- [<span data-ttu-id="dc3a2-130">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc3a2-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dc3a2-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="dc3a2-131">Debugging</span></span>](index.md)
