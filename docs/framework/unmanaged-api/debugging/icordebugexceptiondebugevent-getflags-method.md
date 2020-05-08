---
title: 'ICorDebugExceptionDebugEvent:: GetFlags – metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 5793d939c8497ef842f614048707f69faa8ac568
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976041"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="cf871-102">ICorDebugExceptionDebugEvent:: GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="cf871-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="cf871-103">Získá příznak označující, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="cf871-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf871-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf871-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf871-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf871-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="cf871-106">mimo Ukazatel na hodnotu [CorDebugExceptionFlags –](cordebugexceptionflags-enumeration.md) , která určuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="cf871-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf871-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf871-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf871-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cf871-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf871-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf871-109">Requirements</span></span>  
 <span data-ttu-id="cf871-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf871-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf871-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf871-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf871-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cf871-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf871-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf871-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf871-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf871-114">See also</span></span>

- [<span data-ttu-id="cf871-115">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="cf871-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="cf871-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf871-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
