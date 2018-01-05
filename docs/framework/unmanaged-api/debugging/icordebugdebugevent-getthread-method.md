---
title: "ICorDebugDebugEvent::GetThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: faf1ace6c65f38e9a1d5b958b633c95dbcd3dcf8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="46127-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="46127-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="46127-103">Získá vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="46127-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46127-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46127-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46127-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46127-105">Parameters</span></span>  
 <span data-ttu-id="46127-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="46127-106">ppThread</span></span>  
 <span data-ttu-id="46127-107">[out] Ukazatel na adresu ICorDebugThread objekt, který reprezentuje vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="46127-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46127-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46127-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46127-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="46127-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46127-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46127-110">Requirements</span></span>  
 <span data-ttu-id="46127-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46127-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46127-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46127-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46127-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46127-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46127-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46127-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46127-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="46127-115">See Also</span></span>  
 [<span data-ttu-id="46127-116">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46127-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="46127-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="46127-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
