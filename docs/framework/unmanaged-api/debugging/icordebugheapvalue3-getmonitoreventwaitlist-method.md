---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="81e9d-102">ICorDebugHeapValue3::GetMonitorEventWaitList – metoda</span><span class="sxs-lookup"><span data-stu-id="81e9d-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="81e9d-103">Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí s monitorování zámku.</span><span class="sxs-lookup"><span data-stu-id="81e9d-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81e9d-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81e9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81e9d-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="81e9d-106">[out] ICorDebugThreadEnum enumerátor, který poskytuje seřazený seznam vláken.</span><span class="sxs-lookup"><span data-stu-id="81e9d-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81e9d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="81e9d-107">Return Value</span></span>  
 <span data-ttu-id="81e9d-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="81e9d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="81e9d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81e9d-109">HRESULT</span></span>|<span data-ttu-id="81e9d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="81e9d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81e9d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="81e9d-111">S_OK</span></span>|<span data-ttu-id="81e9d-112">V seznamu není prázdná.</span><span class="sxs-lookup"><span data-stu-id="81e9d-112">The list is not empty.</span></span>|  
|<span data-ttu-id="81e9d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="81e9d-113">S_FALSE</span></span>|<span data-ttu-id="81e9d-114">Seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="81e9d-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="81e9d-115">Výjimky</span><span class="sxs-lookup"><span data-stu-id="81e9d-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81e9d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81e9d-116">Remarks</span></span>  
 <span data-ttu-id="81e9d-117">První vlákno v seznamu se první vlákno, které je publikována v rámci další volání <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81e9d-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81e9d-118">Další vlákno v seznamu je vydala následující volání a tak dále.</span><span class="sxs-lookup"><span data-stu-id="81e9d-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="81e9d-119">Pokud v seznamu není prázdný, vrátí tato metoda S_OK.</span><span class="sxs-lookup"><span data-stu-id="81e9d-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="81e9d-120">Pokud je seznam prázdný, vrátí metoda S_FALSE; v takovém případě je stále platný, výčtu, i když je prázdný.</span><span class="sxs-lookup"><span data-stu-id="81e9d-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="81e9d-121">V obou případech je rozhraní výčtu použitelné pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="81e9d-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="81e9d-122">Vlákna rozhraní distribuován z něj jsou však platný až do konce vlákno.</span><span class="sxs-lookup"><span data-stu-id="81e9d-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="81e9d-123">Pokud `ppThreadEnum` není platný ukazatel, výsledkem nedefinovaný.</span><span class="sxs-lookup"><span data-stu-id="81e9d-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="81e9d-124">Pokud dojde k chybě tak, že nelze určit, která, pokud existuje, vláken, které čekají na monitorování, vrátí metoda HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="81e9d-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e9d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81e9d-125">Requirements</span></span>  
 <span data-ttu-id="81e9d-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e9d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e9d-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81e9d-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81e9d-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81e9d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81e9d-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e9d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e9d-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="81e9d-130">See Also</span></span>  
 [<span data-ttu-id="81e9d-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="81e9d-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="81e9d-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="81e9d-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
