---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967923"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="083e9-102">ICorDebugVirtualUnwinder:: Next – metoda</span><span class="sxs-lookup"><span data-stu-id="083e9-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="083e9-103">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="083e9-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="083e9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="083e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="083e9-105">Parameters</span></span>  
 <span data-ttu-id="083e9-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="083e9-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="083e9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="083e9-107">Return Value</span></span>  
 <span data-ttu-id="083e9-108">`S_OK`Pokud se unwind úspěšně nastalo, `CORDBG_S_AT_END_OF_STACK` nebo pokud se unwind nedá dokončit, protože neexistují žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="083e9-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="083e9-109">Pokud se vrátí neúspěšná hodnota HRESULT, vrátí `CORDBG_E_DATA_TARGET_ERROR`rozhraní API ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="083e9-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="083e9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="083e9-110">Remarks</span></span>  
 <span data-ttu-id="083e9-111">Zásobník prohlížeč by měl zajistit, že předává průběh vpřed, takže nakonec volání `Next` vrátí HRESULT nebo. `CORDBG_S_AT_END_OF_STACK`</span><span class="sxs-lookup"><span data-stu-id="083e9-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="083e9-112">Vrácení `S_OK` bez omezení může způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="083e9-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="083e9-113">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="083e9-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="083e9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="083e9-114">Requirements</span></span>  
 <span data-ttu-id="083e9-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="083e9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="083e9-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="083e9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="083e9-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="083e9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="083e9-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="083e9-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083e9-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="083e9-119">See also</span></span>

- [<span data-ttu-id="083e9-120">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="083e9-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="083e9-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="083e9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
