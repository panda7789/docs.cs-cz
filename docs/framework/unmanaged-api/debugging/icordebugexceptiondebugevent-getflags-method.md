---
title: 'ICorDebugExceptionDebugEvent:: GetFlags – metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 6c330ce5b375daacdf257eda16fd5e34012f5d69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084756"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="c053a-102">ICorDebugExceptionDebugEvent:: GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="c053a-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="c053a-103">Získá příznak označující, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="c053a-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c053a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c053a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c053a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c053a-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="c053a-106">mimo Ukazatel na hodnotu [CorDebugExceptionFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , která určuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="c053a-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c053a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c053a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c053a-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c053a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c053a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c053a-109">Requirements</span></span>  
 <span data-ttu-id="c053a-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c053a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c053a-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c053a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c053a-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c053a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c053a-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c053a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c053a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c053a-114">See also</span></span>

- [<span data-ttu-id="c053a-115">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c053a-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="c053a-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c053a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
