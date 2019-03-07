---
title: ICorDebugProcess6::ProcessStateChanged – metoda
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f25e25f94dae1a959cbb813a44a7f4f09eaa69c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474589"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="11d0a-102">ICorDebugProcess6::ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="11d0a-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="11d0a-103">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , který je proces spuštěn.</span><span class="sxs-lookup"><span data-stu-id="11d0a-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d0a-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11d0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11d0a-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="11d0a-106">[in] Člen [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) výčet</span><span class="sxs-lookup"><span data-stu-id="11d0a-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11d0a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11d0a-107">Remarks</span></span>  
 <span data-ttu-id="11d0a-108">Ladicí program volá tuto metodu za účelem oznámit [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , který je proces spuštěn.</span><span class="sxs-lookup"><span data-stu-id="11d0a-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11d0a-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="11d0a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d0a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11d0a-110">Requirements</span></span>  
 <span data-ttu-id="11d0a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11d0a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d0a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11d0a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11d0a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11d0a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11d0a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11d0a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d0a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11d0a-115">See also</span></span>
- [<span data-ttu-id="11d0a-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d0a-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="11d0a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="11d0a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
