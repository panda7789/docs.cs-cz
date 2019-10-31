---
title: ICorDebugProcess6::ProcessStateChanged – metoda
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 3927e57883ebe282b262cb03ececc3b2cd96fd46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123419"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="16a7f-102">ICorDebugProcess6::ProcessStateChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="16a7f-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="16a7f-103">Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="16a7f-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16a7f-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16a7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16a7f-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="16a7f-106">pro Člen výčtu [ProcessStateChanged –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="16a7f-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16a7f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16a7f-107">Remarks</span></span>  
 <span data-ttu-id="16a7f-108">Ladicí program volá tuto metodu pro oznamování [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , že proces běží.</span><span class="sxs-lookup"><span data-stu-id="16a7f-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16a7f-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16a7f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16a7f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16a7f-110">Requirements</span></span>  
 <span data-ttu-id="16a7f-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16a7f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16a7f-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16a7f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16a7f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16a7f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16a7f-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16a7f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a7f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16a7f-115">See also</span></span>

- [<span data-ttu-id="16a7f-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16a7f-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="16a7f-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="16a7f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
