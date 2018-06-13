---
title: Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f08f24e16b34d911793b5c8d4a28168f7677b22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418965"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="5a503-102">Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="5a503-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="5a503-103">[V podporované [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="5a503-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="5a503-104">Povolí nebo zakáže určité typy [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětná volání výjimek.</span><span class="sxs-lookup"><span data-stu-id="5a503-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a503-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a503-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a503-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a503-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="5a503-107">[v]</span><span class="sxs-lookup"><span data-stu-id="5a503-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a503-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a503-108">Remarks</span></span>  
 <span data-ttu-id="5a503-109">Pokud hodnota `enableExceptionsOutsideOfJMC` je `false`:</span><span class="sxs-lookup"><span data-stu-id="5a503-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="5a503-110">Výjimka DEBUG_EXCEPTION_FIRST_CHANCE nebude způsobit zpětné volání pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="5a503-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="5a503-111">Výjimka DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nebude za následek zpětné volání pro ladicí program Pokud výjimka řídicí sekvence nikdy do uživatelského kódu (tedy cesty z počátek výjimky na obslužnou rutinu výjimky nemá žádné metody označené jako JustMyCode nebo SVK).</span><span class="sxs-lookup"><span data-stu-id="5a503-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="5a503-112">Výchozí hodnota `enableExceptionsOutsideOfJMC` je `true`.</span><span class="sxs-lookup"><span data-stu-id="5a503-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a503-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a503-113">Requirements</span></span>  
 <span data-ttu-id="5a503-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a503-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a503-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a503-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a503-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a503-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a503-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a503-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a503-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a503-118">See Also</span></span>  
 [<span data-ttu-id="5a503-119">ICorDebugProcess8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a503-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [<span data-ttu-id="5a503-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5a503-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
