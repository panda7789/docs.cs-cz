---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103768918f67ca695a47c52b9cd97f24fb8d46ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081570"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="fb850-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="fb850-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="fb850-103">Získá vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="fb850-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb850-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb850-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb850-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb850-105">Parameters</span></span>  
 <span data-ttu-id="fb850-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="fb850-106">ppThread</span></span>  
 <span data-ttu-id="fb850-107">[out] Ukazatel na adresu icordebugthread – objekt, který představuje vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="fb850-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb850-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb850-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb850-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fb850-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb850-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb850-110">Requirements</span></span>  
 <span data-ttu-id="fb850-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb850-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb850-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb850-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb850-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb850-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb850-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb850-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb850-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb850-115">See also</span></span>

- [<span data-ttu-id="fb850-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb850-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="fb850-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb850-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
