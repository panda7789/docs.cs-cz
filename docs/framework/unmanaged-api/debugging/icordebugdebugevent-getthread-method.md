---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103768918f67ca695a47c52b9cd97f24fb8d46ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996122"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="76559-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="76559-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="76559-103">Získá vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="76559-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76559-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76559-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76559-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76559-105">Parameters</span></span>  
 <span data-ttu-id="76559-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="76559-106">ppThread</span></span>  
 <span data-ttu-id="76559-107">[out] Ukazatel na adresu icordebugthread – objekt, který představuje vlákno, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="76559-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76559-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76559-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76559-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="76559-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76559-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76559-110">Requirements</span></span>  
 <span data-ttu-id="76559-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76559-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76559-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76559-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76559-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76559-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76559-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76559-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76559-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76559-115">See also</span></span>

- [<span data-ttu-id="76559-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76559-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="76559-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="76559-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
