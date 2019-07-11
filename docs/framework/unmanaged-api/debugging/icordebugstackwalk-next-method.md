---
title: ICorDebugStackWalk::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6c96e64b1197b5762c0ad7dbed5458b5d71a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760895"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="213c0-102">ICorDebugStackWalk::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="213c0-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="213c0-103">Přesune [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu do dalšího snímku.</span><span class="sxs-lookup"><span data-stu-id="213c0-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="213c0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="213c0-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="213c0-105">Return Value</span></span>  
 <span data-ttu-id="213c0-106">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="213c0-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="213c0-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="213c0-107">HRESULT</span></span>|<span data-ttu-id="213c0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="213c0-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="213c0-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="213c0-109">S_OK</span></span>|<span data-ttu-id="213c0-110">Modul runtime úspěšně zachytila na další snímek (viz poznámky).</span><span class="sxs-lookup"><span data-stu-id="213c0-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="213c0-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="213c0-111">E_FAIL</span></span>|<span data-ttu-id="213c0-112">`ICorDebugStackWalk` Objektu nelze advanced.</span><span class="sxs-lookup"><span data-stu-id="213c0-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="213c0-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="213c0-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="213c0-114">Byl dosažen konec zásobníku jako výsledek tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="213c0-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="213c0-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="213c0-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="213c0-116">Už na konec zásobníku; ukazatel na rámec Proto je možný žádné další rámce.</span><span class="sxs-lookup"><span data-stu-id="213c0-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="213c0-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="213c0-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="213c0-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="213c0-118">Remarks</span></span>  
 <span data-ttu-id="213c0-119">`Next` Metody zálohy `ICorDebugStackWalk` objektu na volání rámec pouze v případě, že modul runtime může vrátit se zpět aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="213c0-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="213c0-120">V opačném případě objekt přejde na další snímek, aby bylo možné vrátit se zpět modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="213c0-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="213c0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="213c0-121">Requirements</span></span>  
 <span data-ttu-id="213c0-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="213c0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="213c0-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="213c0-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="213c0-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="213c0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="213c0-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="213c0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213c0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="213c0-126">See also</span></span>

- [<span data-ttu-id="213c0-127">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="213c0-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="213c0-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="213c0-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="213c0-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="213c0-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
