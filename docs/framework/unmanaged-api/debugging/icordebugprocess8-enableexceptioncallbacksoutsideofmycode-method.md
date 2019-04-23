---
title: Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184831"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="4592a-102">Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="4592a-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="4592a-103">[Podporované v [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="4592a-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="4592a-104">Povolí nebo zakáže určité typy [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="4592a-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4592a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4592a-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4592a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4592a-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="4592a-107">[in]</span><span class="sxs-lookup"><span data-stu-id="4592a-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4592a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4592a-108">Remarks</span></span>  
 <span data-ttu-id="4592a-109">Pokud hodnota `enableExceptionsOutsideOfJMC` je `false`:</span><span class="sxs-lookup"><span data-stu-id="4592a-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="4592a-110">S výjimkou DEBUG_EXCEPTION_FIRST_CHANCE opozdí ve zpětném volání k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="4592a-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="4592a-111">S výjimkou DEBUG_EXCEPTION_CATCH_HANDLER_FOUND opozdí ve zpětném volání k ladicímu programu Pokud výjimka nikdy řídicí sekvence do uživatelského kódu (to znamená, cesty z výjimky původ na obslužnou rutinu výjimky nemá žádné metody označené jako JustMyCode nebo JMC).</span><span class="sxs-lookup"><span data-stu-id="4592a-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="4592a-112">Výchozí hodnota `enableExceptionsOutsideOfJMC` je `true`.</span><span class="sxs-lookup"><span data-stu-id="4592a-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4592a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4592a-113">Requirements</span></span>  
 <span data-ttu-id="4592a-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4592a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4592a-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4592a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4592a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4592a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4592a-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4592a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4592a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4592a-118">See also</span></span>

- [<span data-ttu-id="4592a-119">ICorDebugProcess8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4592a-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="4592a-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4592a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
