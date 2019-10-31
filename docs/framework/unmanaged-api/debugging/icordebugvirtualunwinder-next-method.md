---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: ed80b7a630f78002ded14a1bec206cc8712bd504
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121863"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="772e1-102">ICorDebugVirtualUnwinder:: Next – metoda</span><span class="sxs-lookup"><span data-stu-id="772e1-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="772e1-103">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="772e1-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="772e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="772e1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="772e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="772e1-105">Parameters</span></span>  
 <span data-ttu-id="772e1-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="772e1-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="772e1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="772e1-107">Return Value</span></span>  
 <span data-ttu-id="772e1-108">`S_OK`, zda došlo k rewindu úspěšně, nebo `CORDBG_S_AT_END_OF_STACK`, Pokud unwind nelze dokončit, protože neexistují žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="772e1-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="772e1-109">Pokud je vrácena neúspěšná hodnota HRESULT, vrátí rozhraní API ICorDebug `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="772e1-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="772e1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="772e1-110">Remarks</span></span>  
 <span data-ttu-id="772e1-111">Prohlížeč zásobníku by měl zajistit, že bude předávat pokrok, aby nakonec volání `Next` vrátilo neúspěch HRESULT nebo `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="772e1-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="772e1-112">Vrácení `S_OK` bez omezení může způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="772e1-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="772e1-113">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="772e1-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="772e1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="772e1-114">Requirements</span></span>  
 <span data-ttu-id="772e1-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772e1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772e1-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="772e1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="772e1-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="772e1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="772e1-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="772e1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772e1-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="772e1-119">See also</span></span>

- [<span data-ttu-id="772e1-120">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="772e1-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="772e1-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="772e1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
