---
title: Rozhraní ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 04e7b9a064d4a06a06b8a1518f06092ba79a3561
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783493"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="df85a-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="df85a-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="df85a-103">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) , aby poskytovala informace o načtených modulech.</span><span class="sxs-lookup"><span data-stu-id="df85a-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="df85a-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="df85a-104">Method</span></span>  
  
|<span data-ttu-id="df85a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="df85a-105">Method</span></span>|<span data-ttu-id="df85a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="df85a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df85a-107">GetLoadedModules – metoda</span><span class="sxs-lookup"><span data-stu-id="df85a-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="df85a-108">Načte seznam modulů, které byly doposud načteny.</span><span class="sxs-lookup"><span data-stu-id="df85a-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df85a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df85a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df85a-110">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="df85a-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="df85a-111">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="df85a-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df85a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df85a-112">Requirements</span></span>  
 <span data-ttu-id="df85a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df85a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df85a-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df85a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df85a-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df85a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df85a-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df85a-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df85a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df85a-117">See also</span></span>

- [<span data-ttu-id="df85a-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="df85a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="df85a-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="df85a-119">Debugging</span></span>](index.md)
