---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 66b4abc4bebfbbde2e6a6b25d2bc0e88839a363f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136650"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="7791d-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="7791d-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="7791d-103">Získá vlákno, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="7791d-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7791d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7791d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7791d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7791d-105">Parameters</span></span>  
 <span data-ttu-id="7791d-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="7791d-106">ppThread</span></span>  
 <span data-ttu-id="7791d-107">mimo Ukazatel na adresu objektu ICorDebugThread, který představuje vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="7791d-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7791d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7791d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7791d-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7791d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7791d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7791d-110">Requirements</span></span>  
 <span data-ttu-id="7791d-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7791d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7791d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7791d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7791d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7791d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7791d-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7791d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7791d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7791d-115">See also</span></span>

- [<span data-ttu-id="7791d-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7791d-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="7791d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7791d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
