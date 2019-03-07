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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 802d4987b3be86b5a6302b78f75e4f0c02d49f3e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492033"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="f888d-102">ICorDebugManagedCallback2::ExceptionUnwind – metoda</span><span class="sxs-lookup"><span data-stu-id="f888d-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="f888d-103">Poskytuje stavu oznámení během procesu odvíjení výjimky.</span><span class="sxs-lookup"><span data-stu-id="f888d-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f888d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f888d-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f888d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f888d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f888d-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="f888d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f888d-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="f888d-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="f888d-108">[in] Hodnota cordebugexceptionunwindcallbacktype – výčet, který určuje události, ke které je právě signalizována zpětného volání ve fázi unwind.</span><span class="sxs-lookup"><span data-stu-id="f888d-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f888d-109">[in] Hodnota [cordebugexceptionflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) výčet, který určuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="f888d-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f888d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f888d-110">Remarks</span></span>  
 <span data-ttu-id="f888d-111">`ExceptionUnwind` je volána v různých fázích v průběhu fáze unwind procesu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f888d-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="f888d-112">`ExceptionUnwind` lze volat vícekrát během odvíjení jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="f888d-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="f888d-113">Pokud `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, ukazatele na instrukci bude v rámci typu list vlákna, v okamžiku pořadí před (to může být několik pokyny před) instrukce, která vedla k výjimce.</span><span class="sxs-lookup"><span data-stu-id="f888d-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f888d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f888d-114">Requirements</span></span>  
 <span data-ttu-id="f888d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f888d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f888d-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f888d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f888d-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f888d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f888d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f888d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f888d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f888d-119">See also</span></span>
- [<span data-ttu-id="f888d-120">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f888d-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f888d-121">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f888d-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
