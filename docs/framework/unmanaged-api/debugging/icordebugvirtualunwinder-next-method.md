---
title: "ICorDebugVirtualUnwinder::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61f7e5afc65019f1817b15ae84ca3f7b42e3ece9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="a69b7-102">ICorDebugVirtualUnwinder::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a69b7-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="a69b7-103">Přejde k kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="a69b7-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a69b7-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a69b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a69b7-105">Parameters</span></span>  
 <span data-ttu-id="a69b7-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="a69b7-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a69b7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a69b7-107">Return Value</span></span>  
 <span data-ttu-id="a69b7-108">`S_OK`Pokud došlo k chybě unwind úspěšně, nebo `CORDBG_S_AT_END_OF_STACK` Pokud unwind nemůže být dokončena, protože nejsou k dispozici žádné další rámce.</span><span class="sxs-lookup"><span data-stu-id="a69b7-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="a69b7-109">Pokud dojde při selhání je vrácen HRESULT ICorDebug rozhraní API vrátí `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="a69b7-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a69b7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a69b7-110">Remarks</span></span>  
 <span data-ttu-id="a69b7-111">Walkera zásobníku se ujistěte, že umožňuje postup směrem vpřed, takže to nakonec volání `Next` vrátí dojde při selhání HRESULT nebo `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="a69b7-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="a69b7-112">Vrácení `S_OK` po neomezenou dobu může způsobit nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="a69b7-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a69b7-113">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="a69b7-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69b7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a69b7-114">Requirements</span></span>  
 <span data-ttu-id="a69b7-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a69b7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a69b7-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a69b7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a69b7-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a69b7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a69b7-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a69b7-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69b7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a69b7-119">See Also</span></span>  
 [<span data-ttu-id="a69b7-120">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a69b7-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="a69b7-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a69b7-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
