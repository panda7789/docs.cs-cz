---
title: "ICorDebugManagedCallback2::ExceptionUnwind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64b85311f625e39dd25c48a60dde2fbaf66a957f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="f293f-102">ICorDebugManagedCallback2::ExceptionUnwind – metoda</span><span class="sxs-lookup"><span data-stu-id="f293f-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="f293f-103">Poskytuje oznámení o stavu během procesu unwinding výjimka.</span><span class="sxs-lookup"><span data-stu-id="f293f-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f293f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f293f-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f293f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f293f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f293f-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující vláken, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="f293f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f293f-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="f293f-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="f293f-108">[v] Hodnota CorDebugExceptionUnwindCallbackType – výčet, který určuje událost, která se během fáze unwind signalizace podle zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="f293f-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f293f-109">[v] Hodnota [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) výčet, který určuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="f293f-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f293f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f293f-110">Remarks</span></span>  
 <span data-ttu-id="f293f-111">`ExceptionUnwind`je volána v různých fázích během fáze unwind proces zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f293f-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="f293f-112">`ExceptionUnwind`je možné volat vícekrát při unwinding jeden výjimka.</span><span class="sxs-lookup"><span data-stu-id="f293f-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="f293f-113">Pokud `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, ukazatelem na instrukce bude v listu rámečku vlákna v bodě pořadí před (to může být několik pokyny před) pokyn, se vyvolala výjimka.</span><span class="sxs-lookup"><span data-stu-id="f293f-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f293f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f293f-114">Requirements</span></span>  
 <span data-ttu-id="f293f-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f293f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f293f-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f293f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f293f-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f293f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f293f-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f293f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f293f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f293f-119">See Also</span></span>  
 [<span data-ttu-id="f293f-120">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f293f-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="f293f-121">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f293f-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
