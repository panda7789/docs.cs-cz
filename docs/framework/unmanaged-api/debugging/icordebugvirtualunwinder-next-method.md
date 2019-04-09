---
title: ICorDebugVirtualUnwinder::Next – metoda
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74be827dc97213507b96da9e025923f859011acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076884"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="9388e-102">ICorDebugVirtualUnwinder::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9388e-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="9388e-103">Přejde k kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="9388e-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9388e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9388e-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="9388e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9388e-105">Parameters</span></span>  
 <span data-ttu-id="9388e-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="9388e-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9388e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9388e-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="9388e-108">Pokud unwind proběhlo úspěšně, nebo `CORDBG_S_AT_END_OF_STACK` Pokud unwind nelze dokončit, protože nejsou žádné další rámce.</span><span class="sxs-lookup"><span data-stu-id="9388e-108">if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="9388e-109">Pokud se vrátí selhání HRESULT je vrácena, icordebug – rozhraní API `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="9388e-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9388e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9388e-110">Remarks</span></span>  
 <span data-ttu-id="9388e-111">Zásobníkem byste se ujistit, že je postup směrem vpřed, takže to nakonec volání `Next` vrátí neúspěšného HRESULT nebo `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="9388e-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="9388e-112">Vrací `S_OK` po neomezenou dobu, může způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="9388e-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9388e-113">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9388e-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9388e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9388e-114">Requirements</span></span>  
 <span data-ttu-id="9388e-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9388e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9388e-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9388e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9388e-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9388e-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9388e-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9388e-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9388e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9388e-119">See also</span></span>

- [<span data-ttu-id="9388e-120">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9388e-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="9388e-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9388e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
