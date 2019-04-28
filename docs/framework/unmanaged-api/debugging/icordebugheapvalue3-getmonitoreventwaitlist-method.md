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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db331d75244d59aacf2207a6b83a3f337a64b989
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700967"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="478c1-102">ICorDebugHeapValue3::GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="478c1-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="478c1-103">Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí se zámkem monitorování.</span><span class="sxs-lookup"><span data-stu-id="478c1-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="478c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="478c1-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="478c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="478c1-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="478c1-106">[out] Icordebugthreadenum – enumerátor, který poskytuje seřazený seznam vláken.</span><span class="sxs-lookup"><span data-stu-id="478c1-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="478c1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="478c1-107">Return Value</span></span>  
 <span data-ttu-id="478c1-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="478c1-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="478c1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="478c1-109">HRESULT</span></span>|<span data-ttu-id="478c1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="478c1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="478c1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="478c1-111">S_OK</span></span>|<span data-ttu-id="478c1-112">Seznam není prázdný.</span><span class="sxs-lookup"><span data-stu-id="478c1-112">The list is not empty.</span></span>|  
|<span data-ttu-id="478c1-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="478c1-113">S_FALSE</span></span>|<span data-ttu-id="478c1-114">Seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="478c1-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="478c1-115">Výjimky</span><span class="sxs-lookup"><span data-stu-id="478c1-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="478c1-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="478c1-116">Remarks</span></span>  
 <span data-ttu-id="478c1-117">První vlákno v seznamu je první vlákno, které se vydal další volání <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="478c1-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="478c1-118">Další vlákno v seznamu je vydána následující volání a tak dále.</span><span class="sxs-lookup"><span data-stu-id="478c1-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="478c1-119">Pokud seznam není prázdný, tato metoda vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="478c1-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="478c1-120">Pokud je seznam prázdný, vrátí metoda S_FALSE; v tomto případě je stále platné, výčtu, i když je prázdný.</span><span class="sxs-lookup"><span data-stu-id="478c1-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="478c1-121">V obou případech rozhraní výčtu je použitelné pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="478c1-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="478c1-122">Však rozhraní vlákna distribuován z něj platí až do ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="478c1-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="478c1-123">Pokud `ppThreadEnum` není platný ukazatel, výsledek nedefinován.</span><span class="sxs-lookup"><span data-stu-id="478c1-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="478c1-124">Pokud dojde k chybě, takže ji nelze určit, které případně vlákna čekají na monitorování, metoda vrátí HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="478c1-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="478c1-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="478c1-125">Requirements</span></span>  
 <span data-ttu-id="478c1-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="478c1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="478c1-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="478c1-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="478c1-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="478c1-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="478c1-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="478c1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="478c1-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="478c1-130">See also</span></span>

- [<span data-ttu-id="478c1-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="478c1-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="478c1-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="478c1-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
