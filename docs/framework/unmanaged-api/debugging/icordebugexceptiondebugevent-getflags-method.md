---
title: "ICorDebugExceptionDebugEvent::GetFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33534a65f7a58981abd3df324b5fe005a06669d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="eee79-102">ICorDebugExceptionDebugEvent::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="eee79-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="eee79-103">Získá příznak označující, zda mohou být zachyceny výjimku.</span><span class="sxs-lookup"><span data-stu-id="eee79-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eee79-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eee79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eee79-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="eee79-106">[out] Ukazatel [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) hodnotu, která určuje, zda mohou být zachyceny výjimku.</span><span class="sxs-lookup"><span data-stu-id="eee79-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eee79-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eee79-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eee79-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="eee79-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee79-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eee79-109">Requirements</span></span>  
 <span data-ttu-id="eee79-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee79-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee79-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eee79-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eee79-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eee79-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eee79-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee79-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee79-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="eee79-114">See Also</span></span>  
 [<span data-ttu-id="eee79-115">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="eee79-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="eee79-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="eee79-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
