---
title: ICorDebugProcess6::ProcessStateChanged – metoda
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb158b383745cd7e44c8fede6ddd43ae81ced2d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930768"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="16fc4-102">ICorDebugProcess6::ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="16fc4-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="16fc4-103">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="16fc4-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16fc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16fc4-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16fc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16fc4-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="16fc4-106">pro Člen výčtu [ProcessStateChanged –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="16fc4-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16fc4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16fc4-107">Remarks</span></span>  
 <span data-ttu-id="16fc4-108">Ladicí program volá tuto metodu pro oznamování [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="16fc4-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16fc4-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16fc4-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16fc4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16fc4-110">Requirements</span></span>  
 <span data-ttu-id="16fc4-111">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16fc4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16fc4-112">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16fc4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16fc4-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16fc4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16fc4-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16fc4-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16fc4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16fc4-115">See also</span></span>

- [<span data-ttu-id="16fc4-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16fc4-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="16fc4-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="16fc4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
