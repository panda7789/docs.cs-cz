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
ms.workload: dotnet
ms.openlocfilehash: c6e7767ca5467f69dc7f53728bda9daf5f08331c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="2b9a3-102">ICorDebugExceptionDebugEvent::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2b9a3-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="2b9a3-103">Získá příznak označující, zda mohou být zachyceny výjimku.</span><span class="sxs-lookup"><span data-stu-id="2b9a3-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b9a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b9a3-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b9a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b9a3-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="2b9a3-106">[out] Ukazatel [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) hodnotu, která určuje, zda mohou být zachyceny výjimku.</span><span class="sxs-lookup"><span data-stu-id="2b9a3-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b9a3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b9a3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b9a3-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="2b9a3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b9a3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b9a3-109">Requirements</span></span>  
 <span data-ttu-id="2b9a3-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b9a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b9a3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b9a3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b9a3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b9a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b9a3-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b9a3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b9a3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b9a3-114">See Also</span></span>  
 [<span data-ttu-id="2b9a3-115">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b9a3-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="2b9a3-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2b9a3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
