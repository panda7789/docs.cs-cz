---
title: Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: e54dd051f0dbd9c1964d381c2e05189c375fa66d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210134"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="abd84-102">Metoda ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="abd84-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="abd84-103">[Podporováno v .NET Framework 4,6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="abd84-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="abd84-104">Povolí nebo zakáže určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="abd84-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd84-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abd84-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abd84-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="abd84-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="abd84-107">pro</span><span class="sxs-lookup"><span data-stu-id="abd84-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abd84-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abd84-108">Remarks</span></span>  
 <span data-ttu-id="abd84-109">Pokud `enableExceptionsOutsideOfJMC` je hodnota `false` :</span><span class="sxs-lookup"><span data-stu-id="abd84-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="abd84-110">Výjimka DEBUG_EXCEPTION_FIRST_CHANCE nebude mít za následek zpětné volání ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="abd84-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="abd84-111">Výjimka DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nebude mít za následek zpětné volání ladicího programu, pokud výjimka nikdy neřídí kód uživatele (to znamená, že cesta z původ výjimky do obslužné rutiny výjimky nemá žádné metody označené jako JustMyCode nebo JMC).</span><span class="sxs-lookup"><span data-stu-id="abd84-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="abd84-112">Výchozí hodnota `enableExceptionsOutsideOfJMC` je `true` .</span><span class="sxs-lookup"><span data-stu-id="abd84-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abd84-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abd84-113">Requirements</span></span>  
 <span data-ttu-id="abd84-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abd84-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd84-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="abd84-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abd84-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="abd84-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abd84-117">**Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd84-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd84-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="abd84-118">See also</span></span>

- [<span data-ttu-id="abd84-119">Rozhraní ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="abd84-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="abd84-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abd84-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
