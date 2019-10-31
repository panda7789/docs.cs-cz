---
title: ICorDebugHeapValue3::GetMonitorEventWaitList – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: 0fbff178efd4d0dff3593907b3d40e946be2ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121295"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="063ff-102">ICorDebugHeapValue3::GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="063ff-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="063ff-103">Poskytuje uspořádaný seznam vláken, která jsou zařazená do fronty pro událost přidruženou ke zámku monitoru.</span><span class="sxs-lookup"><span data-stu-id="063ff-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="063ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="063ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="063ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="063ff-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="063ff-106">mimo Enumerátor ICorDebugThreadEnum, který poskytuje uspořádaný seznam vláken.</span><span class="sxs-lookup"><span data-stu-id="063ff-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="063ff-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="063ff-107">Return Value</span></span>  
 <span data-ttu-id="063ff-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="063ff-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="063ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="063ff-109">HRESULT</span></span>|<span data-ttu-id="063ff-110">Popis</span><span class="sxs-lookup"><span data-stu-id="063ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="063ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="063ff-111">S_OK</span></span>|<span data-ttu-id="063ff-112">Seznam není prázdný.</span><span class="sxs-lookup"><span data-stu-id="063ff-112">The list is not empty.</span></span>|  
|<span data-ttu-id="063ff-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="063ff-113">S_FALSE</span></span>|<span data-ttu-id="063ff-114">Seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="063ff-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="063ff-115">Výjimky</span><span class="sxs-lookup"><span data-stu-id="063ff-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="063ff-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="063ff-116">Remarks</span></span>  
 <span data-ttu-id="063ff-117">Prvním vláknem v seznamu je první vlákno, které je vydané při příštím volání <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="063ff-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="063ff-118">Další vlákno v seznamu se uvolní při následujícím volání, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="063ff-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="063ff-119">Pokud seznam není prázdný, vrátí tato metoda hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="063ff-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="063ff-120">Pokud je seznam prázdný, vrátí metoda S_FALSE; v tomto případě je výčet stále platný, i když je prázdný.</span><span class="sxs-lookup"><span data-stu-id="063ff-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="063ff-121">V obou případech je rozhraní výčtu použitelné pouze pro dobu trvání aktuálního synchronizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="063ff-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="063ff-122">Nicméně rozhraní vlákna, která jsou z něj, jsou platná až do ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="063ff-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="063ff-123">Pokud `ppThreadEnum` není platný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="063ff-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="063ff-124">Pokud dojde k chybě, kterou nelze určit, který z nich, pokud nějaká existuje, čeká na monitorování, metoda vrátí hodnotu HRESULT, která označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="063ff-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="063ff-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="063ff-125">Requirements</span></span>  
 <span data-ttu-id="063ff-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="063ff-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="063ff-127">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="063ff-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="063ff-128">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="063ff-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="063ff-129">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="063ff-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063ff-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="063ff-130">See also</span></span>

- [<span data-ttu-id="063ff-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="063ff-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="063ff-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="063ff-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
