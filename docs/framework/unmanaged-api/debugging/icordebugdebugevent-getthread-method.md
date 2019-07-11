---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde1083fe232563aa6129cec79fdfc6c16c77d03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750015"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="6b63b-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="6b63b-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="6b63b-103">Získá vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="6b63b-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b63b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b63b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b63b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b63b-105">Parameters</span></span>  
 <span data-ttu-id="6b63b-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="6b63b-106">ppThread</span></span>  
 <span data-ttu-id="6b63b-107">[out] Ukazatel na adresu icordebugthread – objekt, který představuje vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="6b63b-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b63b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b63b-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b63b-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6b63b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b63b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b63b-110">Requirements</span></span>  
 <span data-ttu-id="6b63b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b63b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b63b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b63b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b63b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b63b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b63b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b63b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b63b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b63b-115">See also</span></span>

- [<span data-ttu-id="6b63b-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b63b-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="6b63b-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6b63b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
