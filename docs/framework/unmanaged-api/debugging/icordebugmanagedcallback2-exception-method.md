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
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781533"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="d6447-102">ICorDebugManagedCallback2::Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="d6447-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="d6447-103">Oznamuje ladicímu programu, že bylo zahájeno hledání obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="d6447-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6447-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6447-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6447-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6447-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d6447-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vyvolána.</span><span class="sxs-lookup"><span data-stu-id="d6447-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d6447-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, na kterém byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d6447-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="d6447-108">pro Ukazatel na objekt ICorDebugFrame, který představuje rámec určený parametrem `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="d6447-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="d6447-109">Další informace najdete v tabulce v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="d6447-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="d6447-110">pro Celé číslo, které určuje posun, jak je určeno parametrem `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="d6447-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="d6447-111">Další informace najdete v tabulce v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="d6447-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="d6447-112">pro Hodnota výčtu CorDebugExceptionCallbackType –, která určuje typ zpětného volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d6447-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d6447-113">pro Hodnota výčtu [CorDebugExceptionFlags –](cordebugexceptionflags-enumeration.md) , která určuje další informace o výjimce</span><span class="sxs-lookup"><span data-stu-id="d6447-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6447-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6447-114">Remarks</span></span>  
 <span data-ttu-id="d6447-115">`Exception` zpětné volání se volá v různých bodech ve fázi hledání v procesu zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="d6447-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="d6447-116">To znamená, že může být voláno více než jednou při odvíjení výjimky.</span><span class="sxs-lookup"><span data-stu-id="d6447-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="d6447-117">Zpracovávaná výjimka může být načtena z objektu ICorDebugThread, na který odkazuje parametr `pThread`.</span><span class="sxs-lookup"><span data-stu-id="d6447-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="d6447-118">Konkrétní rámec a posun jsou určeny parametrem `dwEventType` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d6447-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="d6447-119">Hodnota `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="d6447-119">Value of `dwEventType`</span></span>|<span data-ttu-id="d6447-120">Hodnota `pFrame`</span><span class="sxs-lookup"><span data-stu-id="d6447-120">Value of `pFrame`</span></span>|<span data-ttu-id="d6447-121">Hodnota `nOffset`</span><span class="sxs-lookup"><span data-stu-id="d6447-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="d6447-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d6447-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="d6447-123">Rámec, který vyvolal výjimku.</span><span class="sxs-lookup"><span data-stu-id="d6447-123">The frame that threw the exception.</span></span>|<span data-ttu-id="d6447-124">Ukazatel na instrukci v rámci.</span><span class="sxs-lookup"><span data-stu-id="d6447-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="d6447-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d6447-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="d6447-126">Rámec uživatelského kódu nejblíže k bodu vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="d6447-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="d6447-127">Ukazatel na instrukci v rámci.</span><span class="sxs-lookup"><span data-stu-id="d6447-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="d6447-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="d6447-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="d6447-129">Rámec obsahující popisovač catch.</span><span class="sxs-lookup"><span data-stu-id="d6447-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="d6447-130">Posun jazyka MSIL (Microsoft Intermediate Language) od začátku obslužné rutiny catch.</span><span class="sxs-lookup"><span data-stu-id="d6447-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="d6447-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="d6447-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="d6447-132">NULL</span><span class="sxs-lookup"><span data-stu-id="d6447-132">NULL</span></span>|<span data-ttu-id="d6447-133">Nedefinované.</span><span class="sxs-lookup"><span data-stu-id="d6447-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6447-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6447-134">Requirements</span></span>  
 <span data-ttu-id="d6447-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6447-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6447-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d6447-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6447-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d6447-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6447-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6447-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6447-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6447-139">See also</span></span>

- [<span data-ttu-id="d6447-140">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6447-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d6447-141">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6447-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
