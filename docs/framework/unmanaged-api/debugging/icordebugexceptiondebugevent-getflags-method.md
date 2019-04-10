---
title: ICorDebugExceptionDebugEvent::GetFlags – metoda
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af4c7feb7076eeac6089a3255c7832c17a43469b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208836"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="96c2d-102">ICorDebugExceptionDebugEvent::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="96c2d-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="96c2d-103">Získá příznak, který označuje, zda lze zachytit výjimku.</span><span class="sxs-lookup"><span data-stu-id="96c2d-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96c2d-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96c2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96c2d-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="96c2d-106">[out] Ukazatel [cordebugexceptionflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) hodnotu, která určuje, zda lze zachytit výjimku.</span><span class="sxs-lookup"><span data-stu-id="96c2d-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96c2d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96c2d-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96c2d-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="96c2d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96c2d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96c2d-109">Requirements</span></span>  
 <span data-ttu-id="96c2d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96c2d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96c2d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96c2d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96c2d-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="96c2d-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="96c2d-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="96c2d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96c2d-114">See also</span></span>

- [<span data-ttu-id="96c2d-115">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="96c2d-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="96c2d-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96c2d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
