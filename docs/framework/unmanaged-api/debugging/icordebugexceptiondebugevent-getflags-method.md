---
title: ICorDebugExceptionDebugEvent::GetFlags – metoda
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b9c07b010447b4a437febb4b60565111a85c8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415451"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="a85fe-102">ICorDebugExceptionDebugEvent::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="a85fe-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="a85fe-103">Získá příznak označující, zda mohou být zachyceny výjimku.</span><span class="sxs-lookup"><span data-stu-id="a85fe-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a85fe-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a85fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a85fe-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="a85fe-106">[out] Ukazatel [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) hodnotu, která určuje, zda mohou být zachyceny výjimku.</span><span class="sxs-lookup"><span data-stu-id="a85fe-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a85fe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a85fe-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a85fe-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="a85fe-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a85fe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a85fe-109">Requirements</span></span>  
 <span data-ttu-id="a85fe-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a85fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a85fe-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a85fe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a85fe-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a85fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a85fe-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a85fe-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85fe-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a85fe-114">See Also</span></span>  
 [<span data-ttu-id="a85fe-115">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a85fe-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="a85fe-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a85fe-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
