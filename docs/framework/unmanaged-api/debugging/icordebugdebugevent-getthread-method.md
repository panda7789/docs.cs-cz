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
ms.openlocfilehash: 13b950545c2c8c8b54d24b932351d80280e1dac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="fdd49-102">ICorDebugDebugEvent::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd49-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="fdd49-103">Získá vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="fdd49-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdd49-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdd49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdd49-105">Parameters</span></span>  
 <span data-ttu-id="fdd49-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="fdd49-106">ppThread</span></span>  
 <span data-ttu-id="fdd49-107">[out] Ukazatel na adresu ICorDebugThread objekt, který reprezentuje vláken, na kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="fdd49-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdd49-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdd49-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdd49-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="fdd49-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd49-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdd49-110">Requirements</span></span>  
 <span data-ttu-id="fdd49-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd49-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd49-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdd49-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdd49-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdd49-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdd49-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd49-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd49-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdd49-115">See Also</span></span>  
 [<span data-ttu-id="fdd49-116">Rozhraní ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="fdd49-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="fdd49-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdd49-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
