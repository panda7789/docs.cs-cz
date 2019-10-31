---
title: ICorDebugManagedCallback2::ExceptionUnwind – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: fa317e1217ac0a9ca46bfeb312446534b1fca63a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131567"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="d5e4e-102">ICorDebugManagedCallback2::ExceptionUnwind – metoda</span><span class="sxs-lookup"><span data-stu-id="d5e4e-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="d5e4e-103">Poskytuje oznámení o stavu během procesu odvíjení výjimky.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5e4e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5e4e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d5e4e-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vyvolána.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d5e4e-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, na kterém byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="d5e4e-108">pro Hodnota výčtu CorDebugExceptionUnwindCallbackType –, která určuje událost, která je signálem zpětného volání během fáze unwind.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d5e4e-109">pro Hodnota výčtu [CorDebugExceptionFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , která určuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5e4e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5e4e-110">Remarks</span></span>  
 <span data-ttu-id="d5e4e-111">`ExceptionUnwind` je volána v různých bodech během fáze unwind v procesu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="d5e4e-112">`ExceptionUnwind` lze volat více než jednou při odvíjení jedné výjimky.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="d5e4e-113">Pokud `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, bude ukazatel na instrukci v rámci koncového bodu vlákna před (to může být několik pokynů před) instrukcí, která vedla k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d5e4e-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e4e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5e4e-114">Requirements</span></span>  
 <span data-ttu-id="d5e4e-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e4e-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5e4e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5e4e-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d5e4e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e4e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e4e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e4e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5e4e-119">See also</span></span>

- [<span data-ttu-id="d5e4e-120">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5e4e-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d5e4e-121">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5e4e-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
