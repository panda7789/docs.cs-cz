---
title: 'ICorDebugVirtualUnwinder:: GetContext – Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ff5e5bdd66ec44a0931b51212f07485718507576
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790843"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="2d393-102">ICorDebugVirtualUnwinder:: GetContext – Metoda</span><span class="sxs-lookup"><span data-stu-id="2d393-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="2d393-103">Získá aktuální kontext tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="2d393-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d393-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d393-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d393-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d393-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="2d393-106">pro Příznaky, které určují, které části kontextu se mají vrátit (definované v souboru WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="2d393-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="2d393-107">pro Počet bajtů v `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="2d393-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2d393-108">mimo Ukazatel na počet bajtů skutečně zapsaných do `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="2d393-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="2d393-109">mimo Bajtové pole obsahující aktuální kontext tohoto unwindu.</span><span class="sxs-lookup"><span data-stu-id="2d393-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d393-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d393-110">Return Value</span></span>  
 <span data-ttu-id="2d393-111">Jakákoli neúspěšná hodnota HRESULT přijatá v mscordbi se považuje za závažnou a způsobí, že rozhraní API ICorDebug vrátí `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="2d393-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d393-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d393-112">Remarks</span></span>  
 <span data-ttu-id="2d393-113">Nastavte počáteční hodnotu argumentu `contextBuf` na vyrovnávací paměť kontextu vrácenou voláním metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2d393-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d393-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2d393-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="2d393-115">Vzhledem k tomu, že unwind může obnovit pouze podmnožinu registrů, jako jsou pouze nestálé Registry, kontext nemusí přesně odpovídat stavu registrace v době samotného volání metody.</span><span class="sxs-lookup"><span data-stu-id="2d393-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d393-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d393-116">Requirements</span></span>  
 <span data-ttu-id="2d393-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d393-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d393-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d393-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d393-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d393-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d393-120">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d393-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d393-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d393-121">See also</span></span>

- [<span data-ttu-id="2d393-122">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d393-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="2d393-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d393-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
