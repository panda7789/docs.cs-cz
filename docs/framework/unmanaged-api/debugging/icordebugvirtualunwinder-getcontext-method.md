---
title: ICorDebugVirtualUnwinder::GetContext – metoda
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8377c374ae71c45cf198446d66a5f9a235a2142f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775360"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="7fd2b-102">ICorDebugVirtualUnwinder::GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7fd2b-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="7fd2b-103">Získá aktuální kontext tohoto unwinder.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fd2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fd2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fd2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fd2b-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="7fd2b-106">[in] Příznaky, které určují, které části kontext, který má vrátit (definované v souboru WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="7fd2b-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="7fd2b-107">[in] Počet bajtů v `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7fd2b-108">[out] Ukazatel na počet bajtů zapsaný ve skutečnosti na `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="7fd2b-109">[out] Bajtové pole obsahující aktuální kontext tohoto unwinder.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fd2b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7fd2b-110">Return Value</span></span>  
 <span data-ttu-id="7fd2b-111">Žádné služeb při selhání přijme mscordbi hodnotu HRESULT je považovat za fatální a způsobí, že icordebug – rozhraní API vrátit `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fd2b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fd2b-112">Remarks</span></span>  
 <span data-ttu-id="7fd2b-113">Nastavit počáteční hodnotu `contextBuf` argument do vyrovnávací paměti kontextu vrácená voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fd2b-114">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="7fd2b-115">Protože odvíjení může pouze obnovení část registrů, jako je například stálé zaregistruje pouze, kontext nemusí přesně odpovídat stav registrace při volání metody skutečný.</span><span class="sxs-lookup"><span data-stu-id="7fd2b-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fd2b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fd2b-116">Requirements</span></span>  
 <span data-ttu-id="7fd2b-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fd2b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fd2b-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fd2b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fd2b-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fd2b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fd2b-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fd2b-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd2b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fd2b-121">See also</span></span>

- [<span data-ttu-id="7fd2b-122">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fd2b-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="7fd2b-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7fd2b-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
