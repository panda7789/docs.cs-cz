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
ms.openlocfilehash: 2655151d34275b1b0fdc5d0903dd57fcea646014
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137307"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="438d8-102">ICorDebugModule3::CreateReaderForInMemorySymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="438d8-102">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>
<span data-ttu-id="438d8-103">Vytvoří čtečku symbolů ladění pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="438d8-103">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="438d8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="438d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="438d8-105">Parameters</span></span>  
 <span data-ttu-id="438d8-106">riid</span><span class="sxs-lookup"><span data-stu-id="438d8-106">riid</span></span>  
 <span data-ttu-id="438d8-107">pro IID rozhraní modelu COM, které má být vráceno.</span><span class="sxs-lookup"><span data-stu-id="438d8-107">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="438d8-108">Obvykle se jedná o [rozhraní ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="438d8-108">Typically, this is an [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="438d8-109">ppObj</span><span class="sxs-lookup"><span data-stu-id="438d8-109">ppObj</span></span>  
 <span data-ttu-id="438d8-110">mimo Ukazatel na ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="438d8-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="438d8-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="438d8-111">Return Value</span></span>  
 <span data-ttu-id="438d8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="438d8-112">S_OK</span></span>  
 <span data-ttu-id="438d8-113">Čtecí modul se úspěšně vytvořil.</span><span class="sxs-lookup"><span data-stu-id="438d8-113">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="438d8-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="438d8-114">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="438d8-115">Modul není v paměti nebo dynamickém modulu.</span><span class="sxs-lookup"><span data-stu-id="438d8-115">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="438d8-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="438d8-116">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="438d8-117">Aplikace nedodala symboly nebo ještě nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="438d8-117">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="438d8-118">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="438d8-118">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="438d8-119">Nelze vytvořit čtecí modul.</span><span class="sxs-lookup"><span data-stu-id="438d8-119">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="438d8-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="438d8-120">Remarks</span></span>  
 <span data-ttu-id="438d8-121">Tato metoda může být také použita k vytvoření objektu čtečky symbolů pro moduly v paměti (nedynamické), ale pouze po prvním zpřístupnění symbolů (označeno zpětným voláním [metody UpdateModuleSymbols –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="438d8-121">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="438d8-122">Tato metoda vrací novou instanci čtenáře pokaždé, když je volána (například [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="438d8-122">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="438d8-123">Proto by měl ladicí program uložit výsledek do mezipaměti a požádat o novou instanci pouze v případě, že došlo ke změně podkladových dat (tj. při přijetí zpětného volání [metody LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="438d8-123">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="438d8-124">Dynamické moduly nemají k dispozici žádné symboly, dokud není načten první typ (jak je uvedeno v zpětném volání [metody LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="438d8-124">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="438d8-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="438d8-125">Requirements</span></span>  
 <span data-ttu-id="438d8-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="438d8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="438d8-127">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="438d8-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="438d8-128">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="438d8-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="438d8-129">**Verze .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="438d8-129">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438d8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="438d8-130">See also</span></span>

- [<span data-ttu-id="438d8-131">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="438d8-131">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="438d8-132">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="438d8-132">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="438d8-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="438d8-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
