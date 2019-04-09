---
title: ICorDebugManagedCallback2::Exception – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8952b34781045089945e7e72e179e88300b5fdd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103347"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="d5e76-102">ICorDebugManagedCallback2::Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="d5e76-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="d5e76-103">Upozorní ladicího programu, že bylo zahájeno hledání pro obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="d5e76-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5e76-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5e76-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d5e76-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="d5e76-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d5e76-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="d5e76-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="d5e76-108">[in] Ukazatel na objekt ICorDebugFrame, který představuje rámec, počítáno od `dwEventType` parametru.</span><span class="sxs-lookup"><span data-stu-id="d5e76-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="d5e76-109">Další informace najdete v tabulce v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="d5e76-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="d5e76-110">[in] Celé číslo, které určuje prodlevu, počítáno od `dwEventType` parametru.</span><span class="sxs-lookup"><span data-stu-id="d5e76-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="d5e76-111">Další informace najdete v tabulce v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="d5e76-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="d5e76-112">[in] Hodnota cordebugexceptioncallbacktype – výčet, který určuje typ této výjimky zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d5e76-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d5e76-113">[in] Hodnota [cordebugexceptionflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) výčet, který určuje další informace o výjimce</span><span class="sxs-lookup"><span data-stu-id="d5e76-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5e76-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5e76-114">Remarks</span></span>  
 <span data-ttu-id="d5e76-115">`Exception` Zpětného volání je volána v různých fázích v průběhu fáze hledání procesu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="d5e76-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="d5e76-116">To znamená ho může být volána více než jednou při uvolnění výjimku.</span><span class="sxs-lookup"><span data-stu-id="d5e76-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="d5e76-117">Zpracovává výjimky můžete získat z objekt ICorDebugThread, na který odkazuje `pThread` parametru.</span><span class="sxs-lookup"><span data-stu-id="d5e76-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="d5e76-118">Konkrétní rámce a posun jsou určeny `dwEventType` parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d5e76-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="d5e76-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d5e76-119">Value of</span></span> `dwEventType`|<span data-ttu-id="d5e76-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d5e76-120">Value of</span></span> `pFrame`|<span data-ttu-id="d5e76-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d5e76-121">Value of</span></span> `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="d5e76-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d5e76-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="d5e76-123">Rámce, který vyvolal výjimku.</span><span class="sxs-lookup"><span data-stu-id="d5e76-123">The frame that threw the exception.</span></span>|<span data-ttu-id="d5e76-124">Ukazatele na instrukci v rámci.</span><span class="sxs-lookup"><span data-stu-id="d5e76-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="d5e76-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d5e76-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="d5e76-126">Snímek uživatelského kódu co nejblíž koncovým bodem vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="d5e76-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="d5e76-127">Ukazatele na instrukci v rámci.</span><span class="sxs-lookup"><span data-stu-id="d5e76-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="d5e76-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="d5e76-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="d5e76-129">Rámce, který obsahuje obslužné rutiny catch.</span><span class="sxs-lookup"><span data-stu-id="d5e76-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="d5e76-130">Posun Microsoft intermediate language (MSIL) od obslužné rutiny catch.</span><span class="sxs-lookup"><span data-stu-id="d5e76-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="d5e76-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="d5e76-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="d5e76-132">NULL</span><span class="sxs-lookup"><span data-stu-id="d5e76-132">NULL</span></span>|<span data-ttu-id="d5e76-133">Nedefinovaný.</span><span class="sxs-lookup"><span data-stu-id="d5e76-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5e76-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5e76-134">Requirements</span></span>  
 <span data-ttu-id="d5e76-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e76-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e76-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5e76-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5e76-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5e76-137">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d5e76-138">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d5e76-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5e76-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5e76-139">See also</span></span>

- [<span data-ttu-id="d5e76-140">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5e76-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d5e76-141">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5e76-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
