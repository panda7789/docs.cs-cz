---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2838c6c1fe8641e343fac1a3efa82a39ee177abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="4481d-102">ICorDebugModule3::CreateReaderForInMemorySymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="4481d-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="4481d-103">Vytvoří symbol čtečku ladění pro dynamické modul.</span><span class="sxs-lookup"><span data-stu-id="4481d-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4481d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4481d-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4481d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4481d-105">Parameters</span></span>  
 <span data-ttu-id="4481d-106">riid</span><span class="sxs-lookup"><span data-stu-id="4481d-106">riid</span></span>  
 <span data-ttu-id="4481d-107">[v] Identifikátory IID rozhraní COM vrátit.</span><span class="sxs-lookup"><span data-stu-id="4481d-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="4481d-108">Obvykle se jedná [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4481d-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="4481d-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="4481d-109">ppObj</span></span>  
 <span data-ttu-id="4481d-110">[out] Ukazatel na ukazatel na vrácený rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4481d-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4481d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4481d-111">Return Value</span></span>  
 <span data-ttu-id="4481d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4481d-112">S_OK</span></span>  
 <span data-ttu-id="4481d-113">Čtečka se úspěšně vytvořil.</span><span class="sxs-lookup"><span data-stu-id="4481d-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="4481d-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="4481d-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="4481d-115">Modul není modul v paměti nebo dynamické.</span><span class="sxs-lookup"><span data-stu-id="4481d-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="4481d-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4481d-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="4481d-117">Symboly aplikací, nebyla zadána nebo ještě nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4481d-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="4481d-118">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="4481d-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4481d-119">Nelze vytvořit program pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4481d-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4481d-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4481d-120">Remarks</span></span>  
 <span data-ttu-id="4481d-121">Tato metoda může být také použít k vytvoření objektu čtečky symbol pro moduly (bez dynamické) v paměti, ale pouze po symboly jsou k dispozici nejprve (indikován [updatemodulesymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="4481d-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="4481d-122">Tato metoda vrátí novou instanci čtečky pokaždé, když je volána (jako je [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span><span class="sxs-lookup"><span data-stu-id="4481d-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)).</span></span> <span data-ttu-id="4481d-123">Proto by měl ladicího programu mezipaměti výsledek a jenom v případě, že mohlo dojít ke změně v základních datech požádat o novou instanci (to znamená, když [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) přijetí zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="4481d-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="4481d-124">Dynamických modulech nemají žádné symboly, které jsou k dispozici, dokud se načetl první typ (jak [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="4481d-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4481d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4481d-125">Requirements</span></span>  
 <span data-ttu-id="4481d-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4481d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4481d-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4481d-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4481d-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4481d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4481d-129">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="4481d-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4481d-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="4481d-130">See Also</span></span>  
 [<span data-ttu-id="4481d-131">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4481d-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="4481d-132">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4481d-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="4481d-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4481d-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
