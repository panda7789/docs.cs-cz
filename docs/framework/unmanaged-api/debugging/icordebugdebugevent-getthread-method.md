---
title: ICorDebugDebugEvent::GetThread – metoda
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5b4a15f637526cd2faadd2d9d3da143c40140f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414902"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="41e81-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="41e81-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="41e81-103">Získá vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="41e81-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41e81-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41e81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41e81-105">Parameters</span></span>  
 <span data-ttu-id="41e81-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="41e81-106">ppThread</span></span>  
 <span data-ttu-id="41e81-107">[out] Ukazatel na adresu ICorDebugThread objekt, který reprezentuje vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="41e81-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e81-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41e81-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41e81-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="41e81-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e81-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41e81-110">Requirements</span></span>  
 <span data-ttu-id="41e81-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e81-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e81-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41e81-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41e81-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41e81-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e81-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e81-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e81-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="41e81-115">See Also</span></span>  
 [<span data-ttu-id="41e81-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41e81-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="41e81-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="41e81-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
