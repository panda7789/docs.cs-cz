---
title: ICorDebugProcess6::ProcessStateChanged – metoda
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5861762242412d7ab6f0c02f2b8f5c149f9453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420176"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="c8862-102">ICorDebugProcess6::ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="c8862-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="c8862-103">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kterém proces běží.</span><span class="sxs-lookup"><span data-stu-id="c8862-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8862-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8862-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8862-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8862-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="c8862-106">[v] Člen [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) – výčet</span><span class="sxs-lookup"><span data-stu-id="c8862-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8862-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8862-107">Remarks</span></span>  
 <span data-ttu-id="c8862-108">Ladicí program volá tuto metodu za účelem oznámit [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kterém proces běží.</span><span class="sxs-lookup"><span data-stu-id="c8862-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8862-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="c8862-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8862-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8862-110">Requirements</span></span>  
 <span data-ttu-id="c8862-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8862-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8862-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8862-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8862-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8862-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8862-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8862-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8862-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8862-115">See Also</span></span>  
 [<span data-ttu-id="c8862-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8862-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="c8862-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c8862-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
