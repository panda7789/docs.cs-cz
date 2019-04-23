---
title: ICorDebugModule3::CreateReaderForInMemorySymbols – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfe83707b6354c42a4c3c81e911918b2ea79ec4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108911"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="40b19-102">ICorDebugModule3::CreateReaderForInMemorySymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="40b19-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="40b19-103">Vytvoří čtečku symbolů ladění pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="40b19-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40b19-104">Syntax</span></span>  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="40b19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40b19-105">Parameters</span></span>  
 <span data-ttu-id="40b19-106">riid</span><span class="sxs-lookup"><span data-stu-id="40b19-106">riid</span></span>  
 <span data-ttu-id="40b19-107">[in] Identifikátor IID rozhraní COM se vraťte.</span><span class="sxs-lookup"><span data-stu-id="40b19-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="40b19-108">Obvykle se jedná [isymunmanagedreader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="40b19-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="40b19-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="40b19-109">ppObj</span></span>  
 <span data-ttu-id="40b19-110">[out] Ukazatel na ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="40b19-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40b19-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40b19-111">Return Value</span></span>  
 <span data-ttu-id="40b19-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="40b19-112">S_OK</span></span>  
 <span data-ttu-id="40b19-113">Čtecí modul se úspěšně vytvořil.</span><span class="sxs-lookup"><span data-stu-id="40b19-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="40b19-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="40b19-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="40b19-115">Modul není v paměti nebo dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="40b19-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="40b19-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40b19-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="40b19-117">Symboly nebyly poskytnuté aplikací nebo dosud nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="40b19-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="40b19-118">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="40b19-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="40b19-119">Nelze vytvořit čtecí modul.</span><span class="sxs-lookup"><span data-stu-id="40b19-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40b19-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40b19-120">Remarks</span></span>  
 <span data-ttu-id="40b19-121">Tato metoda může také být použité k vytvoření objektu čtečky symbolů pro moduly (nedynamickou) v paměti, ale pouze po symboly jsou k dispozici nejprve (indikován [updatemodulesymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="40b19-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="40b19-122">Tato metoda vrací novou instanci čtečky pokaždé, když je volána (jako je [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="40b19-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="40b19-123">Proto by měl ladicí program uložte do mezipaměti výsledek a požádat o novou instanci pouze v případě, že mohlo dojít ke změně podkladová data (to znamená, když [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) přijetí zpětné volání).</span><span class="sxs-lookup"><span data-stu-id="40b19-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="40b19-124">Dynamické moduly nemají žádné symboly k dispozici, dokud se načetl první typ (jak je uvedeno ve [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="40b19-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40b19-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40b19-125">Requirements</span></span>  
 <span data-ttu-id="40b19-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40b19-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40b19-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40b19-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40b19-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40b19-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40b19-129">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="40b19-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b19-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40b19-130">See also</span></span>

- [<span data-ttu-id="40b19-131">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40b19-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="40b19-132">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40b19-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="40b19-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="40b19-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
