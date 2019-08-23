---
title: 'ICorDebugVirtualUnwinder:: GetContext – Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6a8be489ff2a99bb9da393577514b2442d50db8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967956"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="a69f4-102">ICorDebugVirtualUnwinder:: GetContext – Metoda</span><span class="sxs-lookup"><span data-stu-id="a69f4-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="a69f4-103">Získá aktuální kontext tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="a69f4-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a69f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a69f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a69f4-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="a69f4-106">pro Příznaky, které určují, které části kontextu se mají vrátit (definované v souboru WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="a69f4-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="a69f4-107">pro Počet bajtů v `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="a69f4-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a69f4-108">mimo Ukazatel na počet bajtů, které `contextBuf`jsou ve skutečnosti zapsány.</span><span class="sxs-lookup"><span data-stu-id="a69f4-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="a69f4-109">mimo Bajtové pole obsahující aktuální kontext tohoto unwindu.</span><span class="sxs-lookup"><span data-stu-id="a69f4-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a69f4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a69f4-110">Return Value</span></span>  
 <span data-ttu-id="a69f4-111">Jakákoli neúspěšná hodnota HRESULT přijatá v mscordbi se považuje za závažnou a způsobí, že `CORDBG_E_DATA_TARGET_ERROR`rozhraní ICorDebug API vrátí.</span><span class="sxs-lookup"><span data-stu-id="a69f4-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a69f4-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a69f4-112">Remarks</span></span>  
 <span data-ttu-id="a69f4-113">Nastavte počáteční hodnotu `contextBuf` argumentu na vyrovnávací paměť kontextu vrácenou voláním metody [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a69f4-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a69f4-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a69f4-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="a69f4-115">Vzhledem k tomu, že unwind může obnovit pouze podmnožinu registrů, jako jsou pouze nestálé Registry, kontext nemusí přesně odpovídat stavu registrace v době samotného volání metody.</span><span class="sxs-lookup"><span data-stu-id="a69f4-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69f4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a69f4-116">Requirements</span></span>  
 <span data-ttu-id="a69f4-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a69f4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a69f4-118">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a69f4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a69f4-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a69f4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a69f4-120">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a69f4-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69f4-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a69f4-121">See also</span></span>

- [<span data-ttu-id="a69f4-122">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a69f4-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a69f4-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a69f4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
