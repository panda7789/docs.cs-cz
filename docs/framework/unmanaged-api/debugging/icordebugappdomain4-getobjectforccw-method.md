---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 8b046eb5926bb9aa4738e8fff8e61b0b7c23a3aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088833"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="638ca-102">Metoda ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="638ca-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="638ca-103">Načte spravovaný objekt z ukazatele na obálku s přívolatelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="638ca-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="638ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="638ca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="638ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="638ca-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="638ca-106">pro Ukazatel na obálku s přívolatelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="638ca-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="638ca-107">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá zadanému ukazateli doleva.</span><span class="sxs-lookup"><span data-stu-id="638ca-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="638ca-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="638ca-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="638ca-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="638ca-109">Requirements</span></span>  
 <span data-ttu-id="638ca-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="638ca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="638ca-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="638ca-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="638ca-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="638ca-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="638ca-113">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="638ca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638ca-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="638ca-114">See also</span></span>

- [<span data-ttu-id="638ca-115">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="638ca-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="638ca-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="638ca-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
