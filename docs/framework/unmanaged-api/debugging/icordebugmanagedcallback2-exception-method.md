---
title: "ICorDebugManagedCallback2::Exception – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a78900a6e37c3ae136489c35da7b0cd2931f24a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="a4750-102">ICorDebugManagedCallback2::Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="a4750-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="a4750-103">Aby bylo zahájeno hledání pro obslužnou rutinu výjimky upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="a4750-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4750-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4750-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a4750-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4750-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a4750-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující vláken, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="a4750-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a4750-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="a4750-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="a4750-108">[v] Ukazatel na ICorDebugFrame objekt, který reprezentuje rámce, počítáno od `dwEventType` parametr.</span><span class="sxs-lookup"><span data-stu-id="a4750-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="a4750-109">Další informace najdete v tabulce v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="a4750-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="a4750-110">[v] Celé číslo, které určuje posun, počítáno od `dwEventType` parametr.</span><span class="sxs-lookup"><span data-stu-id="a4750-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="a4750-111">Další informace najdete v tabulce v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="a4750-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="a4750-112">[v] Hodnota CorDebugExceptionCallbackType – výčet, který určuje typ této výjimky zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a4750-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a4750-113">[v] Hodnota [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) výčet, který určuje další informace o výjimce</span><span class="sxs-lookup"><span data-stu-id="a4750-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4750-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4750-114">Remarks</span></span>  
 <span data-ttu-id="a4750-115">`Exception` Zpětné volání je volána v různých okamžicích v průběhu vyhledávání fáze procesu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="a4750-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="a4750-116">To znamená, že ho lze volat více než jednou při unwinding výjimku.</span><span class="sxs-lookup"><span data-stu-id="a4750-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="a4750-117">Výjimka zpracovává mohou být načteny z objektu ICorDebugThread odkazuje `pThread` parametr.</span><span class="sxs-lookup"><span data-stu-id="a4750-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="a4750-118">Určitého snímku a posun jsou určeny `dwEventType` parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a4750-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="a4750-119">Hodnota`dwEventType`</span><span class="sxs-lookup"><span data-stu-id="a4750-119">Value of `dwEventType`</span></span>|<span data-ttu-id="a4750-120">Hodnota`pFrame`</span><span class="sxs-lookup"><span data-stu-id="a4750-120">Value of `pFrame`</span></span>|<span data-ttu-id="a4750-121">Hodnota`nOffset`</span><span class="sxs-lookup"><span data-stu-id="a4750-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="a4750-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a4750-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="a4750-123">Rámečku, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="a4750-123">The frame that threw the exception.</span></span>|<span data-ttu-id="a4750-124">Ukazatel instrukce v rámečku.</span><span class="sxs-lookup"><span data-stu-id="a4750-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="a4750-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a4750-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="a4750-126">Na uživatelském kódu rámce nejbližší bod vyvolaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="a4750-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="a4750-127">Ukazatel instrukce v rámečku.</span><span class="sxs-lookup"><span data-stu-id="a4750-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="a4750-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="a4750-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="a4750-129">Rámce, který obsahuje obslužná rutina catch.</span><span class="sxs-lookup"><span data-stu-id="a4750-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="a4750-130">Posun Microsoft (MSIL intermediate language) na začátek obslužná rutina catch.</span><span class="sxs-lookup"><span data-stu-id="a4750-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="a4750-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="a4750-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="a4750-132">NULL</span><span class="sxs-lookup"><span data-stu-id="a4750-132">NULL</span></span>|<span data-ttu-id="a4750-133">Není definována.</span><span class="sxs-lookup"><span data-stu-id="a4750-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4750-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4750-134">Requirements</span></span>  
 <span data-ttu-id="a4750-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4750-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4750-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4750-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4750-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4750-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4750-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4750-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4750-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4750-139">See Also</span></span>  
 [<span data-ttu-id="a4750-140">ICorDebugManagedCallback2 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4750-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="a4750-141">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4750-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
