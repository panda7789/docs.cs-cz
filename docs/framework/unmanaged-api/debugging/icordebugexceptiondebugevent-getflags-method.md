---
title: 'ICorDebugExceptionDebugEvent:: GetFlags – metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782921"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="69089-102">ICorDebugExceptionDebugEvent:: GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="69089-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="69089-103">Získá příznak označující, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="69089-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69089-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69089-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69089-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69089-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="69089-106">mimo Ukazatel na hodnotu [CorDebugExceptionFlags –](cordebugexceptionflags-enumeration.md) , která určuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="69089-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69089-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69089-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69089-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="69089-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69089-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69089-109">Requirements</span></span>  
 <span data-ttu-id="69089-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69089-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69089-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69089-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69089-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69089-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69089-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69089-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69089-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69089-114">See also</span></span>

- [<span data-ttu-id="69089-115">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69089-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="69089-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="69089-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
