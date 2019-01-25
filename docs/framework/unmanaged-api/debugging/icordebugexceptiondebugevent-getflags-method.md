---
title: ICorDebugExceptionDebugEvent::GetFlags – metoda
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739b2412d6b75df0921f778c95cc2fe65fef9b79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636037"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="53818-102">ICorDebugExceptionDebugEvent::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="53818-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="53818-103">Získá příznak, který označuje, zda lze zachytit výjimku.</span><span class="sxs-lookup"><span data-stu-id="53818-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53818-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53818-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53818-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53818-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="53818-106">[out] Ukazatel [cordebugexceptionflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) hodnotu, která určuje, zda lze zachytit výjimku.</span><span class="sxs-lookup"><span data-stu-id="53818-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53818-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53818-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53818-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="53818-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53818-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53818-109">Requirements</span></span>  
 <span data-ttu-id="53818-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53818-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53818-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53818-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53818-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53818-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53818-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53818-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53818-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53818-114">See also</span></span>
- [<span data-ttu-id="53818-115">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53818-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="53818-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="53818-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
