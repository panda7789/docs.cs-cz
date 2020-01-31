---
title: Rozhraní ICorDebugProcess8
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 813afc047f9fda060f1cf1af780336ff8b7c18be
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792153"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="d1d70-102">Rozhraní ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="d1d70-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="d1d70-103">[Podporováno v .NET Framework 4,6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d1d70-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="d1d70-104">Logicky rozšiřuje rozhraní ICorDebugProcess a povoluje nebo zakazuje určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d1d70-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1d70-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d1d70-105">Methods</span></span>  
  
|<span data-ttu-id="d1d70-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d1d70-106">Method</span></span>|<span data-ttu-id="d1d70-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d1d70-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1d70-108">EnableExceptionCallbacksOutsideOfMyCode – metoda</span><span class="sxs-lookup"><span data-stu-id="d1d70-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="d1d70-109">Povolí nebo zakáže určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d1d70-109">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1d70-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1d70-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d70-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1d70-111">Requirements</span></span>  
 <span data-ttu-id="d1d70-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d70-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d70-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1d70-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1d70-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d1d70-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d70-115">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d70-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d70-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1d70-116">See also</span></span>

- [<span data-ttu-id="d1d70-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d1d70-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d1d70-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="d1d70-118">Debugging</span></span>](index.md)
