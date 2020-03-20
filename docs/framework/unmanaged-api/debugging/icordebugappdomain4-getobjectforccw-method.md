---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179053"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="9ff43-102">Metoda ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="9ff43-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="9ff43-103">Získá spravovaný objekt z ukazatele obálky com volatelné (CCW).</span><span class="sxs-lookup"><span data-stu-id="9ff43-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ff43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ff43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ff43-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="9ff43-106">[v] Com volatelné obálky (CCW) ukazatel.</span><span class="sxs-lookup"><span data-stu-id="9ff43-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="9ff43-107">[out] Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá danému ukazateli CCW.</span><span class="sxs-lookup"><span data-stu-id="9ff43-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ff43-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ff43-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ff43-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ff43-109">Requirements</span></span>  
 <span data-ttu-id="9ff43-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ff43-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff43-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ff43-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ff43-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ff43-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ff43-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff43-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ff43-114">See also</span></span>

- [<span data-ttu-id="9ff43-115">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ff43-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="9ff43-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ff43-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
