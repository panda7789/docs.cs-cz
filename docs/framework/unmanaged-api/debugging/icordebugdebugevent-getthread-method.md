---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 0900ac2ae5bcf2141e720dad6efdf68d4fafaccc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793538"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="2ab4e-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="2ab4e-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="2ab4e-103">Získá vlákno, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="2ab4e-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ab4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ab4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ab4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ab4e-105">Parameters</span></span>  
 <span data-ttu-id="2ab4e-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="2ab4e-106">ppThread</span></span>  
 <span data-ttu-id="2ab4e-107">mimo Ukazatel na adresu objektu ICorDebugThread, který představuje vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="2ab4e-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ab4e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ab4e-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ab4e-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2ab4e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ab4e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ab4e-110">Requirements</span></span>  
 <span data-ttu-id="2ab4e-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ab4e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ab4e-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2ab4e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ab4e-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2ab4e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ab4e-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ab4e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab4e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ab4e-115">See also</span></span>

- [<span data-ttu-id="2ab4e-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ab4e-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="2ab4e-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2ab4e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
